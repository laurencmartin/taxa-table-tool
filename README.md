# taxa-table-tool

A macro-enabled Excel spreadsheet that denominates taxonomy tables to ensure its compliance for use with the *tax_glom* function of the *phyloseq* package. It adds unique species labels to all genera that share species names.

**Why?**

While analysing V1-V2 hypervariable and full-length 16S rRNA sequencing data, we noticed that the bacterial taxa could not be collapsed into species-level ranks, as a number of species with identical names had different higher taxonomic rank labels (often at genus level) and thus, assignment of detected ASVs with species labels could not be performed without manual curation.

Errors are thrown when attempting to assign labels running these lines in R:
```
ps.species <- tax_glom(ps, taxrank="Species")
taxa_names(ps.species) = c(tax_table(ps.species)[,6])
```
To streamline the process, mitigate the introduction of error into the datasets, and facilitate progression to the next steps of the data analysis, a custom, automated taxonomy renaming tool was developed with  Excel (Version 2209) and built-in Visual Basic for Applications programming language. 

**How it works:**
1. Given a taxonomy table in CSV format, the data is organised into its relevant taxonomic ranks in preparation for subsequent detection and re-labelling steps.
2. Following the organisation of the data, the tool observes the genera and species present and records unique entries of each genus and species, as well as their joint appearance.
3. If a duplicate species label differing from the first genus counterpart is detected, it will automatically append an underscore and an available number corresponding to each instance e.g., “Mycoplasma_hominis, Staphylococcus_hominis_1, Campylobacter_hominis_2”.
4. Output is provided in the form of a CSV-formatted taxonomy table.
  
The denominated taxonomy table can then be imported into R for *phyloseq* object generation and subsequent agglomeration of the taxa to species rank.

Please cite this tool as follows:

<sub> _Citation coming soon to a screen near you_ </sub>

We hope this helps! :)

![image](https://github.com/laurencmartin/taxa-table-tool/assets/71465646/367eb654-55d3-41d2-8969-bb2510511ac7)
![image](https://github.com/laurencmartin/taxa-table-tool/assets/71465646/9f5c392d-18a4-4f27-9205-411404b13773)

<sub>This tool was originally developed for the MSc (Human Genetics) thesis of Lauren C. Martin, conducted in the Stellenbosch University Neuropsychiatric Genetics research group, entitled "Species-level profiling of the maternal vaginal bacteriome using full-length 16S rRNA amplicon sequencing with application to FASD".</sub>

<sub> Application of this tool features in **Short-read full-length 16S rRNA amplicon sequencing for characterisation of the respiratory bacteriome of captive and free-ranging African elephants (_Loxodonta africana_)**.</sub>

<sub> **Developed by Déan Nell.** </sub>
