# Known issues

These are problems we know about in the current beta, each with what to do meanwhile. If you hit something that isn't here, please [open an issue](https://github.com/nkkoran/bioflow-releases/issues/new/choose), or use **Help ▸ Report a Problem…** in the app.

## Runs

**A step can show as failed when Slurm has forgotten its job.**
- **What happens:** clusters keep a job's accounting record for a limited time, often a few days. If BioFlow last looked at a run before its job ended, and only looks again after that record is gone, it can't tell whether the job finished, and marks the step failed. It says: "Slurm has no record of job … any more, so BioFlow cannot tell whether this step finished."
- **Who it affects:** runs left for days with BioFlow closed.
- **What to do:** open the run folder (the Runs tab's **⋯** menu ▸ **Open run folder**). If the step's outputs are there and look complete, the step did finish. Otherwise, select the step and click **Re-run from here**. To avoid it, open BioFlow at least once a day while a long run goes.

**A job Slurm was slow to accept can be counted as refused.**
- **What happens:** if `sbatch` answers with an error such as "Socket timed out" while the cluster is busy, BioFlow treats the job as refused ("Slurm refused this step: …"), though Slurm may have queued it anyway. That job can then run without BioFlow following it.
- **Who it affects:** anyone, rarely, when the cluster's scheduler is overloaded.
- **What to do:** in the **Terminal** tab, run `squeue -u $USER --format="%i %j %T"`. Jobs BioFlow starts are named `bioflow-<step>`. Cancel any left over with `scancel <job id>`, then use **Re-run from here** on the step.

**"open failed" from the cluster under heavy load.**
- **What happens:** a cluster lets one sign-in open about 10 channels at once. BioFlow can open more when several things happen together: browsing files, copying files, a busy Runs tab, the Terminal and the R workspace. A command may then fail with an error such as "Channel open failure: open failed". BioFlow tries again a few times first.
- **Who it affects:** heavy use, mostly during large copies.
- **What to do:** wait for copies to finish, then try again.

## Programs on the cluster

**REGENIE on Rorqual.**
- **What happens:** Rorqual offers no REGENIE module. When a REGENIE step runs there, Run's checks offer **Install REGENIE now**, which installs BioFlow's pinned REGENIE 4.1.3 into `~/bioflow/tools`. That build needs the OpenMP library (libgomp). BioFlow fixes that with the Alliance's `setrpaths.sh` where it can; if REGENIE still can't start, the install says so and names the missing library.
- **Who it affects:** REGENIE analyses (GWAS with REGENIE, rare-variant tests) on clusters with no REGENIE 3.6 or newer.
- **What to do:** if the install fails, choose **Settings ▸ Clusters ▸ Run tools from ▸ Pinned containers** to run REGENIE from its container (the cluster needs Apptainer). Or name a REGENIE module your cluster has in **Settings ▸ Modules**.

## Windows

**Analyses can't run on This computer.**
- **What happens:** every step runs as a bash script, and Windows has no bash for it. **Run on this computer** and **Practice on simulated data** are not offered, and **Settings ▸ This computer** says why.
- **Who it affects:** Windows.
- **What to do:** run on a cluster.

**"Stay signed in between app restarts" doesn't work.**
- **What happens:** the switch is shown, but connecting with it on fails: "OpenSSH ControlPersist transport is currently supported on macOS and Linux." The `bioflow` command line signs in only through it, so it can't sign in on Windows either.
- **Who it affects:** Windows.
- **What to do:** leave the switch off. Duo then asks at each sign-in.

**A local folder of chromosomes isn't recognised as a set.**
- **What happens:** for files on this computer, chromosome numbers are read from names split at `/`, which Windows paths don't use. A folder per chromosome on this computer is then not seen as one set.
- **Who it affects:** Windows, for files on this computer, not on the cluster.
- **What to do:** put the files on the cluster and choose them there.

**Joining tables on this computer names them by their whole path.**
- **What happens:** in the file list, **Join these…** on two tables on this computer names each table by its whole Windows path, and the join may fail.
- **Who it affects:** Windows, for tables on this computer.
- **What to do:** join tables that are on the cluster.

## Not in this beta

The UK Biobank Research Analysis Platform (RAP), Globus transfers and nf-core pipelines are not yet tested with real accounts, so they are switched off. A pipeline that uses one opens, but doesn't run.
