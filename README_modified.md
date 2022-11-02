When testing NS-Forest_v3 (https://github.com/JCVenterInstitute/NSForest) I found several issues, most of them fixed following the advice by @ChristinaSteyn in one of the repository issues (https://github.com/JCVenterInstitute/NSForest/issues/7#issue-1124094198).

In addition, I found out that if a gene with a name starting with a number is selected as first option in a betaQuery variable, then the code will break as pandas.DataFrame.query (https://github.com/JCVenterInstitute/NSForest/blob/968fa470a4380a753a187e0d66282e54342e2273/NSForest_v3.py#L127) will not understand the input. I have fixed this issue along with the others in NSForest_v3_modified.py:

In short, I modify the gene names in the adata object by adding a prefix of 4 characters ('AER_' in this case but it could be anything as long as it is not part of an existing gene name in the genome) and remove the prefix before exporting the results.
