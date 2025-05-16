# TIDO
Github repository related to the usage of the Threat Intelligence Decision Ontology (TIDO)

The directory is divided into the following sections:
- `CQ_queries`: The competency questions used to evaluate the TIDO ontology, along with the answer returned when ran over the extended decision instances 1 and 2 given in the `DIs` folder. 
- `DIs` folder: The annotated decision instances that were identified from the 'De Dienst' podcast (todo:insert citation). 
    - `xml`: The original .xml files downloaded from diagrams.net. 
    - `original`: The .ttl format retured when parsing the .xml files with CHOWLK (todo: insert citation).
    - `extended`: The original .ttl file enriched with additional meta-data. This meta-data includes for every step in the decision instance:
        - The speaker in the podcast, indicated with a `prov:wasAssociatedWith` relation
        - The start time of the step, indicated with a `prov:startedAtTime` relation
        - The end time of the step, indicated with a `prov:endedAtTime` relation
        - The transcript of the audio segment, indicated with `rdf:value` and labeled with the `@nl` language tag
        - The a translation of the audio segment, indicated with `rdf:value` and labeled with the `@en` language tag
        - The case to which the case belongs, indicated with the `tido:contribesTo` relation
- `docs` folder: The files used to render the website
- `transcribe_and_translate.ipynb`: The notebook used to derive the transcriptions and translations from the audio file. This was node using the Whisper "medium" model (todo: insert citation). Additionally, individual speakers were identified using the "pyannote/speaker-diarization-3.1" model (todo: insert citation). When running the notebook, you will be prompted to provide names for each identified speaker. Also, if the intervals from the Whisper and Pyannote model don't match, you will be asked to provide the names of alle the speakers from that interval.
- `transcriptions` folder: The transcriptions and translations produced by the `transcribe_and_translate.ipynb` notebook. These are provided into two formats:
    - `text` folder: Plain text format, divided by 'speaker intervals'. These speaker intervals are intervals with a single continuous speaker. 
    - `dataframes` folder: the same content as the .txt files, but now in .csv format. 
- `TIDO_ORSD.xlsx`: A local copy of the Ontology Requirement Specification Document (ORSD) used for the development of TIDO (todo: insert citation).
- `parse_ontology.ipynb`: Notebook used to add the class and relation descriptions from `TIDO_ORSD.xlsx` to the `TIDO.ttl` file. Additionally, it is used the  
