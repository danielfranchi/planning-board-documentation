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



