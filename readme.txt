The process of generating dialog turns from Reddit posts and further training involves several steps:

1: Reddit Post Searching and Downloading: The code file "reddit_scrapper.ipynb" is used to search for and download Reddit posts. It utilizes 24 different history keywords and a predefined hot keyword. The downloaded posts are further filtered to include only those with at least one non-sticky comment. Sticky comments, typically made by admins, do not provide relevant information about the post's question. The downloaded posts are saved in an intermediate dataset on Huggingface.

2: Dialog Generation from Downloaded Posts: The code file "generate_reddit_ah_dialogs.ipynb" generates dialogs using OpenAI's ChatAPI based on the Reddit posts stored in the Huggingface dataset from the previous step. The resulting dialogs are saved in another intermediate dataset on Huggingface, which includes both the Reddit posts and the generated dialogs.

3: Annotation Generation from Dialogs: The file "generate_reddit_ah_dialog_annotations.ipynb" generates annotations by utilizing the Huggingface dataset containing the Reddit post dialogs from the previous step. OpenAI's ChatAPI is used to generate annotations, which are then saved in yet another intermediate dataset on Huggingface. This dataset contains the Reddit posts, the dialogs, and the generated annotations.

4: Consolidation of Intermediate Datasets: The three intermediate datasets mentioned above are merged into a single Huggingface dataset, which can be accessed at this URL: https://huggingface.co/datasets/Deojoandco/reddit-ah-dialog-annotations.

5: Dialog Turn Generation: The file "anotation_dialogs_to_turns.ipynb" takes the consolidated dataset and creates a dialog turn for each conversation. This process results in a separate dataset on Huggingface, which can be found at the following URL: https://huggingface.co/datasets/Deojoandco/reddit-ah-dialogturns-annotations.

6: GPT2 Model Training with Dialog Turns: The file "ah_gpt2_training.ipynb" utilizes the generated dialog turns to train the GPT2 model. The trained model is uploaded to huggingface: 'Deojoandco/ah-GPT2-v4'

7: DialoGPT Model Training with Dialog Turns: The file "ah_dialogpt_training.ipynb" employs the generated dialog turns to train the DialoGPT model. The trained model is uploaded to huggingface: 'Deojoandco/ahDialoGPT-small-v4'

8: GPT2 Trained Chatbot: 'ah_gpt2_chatter.ipynb' is a commandline chatbot using the GPT2 trained model 'Deojoandco/ah-GPT2-v4'

9: DialoGPT Trained Chatbot: 'ah_dialogpt_chatter.ipynb' is a commandline chatbot using the DialoGPT trained model 'Deojoandco/ahDialoGPT-small-v4'