# Revision-sheet generator

Copying comments of reviewers of reviewers into a table can be tedious.
This python script automatically generates a revision sheet (word or latex) from a text file containing comments of reviewers.

# Usage and options

The script creates a separate comment-row for each paragraph ending with a new line.
Entering a ```\newline``` at the end of a paragraph (in the text file) indicates that both paragraphs should be transferred to the same row.

```
usage: generate_revision_sheet.py [-h] [--input INPUT] [--format FORMAT]
                                  [--output OUTPUT] [--i I]

Revision-sheet generator

optional arguments:
  -h, --help       show this help message and exit
  --input INPUT    path to the review text file
  --format FORMAT  format of the output document , w for word (default) or
                   t for tex
  --output OUTPUT  path to the file where to put the results (optional)
  --i I            start of comment numbering (optional)

```

TODO: 
- [ ] do not continue numbering (instead use prefixes, e.g., #ECIS_13 or #CAIS_R2_15; and possibly reviewer/ae prefixes, e.g., #CAIS_R2_R1_3 - for revision 2 and reviewer 1) - this makes it much easier to prepare the final revision sheets (simply search and replace)


# Example

Running ``` python3 generate_revision_sheet.py --input feedback.txt --format w``` on the [feedback file](feedback.txt)
```
Thank you for submitting your paper to this journal. Please explain how you address the reviewers' comments.

Reviewer 1:
I really enjoyed reading the paper. The only comments I have are:
The introduction needs to be more precise
The background needs to be rewritten
The methods are nice but you could also do something else

Reviewer 2:
I think this paper should never be published. It has major flaws in each section:

Introduction\newline
The topic is only relevant for practitioners. This is unacceptable.

...

```

returns the following table:

| Nr. | Comment                                                                                                      | How the comment is addressed |
| :-- | :----------------------------------------------------------------------------------------------------------- | :--------------------------- |
| 1   | Thank you for submitting your paper to this journal. Please explain how you address the reviewers' comments. |                              |
| 2   | Reviewer 1: I really enjoyed reading the paper. The only comments I have are:                                |                              |
| 3   | The introduction needs to be more precise                                                                    |                              |
| 4   | The background needs to be rewritten                                                                         |                              |
| 5   | The methods are nice but you could also do something else                                                    |                              |
| 6   | Reviewer 2: I think this paper should never be published. It has major flaws in each section:                |                              |
| 7   | Introduction The topic is only relevant for practitioners. This is unacceptable.                             |                              |
| 8   | ...                                                                                                          |                              |

# Similar Projects

- [Extract review comments from PDF](https://github.com/0xabu/pdfannots)
