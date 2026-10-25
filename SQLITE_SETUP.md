# SQLite integration notes — Food Donation App

## What changed
- Added `DatabaseHelper.java` using Android `SQLiteOpenHelper`.
- Added a `users` table and a `donations` table.
- Registration now saves user profile details to SQLite and rejects duplicate usernames/emails.
- Passwords are stored as salted PBKDF2 hashes rather than plain text.
- Login now checks SQLite instead of the hardcoded `User123` / `mypassword` credentials.
- Successful registration and login set the current username in `UserPrefs` for the donation form.
- The existing donation form saves its fields to SQLite when Post is pressed.
- Signup now opens the donation form (`MainActivity2`) so registration and login follow the same flow.
- Existing layouts were kept intact.

## Database tables
- `users`: name, date of birth, phone, email, username, password hash and salt.
- `donations`: donor username, name, description, type, size, transportation, pickup date/time, location, status and creation timestamp.

## Open and test
1. Open the `FoodDonationApp` folder in Android Studio and let Gradle sync.
2. Run the app on an emulator or Android device.
3. Create a new account with a unique email and username and a password of at least 6 characters.
4. The app should open the donation form. Fill in the donation name, location, type, size, transportation and date/time, then press **Post**.
5. Close and reopen the app, log in with that account, and post another donation to verify login uses the saved SQLite account.
6. Duplicate usernames/emails should be rejected.

## Important limitation
SQLite is local to one installation of the app. This version stores and retrieves data on the same device; it does not synchronize donations across different users' phones. A separate list/history screen is not present in the original project, so the saved donation records are not yet shown in a list UI. `DatabaseHelper.getDonationsForUser()` is included to support adding that screen next.

## Build note
A build could not be verified in this environment because the Gradle wrapper needs to download Gradle 9.3.1, and network access to `services.gradle.org` was unavailable. Please run **Build > Make Project** in Android Studio after opening the project and share any errors if they appear.
