# Reddit Suicidality Monitor
##### *Streams, classifies and messages new posts of Reddit users*

### Introduction
This is a Reddit bot system that allows 0...* users to be 'monitored' wherein any new posts they make are grabbed, classified as showing suicidality or not and, based on this prediction, a private message is sent to them that includes an inspirational quote and suicide helpline numbers.

I have provided the code to build the classifier in case you're curious to tweak things but if you just wish to use the system you only need to use the Main_Program.ipynb.

This project was done in Jupyter Lab but I have made it possible to run in Colab. You will need to manually install libraries if you wish to use Jupyter.

*Please use responsibly*

### File information
* **Building_Classifier.ipynb** 
I have provided the code to build the classifier in case you're curious to tweak things but if you just wish to use the system you only need to use the Main_Program.ipynb.
* **Main_Program.ipynb** The main system to run the bot. Instructions are provided below.
* **Security.ipynb** This is code to manage the security features of the bot. I have implemented an encryption and decryption system of the grabbed posts and usernames of monitored Redditors. Use this file to manually encrypt and decrypt e.g. if you want to look at the logged submissions or modify the list of monitored users.
* **important_words_3000.txt** The top 3000 words that are indicative of suicide, based on analysis using Sci-kit learn's SelectKBest and Chi2 libraries in Building_Classifier.ipynb.
* **inspirational_quotes.txt** A list of thirty hand-selected quotes taken from [here](https://www.yourtango.com/2016297532/uplifting-suicide-prevention-quotes).
* **key.key** A key generated using Fernet library, used to encrypt and decrypt sensitive files. It's possible to generate a new one using Security.ipynb.
* **model_logistic_regression_3000.pkl** Logistic regression classification model built using the top 3000 most weighty words.
* **suicidality_dataset_raw_fixed** Compilation of 2000 posts from 5 different non-mental-health subreddits and 10,000 posts from /r/SuicideWatch, totalling 20,000 posts. Of these, 100 were manually annotated by 3 non-clinically-trained people. [Source for individual datasets](http://www.opendatacommons.org/licenses/pddl/1.0/)
* **tfidf_3000.pkl** TF-IDF model to extract numerical features from textual data. Trained in Building_Classifier.ipynb.

### How to use
1) You must have a Reddit account which will act as the bot. Go to https://www.reddit.com/prefs/apps to authenticate and get a client ID and client secret, which you will use alongside your username and password, for PRAW (https://praw.readthedocs.io/en/stable/getting_started/authentication.html) in Main_Program.ipynb
2) If you are using Colab you must manually upload all the necessary files:
    * model_logistic_regression_3000.pkl
    * tfidf_3000.pkl
    * important_words_3000.txt
    * inspirational_quotes.txt 
    * key.key (it's also possible to generate a new one using Security.ipynb)
3) Run the cells consecutively. Two files will be created and encrypted and the bot will be active:
    * usernames_to_monitor.txt
    * submission_log.csv
4) In order to be monitored, a user must first message the bot asking to be monitored, this is a privacy feature due to the sensitive nature of the target set. Once again I emphasise do not use this as is. It is a proof of concept. Proper considerations must be taken to ensure privacy.
5) When the monitored user makes a post, it is grabbed, classified, logged and responded to (if predicted suicidal).
