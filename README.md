# Paramedic AI Protocol Assistant

A minimalist, single-file web application designed to assist paramedics by suggesting medical protocols. It allows for the input of patient vital signs and chief complaints, then utilizes the Google Gemini API for an initial AI-driven suggestion. This suggestion is then processed through a simulated "dual-layer" system, where an interpretation layer attempts to validate and standardize the AI's output against a local, in-browser medical database. The aim is a fast, clean, and intuitive user experience.

## How to Use

1.  **Save the file**: Save the entire content of `index.html` as `index.html` on your computer.
2.  **Open in Browser**: Open the `index.html` file using any modern web browser (e.g., Chrome, Firefox, Edge, Safari).
3.  **Input Vitals**: Enter the patient's vital signs (Heart Rate, Blood Pressure, Respiratory Rate, SpO2, Temperature) and their chief complaint into the provided fields. Default values are pre-filled for quick testing.
4.  **Get Suggestion**: Click the "Suggest Protocol" button.
5.  **View Results**: The application will display:
    *   **AI Reasoning (Gemini)**: The raw, detailed suggestion and reasoning from the Google Gemini AI.
    *   **Interpreted Protocol (Database Check)**: A more refined and standardized protocol, derived by interpreting the AI's output and cross-referencing it with an internal, simulated medical database and critical vital sign checks.

## Code Explanation

This project is a single-file web application (`index.html`) containing all necessary HTML, CSS, and JavaScript.

*   **HTML Structure**: Provides a clean, responsive two-column layout. The left column contains input fields for patient vital signs and the chief complaint, along with the "Suggest Protocol" button. The right column displays the AI's reasoning and the interpreted protocol.
*   **CSS Styling**: Implements a minimalist, clean white user interface with a simple and fast design. Basic responsive styles ensure usability on different screen sizes.
*   **JavaScript Logic**:
    *   **Data Collection**: Gathers patient vital signs and chief complaint directly from the HTML form inputs.
    *   **AI Reasoning Layer (Gemini API Integration)**:
        *   Constructs a detailed and structured prompt for the Google Gemini Pro model using the collected patient data.
        *   Makes an asynchronous `fetch` request to the Google Gemini API (using the provided API key) to get an AI-driven suggestion for immediate next steps, medical protocols, and reasoning.
    *   **Interpretation and Checking Layer (Simulated Medical Database)**:
        *   After receiving the AI's text-based response, this layer processes the output.
        *   It attempts to identify keywords or common medical conditions within the AI's suggestion and the patient's chief complaint.
        *   These keywords are then used to look up a corresponding standard protocol from a pre-defined `Map` (`medicalProtocols`) within the JavaScript code, simulating a local medical database.
        *   Additionally, this layer includes essential "critical vital sign checks" (e.g., low SpO2, hypotension, abnormal heart/respiratory rates). These checks can add to or modify the suggested protocol, ensuring crucial life-saving interventions are considered even if not explicitly detailed by the AI or matched by primary keywords.
        *   The goal is to provide a more standardized and "checked" protocol for paramedics, combining AI intelligence with structured medical knowledge.
    *   **UI Updates**: Manages the display of loading states, error messages, the raw AI reasoning, and the final interpreted protocol in their respective HTML elements.
*   **API Key**: The Google Gemini API key is embedded directly within the `index.html` file. **For a production application, it is strongly recommended to proxy API requests through a secure backend server to prevent client-side exposure of API keys and manage usage securely.**

## License

This project is licensed under the MIT License.