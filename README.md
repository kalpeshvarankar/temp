# Project Title: Text Analysis for Articles
In this project, I developed a Python script to perform web scraping, text analysis, and sentiment evaluation of articles extracted from specified URLs. 
The solution is structured into several functions, each responsible for a specific task, thereby ensuring modularity and clarity in the code. 
Below, I have outlined the key steps and methodologies that i have used in the solution:


# A. Approach:
## 1. Web Scraping
#### Function: extract_content_from_urls(url)
The first step is extracting content from the provided URLs. This is achieved through the requests library to send HTTP GET requests, and BeautifulSoup to parse the HTML content.
- Title Extraction: The script retrieves the title from the <h1> tag of the webpage.
- Text Extraction: The main content is gathered from all <p> (paragraph) tags, concatenating them into a single string.
- Error Handling: The function includes exception handling to manage any potential errors that may occur during the request or content parsing.

## 2. Saving Extracted Data
#### Function: save_to_file(url_id, title, article_text)
After content extraction, the script saves the article's title and text to a file named after the URL ID. This function handles file operations using a context manager to ensure proper closure after writing.


## 3. Stopwords Management
#### Function: load_all_stopwords(folder_path)
The solution loads stopwords from text files located in a specified folder. Each word is added to a set to facilitate quick lookup, which enhances efficiency during text processing.


## 4. Text Preprocessing
#### Function: text_cleaning(text)
This function is crucial for preparing the text for analysis. It involves:
- Lowercasing: Standardizes the text.
- Punctuation Removal: Utilizes regular expressions to clean the text.
- Tokenization: Splits the text into individual tokens (words).
- Stopword Removal: Filters out common stopwords to focus on meaningful words.


## 5. Sentiment Analysis
#### Functions: load_positive_negative_words(folder_path, stop_words_list) and calculate_sentiment(cleaned_tokens, words_dict)
The script loads lists of positive and negative words and calculates sentiment scores based on the presence of these words in the cleaned tokens.
- Sentiment Scores: Positive and negative scores are computed by counting occurrences of respective words, leading to overall polarity and subjectivity scores.


## 6. Readability Metrics
#### Function: calculate_readability(text)
Readability scores are calculated using the Gunning Fog Index, which assesses the complexity of the text based on sentence length and word complexity. Key metrics include average sentence length, percentage of complex words, and the Fog Index.


## 7. Additional Text Features
#### Functions: count_syllables(word), count_personal_pronouns(text), and calculate_average_word_length(tokens)
These functions compute various text features, including:
- Syllable Count: Based on vowel detection with specific exceptions.
- Personal Pronouns Count: Utilizes regex to identify occurrences while excluding certain cases.
- Average Word Length: Calculated to provide insights into the text's complexity.


## 8. Execution and Data Handling
In the __main__ block, the script reads input data from an Excel file, processes each URL to extract content, perform analysis, and store results in a structured DataFrame. The final output includes a range of sentiment and readability metrics, ready for further analysis or reporting.



# B. How to Run the Script
To run the script for text analysis, follow these steps:

1. **Prepare Your Input File**: Ensure you have an Excel file with a column named `URL` that contains the URLs of the articles you want to analyze.

2. **Run the Script**: Open your terminal or command prompt, navigate to the directory where the `black_coffer.py` script is located, and execute the following command:

   ```bash
   python black_coffer.py <input_file.xlsx> <output_file.csv>

   Replace <input_file.xlsx> with the path to your Excel file and <output_file.csv> with the name you want for the output CSV file.

   After running the script, the results will be saved in the specified Excel (.xlsx) file. You can open it to review the extracted data, sentiment scores, readability metrics and so on.



# C. Dependencies required:
## Dependencies
To run this project, you need to have the following Python libraries installed:

- **pandas**: For data manipulation and analysis.
- **requests**: For sending HTTP requests to retrieve HTML content from the URLs.
- **nltk**: For natural language processing tasks.
    - Note: Ensure that you have downloaded the necessary NLTK resources by running the following commands in your Python environment:
      ```python
         import nltk
         nltk.download('punkt')
         nltk.download('punkt_tab')  # Explicitly downloading punkt_tab
      ```
- **beautifulsoup4**: For parsing HTML and extracting text from web pages.
- **openpyxl**: For reading and writing Excel files.

### Installation
You can install the required packages using pip. Run the following commands in your terminal:

```bash
pip install pandas
pip install requests
pip install nltk
pip install beautifulsoup4
pip install openpyxl
