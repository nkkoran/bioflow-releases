# The BioFlow Studio guide

BioFlow Studio sets up an analysis (a GWAS, a polygenic score, Mendelian randomization and more) from your files, runs it as Slurm jobs on your cluster under your own account, and shows what it found. This guide is for someone who has never seen it. Read the pages in order the first time; each one is a task.

1. [Install and first launch](guide/install.md): download, open, the first window, updates.
2. [Sign in to a cluster](guide/sign-in.md): Rorqual and the other Alliance clusters, Duo, **Stay signed in between app restarts**, and what signing in does on the cluster.
3. [Your files](guide/files.md): the file browser, choosing genotypes and a phenotype table, sets of chromosomes, and Data Preview.
4. [Set up an analysis](guide/set-up.md): the gallery, describing what you want in your own words, the walkthrough, what is left to fix, and what each step runs.
5. [Run and watch](guide/run.md): **Run** and its review, trying it on a slice first, the Runs tab, the bell, and runs that go on with BioFlow closed.
6. [Results](guide/results.md): the summary, **Things to check**, the Manhattan and QQ plots, lead loci, the run's report, exports and the results library.
7. [When something goes wrong](guide/when-it-fails.md): why a step failed and the fix, **Re-run from here**, and **Report a problem…**.
8. [R, the terminal and code](guide/r-and-code.md): the tools drawer: Terminal, R workspace, Code and Files.
9. [Settings and look](guide/settings.md): the sections of Settings, theme, density, Motion and Blueprint mode, and the keys.
10. [What BioFlow sends where](guide/sends-where.md): what stays on your cluster, and every lookup or download that leaves it.

Known problems in this beta, and what to do meanwhile, are in [KNOWN-ISSUES.md](KNOWN-ISSUES.md).

The screenshots come from a stand-in cluster, named `127.0.0.1` in them, with a simulated cohort of 500 people, so your numbers will differ. They are in the light theme; the app starts in the dark one.

In the app, **Help ▸ Getting started** opens this page, and **Learn more** beside the sign-in dialog, the gallery, the walkthrough, the Runs tab, the results library, Data Preview, the tools drawer, a failed step and each section of Settings opens the page about it.
