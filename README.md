

# Xenotra - Decentralized Social Login Contract (Clarity)

This smart contract provides a decentralized user registration and profile management system on the Stacks blockchain. It allows users to register with a unique username and email, manage their profile image, and update or delete their profile, while ensuring username uniqueness across the system.

---

## ✨ Features

* ✅ **User Registration**: Users can register with a unique username and email.
* 🔐 **Decentralized Identity**: Each user is identified by their wallet address (`principal`).
* 🔄 **Profile Updates**: Users can update their username and email.
* 🖼️ **Profile Image Management**: Users can set or clear a profile image.
* 🗑️ **Account Deletion**: Users can delete their profile.
* 🔍 **Username Availability Check**: Check if a username is available.
* 📈 **User Analytics**: Read-only access to total user count and profile details.

---

## 📚 Contract Details

### 🗺️ Maps

* `users (principal => { username, email, profile-image })`: Stores user data.
* `taken-usernames (string-ascii 50 => bool)`: Tracks already registered usernames.

### 📦 Data Variables

* `user-count (uint)`: Tracks total registered users.

---

## 🔐 Error Constants

| Constant                | Message                                                                       |
| ----------------------- | ----------------------------------------------------------------------------- |
| `ERR-USER-EXISTS`       | "User already exists"                                                         |
| `ERR-USER-NOT-FOUND`    | "User not found"                                                              |
| `ERR-INVALID-USERNAME`  | "Invalid username: must be between 3 and 50 characters"                       |
| `ERR-INVALID-EMAIL`     | "Invalid email: must be between 5 and 100 characters and contain '@' and '.'" |
| `ERR-INVALID-IMAGE-URL` | "Invalid image URL: must be a valid URL string"                               |
| `ERR-USERNAME-TAKEN`    | "Username is already taken"                                                   |

---

## 🔧 Public Functions

### `register-user (username, email)`

Registers a new user with a unique username and email. Validates input and checks for uniqueness.

---

### `update-profile (new-username, new-email)`

Allows a user to update their username and/or email. Will check for username availability if changed.

---

### `set-profile-image (image-url)`

Sets or updates the profile image URL for the user.

---

### `clear-profile-image ()`

Removes the user's profile image.

---

### `delete-profile ()`

Deletes the user's profile and frees up the username.

---

## 🔍 Read-Only Functions

### `get-user-info (user: principal)`

Returns user information if the profile exists.

---

### `get-user-count ()`

Returns the total number of registered users.

---

### `is-user-registered (user: principal)`

Returns `true` if the user has a registered profile.

---

### `is-username-available (username: string-ascii 50)`

Checks if a given username is available for registration.

---

## 🔒 Private Functions

### `validate-username (username)`

Ensures username length is between 3 and 50 characters.

---

### `validate-email (email)`

Checks email length and ensures it contains both `@` and `.` characters.

---

### `check-username-match (username, user, found)`

Helper function to compare usernames (used for optimization in future cases).

---

## 🏁 Deployment Instructions

1. Clone the repository and navigate to your Clarity project directory.
2. Deploy the contract using Clarinet or directly through Stacks CLI.

```bash
clarinet contract publish social-login
```

---

## 🧪 Testing Recommendations

Use Clarinet to write unit tests for the following:

* Registration success/failure (duplicate, invalid input).
* Username availability.
* Profile image update and clear.
* Profile update with changed username.
* Profile deletion and re-registration.
* Read-only data consistency.

---

## 🔄 Future Improvements

* Add support for social identity proofs (e.g., Twitter, GitHub).
* Add email verification via external oracle.
* Add optional display name and bio fields.
* Rate-limit registration attempts.
* Add admin interface to manage users (e.g., for reporting spam).

---

## 📜 License

MIT License – use freely with attribution.

---
