<H3>ENTER YOUR NAME : Gayathri A</H3>
<H3>ENTER YOUR REGISTER NO. 212221230028</H3>
<H3>EX. NO.6</H3>
<H3>DATE: 20/04/2024</H3>
<H1 ALIGN =CENTER>Implementation of Semantic ANalysis</H1>
<H3>Aim: to perform Parts of speech identification and Synonym using Natural Language Processing (NLP) techniques. </H3> 
 <BR>
<h3>Algorithm:</h3>
Step 1: Import the nltk library.<br>
Step 2: Download the 'punkt', 'wordnet', and 'averaged_perceptron_tagger' resources.<br>
Step 3:Accept user input for the text.<br>
Step 4:Tokenize the input text into words using the word_tokenize function.<br>
Step 5:Iterate through each word in the tokenized text.<br>
•	Perform part-of-speech tagging on the tokenized words using nltk.pos_tag.<br>
•	Print each word along with its corresponding part-of-speech tag.<br>
•	For each verb , iterate through its synsets (sets of synonyms) using wordnet.synsets(word).<br>
•	Extract synonyms and antonyms using lemma.name() and lemma.antonyms()[0].name() respectively.<br>
•	Print the unique sets of synonyms and antonyms.
<H3>Program:</H3>

```
import nltk
from nltk.corpus import wordnet

nltk.download('punkt')
nltk.download('averaged_perceptron_tagger')
nltk.download('wordnet')

def get_synonyms(word):
    synonyms = set()
    for syn in wordnet.synsets(word):
        for lemma in syn.lemmas():
            synonyms.add(lemma.name())
    return synonyms

def process_text_file(file_path):
    with open(file_path, 'r') as file:
        text = file.read()
    return text  # Return the processed text

text = process_text_file('ml.txt')

# Tokenize the text into sentences
sentences = nltk.sent_tokenize(text)

for sentence in sentences:
    # Tokenize each sentence into words
    words = nltk.word_tokenize(sentence)

    # Perform part-of-speech tagging
    pos_tags = nltk.pos_tag(words)
    for word, tag in pos_tags:
       print(word,tag)
    synonyms = []
    antonyms = []
    for word in words:
       for syn in wordnet.synsets(word):
         for lemma in syn.lemmas():
            synonyms.append(lemma.name())
              if lemma.antonyms():
                 antonyms.append(lemma.antonyms()[0].name())
    print("Synonyms:",set(synonyms))
    print("Antonyms:",set(antonyms))

    # Extract verbs
    verbs = [word for word, pos in pos_tags if pos.startswith('V')]

    # Get synonyms for each verb
    for verb in verbs:
        synonyms = get_synonyms(verb)
        print(f"Verb: {verb}")
        print(f"Synonyms: {', '.join(synonyms)}\n")
```

<H3>Output</H3>

![image](https://github.com/Gayathriraj18/Ex-6--AAI/assets/94154854/4cb7ed3e-4afb-4c96-a8c2-b969085366e1)

![image](https://github.com/Gayathriraj18/Ex-6--AAI/assets/94154854/d2240686-75b3-4329-8667-53ed0499112b)

![image](https://github.com/Gayathriraj18/Ex-6--AAI/assets/94154854/789a57a3-f4ce-4f8e-816f-167195471a40)


<H3>Result:</H3>
Thus ,the program to perform the Parts of Speech identification and Synonymis executed sucessfully.
