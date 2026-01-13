# Dictionary-Attack-against-a-Spam-Filter---Naive-bias-classification-
The aim of this experiment is to systematically analyze the robustness of a multinomial Naive Bayes spam classifier against a dictionary-based evasion attack. The experiment focuses on understanding how the classifier’s probabilistic decision mechanism, which relies on class-conditional word likelihoods and a bag-of-words.

# Abstract:
Spam filtering is a critical application of machine learning in modern communication systems, where
automated classifiers must operate reliably in the presence of adversarial behavior. Classical
approaches such as the multinomial Naive Bayes classifier remain widely used due to their simplicity
and efficiency; however, their robustness against evasion attacks is limited. In this project, we
investigate the impact of a dictionary-based adversarial attack on a Naive Bayes spam filter trained on
the SMS Spam Collection dataset. The attack consists of appending legitimate-looking words to spam
messages in order to bias the classifier toward the ham class without altering the underlying malicious
intent. We conduct a controlled experiment in which the number of attacked spam messages is
gradually increased and evaluate the resulting degradation in classification performance using
accuracy and macro-averaged F1-score. The experimental results demonstrate that the Naive Bayes
classifier is highly vulnerable to this form of evasion, with performance deteriorating significantly as
the attack intensity increases. These findings highlight the limitations of bag-of-words models in
adversarial settings and emphasize the need for more robust text representations and classification
techniques for spam detection.

# Aim of the experiment:
The aim of this experiment is to systematically analyze the robustness of a multinomial Naive Bayes
spam classifier against a dictionary-based evasion attack. The experiment focuses on understanding
how the classifier’s probabilistic decision mechanism, which relies on class-conditional word
likelihoods and a bag-of-words representation, can be exploited by artificially increasing the
frequency of ham-indicative tokens in spam messages. By injecting a controlled number of legitimatelooking
words into spam messages at test time and progressively increasing the number of attacked
messages, the study quantifies the effect of adversarial manipulation on the classifier’s posterior class
probabilities. The impact of the attack is evaluated using accuracy and macro-averaged F1-score,
enabling an assessment of both overall performance degradation and class-wise misclassification
behavior. Ultimately, the experiment aims to demonstrate how linear evidence accumulation and the
conditional independence assumption in Naive Bayes models lead to vulnerabilities under adversarial
input perturbations.

# Mathematical Intuition:
The multinomial Naive Bayes classifier models a text message as a bag-of-words count vector
<img width="1223" height="350" alt="image" src="https://github.com/user-attachments/assets/3abeb01d-6832-493d-bd82-d3ecbf51bb01" />
<img width="678" height="140" alt="image" src="https://github.com/user-attachments/assets/5ae47693-97f7-433a-a185-eebb1d1c27f6" />
Classification is performed by selecting the class with the maximum log-posterior probability.
In a dictionary attack, a spam message is modified by appending additional words that are statistically
associated with the ham class. Mathematically, this increases the values of 𝑥􀯜for words 𝑤􀯜such that
log 𝑃(𝑤􀯜 ∣ ham) > log 𝑃(𝑤􀯜 ∣ spam). Each appended “good word” therefore contributes a positive
additive term to the ham score while leaving the spam score largely unchanged. Because the Naive
Bayes decision function is linear in the word counts, the cumulative contribution of these added hamindicative
words can outweigh the contribution of the original spam-indicative words.
As a result, even though the semantic meaning of the message remains spam-like, the posterior
probability for the ham class becomes larger than that for the spam class, causing the classifier to
misclassify the message. This vulnerability arises directly from the conditional independence
assumption and the linear accumulation of evidence in the multinomial Naive Bayes model.

# Task Overview and flowchart:
<img width="538" height="762" alt="image" src="https://github.com/user-attachments/assets/58803789-20ea-41dd-8f75-6e323c65b258" />

# Concept summary:
## Algorithm: 
Train a Multinomial Naive Bayes spam classifier, append ham-indicative
dictionary words to increasing numbers of spam messages at test time, and evaluate
performance degradation using accuracy and macro-F1.
## Input: 
Labeled SMS spam dataset, external dictionary of common words, and fixed
experimental parameters.
## Output: 
Accuracy and macro-F1 scores showing the impact of the dictionary attack as the
number of attacked messages increases

# Model Training:
The SMS dataset is first split into training and testing subsets. During the model training phase, the
training messages are transformed into bag-of-words count vectors using a CountVectorizer, and a
Multinomial Naive Bayes classifier is trained to learn class-conditional word probabilities for spam
and ham. After training, the model is evaluated on clean test data to establish a baseline. Selected
spam messages in the test set are then modified by appending ham-indicative dictionary words, and
the trained model classifies these adversarial examples. The effect of the attack is analyzed by
measuring changes in accuracy and macro-averaged F1-score as the number of attacked messages
increases.

# Model Evaluation and Result evaluation:
<img width="827" height="247" alt="image" src="https://github.com/user-attachments/assets/e690f6cd-5095-4c9b-b955-24d088d800b6" />
<img width="628" height="433" alt="image" src="https://github.com/user-attachments/assets/5fb0851e-258a-4119-b8db-d56433a98231" />
<img width="820" height="367" alt="image" src="https://github.com/user-attachments/assets/0625d30c-9c46-4648-9f33-71b6ade6501d" />
<img width="631" height="416" alt="image" src="https://github.com/user-attachments/assets/e4130a0c-7d43-49bb-be8f-da860e9c641a" />
<img width="855" height="408" alt="image" src="https://github.com/user-attachments/assets/ce18ea6c-2eea-438b-a503-75ea7a487e64" />
<img width="837" height="191" alt="image" src="https://github.com/user-attachments/assets/7f921653-8545-4d1b-bd59-6c00ca69f075" />

# Conclusion:
In this project, a multinomial Naive Bayes spam classifier was implemented and evaluated under a
dictionary-based evasion attack using the SMS Spam Collection dataset. While the classifier achieved
strong baseline performance on clean data, the experimental results demonstrated a significant
vulnerability to adversarial manipulation. By appending ham-indicative words to spam messages at
test time, the attacker was able to systematically reduce the classifier’s effectiveness. Both accuracy
and macro-averaged F1-score degraded as the number of attacked messages increased, with the
macro-F1 metric revealing a pronounced decline in spam detection capability. These findings confirm
that the linear evidence accumulation and conditional independence assumptions inherent in bag-ofwords
Naive Bayes models make them particularly susceptible to simple evasion strategies, even
when the semantic meaning of the message remains unchanged.










