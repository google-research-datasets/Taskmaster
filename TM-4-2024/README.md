# COPYRIGHT NOTICE

This is the work of Bill Byrne, and Saravanan Ganesh from Google LLC, made available under the Creative Commons Attribution 4.0 License. A full copy of the license can be found at https://creativecommons.org/licenses/by/4.0/

# DATA
These datasets are released with the paper 'PERL: Parameter Efficient Reinforcement Learning from Human Feedback' at https://arxiv.org/abs/2403.10704. Please cite accordingly.

## BASICS
The Taskmaster-4 dataset consists of 6500 coffee ordering dialogs (located in Taskmaster/TM-4-2024/data/), and 3000 reward examples (located in Taskmaster/TM-4-2024/reward).

## COLLECTION METHODOLOGY
This collection was created using the "self-dialog" method. This means a single, crowd-sourced worker is paid to create a conversation writing turns for both speakers, i.e. the customer and the coffee agent. In order to gather a wide range of conversational scenarios and linguistic phenomena, workers were given both open-ended as well as highly structured conversational tasks. In all, we used over three dozen sets of instructions while building this corpus. The "instructions" field in data.json provides the exact scenario workers were given to complete each dialog. In this way, conversations involve a wide variety of paths.
