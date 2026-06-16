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