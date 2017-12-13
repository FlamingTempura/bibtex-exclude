## bibtex-exclude

bibtex-exclude is a tool to help with conducting a literature review by applying exclusion criteria to entries within BibTeX files.

Install:
```
npm install bibtex-exclude --global
```

### Instructions

1. Create a directory to work in. Within this, create the directories `databases` and `exclusion`.

2. Search academic databases and export results as BibTeX into the `databases` directory. E.g. you might put the exported results of a search on ACM DL in `databases/acm.bib`.

3. Run `bibtex-exclude`. Results from each database will be combined (with duplicates merged) and output to `results.bib`.

4. Read through `results.bib`. Any results which don't conform to your review inclusion criteria should be copied and pasted to bib files in the `exclusion/` directory. The name for each bib file should correspond to the reason for exclusion - e.g. `exclusion/not-empirical.bib` might contain any BibTeX entries which correspond to papers which do not report empirical findings.

5. Run `node index.js` to update `results.bib`. Again, the results from each database will be included. Any entries in the exclusion bib files will be removed. The tool will also output the count of results at each stage, e.g.:
   ``` 
Loading databases...
                           acm: 40
                     ebscohost: 129
                         jstor: 12
                         known: 17
                        pubmed: 15
                        scopus: 355
                  webofscience: 151
                         Total: 719

Removing duplicates...
                    duplicates: (240)
                         Total: 479

Applying exclusions...
                     off-topic: (256)
              not-quantitative: (137)
                 not-empirical: (38)
                   not-english: (13)
                TOTAL ELIGIBLE: 35 (479 - 444)
Results written to results.bib
```

If you wish to repeat the literature review in the future, you can re-use the exclusion lists to exclude those records from new database results. This makes it much easier to keep a literature review up-to-date.

Exclusion lists could also be built from database searches for papers which should not form part of your results.