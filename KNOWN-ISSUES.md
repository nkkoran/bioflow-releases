# Known issues

These are problems we know about in the current beta, each with what to do meanwhile. If you hit something that isn't here, please [open an issue](https://github.com/nkkoran/bioflow-releases/issues/new/choose), or use **Help ▸ Report a problem…** in the app ([the guide](guide/when-it-fails.md#tell-us) says how).

## Programs on the cluster

**REGENIE on Rorqual.**
- **What happens:** Rorqual offers no REGENIE module. When a REGENIE step runs there, Run's checks offer **Install REGENIE now**, which installs BioFlow's pinned REGENIE 4.1.3 into `~/bioflow/tools`. That build needs the OpenMP library (libgomp). BioFlow fixes that with the Alliance's `setrpaths.sh` where it can; if REGENIE still can't start, the install says so and names the missing library.
- **Who it affects:** REGENIE analyses (GWAS with REGENIE, rare-variant tests) on clusters with no REGENIE 3.6 or newer.
- **What to do:** if the install fails, choose **Settings ▸ Clusters ▸ Run tools from ▸ Pinned containers** to run REGENIE from its container (the cluster needs Apptainer). Or name a REGENIE module your cluster has in **Settings ▸ Programs** (**REGENIE module**, under the modules on the cluster).

## Windows

**Analyses can't run on This computer.**
- **What happens:** every step runs as a bash script, and Windows has no bash for it. **Run on this computer** and **Practice on simulated data** are not offered, and **Settings ▸ Programs ▸ This computer** says why.
- **Who it affects:** Windows.
- **What to do:** run on a cluster.

**No "Stay signed in between app restarts".**
- **What happens:** staying signed in uses OpenSSH's ControlPersist, which Windows' OpenSSH lacks, so the switch isn't offered and Duo asks at each sign-in. The `bioflow` command line signs in only through a kept sign-in, so it can't sign in on Windows.
- **Who it affects:** Windows.
- **What to do:** keep the app open between analyses, so one sign-in lasts.

**A local folder of chromosomes isn't recognised as a set.**
- **What happens:** for files on this computer, chromosome numbers are read from names split at `/`, which Windows paths don't use. A folder per chromosome on this computer is then not seen as one set.
- **Who it affects:** Windows, for files on this computer, not on the cluster.
- **What to do:** put the files on the cluster and choose them there.

**Joining tables on this computer names them by their whole path.**
- **What happens:** in the file browser, **Join these…** on two tables on this computer names each table by its whole Windows path, and the join may fail.
- **Who it affects:** Windows, for tables on this computer.
- **What to do:** join tables that are on the cluster.

## Not in this beta

The UK Biobank Research Analysis Platform (RAP), Globus transfers and nf-core pipelines are not yet tested with real accounts, so they are switched off. A pipeline that uses one opens, but doesn't run.
