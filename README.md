# BMI Vue Application

## Overview

The BMI Vue Application is a web-based application developed using Vue.js that allows users to calculate and manage Body Mass Index (BMI) records. Users can add personal information, calculate BMI values automatically, view the most recently added record, and maintain a list of all recorded individuals.

The project demonstrates the use of Vue.js fundamentals, including form handling, event handling, data binding, conditional rendering, and list rendering.

---

## Problem Analysis

The initial version of the application stores all functionality inside a single `App.vue` file. Although the application functions correctly, several software design issues become apparent as the project grows.

### 1. App.vue Has Too Many Responsibilities

The `App.vue` file handles multiple concerns simultaneously, including:

- Page layout and user interface
- Form input handling
- BMI calculation logic
- Display of person records

As a result, the component becomes difficult to understand, maintain, and extend.

### 2. The Form Cannot Be Reused

The form implementation is tightly coupled to the main application component.

As a result:

- The form cannot be easily reused in another page or feature.
- Any future modifications may require code duplication.

### 3. Person Display Code Is Repetitive

Person information is displayed in multiple locations, resulting in repeated code.

This means:

- Updating the display format requires modifications in several places.
- Code maintenance becomes more difficult.

### 4. The File Becomes Too Large

As new features are added, the size of `App.vue` continues to increase.

Potential issues include:

- Reduced readability
- More difficult debugging
- Harder navigation through the code

### 5. UI Layout and Business Logic Are Mixed

The application combines user interface elements and business logic within the same file.

This creates:

- Poor separation of concerns
- Reduced maintainability
- Increased complexity as the application grows

---

## Technologies Used

- Vue.js
- JavaScript
- HTML5
- CSS3

---

## Installation

Install project dependencies:

```bash
npm install
```

## Run Development Server

Compile and run the application in development mode:

```bash
npm run serve
```

## Build for Production

Compile and optimize the application for production deployment:

```bash
npm run build
```

## Lint and Fix Files

Analyze and automatically fix code style issues:

```bash
npm run lint
```

---

## Project Configuration

For additional configuration options, refer to the Vue CLI documentation:

https://cli.vuejs.org/config/

---

## Author

Developed as part of the **SECJ3483 Web Technology** coursework to demonstrate Vue.js fundamentals, form handling, event handling, conditional rendering, and list rendering.

1. What improved after refactoring?

After refactoring, the application became more modular and organized. Each part of the UI was separated into reusable components and views, making the code easier to maintain, debug, and scale. The App.vue file is now cleaner and only manages shared state.

2. Why should data be passed using props instead of direct access?

Props ensure a one-way data flow from parent to child, which makes the application more predictable and easier to debug. It prevents child components from directly modifying parent data, reducing unexpected side effects and improving maintainability.

3. Why should a child component use emit to send data to a parent component?

Because in Vue, data should flow upward using events. emit allows the child component to communicate changes or actions to the parent without directly modifying parent state. This keeps components loosely coupled and improves reusability.

4. Which component is the most reusable in this application? Explain.

The most reusable component is PersonCard. It only depends on a person prop and can be used in both the list view and last person display. It is flexible and does not depend on application logic, making it easy to reuse anywhere.

5. What is the difference between components and views in this lab?

Components are small, reusable UI building blocks (e.g., PersonCard, PersonForm). Views are larger page-level structures that combine multiple components (e.g., AddPersonView, PersonListView). Views manage layout and composition, while components focus on specific functionality.