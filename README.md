# Spring AI Powered API for Chatbot, Image Generation, and Recipe Generation

This project explores the capabilities of Spring AI to build intelligent applications leveraging OpenAI models. It provides APIs for:

* **Chatbot:** Engaging in conversational interactions using GPT-4.0 or GPT-3.5.
* **Image Generation:** Creating images based on text prompts using DALL-E 2 or DALL-E 3.
* **Recipe Generation:** Generating recipes based on provided ingredients, dietary restrictions, and cuisine preferences.

## Technologies Used

* **Java:** The primary programming language.
* **Spring Boot:** Framework for building the application.
* **Spring AI:** Abstraction layer for interacting with various AI models.
* **OpenAI API:** Accessing GPT and DALL-E models.
* **Maven:** Build automation tool.
* **(Optional) Lombok:** For reducing boilerplate code.
* **(Optional) Spring Web:** For building RESTful APIs.

## Prerequisites

* **Java Development Kit (JDK):** Ensure you have a compatible JDK installed.
* **Maven:** Install Maven if you don't have it already.
* **OpenAI API Key:** You will need an API key from OpenAI to access their models. You can obtain one from the [OpenAI Platform](https://platform.openai.com/).

## Setup and Installation

1.  **Clone the Repository:**
    ```bash
    git clone <(https://github.com/keshavarun20/spring-ai-multitool/)>
    cd <YOUR_PROJECT_DIRECTORY>
    ```

2.  **Configure OpenAI API Key:**
    * Create an `application.properties` or `application.yml` file in the `src/main/resources` directory.
    * Add your OpenAI API key:
        ```properties
        spring.ai.openai.api-key=<YOUR_OPENAI_API_KEY>
        ```
        or
        ```yaml
        spring:
          ai:
            openai:
              api-key: <YOUR_OPENAI_API_KEY>
        ```

3.  **Build the Project:**
    ```bash
    mvn clean install
    ```

## Running the Application

1.  **Navigate to the Project Directory:**
    ```bash
    cd <YOUR_PROJECT_DIRECTORY>
    ```

2.  **Run the Spring Boot Application:**
    ```bash
    mvn spring-boot:run
    ```
    The application will typically start on `http://localhost:8080`.

## API Endpoints (as seen in Postman/Browser)

When making requests to these endpoints, you will construct the request URL with parameters. The successful responses (typically with a `200 OK` status code) will contain the generated content in the body as JSON.

### Chatbot

* **Endpoint:** `/api/ask-ai` (GET)
* **Request Parameters (in URL):**
    * `prompt`: The message you want to send to the chatbot (e.g., `prompt=Tell me a joke`).
* **Example Request URL:** `http://localhost:8080/api/ask-ai?prompt=Tell%20me%20a%20joke`
* **Successful Response (200 OK) Body (JSON):**
    ```json
    {
      "response": "Why don't scientists trust atoms? Because they make up everything!"
    }
    ```
    **Postman/Browser Observation:** Construct the URL with the `prompt` parameter. The JSON response containing the `response` will be in the "Body" tab of the Postman response or rendered by the browser.

### Image Generation

* **Endpoint:** `/api/generate-image` (GET)
* **Request Parameters (in URL):**
    * `prompt`: The description of the image you want to generate (e.g., `prompt=A futuristic cityscape`).
* **Example Request URL:** `http://localhost:8080/api/generate-image?prompt=A%20futuristic%20cityscape`
* **Successful Response (200 OK) Body (JSON):**
    ```json
    {
      "imageUrl": "URL_OF_THE_GENERATED_IMAGE"
    }
    ```
    **Postman/Browser Observation:** Build the URL with `prompt` and optionally `model` parameters. The `imageUrl` will be in the JSON response body.

### Recipe Generation

* **Endpoint:** `/api/generate-recipe` (GET)
* **Request Parameters (in URL):**
    * `ingredients`: A comma-separated list of ingredients (e.g., `ingredients=chicken,broccoli,rice`).
    * `dietaryRestrictions` (Optional): A comma-separated list of dietary restrictions (e.g., `dietaryRestrictions=gluten-free,vegetarian`).
    * `cuisine` (Optional): The desired cuisine (e.g., `cuisine=Italian`).
* **Example Request URL:** `http://localhost:8080/api/generate-recipe?ingredients=chicken,broccoli,rice&dietaryRestrictions=gluten-free&cuisine=Italian`
* **Successful Response (200 OK) Body (JSON):**
    ```json
    {
      "recipeName": "Chicken and Broccoli Risotto",
      "ingredients": ["chicken", "broccoli", "arborio rice", ...],
      "instructions": ["...", "...", "..."]
    }
    ```
    **Postman/Browser Observation:** Construct the URL with the `ingredients`, `dietaryRestrictions`, and `cuisine` parameters. The recipe details will be in the JSON response body.
