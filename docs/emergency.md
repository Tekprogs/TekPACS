# Emergency administrator (command line)

Get back into the console when nobody can sign in as an administrator, using the DicomServer.Setup utility on the server.

### 1. Open an administrator command prompt on the server

1.  Sign in to the server itself (console or Remote Desktop) with an account that is a local administrator of the server.
2.  Domain admin rights are not needed.
3.  Open Command Prompt or PowerShell as administrator.
4.  Go to the Setup folder: `cd "C:\Program Files\Tekprogs\DICOM Server\Setup"`.

### 2. Add an emergency administrator

1.  Run `DicomServer.Setup add-admin DOMAIN\user` (or `COMPUTER\user` for a local account).
2.  The account is added to the 'Administrator accounts' list in the configuration straight away.
3.  It takes effect at that account's next sign-in, so sign out and back in if the account is already signed in.

### 3. Check what the server thinks of an account

1.  Run `DicomServer.Setup test-login` and enter the user name and password when asked.
2.  It signs in exactly like the web console does and prints the account's groups and the role it resolves to (Administrator, User or no access).
3.  Use it to see why a sign-in is refused.

### 4. Fix a setting that locks you out

1.  Run `DicomServer.Setup show` to print the configuration.
2.  Change a value with `DicomServer.Setup set Key=Value`, for example `set Web.HttpsPort=8443` or `set Dicom.AeTitle=PACS1`.
3.  Then run `DicomServer.Setup restart` so the service picks it up.

### 5. Other commands

1.  `DicomServer.Setup` on its own starts the setup wizard.
2.  `cert new` makes a fresh self-signed certificate for TLS / HTTPS.
3.  `apply-memory` writes the garbage-collector settings to the service environment.
4.  `restore-snapshot "<backup target>"` rebuilds the server from a backup. See [Disaster recovery](disaster-recovery.md).
5.  Once you are back in, tidy up on the Web & login page under Settings and remove the emergency account if it is no longer needed.

[Keeping the server healthy](health.md) · [All guides](index.md)
