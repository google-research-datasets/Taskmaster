# COPYRIGHT NOTICE

This is the work of Bill Byrne, Karthik Krishnamoorthi, Chinnadhurai Sankar, Arvind Neelakantan, Amit Dubey, Kyu-Young Kim and Andy Cedilnik from Google LLC, made available under the Creative Commons Attribution 4.0 License. A full copy of the license can be found at https://creativecommons.org/licenses/by/4.0/

# DESCRIPTION OF DATA AND COLLECTION METHODOLOGIES

The dataset consists of 13,215 task-based dialogs, including 5,507 spoken and 7,708 written dialogs created with two distinct procedures. Each conversation falls into one of six domains: ordering pizza, creating auto repair appointments, setting up ride service, ordering movie tickets, ordering coffee drinks and making restaurant reservations.

Two-person, spoken dialogs were created using a Wizard of Oz methodology in which crowdsourced workers played the role of a 'user' and trained call center operators played the role of the 'assistant'. In this way, users were led to believe they were interacting with an automated system while it was in fact a human. As a result, users could express their turns in natural ways but in the context of an automated interface. For the written dialogs, we engaged crowdsourced workers to write the full conversation themselves based on scenarios outlined for each task, thereby playing roles of both the user and assistant. In a departure from traditional annotation techniques, dialogs are labeled with simple API arguments, i.e. the slot values required to execute the task transaction, instead of traditional semantic intents and dialog acts.

Instructions for each dialog type can be found in the 'instructions' folders on the dataset landing page and can be downloaded with the entire dataset.

A full description of the data, methodology and analyses as well as sample conversations and user instructions can also be found in our EMNLP paper cited below. (Please cite in your work where relevant.)

@inproceedings{byrne-etal-2019-taskmaster,
title = {Taskmaster-1:Toward a Realistic and Diverse Dialog Dataset},
author  = {Bill Byrne and Karthik Krishnamoorthi and Chinnadhurai Sankar and Arvind Neelakantan and Daniel Duckworth and Semih Yavuz and Ben Goodrich and Amit Dubey and Kyu-Young Kim and Andy Cedilnik},
booktitle = {2019 Conference on Empirical Methods in Natural Language Processing and 9th International Joint Conference on Natural Language Processing},
address = {Hong Kong},
year  = {2019}
}

# EXPLANATION OF DATA FILES

The bulk of the corpus is provided in JSON format in two data files.
self-dialogs.json contains all the one-person dialogs.
woz-dialogs.json contains all the WOz dialogs.

One-person dialogs can be divided into train/dev/test sets by matching the dialog IDs from the following files:
https://storage.cloud.google.com/dialog-data-corpus/TASKMASTER-1-2019/train-dev-test/train.csv
https://storage.cloud.google.com/dialog-data-corpus/TASKMASTER-1-2019/train-dev-test/dev.csv
https://storage.cloud.google.com/dialog-data-corpus/TASKMASTER-1-2019/train-dev-test/test.csv

Additionally, the following files are provided to describe the data structure and annotation schema.
sample.json  - A sample conversation describing the format of the data.
ontology.json - Schema file describing the annotation ontology.

Each conversation in the data file has the following structure:
  conversationId: A universally unique identifier with the prefix 'dlg-'. The ID has no meaning.
  utterances: An array of utterances that make up the conversation.
  instructionId: A reference to the file(s) containing the user (and, if applicable, agent) instructions for this conversation.

Each utterance has the following fields:
  index: A 0-based index indicating the order of the utterances in the conversation.
  speaker: Either USER or ASSISTANT, indicating which role generated this utterance.
  text: The raw text of the utterance. In case of self dialogs, this is written by the crowdsourced worker. In case of the WOz dialogs, 'ASSISTANT' turns are written and 'USER' turns are transcribed from the spoken recordings of crowdsourced workers.
  segments: An array of various text spans with semantic annotations.

Each segment has the following fields:
  startIndex: The position of the start of the annotation in the utterance text.
  endIndex: The position of the end of the annotation in the utterance text.
  text: The raw text that has been annotated.
  annotations: An array of annotation details for this segment.

Each annotation has a single field:
  name: The annotation name.

# EXPLANATION OF ONTOLOGY

Dialog annotations are based on the API calls associated with each type of task-based dialog. The full JSON description of the ontology can be found in ontology.json. Each conversation was annotated by two workers. Both annotations are included in this collection.

The API-based annotations can be divided into two categories:
API argument labels: These refer to the parameter values specified for a given transaction. For example, a pizza order must minimally provide values for store name, number of pizzas, sizes, topping(s) and sometimes crust type (known as 'required' parameters in ontology.json). Named pizzas like 'veggie lovers' come with a predetermined set of toppings and so only the number pizzas and sizes are required. Users may also specify optional arguments (known as 'optional' parameters in ontology.json) such as 'extra cheese' or substitutions like 'pesto instead of tomato sauce', omissions like 'no tomatoes', etc.
Transaction status labels: In addition to the parameter values, the success or failure of the transaction itself is labeled with 'accept' or 'reject'. If the dialog only makes general reference to a transaction, e.g. 'OK your pizza has been ordered' or 'Sorry we just discontinued that pizza so it's no longer available', the label 'accept' or 'reject' is added to the vertical name, i.e. 'pizza_ordering.accept'. However, in most cases these labels are added to the individual parameters involved in the transaction, whether accepted or rejected. For example, in 'It looks like we are out of pepperoni tonight', 'pepperoni' would be labeled 'type.topping.reject' while the rest of the values would get the 'accept' label.

Please note: 146 dialogs were left unannotated due to the fact that their content has to do more with preference discussion than task completion. We will update the corpus with these dialgos flagged as such.

# API VALIDATION

The ontology classifies API arguments for each vertical into 'required' and 'optional'. For example. 'name.restaurant' is a required parameter whereas 'type.seating' is optional during a restaurant reservation. Conversations that did not contain any of the 'required' parameters were removed from the released dataset.

Additionally, no requirement was imposed on the minimum number of 'required' parameters to be eligible for being part of the released dataset. A common theme among conversations with missing 'required' parameters was the worker's assumption that they were talking to the business directly. For example, in pizza ordering dialogs workers sometimes failed to give a business name. Similar mistakes are seen with the origin or destination fields for ride booking, shop name for auto repair, number of guests of table reservations, etc.

# TRANSCRIPTION NOTES

In a separate task, transcription of crowdsourced user utterances from the two-person dialogs were checked for errors but may still include an occasional typo, misspelling or ungrammatical sequence. In cases where a dialog failed to make sense, workers doing these corrections were given the freedom to insert or delete turns or replace entire phrases with language that made the dialog follow a more sensible path. Shorthand typing conventions originally used by the call center operators such as 'cuz', 'lol' and other non-standard English phrases were left as is. Disfluencies such as 'they um, they want Korean cuisine' were also usually transcribed as spoken, but sometimes transcribers corrected them.

Comments or questions? Join taskmaster-datasets@googlegroups.com to discuss.
