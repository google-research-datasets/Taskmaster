# DRAFT - DATASET NOT YET RELEASED

# COPYRIGHT NOTICE

This is the work of Bill Byrne, Karthik Krishnamoorthi, and Saravanan Ganesh from Google LLC, made available under the Creative Commons Attribution 4.0 License. A full copy of the license can be found at https://creativecommons.org/licenses/by/4.0/

# DATA

## NUMBERS
The Taskmaster-3 dataset consists of 23,757 movie ticketing dialogs (located in Taskmaster/TM-3-2020/data/).

## STRUCTURE
Each conversation in the data file has the following structure:
* __conversation_id:__ A universally unique identifier with the prefix 'dlg-'. The ID has no meaning.
* __utterances:__ An array of utterances that make up the conversation.
* __vertical:__ Information about the task vertical.
* __scenario:__ Information about the task scenario.
* __instructions:__ Instructions for the crowdsourced worker used in creating the conversation.

Each utterance has the following fields:
* __index:__ A 0-based index indicating the order of the utterances in the conversation.
* __speaker:__ Either "user" or "assistant", indicating which role generated this utterance.
* __text:__ The raw text of the utterance.
* __apis:__ An array of API invocations made during the utterance. 
* __segments:__ An array of various text spans with semantic annotations.

Each API has the following structure:
* __name:__ The name of the API invoked (e.g. find_movies).
* __index:__ The index of the parent utterance.
* __args:__ Key-Value pairs representing the argument names and values for the API.
* __response:__ Key-Value pairs containing the API response.

Each segment has the following fields:
* __start_index:__ The position of the start of the annotation in the utterance text.
* __end_index:__ The position of the end of the annotation in the utterance text.
* __text:__ The raw text that has been annotated.
* __annotations:__ An array of annotation details for this segment.

Each annotation has a single field:

* __name:__ The annotation name.

## COLLECTION METHODOLOGY
This collection was created using the "self-dialog" method.

## INSTRUCTIONS
As with the previously released datasets, crowdsourced workers were given instructions explaining one of dozens of movie ticketing scenarios. In order to gather a wide range of conversational scenarios and linguistic phenomena, workers were given both open-ended as well as highly structured conversational tasks.

# ONTOLOGY
Dialog annotations focus on common movie ticketing entities and API calls and responses.

# NOTES
Dialogs were checked for errors but may still include an occasional typo, misspelling or ungrammatical sequence. Shorthand typing conventions originally used by the  such as 'cuz', 'lol' and other non-standard English phrases were left as is. 

_Comments or questions? Join taskmaster-datasets@googlegroups.com to discuss._

