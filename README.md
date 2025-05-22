# TIDO
Github repository related to the usage of the Threat Intelligence Decision Ontology (TIDO)


## Repository structure and description:
- `audio_files` folder: Folder used to locally store the audio files. It is left empty on purpose as the audio files can be downloaded from [this website](https://www.podcastluisteren.nl/pod/De-Dienst) (todo: include instructions on how to do so)
- `transcribe_and_translate.ipynb`: The notebook used to derive the transcriptions and translations from the audio file. This was node using the Whisper "medium" model[^whisper]. Additionally, individual speakers were identified using the "pyannote/speaker-diarization-3.1" model[^pyannote]. When running the notebook, you will be prompted to provide names for each identified speaker. Also, if the intervals from the Whisper and Pyannote model don't match, you will be asked to provide the names of alle the speakers from that interval.
- `transcriptions` folder: The transcriptions and translations produced by the `transcribe_and_translate.ipynb` notebook. These are provided into two formats:
    - `text` folder: Plain text format, divided by 'speaker intervals'. These speaker intervals are intervals with a single continuous speaker. 
    - `dataframes` folder: the same content as the .txt files, but now in .csv format. 
- `TIDO_ORSD.xlsx`: A local copy of the Ontology Requirement Specification Document (ORSD) used for the development of TIDO (todo: insert citation).
- `parse_ontology.ipynb`: Notebook used to add the class and relation descriptions from `TIDO_ORSD.xlsx` to the `TIDO.ttl` file. Additionally, it is used to merge the dataframes from the `transcriptions/dataframe/` folder with the KGs in the  `DIs/original/` folder. The output is stored in the `DIs/extended/` folder. 
- `DIs` folder: The annotated decision instances that were identified from the 'De Dienst' podcast[^dedienst]. 
    - `xml`: The original .xml files downloaded from diagrams.net. 
    - `original`: The .ttl format returned when parsing the .xml files with CHOWLK[^chowlk].
    - `extended`: The original .ttl file enriched with additional meta-data. This meta-data includes for every step in the decision instance:
        - The speaker in the podcast, indicated with a `prov:wasAssociatedWith` relation
        - The start time of the step, indicated with a `prov:startedAtTime` relation
        - The end time of the step, indicated with a `prov:endedAtTime` relation
        - The transcript of the audio segment, indicated with `rdf:value` and labeled with the `@nl` language tag
        - The a translation of the audio segment, indicated with `rdf:value` and labeled with the `@en` language tag
        - The case to which the case belongs, indicated with the `tido:contribesTo` relation
- `CQ_queries`: The competency questions used to evaluate the TIDO ontology, along with the answer returned when ran over the extended decision instances 1 and 2 given in the `DIs` folder. 
- `docs` folder: The files used to render the website

<!-- ## Running Instructions

### Downloading audio files
- Navigate to the website [https://www.podcastluisteren.nl/pod/De-Dienst](https://www.podcastluisteren.nl/pod/De-Dienst) -->

## References
[^pyannote]: H. Bredin, ‘pyannote.audio 2.1 speaker diarization pipeline: principle, benchmark, and recipe’, in INTERSPEECH 2023, ISCA, Aug. 2023, pp. 1983–1987. doi: 10.21437/Interspeech.2023-105.
[^chowlk]: S. Chávez-Feria, R. García-Castro, and M. Poveda-Villalón, ‘Chowlk: from UML-Based Ontology Conceptualizations to OWL’, in The Semantic Web, vol. 13261, P. Groth, M.-E. Vidal, F. Suchanek, P. Szekley, P. Kapanipathi, C. Pesquita, H. Skaf-Molli, and M. Tamper, Eds., in Lecture Notes in Computer Science, vol. 13261. , Cham: Springer International Publishing, 2022, pp. 338–352. doi: 10.1007/978-3-031-06981-9_20.
[^graphDB]: R. H. Güting, ‘GraphDB: Modeling and Querying Graphs in Databases’, presented at the VLDB, 1994.
[^whisper]: A. Radford, J. W. Kim, T. Xu, G. Brockman, C. McLeavey, and I. Sutskever, ‘Robust Speech Recognition via Large-Scale Weak Supervision’, in International conference on machine learning, 2023.
[^dedient]: Liesbeth Rasker, ‘De Dienst’. Accessed: May 30, 2024. [Online]. Available: https://podcastluisteren.nl/pod/De-Dienst

