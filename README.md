# MS MARCO and Natural Questions translations using T5

### Developed  by Matheus Gustavo Alves Sasso and Graziella Cardoso Bonadia

This project translates both datasets, MS MARCO and Natural Questions using the Paracrawl dataset as training base. Testing in the Paracrawl dataset we achieved 37.8114 for the sacrebleu metric.

We also used Pytorch lighting as the tensor framework for pytorch and the library transformers to get the T5 model.


## Requirements

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install all the requirements
```bash
pip install jsonlines
pip install ftfy
pip install sarebleu
pip install transformers
pip install pytorch-lightning==0.7.6
pip install -U spacy
python -m spacy download en_core_web_sm
```

## Usage

For the usage, its necessary to run the pipeline on number suggested order, linking the file generated from the previous step from the pipeline as the input of the current one. Next, we can see the pipeline order:

**Natural Questions:**

* 1_SimplifyNQ.ipynb
* 2_SplitInfoNQ.ipynb
* 3_TranslationNQ.ipynb
* 4_UnifyNQDatasets.ipynb

**MS MARCO :**

* 1_SplitInfoMSMARCO.ipynb
* 2_TranslationMSMARCO_Collections_Queries.ipynb
* 3_Organize_MSMARCO_Collections.ipynb


## MS MARCO
The MS MARCO pipeline translates the collections.tsv and all the queries.tsv files from TREC 2020 that can be found on this link: [ms_marco_trec2020](https://microsoft.github.io/TREC-2020-Deep-Learning/) 

## Natural Questions
The Natural Questions pipeline translates any of the dictionary files that can be found on this link: [natural_questions](https://ai.google.com/research/NaturalQuestions/download).

I is important to note that we return directly the returned dictionary for the answers, instead of returning the start_token and end_token from the answer. Those tokens that are returned are from the previous text in english, they cold probably change for the portuguese translation. 

OBS: We are not printing in this example the document_text for esthetical purpose

```python
{'example_id': 5655493461695504401,
 'document_url': 'https://en.wikipedia.org//w/index.php?title=Email_marketing&amp;oldid=814071202',
 'question_text': 'which is the most common use of opt-in e-mail marketing',
 'document_text': "All the text in english. It is very large to paste it here",
 'annotations': [{'long_answer': {'long_answer': "A common example of permission marketing is a newsletter sent to an advertising firm 's customers . Such newsletters inform customers of upcoming events or promotions , or new products . In this type of advertising , a company that wants to send a newsletter to their customers may ask them at the point of purchase if they would like to receive the newsletter .",
    'start_token': 1718,
    'end_token': 1783},
   'short_answers': [{'short_answer': "a newsletter sent to an advertising firm 's customers",
     'start_token': 1725,
     'end_token': 1734}],
   'yes_no_answer': 'NONE'}]}
```


## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.