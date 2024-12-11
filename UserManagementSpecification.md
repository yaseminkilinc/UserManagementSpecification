# User Management Screen Specification

## 1. Requirements
- **Purpose**: This screen allows administrators to manage users within the system.
  - View a list of all users.
  - Add new users.
  - Filter users based on their enabled/disabled status.
- **Target Users**: The screen is accessible only by users with `Admin` or `SuperAdmin` roles.

## 2. UI Components

### 2.1 User List
- **Description**: Displays all users in a tabular format.
- **Columns**:
  - **ID**: Unique identifier for each user.
  - **User Name**: The username of the user.
  - **Email**: The email address of the user.
  - **Enabled**: Displays `true` if the user is active and `false` if disabled.
- **Features**:
  - **Sorting**: Each column is sortable by clicking on the column header.
  - **Filtering**: Users can toggle the "Hide Disabled User" checkbox to show only active users.

### 2.2 New User Form
- **Description**: Allows administrators to add a new user.
- **Fields**:
  - **Username**: Text input. (Mandatory)
  - **Display Name**: Text input. (Optional)
  - **Phone**: Text input. (Optional)
  - **Email**: Text input. (Mandatory)
  - **User Roles**: Dropdown menu with the following options:
    - Guest
    - Admin
    - SuperAdmin
  - **Enabled**: Checkbox to indicate whether the user is active.
- **Buttons**:
  - **Save User**: Submits the form to create a new user.

## 3. Behavior

### 3.1 User List
- **Initial State**: Displays all users (enabled and disabled).
- **Sorting**: Clicking a column header sorts the list by that column.
- **Filtering**:
  - When "Hide Disabled User" is checked, the table updates to show only active users.

### 3.2 New User Form
- **Validation**:
  - The "Username" and "Email" fields are mandatory. An error message is displayed if they are left blank.
  - The "Email" field must contain a valid email format.
- **Submission**:
  - Clicking "Save User" validates the form inputs.
  - If validation succeeds, the new user is added to the user list and the form is reset.
  - If validation fails, error messages are shown next to the invalid fields.

## 4. Initial State
- The user list displays all users, sorted by `ID` in ascending order.
- The "New User" form is empty and ready for input.
- The "Hide Disabled User" checkbox is unchecked by default.

## 5. Error Handling
- **Invalid Input**:
  - If mandatory fields are missing, an error message is displayed: "This field is required."
  - If the email format is invalid, an error message is displayed: "Please enter a valid email address."
- **Backend Errors**:
  - If saving a user fails due to server issues, an error message is displayed: "An error occurred while saving. Please try again."

## 6. Notes for Developers
- **User List Table**:
  - The table should support dynamic updates to reflect changes (e.g., after adding a new user).
  - Sorting and filtering should work on the client-side for performance.
- **Form Submission**:
  - Ensure the form is connected to the backend API for creating users.
  - Validate form inputs on both client and server sides.
- **Styling**:
  - Follow the provided design system for consistent UI/UX.

## 7. Example API Endpoints
- **Get Users**:
  - `GET /api/users`
  - Response: List of users.
- **Create User**:
  - `POST /api/users`
  - Request Body:
    ```json
    {
      "username": "exampleuser",
      "displayName": "Example User",
      "phone": "123-456-7890",
      "email": "example@domain.com",
      "roles": ["Admin"],
      "enabled": true
    }
    ```
  - Response: Status of the operation.

---


