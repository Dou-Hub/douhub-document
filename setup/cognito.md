## Create User Pool

1. Name: appname--user-pool-dev, Region :us-east-1

2. Username - Users can use a username and optionally multiple alternatives to sign up and sign in.
[X] Also allow sign in with preferred username (a username that your users can change)
[X] (Recommended) Enable case insensitivity for username input

3. Which standard attributes are required?
None of them

4. Password Policy
Minimum length: 8
[X] Require numbers
[X] Require special character
[X] Require uppercase letters
[X] Require lowercase letters 

5. Do you want to allow users to sign themselves up?
[X] Only allow administrators to create users 

6. Do you want to enable Multi-Factor Authentication (MFA)?
[X] Off

7. How will a user be able to recover their account?
[X] None – users will have to contact an administrator to reset their passwords

8. Which attributes do you want to verify?
[X] No verification

9. Skip Message Customization !!!

10. Do you want to remember your user's devices?
[X] No

11. Skip App Clients (will do after creating the pool)

12. Skip Triggers


## Create App Clients
### clientName.app (e.g. appname.app)
!!!NOTE!!!
1. DO NOT SELECT "Generate client secret"
2. DO NOT SELECT "Enable token revocation"

[X] Enable lambda trigger based custom authentication (ALLOW_CUSTOM_AUTH)
[X] Enable SRP (secure remote password) protocol based authentication (ALLOW_USER_SRP_AUTH)
[X] Enable refresh token based authentication (ALLOW_REFRESH_TOKEN_AUTH)

Prevent User Existence Errors
[X] Legacy

### clientName.lambda (e.g. appname.lambda)
!!!NOTE!!!
1. DO NOT SELECT "Generate client secret"
2. DO NOT SELECT "Enable token revocation"

[X] Enable username password auth for admin APIs for authentication (ALLOW_ADMIN_USER_PASSWORD_AUTH)
[X] Enable lambda trigger based custom authentication (ALLOW_CUSTOM_AUTH)
[X] Enable username password based authentication (ALLOW_USER_PASSWORD_AUTH)
[X] Enable SRP (secure remote password) protocol based authentication (ALLOW_USER_SRP_AUTH)
[X] Enable refresh token based authentication (ALLOW_REFRESH_TOKEN_AUTH)

Prevent User Existence Errors
[X] Legacy