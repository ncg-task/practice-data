# practice-data

Practice Evaluation Phase dataset for the SemEval 2020 Task 11 NLPContributionGraph Shared Task

#### Input
The dataset is formatted as follows:

    [task-name-folder]/                                # entity_linking, face_alignment, face_detection, natural_language_inference
        ├── [article-counter-folder]/                  # ranges from 0 to N-1 if we annotated N articles per task
        │   ├── [articlename]-Grobid-out.txt           # plaintext output from the [Grobid parser](https://github.com/kermitt2/grobid)
        │   ├── [articlename]-Stanza-out.txt           # plaintext preprocessed output from [Stanza](https://github.com/stanfordnlp/stanza)
        │   └── ...                                    # if N articles were annotated, this repeats (N-1) more times
        └── ...   

#### Submission to Codalab
The submission will have be organized per the following directory structure:

    [task-name-folder]/                                # entity_linking, face_alignment, face_detection, natural_language_inference
        ├── [article-counter-folder]/                  # ranges from 0 to N-1 if we annotated N articles per task
        │   ├── sentences.txt                          # annotated contribution sentences in the file identified by the sentence number in the preprocessed data with counter starting at 1
        │   └── entities.txt                           # annotated phrases from the contribution sentences where the phrase spans are specified by their first and last token numbers with the token counter starting at 1
        │   └── triples/                               # the folder containing information unit triples one per line
        │   │   └── research-problem.txt               # `research problem` triples (one research problem statement per line)
        │   │   └── model.txt                          # `model` triples (one statement per line)
        │   │   └── ...                                # there are 12 information units in all and each article may be annotated by 3 or 6
        │   └── ...                                    # if N articles were annotated, this repeats (N-1) more times
        └── ...                                        # if K tasks were selected overall, this repeats (K-1) more times		
		
A valid sample submission for the practice phase can be downloaded here https://github.com/ncg-task/practice-data/blob/master/submission.zip

#### Additional Notes

Please see the [evaluation script](https://github.com/ncg-task/scoring-program/blob/master/evaluation.py), lines 274 to 285 for the expected information unit file names.

Further, within each file, the expected top-level node names are:

1. research-problem.txt 
`has research problem`

2. code.txt
`Code`

3. dataset.txt
`Dataset`

4. Approach.txt
`has`, `Approach`

5. Model.txt
`has`, `Model`

6. ...

Except for IUs 1, 2, and 3, the rest of the IUs add the predicate `has` in lowercase and the IU name in sentence case (e.g., experimental-setup.txt would be `Experimental setup`).

For concrete examples, please see the files in the triples folders provided as the NCG task [training data](https://github.com/ncg-task/training-data).
