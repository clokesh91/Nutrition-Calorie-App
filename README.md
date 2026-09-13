# Nutrition-Calorie-App

A Streamlit web app that lets a user upload a food image and ask for a calorie estimate. The app uses Google Gemini Vision to identify the food items in the image, estimate calories for each item, and return a simple breakdown.

## What this app does

- Upload a food image (JPG, JPEG, or PNG)
- Enter a custom question or prompt
- Send the image and prompt to Google Gemini
- Receive a calorie breakdown such as:
  - item name
  - estimated calories
  - total calories summary

This project is useful as a personal nutrition helper or a quick prototype for AI-powered food recognition and calorie estimation.

## Tech stack

- Python
- Streamlit
- Google Generative AI (Gemini)
- Pillow for image processing
- python-dotenv for environment variables

## Project structure

- `app.py` – main Streamlit app
- `requirements.txt` – Python dependencies
- `.env` – local environment variables (not committed to Git)

## Setup instructions

### 1. Clone or open the project

Open the project folder in your terminal.

### 2. Create a virtual environment

```bash
python -m venv venv
```

Activate it:

On Windows:

```bash
venv\Scripts\activate
```

On macOS/Linux:

```bash
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Add your Gemini API key

Create a `.env` file in the project root and add your Google API key:

```env
GOOGLE_API_KEY=your_api_key_here
```

You can get the key from Google AI Studio or the Google Cloud project that has the Gemini API enabled.

### 5. Run the app

```bash
streamlit run app.py
```

Then open the local URL shown in the terminal, usually:

```text
http://localhost:8501
```

## How to use the app

1. Open the app in your browser.
2. Enter a prompt in the text box, for example:
   - "Estimate the total calories in this meal."
   - "List each food item and its calorie count."
3. Upload an image of food.
4. Click the button: "Tell me the total calories"
5. Review the AI-generated result with the calorie breakdown.

## Important notes

- The app depends on a valid `GOOGLE_API_KEY` in the `.env` file.
- If the API key is missing or invalid, Gemini requests will fail.
- The calorie estimate is AI-generated and should be treated as a helpful estimate, not a medical or professional nutrition calculation.
- The app currently expects a single uploaded image and does not persist data.

## Code overview

The main logic in `app.py`:

- loads environment variables with `load_dotenv()`
- configures Gemini using `genai.configure(api_key=os.getenv("GOOGLE_API_KEY"))`
- converts the uploaded image into a Gemini-compatible format with `input_image_setup()`
- sends the image and prompt to Gemini using `generate_content()`
- displays the AI response in the Streamlit interface

## Example prompt

```text
Estimate the calorie count for each item in this meal and give me the total calories.
```

## Future improvements

Possible next steps:

- add support for multiple images
- improve the output format for cleaner nutrition tables
- store meal history locally or in a database
- add manual food item correction
- add unit conversion and macro tracking

## License

This project is for personal and educational use unless otherwise specified.
