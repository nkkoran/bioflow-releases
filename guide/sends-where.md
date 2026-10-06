# What BioFlow sends where

[The guide](../GUIDE.md) · Previous: [Settings and look](settings.md)

**Your data stays on your cluster.** BioFlow signs in with your own account and runs your jobs there. Your genotypes, phenotypes and results are read where they are, over your SSH connection, and nothing is uploaded to us. BioFlow has no telemetry, no analytics and no crash reporting: crash reports stay on this computer. It has no server of its own, and no AI model: describing an analysis in words and asking the results questions are rules that run here.

What does leave, and when:

## Every time the app opens

- **The update check:** the app reads the list of releases on this repository (`github.com/nkkoran/bioflow-releases`). GitHub sees your IP address and a random number that the updater keeps, to spread updates out. When there is a new version, the app downloads it from the same place.

## When you use a feature that looks something up

From this computer, and only what's listed:
- **Ensembl** (`rest.ensembl.org`, or `grch37.rest.ensembl.org` for GRCh37), for the genes near a peak: the chromosome and the stretch of positions.
- **The GWAS Catalog** (EBI):
  - **How many loci to expect**, and searching for a published GWAS: the trait's words.
  - **Seen before?**: your lead variants' positions, and the trait's words.
  - **A published study you link**: its accession.
  - **A live analysis, if you make one**: the trait's words, again when you sign in or a run ends.
- **OpenGWAS** (`api.opengwas.io`, with your own token, set in **Settings ▸ Data sources**):
  - a dataset's ID;
  - **Compare with a published GWAS**: your lead variants' positions;
  - **MR clumping on OpenGWAS, when you choose it**: the candidate instruments' variant IDs and p-values.
- **Comparing with a published GWAS file** (FinnGen, Pan-UKB, the EBI's FTP): the stretches of that file around your lead variants are read from where it is published, so its host sees those positions.
- **The PGS Catalog**: the ID of a score you choose.
- **Open Targets**: a gene or protein name, when you ask a drug-target question about the results.
- **Published GWAS lists** (FinnGen, Pan-UKB, the eQTL Catalogue, OpenGWAS's list): their public lists are downloaded and searched on this computer, so nothing you type is sent.
- **Public files you link** (a published GWAS on an approved site, such as EBI, Zenodo or FinnGen's bucket): the app reads the file's size and its first rows to describe it.
- **The genome viewer and genome builds**: the reference genome and liftover chains come from UCSC (`hgdownload.soe.ucsc.edu`), or its mirror on Amazon's servers.
- **Running on this computer**: PLINK 2 and DuckDB are downloaded from their own sites when you install them, and checked against their checksums.

## From the cluster, when a run or an install needs it

- **A public file a step reads, and reference data:** downloaded with `curl` on the login node from where it's published, for example GENCODE gene positions or 1000 Genomes frequencies. The cluster's compute nodes have no internet, so this happens before the jobs start. **Ready to run** lists each download.
- **Programs you agree to install:**
  - PLINK 1.9 from its own site;
  - REGENIE and DuckDB from their GitHub releases;
  - LDSC and others with `git clone`;
  - Python packages from the Alliance's wheelhouse, else PyPI.
- **R packages you agree to install:** from CRAN, R-universe, Bioconductor or GitHub.
- **Containers**, only if you choose **Settings ▸ Clusters ▸ Run tools from ▸ Pinned containers**: pulled from their registry (quay.io by default).
- **A message when a run ends**, only if you set a webhook in **Settings ▸ General ▸ Notifications**, and only on a cluster whose compute nodes reach the internet: a small job posts the analysis's name, the cluster's, and whether it finished (or how many jobs did not).
- **Slurm's e-mail**, if you gave an address: sent by the cluster's Slurm, as for any job.

## Links and reports

- **Links you click** (documentation, CCDB, a study's page, this guide) open in your web browser, and only to the sites the app itself links to.
- **Problem reports** are written to a file on this computer. **Post a public GitHub issue** opens a new issue in your browser with your description, the app's version, your system, the kind of cluster ("Rorqual", "Another cluster", "This computer") and a one-line summary filled in; nothing is sent until you submit it, and the file goes only if you attach it.
