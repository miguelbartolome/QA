# QA-Challenge

## Challenge Instructions

## QA Practical Challenge 💻

This document outlines a practical challenge designed to assess your skills in Quality Assurance for both frontend and backend applications. You'll be tasked with identifying and reporting bugs in a user registration form and testing endpoints of a To-Do List REST API.

The challenge encourages you to demonstrate your creativity and experience in ensuring software quality, going beyond the basic requirements to showcase your vision for quality assurance.

---

## Practice 1: Frontend Challenge: User Registration Form

You will be given access to a simple user registration page. Your task is to perform a thorough quality analysis and provide a bug report for any issues you find. You will be evaluated on the
quantity and, more importantly, the quality of your reported bugs. 

A good bug report should include a clear title, steps to reproduce, actual result, expected result, and a suggested
severity/priority.

### The Frontend application is a simple form with the following fields:

* Full Name (text input)
* Email (email input)
* Password (password input)
* Confirm Password (password input)
* "I agree to the Terms & Conditions" checkbox
* "Sign Up" button

#### URL to test: https:/ /candidate-challenges-e3hbd7ckh3hzbead.westeurope-01.azurewebsites.net

---

## Practice 2: Backend Challenge: To-Do API

We are providing you with Swagger/OpenAPI documentation for a To-Do List REST API and access to a live test environment. Your mission is to test the available endpoints and report any anomalies, inconsistencies, or unexpected behavior. 

You can use any tool you prefer, such as Postman or Insomnia. As with the frontend challenge, the quality and clarity of your report are key.

### API Endpoints:

* GET /tasks: Retrieve all tasks.
* GET /tasks/{id}: Retrieve a single task by its ID.
* POST /tasks: Create a new task. Expected body: { "title": "string", "completed": "boolean" }.
* DELETE /tasks/{id}: Delete a task.

Note: Swagger will provide you with full information on the request/response data for each endpoint.

#### URL to test: https:/ /candidate-challenges-e3hbd7ckh3hzbead.westeurope-01.azurewebsites.net/swagger

