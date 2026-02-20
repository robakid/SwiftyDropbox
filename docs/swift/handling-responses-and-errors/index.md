Handling Responses and Errors
=============================

Dropbox API v2 deals largely with two data types: **structs** and **unions**. Broadly speaking, most route **arguments** are struct types and most route **errors** are union types.

**Note:** In this context, "structs" and "unions" are terms specific to the Dropbox API, and not to any of the languages that are used to query the API, so you should avoid thinking of them in terms of their Swift definitions.

**Struct types** are "traditional" object types, that is, composite types made up of a collection of one or more instance fields. All public instance fields are accessible at runtime, regardless of runtime state.

**Union types**, on the other hand, represent a single value that can take on multiple value types, depending on state. We capture all of these different type scenarios under one "union object", but that object will exist only as one type at runtime. Each union state type, or **tag**, may have an associated value (if it doesn't, the union state type is said to be **void**). Associated value types can either be primitives, structs or unions. Although the Swift SDK represents union types as objects with multiple instance fields, at most one instance field is accessible at runtime, depending on the tag state of the union.

For example, the [/delete](https://www.dropbox.com/developers/documentation/http/documentation#files-delete) endpoint returns an error, `Files.DeleteError`, which is a union type. The `Files.DeleteError` union can take on two different tag states: `path_lookup` (if there is a problem looking up the path) or `path_write` (if there is a problem writing -- or in this case deleting -- to the path). Here, both tag states have non-void associated values (of types `Files.LookupError` and `Files.WriteError`, respectively).

In this way, one union object is able to capture a multitude of scenarios, each of which has their own value type.

To properly handle union types, you should pass each union through a switch statement, and check each possible tag state associated with the union. Once you have determined the current tag state of the union, you can then access the value associated with that tag state (provided there exists an associated value type, i.e., it's not **void**).

Route-specific errors
---------------------

<CodeBlock attributes='{"isFitToPage":true,"style":{},"lang":"swift","label":"Plain text"}'>
  <CodeLine>client.files.deleteV2(path: "/test/path/in/Dropbox/account").response { response, error in</CodeLine>
  <CodeLine>    if let response = response {</CodeLine>
  <CodeLine>        print(response)</CodeLine>
  <CodeLine>    } else if let error = error {</CodeLine>
  <CodeLine>        switch error as CallError {</CodeLine>
  <CodeLine>        case .routeError(let boxed, let userMessage, let errorSummary, let requestId):</CodeLine>
  <CodeLine>            print("RouteError[\(requestId)]:")</CodeLine>
  <CodeLine>            switch boxed.unboxed as Files.DeleteError {</CodeLine>
  <CodeLine>            case .pathLookup(let lookupError):</CodeLine>
  <CodeLine>                switch lookupError {</CodeLine>
  <CodeLine>                case .notFound:</CodeLine>
  <CodeLine>                    print("There is nothing at the given path.")</CodeLine>
  <CodeLine>                case .notFile:</CodeLine>
  <CodeLine>                    print("We were expecting a file, but the given path refers to something that isn't a file.")</CodeLine>
  <CodeLine>                case .notFolder:</CodeLine>
  <CodeLine>                    print("We were expecting a folder, but the given path refers to something that isn't a folder.")</CodeLine>
  <CodeLine>                case .restrictedContent:</CodeLine>
  <CodeLine>                    print("The file cannot be transferred because the content is restricted...")</CodeLine>
  <CodeLine>                case .malformedPath(let malformedPath):</CodeLine>
  <CodeLine>                    print("Malformed path: \(malformedPath)")</CodeLine>
  <CodeLine>                case .other:</CodeLine>
  <CodeLine>                    print("Unknown")</CodeLine>
  <CodeLine>                }</CodeLine>
  <CodeLine>            case .pathWrite(let writeError):</CodeLine>
  <CodeLine>                print("WriteError: \(writeError)")</CodeLine>
  <CodeLine>                // you can handle each `WriteError` case like the `DeleteError` cases above</CodeLine>
  <CodeLine>            case .tooManyWriteOperations:</CodeLine>
  <CodeLine>                print("Another write operation occurring at the same time prevented this from succeeding.")</CodeLine>
  <CodeLine>            case .tooManyFiles:</CodeLine>
  <CodeLine>                print("There are too many files to delete.")</CodeLine>
  <CodeLine>            case .other:</CodeLine>
  <CodeLine>                print("Unknown")</CodeLine>
  <CodeLine>            }</CodeLine>
  <CodeLine>        case .internalServerError(let code, let message, let requestId):</CodeLine>
  <CodeLine>            ....</CodeLine>
  <CodeLine>            ....</CodeLine>
  <CodeLine>            // a not route-specific error occurred</CodeLine>
  <CodeLine>        ....</CodeLine>
  <CodeLine>        ....</CodeLine>
  <CodeLine>        ....</CodeLine>
  <CodeLine>        }</CodeLine>
  <CodeLine>    }</CodeLine>
  <CodeLine>}</CodeLine>
</CodeBlock>

Generic network request errors
------------------------------

In the case of a network error, errors are either specific to the endpoint (as shown above) or more generic errors.

To determine if an error is route-specific or not, the error object should be cast as a `CallError`, and depending on the type of error, handled in the appropriate switch statement.

<CodeBlock attributes='{"isFitToPage":true,"style":{},"lang":"swift","label":"Plain text"}'>
  <CodeLine>client.files.deleteV2(path: "/test/path/in/Dropbox/account").response { response, error in</CodeLine>
  <CodeLine>    if let response = response {</CodeLine>
  <CodeLine>        print(response)</CodeLine>
  <CodeLine>    } else if let error = error {</CodeLine>
  <CodeLine>        switch error as CallError {</CodeLine>
  <CodeLine>        case .routeError(let boxed, let userMessage, let errorSummary, let requestId):</CodeLine>
  <CodeLine>            // a route-specific error occurred</CodeLine>
  <CodeLine>            // see handling above</CodeLine>
  <CodeLine>            ....</CodeLine>
  <CodeLine>            ....</CodeLine>
  <CodeLine>            ....</CodeLine>
  <CodeLine>        case .internalServerError(let code, let message, let requestId):</CodeLine>
  <CodeLine>            print("InternalServerError[\(requestId)]: \(code): \(message)")</CodeLine>
  <CodeLine>        case .badInputError(let message, let requestId):</CodeLine>
  <CodeLine>            print("BadInputError[\(requestId)]: \(message)")</CodeLine>
  <CodeLine>        case .authError(let authError, let userMessage, let errorSummary, let requestId):</CodeLine>
  <CodeLine>            print("AuthError[\(requestId)]: \(userMessage) \(errorSummary) \(authError)")</CodeLine>
  <CodeLine>        case .accessError(let accessError, let userMessage, let errorSummary, let requestId):</CodeLine>
  <CodeLine>            print("AccessError[\(requestId)]: \(userMessage) \(errorSummary) \(accessError)")</CodeLine>
  <CodeLine>        case .rateLimitError(let rateLimitError, let userMessage, let errorSummary, let requestId):</CodeLine>
  <CodeLine>            print("RateLimitError[\(requestId)]: \(userMessage) \(errorSummary) \(rateLimitError)")</CodeLine>
  <CodeLine>        case .httpError(let code, let message, let requestId):</CodeLine>
  <CodeLine>            print("HTTPError[\(requestId)]: \(code): \(message)")</CodeLine>
  <CodeLine>        case .clientError(let error):</CodeLine>
  <CodeLine>            print("ClientError: \(error)")</CodeLine>
  <CodeLine>        }</CodeLine>
  <CodeLine>    }</CodeLine>
  <CodeLine>}</CodeLine>
</CodeBlock>

Response handling edge cases
----------------------------

Some routes return union types as result types, so you should be prepared to handle these results in the same way that you handle union route errors. Please consult the [documentation](https://www.dropbox.com/developers/documentation/http/documentation) for each endpoint that you use to ensure you are properly handling the route's response type.

A few routes return result types that are **datatypes with subtypes**, that is, structs that can take on multiple state types like unions.

For example, the [/delete](https://www.dropbox.com/developers/documentation/http/documentation#files-delete) endpoint returns a generic `Metadata` type, which can exist either as a `FileMetadata` struct, a `FolderMetadata` struct, or a `DeletedMetadata` struct. To determine at runtime which subtype the `Metadata` type exists as, pass the object through a switch statement, and check for each possible class, with the result casted accordingly. See below:

<CodeBlock attributes='{"isFitToPage":true,"style":{},"lang":"swift","label":"Plain text"}'>
  <CodeLine>client.files.deleteV2(path: "/test/path/in/Dropbox/account").response { response, error in</CodeLine>
  <CodeLine>    if let response = response {</CodeLine>
  <CodeLine>        switch response {</CodeLine>
  <CodeLine>        case let fileMetadata as Files.FileMetadata:</CodeLine>
  <CodeLine>            print("File metadata: \(fileMetadata)")</CodeLine>
  <CodeLine>        case let folderMetadata as Files.FolderMetadata:</CodeLine>
  <CodeLine>            print("Folder metadata: \(folderMetadata)")</CodeLine>
  <CodeLine>        case let deletedMetadata as Files.DeletedMetadata:</CodeLine>
  <CodeLine>            print("Deleted entity's metadata: \(deletedMetadata)")</CodeLine>
  <CodeLine>        }</CodeLine>
  <CodeLine>    } else if let error = error {</CodeLine>
  <CodeLine>        switch error as CallError {</CodeLine>
  <CodeLine>        case .routeError(let boxed, let userMessage, let errorSummary, let requestId):</CodeLine>
  <CodeLine>            // a route-specific error occurred</CodeLine>
  <CodeLine>            // see handling above</CodeLine>
  <CodeLine>        case .internalServerError(let code, let message, let requestId):</CodeLine>
  <CodeLine>            ....</CodeLine>
  <CodeLine>            ....</CodeLine>
  <CodeLine>            // a not route-specific error occurred</CodeLine>
  <CodeLine>            // see handling above</CodeLine>
  <CodeLine>        ....</CodeLine>
  <CodeLine>        ....</CodeLine>
  <CodeLine>        ....</CodeLine>
  <CodeLine>        }</CodeLine>
  <CodeLine>    }</CodeLine>
  <CodeLine>}</CodeLine>
</CodeBlock>

This `Metadata` object is known as a **datatype with subtypes** in the API v2 documentation.

Datatypes with subtypes are a way of combining structs and unions. Datatypes with subtypes are struct objects that contain a tag, which specifies which subtype the object exists as at runtime. The reason for this construct, as with unions, is so multiple scenarios can be captured with one object.

In the above example, the `Metadata` type can exist as `FileMetadata`, `FolderMetadata` or `DeleteMetadata`. Each of these types have common instance fields like "name" (the name for the file, folder or deleted type), but also instance fields that are specific to the particular subtype. In order to leverage inheritance, a common supertype called `Metadata` captures all of the common instance fields, but also has a tag instance field, which specifies which subtype the object currently exists as.

In this way, datatypes with subtypes are a hybrid of structs and unions. Only a few routes return result types like this.