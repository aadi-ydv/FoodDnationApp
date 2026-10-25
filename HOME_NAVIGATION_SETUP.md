Food Donation App - Home Navigation Update

What changed:
- Successful login now opens HomeScreen.
- Successful sign-up now opens HomeScreen.
- HomeScreen is the navigation hub with New Donation, My Saved Donations, My Profile / User Info, and Logout.
- New Donation opens the existing MainActivity2 form.
- Saved Donations opens SavedDonationsActivity.
- My Profile opens UserProfileActivity.
- Logout clears the stored logged-in username and returns to the app's welcome screen.

How to test:
1. Open this project folder in Android Studio.
2. Allow Gradle sync to finish.
3. Run the app on your device/emulator.
4. Sign in or create an account; you should land on the Home screen.
5. Test each of the three navigation buttons.
6. Create a donation, return to Home, then open My Saved Donations.
7. Open My Profile / User Info to see the signed-in account's profile fields.

Database note: SQLite is local to this app installation/device. Do not uninstall or clear app storage if you need to preserve existing local records.
