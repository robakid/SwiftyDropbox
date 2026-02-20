DropboxClientsManager Class
===========================

The Swift SDK includes a convenience class, `DropboxClientsManager`, for integrating the different functions of the SDK into one class.

Single Dropbox user case
------------------------

For most apps, it is reasonable to assume that only one Dropbox account (and access token) needs to be managed at a time. In this case, the `DropboxClientsManager` flow looks like this:

*   Call `setupWithAppKey`/`setupWithAppKeyDesktop` (or `setupWithTeamAppKey`/`setupWithTeamAppKeyDesktop`) in integrating app's app delegate
    
*   Client manager determines whether any access tokens are stored -- if any exist, one token is arbitrarily chosen to use
    
*   If no token is found, call `authorizeFromControllerV2` to initiate the OAuth flow
    
*   If auth flow is initiated, call `handleRedirectURL` (or `handleRedirectURLTeam`) in integrating app's app delegate to handle auth redirect back into the app and store the retrieved access token (using a `DropboxOAuthManager` instance)
    
*   Client manager instantiates a `DropboxTransportClient` (if not supplied by the user)
    
*   Client manager instantiates a `DropboxClient` (or `DropboxTeamClient`) with the transport client as a field
    

The `DropboxClient` (or `DropboxTeamClient`) is then used to make all of the desired API calls.

*   On `DropboxClientsManager`, call `unlinkClients` to logout Dropbox user and clear all access tokens
    

Multiple Dropbox user case
--------------------------

For some apps, it is necessary to manage more than one Dropbox account (and access token) at a time. In this case, the `DropboxClientsManager` flow looks like this:

*   Access token uids are managed by the app that is integrating with the SDK for later lookup
    
*   Call `setupWithAppKeyMultiUser`/`setupWithAppKeyMultiUserDesktop` (or `setupWithTeamAppKeyMultiUser`/`setupWithTeamAppKeyMultiUserDesktop`) in integrating app's app delegate
    
    *   _SwiftUI note: You may need to create an Application Delegate if your application doesn't have one._
        
*   Client manager determines whether an access token is stored with the `tokenUid` as a key -- if one exists, this token is chosen to use
    
*   If no token is found, call `authorizeFromControllerV2` to initiate the OAuth flow
    
*   If auth flow is initiated, call `handleRedirectURL` (or `handleRedirectURLTeam`) in integrating app's app delegate to handle auth redirect back into the app and store the retrieved access token (using a `DropboxOAuthManager` instance)
    
    *   _SwiftUI note: You may need to create an Application Delegate if your application doesn't have one._
        
*   At this point, the app that is integrating with the SDK should persistently save the `tokenUid` from the `DropboxAccessToken` field of the `DropboxOAuthResult` object returned from the `handleRedirectURL` (or `handleRedirectURLTeam`) method
    
*   `tokenUid` can be reused either to authorize a new user mid-way through an app's lifecycle via `reauthorizeClient` (or `reauthorizeTeamClient`) or when the app initially launches via `setupWithAppKeyMultiUser`/`setupWithAppKeyMultiUserDesktop` (or `setupWithTeamAppKeyMultiUser`/`setupWithTeamAppKeyMultiUserDesktop`)
    
*   Client manager instantiates a `DropboxTransportClient` (if not supplied by the user)
    
*   Client manager instantiates a `DropboxClient` (or `DropboxTeamClient`) with the transport client as a field
    

The `DropboxClient` (or `DropboxTeamClient`) is then used to make all of the desired API calls.

*   On `DropboxClientsManager` call `resetClients` to logout Dropbox user but not clear any access tokens
    
*   If specific access tokens need to be removed, use the `clearStoredAccessToken` method in `DropboxOAuthManager`