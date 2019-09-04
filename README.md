# Multi-Apim-IDP-AuthN
External idP Openid connect user authN : To connect API portal with multiple API managers and use idP for user authentication.

As we know that Axway API Portal 7.6.2 SPX does not support SSO with multiple API Managers, so we decided with below approach:

API Managers are configured to use External idP for login policies.

Authenticate with Keycloak Policy: This policy invokes the keycloak idp api call to obtain the access token if the user is successfully authenticated. This policy also calls another policy to check if there is an update on idP which is not in sync with API Manager.
Compare User Info Policy: This policy calls Get User Info policy to get the user information from idP and checks if there is an update on idP which is not in sync with API Manager. If there is any update on idP for user data, same is updated on API manager.
Get idP User Info: This policy fetches the user information from idP using the obtained access token.
