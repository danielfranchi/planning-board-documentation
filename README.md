# Planning Board Documentation

![CoffeeScript Dark](https://raw.githubusercontent.com/tandpfun/skill-icons/main/icons/CoffeeScript-Dark.svg)

## Overview

Planning Board is an application developed with React and TypeScript, created with Vite. It is designed to help teams plan and track their tasks efficiently.

## Technologies Used

This project uses several technologies and libraries, including:

- [React](https://reactjs.org/): A JavaScript library for building user interfaces.
- [TypeScript](https://www.typescriptlang.org/): A superset of JavaScript that adds static types.
- [Vite](https://vitejs.dev/): A build tool that provides a faster development environment and more efficient production optimization.
- [Tailwind CSS](https://tailwindcss.com/): A utility-first CSS library for building custom user interfaces.
- [Material UI](https://mui.com/): A React component library for faster and easier web page development.

Each component and functionality of the application will be detailed in the following sections.

# Pages and Components

[Form](#Form)

## main.tsx

The `main.tsx` file is the entry point of the application. It sets up the React application and renders the root component.

## Imports

The file starts by importing several necessary libraries and components:

- `react`: The React library is imported to create the root component.
- `react-dom/client`: Used for rendering the root component into the DOM.
- `./App.tsx`: The main App component of the application.
- `./App.css`: The main CSS file for the application.
- `react-redux`: Used to provide the Redux store to the rest of the application.
- `./store/store.ts`: The Redux store of the application.

## Rendering the App Component

The `ReactDOM.createRoot` function is used to create a root React component at the DOM element with the id of 'root'. The `Provider` component from `react-redux` is used to provide the Redux store to the rest of the application. The `App` component is rendered inside the `Provider` component.

This setup allows the entire application to have access to the Redux store, enabling state management across all components.


## App.tsx

The `App.tsx` file is the entry point of the application. It sets up the overall structure of the application and includes the main components and routes.

## Imports

The file starts by importing several necessary libraries and components:

- `react-router-dom`: Used for setting up the routes of the application.
- `@mui/x-date-pickers` and `@mui/x-date-pickers/AdapterDayjs`: Used to provide a DatePicker with the Dayjs adapter.
- `react`: The React library is imported to use the `useEffect` hook.
- `react-redux`: Used to access the application state and dispatch actions.
- `./service/api`: The API service that defines how HTTP requests are made.
- `./store/storeData/action` and `./store/storeData/types`: Actions and types related to managing the application state.
- `./components/Header`: The Header component that is displayed on all pages.
- `./routes/routes`: The routes of the application.
- `./components/Table`: The Table component that is used to display data.

<br /><br />

## App Component

The App component is a function that sets up the main structure of the application. It uses the `useEffect` hook to fetch data when the component is mounted. The fetched data is then passed to the Table component.

The App component returns a JSX that sets up the structure of the application. It includes the Header component, the application routes, and the Table component.

## Routes

The application routes are set up using the `Routes` component from `react-router-dom`. Currently, there is only one route set up for the root ("/") of the application.

## DatePicker

The DatePicker is provided by the `LocalizationProvider` from `@mui/x-date-pickers` with the `AdapterDayjs`. This allows the DatePicker to use the Dayjs library for date manipulation.

<br /><br />

## Form {Form}

The Form page is responsible for displaying and managing a data entry form. This form allows users to add new items or edit existing items in the data table.

## Imports

- `useState, useEffect` from "react": Used to manage states and effects in the component.
- `useForm` from "react-hook-form": For handling the logic of the form and its validations.
- `useDispatch` from "react-redux": To dispatch actions to the Redux store.
- `useNavigate, useLocation` from "react-router-dom": To navigate and access information about the location.
- `Input` from "../components/Input": Input component for the form.
- `Button` from "../components/Button": Button component for interaction in the form.
- `DatePicker` from "../components/DatePicker": Calendar component for selecting a date.
- `add, editData` from "../store/storeData/action": Actions to add or edit data in the application.
- `api` from "../service/api": API service for making HTTP requests.
- `Dayjs` from "dayjs": Library for date manipulation.
- `Box` from "@mui/material": Material-UI layout component.

## Interfaces

- `FormData`: Interface defining the structure of the form data.

## Form Component

The Form component is a function responsible for configuring and managing the form. It uses various hooks for state management and effects. The form allows users to add new items or edit existing items in the data table.

## State Variables

- `selectedDate`: Stores the selected date in the DatePicker.
- `formSubmitted`: Indicates whether the form has been submitted.
- `formDataFromLocation`: Data received from the location.

## Methods

- `onSubmit(data: FormData)`: Function that processes the form upon submission. It adds or edits data in the table based on the selected action.

## Validation

The form includes validations in the date field (DatePicker) and input fields. The form cannot be submitted if the fields are empty or if the date is not selected, ensuring data integrity.

## Component Structure

The Form component returns a form with fields for entering title, description, date, location, and participants. It then displays a button to submit or edit the data.

The CSS class `bg-[#FDF5E6] shadow-lg p-8 rounded-md` is applied to the form for styling.

## Usage

To add a new item, fill in all required fields and select a valid date in the DatePicker before clicking "Submit". To edit an existing item, the fields will be pre-filled with existing data. Modify the desired fields and click "Edit" to save the changes.

<br /><br />

## Table.tsx

The `Table` component is responsible for rendering data received from `Form.tsx` and displaying it on the screen. It also provides buttons for editing, deleting, and generating PDFs based on the data entries.

## Imports

- `useState` from "react": Used to manage state within the component.
- `useDispatch` from "react-redux": Enables dispatching actions to the Redux store.
- `useNavigate` from "react-router-dom": Facilitates navigation within the application.
- `Modal` from "./Modal": Component for displaying modals.
- `PdfDocument` from "./PdfDocument": Component for rendering PDF documents.
- `deleteData` from "../store/storeData/action": Action for deleting data.
- `api` from "../service/api": Service for making API requests.
- `pdf` from "@react-pdf/renderer": Library for generating PDFs.
- `FaEdit, FaFilePdf, FaTrashAlt` from "react-icons/fa": Icons for edit, PDF generation, and deletion actions.

## Interface

- `Data`: Interface defining the structure of the data entries.

## Functionality

- `edit(id: string)`: Fetches data associated with a specific ID for editing purposes.
- `deleteItem(id: string)`: Deletes a data entry based on the provided ID.
- `handleDelete(id: string)`: Sets the selected item ID for deletion and opens a modal for confirmation.
- `handleConfirm()`: Confirms the deletion of the selected item.
- `generatePdf(data: Data)`: Generates a PDF document containing the provided data.

## Component Structure

- The `Table` component displays a table containing data entries with columns for title, description, date, location, participants, and options.
- Each row displays details of a data entry along with buttons for editing, deleting, and generating a PDF.
- The CSS classes `px`, `py`, and `text` are used for styling the table and its contents.

## Usage

- Clicking the edit button (`FaEdit`) triggers the `edit` function, allowing users to modify the selected data entry.
- Clicking the delete button (`FaTrashAlt`) opens a modal for confirming the deletion of the selected data entry.
- Clicking the PDF button (`FaFilePdf`) generates a PDF document containing the details of the selected data entry.

This component serves as a visual representation of the data collected from `Form.tsx`, providing essential functionalities for managing and interacting with the data entries displayed on the screen.

<br /><br />

## Button.tsx

The `Button` component is designed to render a button element with customizable text, type, and styling options. It includes functionality to handle click events and trigger navigation to a specific route upon clicking the button.

## Imports

- `useNavigate` from "react-router-dom": Used for handling navigation within the application.

## Interface

- `ButtonText`: Interface defining the properties of the button:
  - `text`: Text displayed on the button.
  - `type` (optional): Type of the button (submit, reset, or button).
  - `classButton` (optional): Custom CSS class for styling the button.

## Functionality

- `handleClick(event: React.MouseEvent<HTMLElement>)`: Function that triggers navigation to a specific route (`/form`) when the button's text is "Add vacation plan".

## Component Structure

- The `Button` component renders a button element with the provided text and optional styling class.
- If no custom CSS class is provided, the button defaults to a specific style defined using tailwind CSS classes.
- The button's onClick event is linked to the `handleClick` function, enabling navigation to the "/form" route when the button text matches "Add vacation plan".

## Usage

- The `Button` component is versatile and can be used to create buttons with different text content and functionalities.
- By specifying the `type` property, the button can behave as a regular button, a submit button, or a reset button based on the need.
- Styling can be customized by adding a custom CSS class to the `classButton` property or using the default styling provided within the component.

This component offers a simple and efficient way to create buttons with dynamic text and behaviors, enhancing user interaction and navigation within the application.

<br /><br />

## Header.tsx

The `Header` component represents the header section of the application, containing a title and a button for adding a new vacation plan. It includes functionality to navigate to the root path ("/") upon clicking the header title.

## Imports

- `Button` from "./Button": Imports the `Button` component for rendering buttons.
- `useNavigate` from "react-router-dom": Utilized for handling navigation within the application.

## Functionality

- `redirect()`: Function that triggers navigation to the root path ("/") when called.

## Component Structure

- The `Header` component consists of a header element with a background color of "#435d7d" and white text color.
- It includes a title "Vacation Plan" and a clickable header section that redirects users to the home page ("/") when clicked.
- The header is designed using Flexbox to center items and provide a responsive layout.

## Usage

- The `Header` component serves as the top section of the application, providing users with a navigation link and an option to add a new vacation plan.
- Clicking the header title triggers navigation to the home page, allowing users to easily return to the main content area.
- The "Add vacation plan" button rendered within the header allows users to initiate the process of adding a new vacation plan entry.

This component plays a crucial role in the overall user interface by offering a clear navigation option and a convenient way to add new vacation plans, enhancing the user experience within the application.

<br /><br />

## Input.tsx

The `Input` component is used to render a text input field within a form. It takes input properties such as the input field name and registration function provided by `react-hook-form`.

## Imports
- `UseFormRegister` from "react-hook-form": Used for registering an input field in a form.
- `TextField` from "@mui/material": Component from Material-UI used to render text input fields.

## Interface
- `InputProps`: Interface defining the properties required for the `Input` component:
- `name`: A string representing the name of the input field.
- `register`: A function from `react-hook-form` used for registering the input field.

## Functionality
- `capitalizeFirstLetter(string: string)`: Function that capitalizes the first letter of a given string.
- The `Input` component renders a text input field using Material-UI's `TextField`.
- It registers the input field using the name and required validation provided by `react-hook-form`.
- The input field label displays the capitalized version of the input field name.

## Component Structure
- The `Input` component renders a text input field with the label capitalized and taking up the full width.
- The `TextField` component from Material-UI is utilized for styling and functionalities of the text input field.
- The `register` function is spread into the `TextField` component to handle form registration and validation.

## Usage
- The `Input` component is designed to be reusable across forms within the application.
- By passing the input field name and the `register` function from `react-hook-form`, the component facilitates easy integration of form input fields.
- It enforces required validation on the input field and displays a user-friendly label with the first letter capitalized.

This component simplifies the process of creating text input fields in forms while maintaining consistency and providing essential validation functionality for a better user experience.

<br /><br />

## Modal.tsx

The `Modal` component is used to display a modal dialog box with options for confirmation or cancellation. It provides a message asking the user to confirm an action and includes buttons for both confirming and canceling the action.

## Interface
- `ModalProps`: Interface defining the properties required by the `Modal` component:
  - `isOpen`: A boolean indicating whether the modal is open or closed.
  - `onClose`: A function to handle the modal close event.
  - `onConfirm`: A function to handle the confirmation action.

## Functionality
- If the modal `isOpen` prop is `false`, the component returns `null`, effectively hiding the modal.
- When the modal is open, it displays a semi-transparent background overlay with the main content centered on the screen.
- The main content of the modal includes a message asking the user to confirm an action, typically deletion.
- Two buttons, labeled "Yes" and "No," are provided for the user to confirm or cancel the action.
- Clicking the "Yes" button triggers the `onConfirm` function, and clicking the "No" button triggers the `onClose` function.

## Component Structure
- The `Modal` component utilizes Tailwind CSS classes for styling, creating a visually appealing modal dialog box.
- It includes text content, action buttons, and appropriate spacing to enhance readability and usability.
- The modal is positioned in the center of the screen and has a shadow effect for depth perception.

## Usage
- The `Modal` component is a versatile UI element that can be used for confirmation dialogs, alerts, or any interaction that requires user confirmation.
- By providing the `isOpen`, `onClose`, and `onConfirm` functions, the component offers flexibility in handling different actions and events within the application.
- The modal enhances the user experience by prompting users to confirm critical actions and provides clear options for proceeding or canceling.

This component improves interaction within the application by presenting important messages and actions in a visually prominent and user-friendly manner, ensuring smooth user engagement and decision-making processes.

<br /><br />

## DatePicker.tsx

The `DatePicker` component is a React component that utilizes the DateField component from Material-UI x-date-pickers to handle date selections.

## Imports
- `Dispatch`, `SetStateAction`, `useMemo`, `useState` from "react": Used for managing states and actions.
- `dayjs`, `Dayjs` from "dayjs": Date manipulation library for handling dates.
- `DateField`, `DateValidationError` from "@mui/x-date-pickers": Components from Material-UI x-date-pickers for date selection.

## Interface
- `DatePickerProps`: Interface defining properties for the `DatePicker` component:
  - `selectedDate`: Dayjs object representing the selected date or null.
  - `setSelectedDate`: Dispatch function for setting the selected date.
  - `formSubmitted`: Boolean indicating if the form has been submitted.

## Functionality
- Initializes a `minDate` constant set to January 1, 2000.
- Manages error state and touched state for input validation.
- Calculates error messages based on form submission, touched state, selected date, and errors.
- Handles date changes and validation errors via the `handleChange` function.
- Utilizes the DateField component to render the date picker input field.

## Component Structure
- The `DatePicker` component renders a DateField component for date selection with error handling.
- Provides error feedback based on input validation status.
- Ensures date selection within a valid range and updates states accordingly.

This component simplifies the process of selecting dates in forms and provides clear error feedback to improve the user experience.

