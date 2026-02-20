# Async Data Types

Data types for the async namespace. These types are used for methods that launch asynchronous jobs.

---

## LaunchResultBase

Result returned by methods that launch an asynchronous job. A method who may either launch an asynchronous job, or complete the request synchronously, can use this union by extending it, and adding a 'complete' field with the type of the synchronous response. See `LaunchEmptyResult` for an example.

**Cases:**
- `asyncJobId(String)` - This response indicates that the processing is asynchronous. The string is an id that can be used to obtain the status of the asynchronous job.

---

## LaunchEmptyResult

Result returned by methods that may either launch an asynchronous job or complete synchronously. Upon synchronous completion of the job, no additional information is returned.

**Cases:**
- `asyncJobId(String)` - This response indicates that the processing is asynchronous. The string is an id that can be used to obtain the status of the asynchronous job.
- `complete` - The job finished synchronously and successfully.

---

## PollArg

Arguments for methods that poll the status of an asynchronous job.

**Properties:**
- `asyncJobId: String` - Id of the asynchronous job. This is the value of a response returned from the method that launched the job.

---

## PollResultBase

Result returned by methods that poll for the status of an asynchronous job. Unions that extend this union should add a 'complete' field with a type of the information returned upon job completion. See `PollEmptyResult` for an example.

**Cases:**
- `inProgress` - The asynchronous job is still in progress.

---

## PollEmptyResult

Result returned by methods that poll for the status of an asynchronous job. Upon completion of the job, no additional information is returned.

**Cases:**
- `inProgress` - The asynchronous job is still in progress.
- `complete` - The asynchronous job has completed successfully.

---

## PollError

Error returned by methods for polling the status of asynchronous job.

**Cases:**
- `invalidAsyncJobId` - The job ID is invalid.
- `internalError` - Something went wrong with the job on Dropbox's end. You'll need to verify that the action you were taking succeeded, and if not, try again. This should happen very rarely.
- `other` - An unspecified error.
