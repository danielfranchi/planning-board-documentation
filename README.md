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

## Form.tsx

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

