Personalized Recommender using OpenAI API

Overview:
This Python project demonstrates how to build a Personalized Recommender system using the OpenAI API. The recommender takes user preferences (like favorite genres) and generates a list of suggestions using the GPT-4 model. The results are displayed in a neat and readable format using Pandas.

Features:
API Integration: Connects to OpenAI's API using an API key stored in environment variables.
Personalized Recommendations: Generates suggestions based on user-input preferences.
Data Visualization: Displays recommendations in a clean tabular format.
Error Handling: Catches and displays errors without crashing.

Requirements:
Python 3.12.7 or later
OpenAI Python library
Pandas library
Install the required libraries if you haven’t already:

bash
Copy
Edit
pip install openai pandas
Setup
Obtain an API key from OpenAI.
Set your API key as an environment variable:
bash
Copy
Edit
export OPENAI_API_KEY='your_api_key_here'
Ensure the openai and pandas libraries are installed.
Usage
1. Getting a Standard Response
This part of the code checks if the OpenAI API is set up correctly and prints the version.

python
Copy
Edit
import openai
print(openai.__version__)
Example Output:

Copy
Edit
1.64.0
2. Getting User Preferences
The get_user_preferences function prompts the user to enter their favorite genres.

python
Copy
Edit
def get_user_preferences():
    preferences = {}
    preferences['favorite_genres'] = input("Enter your favorite genres (comma-separated): ")
    return preferences
Example Usage:

java
Copy
Edit
Enter your favorite genres (comma-separated): Comedy, Action
3. Generating Recommendations
The generate_recommendations function sends user preferences to the GPT-4 model to generate recommendations.

python
Copy
Edit
def generate_recommendations(preferences):
    prompt = f"Generate a list of recommendations based on the following preferences: {preferences['favorite_genres']}."
    
    try:
        response = client.chat.completions.create(
            messages=[
                {"role": "user", "content": prompt}
            ],
            model="gpt-4"
        )
        completion_message = response.choices[0].message
        recommendations = completion_message.content.strip().split('\n')
        return recommendations
    except Exception as e:
        print(f"An error occurred: {e}")
        return []
Example Output:

arduino
Copy
Edit
1. "Anchorman: The Legend of Ron Burgundy" - Classic comedy.
2. "Superbad" - Teenage mischief.
...
4. Visualizing Recommendations
The visualize_recommendations function uses Pandas to display recommendations in a clean format.

python
Copy
Edit
def visualize_recommendations(recommendations):
    import pandas as pd
    recommendations_df = pd.DataFrame(recommendations, columns=['Recommendation'])
    print(recommendations_df)
Example Output:

csharp
Copy
Edit
                                        Recommendation
0   1. "Anchorman: The Legend of Ron Burgundy" - C...
1                                                     
2   2. "Superbad" - Witness teenage mischief as th...
3                                                     
4   3. "Bridesmaids" - A hilarious bridal party misadventure.
5. Running the Recommender
The main function ties everything together and runs the recommendation system.

python
Copy
Edit
def main():
    preferences = get_user_preferences()
    recommendations = generate_recommendations(preferences)
    visualize_recommendations(recommendations)

if __name__ == "__main__":
    main()
Example Usage:

java
Copy
Edit
Enter your favorite genres (comma-separated): Comedy, Action
Example Output:

csharp
Copy
Edit
                                       Recommendation
0   1. "The Hangover" - Follow a group of friends ...
1                                                     
2   2. "Step Brothers" - Enjoy the odd but hilario...
Customization
Model Selection: Change "gpt-4" to other available models if needed.
Error Messages: Customize error handling as needed.
Error Handling
If an error occurs during API calls, the function prints an error message instead of crashing:

vbnet
Copy
Edit
An error occurred: [Error details]
Notes
Make sure your API key is valid and has enough quota.
Ensure that the openai and pandas libraries are installed.
This project is a solid starting point for building more complex personalized recommendation systems.

Feel free to expand or modify it for different types of recommendations!
