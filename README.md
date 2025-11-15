# 💬 Reddit Sentiment & Product Insight Analyzer

This is a comprehensive Python script that automates the collection of comments from a specified Reddit thread and uses **Microsoft Azure AI Services** (Azure Language and Azure OpenAI) to perform sentiment analysis, extract key phrases, generate AI-driven replies, and produce a summary report with actionable product recommendations.

The tool is ideal for product managers, business analysts, and market researchers who need to quickly synthesize large volumes of public feedback.

---

## ✨ Features

* **Reddit Data Fetching:** Automatically connects to the Reddit API (PRAW) to collect comments from a given submission ID.
* **Azure Language Analysis:** Uses Azure Text Analytics to determine the **sentiment** (Positive, Neutral, Negative) and extract **key phrases** for each comment.
* **AI Reply Generation:** Leverages **Azure OpenAI** (GPT model) to draft professional, friendly customer support replies for every comment.
* **Thematic Summarization:** Uses Azure OpenAI to summarize all extracted key phrases into **top recurring themes** and propose 1-2 **actionable product improvements** for each theme.
* **Automated Reporting:** Generates two distinct output files:
    * A detailed CSV containing the original comments, NLP scores, and AI-generated replies.
    * A Word document (`.docx`) containing the high-level summary, key themes, and product recommendations.
* **Environment Setup:** Uses `python-dotenv` to securely manage API keys and application credentials.

---

## 🛠️ Prerequisites

To run this application, you will need:

* Python 3.8+
* Access to API Credentials for all required services.

### API Services Required

| Service | Credentials Needed |
| :--- | :--- |
| **Reddit (PRAW)** | Client ID, Client Secret, Username, Password (for script authentication) |
| **Azure Language** | Key, Endpoint (for Sentiment & Key Phrase Extraction) |
| **Azure OpenAI** | Key, Endpoint, Deployment Name (for Reply Generation & Summarization) |

---

## 🚀 Installation & Setup

1.  **Clone the Repository**
2.  **Create the Virtual Environment**
    * It is highly recommended to use a virtual environment.
3.  **Install Dependencies**
    * Install all necessary libraries using the `requirements.txt` file.
    ```bash
    pip install -r requirements.txt
    ```
4.  **Configure Environment Variables**
    * Create a file named `.env` in the root directory of your project and populate it with your credentials.

### `.env` File Structure:

```env
# Reddit API Credentials
REDDIT_CLIENT_ID="[Your Reddit Client ID]"
REDDIT_CLIENT_SECRET="[Your Reddit Client Secret]"
REDDIT_USERNAME="[Your Reddit Username]"
REDDIT_PASSWORD="[Your Reddit Password]"
REDDIT_USER_AGENT="windows:reddit_analyzer:0.1 (by u/YourUsername)"

# Azure Language Service Credentials
AZURE_LANGUAGE_KEY="[Your Azure Language Key]"
AZURE_LANGUAGE_ENDPOINT="[Your Azure Language Endpoint]"

# Azure OpenAI Service Credentials
AZURE_OPENAI_KEY="[Your Azure OpenAI Key]"
AZURE_OPENAI_ENDPOINT="[Your Azure OpenAI Endpoint URL]"
AZURE_OPENAI_DEPLOYMENT="[Your GPT Deployment Name, e.g., gpt-35-turbo]"
```

## 🏃 Usage
The application is run via the command line and requires the URL of the Reddit post you wish to analyze.

1. Save the code as a Python file (e.g., feedback_analyzer.py).

2. Run the script from your activated virtual environment, passing the Reddit post URL as an argument to the run_pipeline function within the if __name__ == "__main__": block.

Example Post URL: https://www.reddit.com/r/cocacola/comments/1j5g5ib/opinions_on_this_one/

#python
if __name__ == "__main__":
    # Replace the URL below with the target Reddit thread
    run_pipeline("[https://www.reddit.com/r/cocacola/comments/1j5g5ib/opinions_on_this_one/](https://www.reddit.com/r/cocacola/comments/1j5g5ib/opinions_on_this_one/)")
    
3. Check the output: The script will generate two files in the project directory, named with the post ID and a timestamp:

reddit_analysis_..._...csv (Detailed data with sentiment scores and AI replies)

reddit_analysis_..._...docx (Summary report for management)

## Example Console Output:
▶️ Fetching comments... 

🔍 Analyzing sentiment and key phrases... 

📝 Generating AI replies... 

📊 Summarizing key themes and recommendations... 

✅ Done! Outputs: 
- Detailed CSV: reddit_analysis_1j5g5ib_20251114_162336.csv 
- Management Report: reddit_analysis_1j5g5ib_20251114_162336.docx
