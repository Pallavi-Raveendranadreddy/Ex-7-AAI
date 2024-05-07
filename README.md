<H3>NAME: Kaushika A</H3>
<H3>REGISTER NO: 212221230048</H3>
<H3>EX: NO.7</H3>
<H3>DATE: 24.04.2024</H3> 
<H1 ALIGN =CENTER>Implementation of Text  Summarization</H1>
<H3>Aim: </H3> 
to perform automatic text summarization using Natural Language Processing (NLP) techniques. <BR>
<h3>Algorithm:</h3>

- `Step 1:` Import necessary libraries for natural language processing tasks.<BR>
- `Step 2:` Download NLTK resources, including the punkt tokenizer and stopwords.<BR>
- `Step 3:` Define Text Preprocessing Function to tokenize, remove stopwords, and perform stemming.<BR>
- `Step 4:` Define the Text Summarization Function using a simple frequency-based approach.<br>
    - Calculate the frequency of each word in the preprocessed text.<br>
    - Calculate a score for each sentence based on the sum of word frequencies.<br>
    - Select the top N sentences with the highest scores to form the summary.<br>
- `Step 5:` Construct the main program to read the paragraph  and perform text summarization<br>
    - Generate and print the original text.<br>
    - Generate and print the text summary using the  Text Summarization function<br>

<H3>Program:</H3>

```py

import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize, sent_tokenize
from nltk.stem import PorterStemmer
nltk.download('punkt')
nltk.download('stopwords')

def preprocess_text(text):
  # Tokenize the text into words
  words = word_tokenize (text)
  # Remove stopwords and punctuation
  stop_words = set(stopwords.words('english'))
  filtered_words = [word for word in words if word.lower() not in stop_words and word.isalnum()]
  # Stemming
  stemmer = PorterStemmer()
  stemmed_words = [stemmer.stem (word) for word in filtered_words]
  return stemmed_words

def generate_summary (text, num_sentences=3):
  sentences = sent_tokenize(text)
  preprocessed_text = preprocess_text(text)
  # Calculate the frequency of each word
  word_frequencies = nltk. FreqDist(preprocessed_text)
  # Calculate the score for each sentence based on word frequency
  sentence_scores = {}
  for sentence in sentences:
    for word, freq in word_frequencies.items():
      if word in sentence.lower():
        if sentence not in sentence_scores:
          sentence_scores [sentence] = freq
        else:
          sentence_scores [sentence] += freq
  # Select top N sentences with highest scores
  summary_sentences = sorted(sentence_scores, key=sentence_scores.get, reverse=True) [:num_sentences]
  return''.join(summary_sentences)

if __name__ == "__main__":
    input_text = """Applied AI, or Applied Artificial Intelligence, refers to the practical implementation of artificial intelligence (AI) technologies to solve real-world problems across various industries and domains. 
Unlike theoretical AI research, which focuses on advancing the understanding of AI algorithms and methodologies, applied AI involves the deployment of AI solutions to address specific challenges or 
improve existing processes.

Applied AI encompasses a wide range of applications, including natural language processing, computer vision, machine learning, robotics, and more. 
These technologies are utilized in fields such as healthcare, finance, manufacturing, transportation, customer service, and many others, to automate tasks, 
make predictions, optimize operations, and enhance decision-making.

Key components of applied AI include data collection, preprocessing, algorithm selection and training, model deployment, and ongoing optimization and maintenance. 
It often involves interdisciplinary collaboration between AI specialists, domain experts, data scientists, software engineers, and other professionals to tailor 
AI solutions to the specific needs and constraints of the problem at hand.

Overall, applied AI plays a crucial role in driving innovation, improving efficiency, and unlocking new opportunities across various sectors, ultimately contributing 
to advancements in technology and society as a whole."""
    summary = generate_summary(input_text)
    print("Original Text:")
    print(input_text)
    print("\nSummary:")
    print(summary)
```

<H3>Output</H3>

![](1.PNG)

<H3>Result:</H3>
Thus ,the program to perform the Text summarization is executed sucessfully.


