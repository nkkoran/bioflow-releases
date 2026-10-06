# When something goes wrong

[The guide](../GUIDE.md) · Previous: [Results](results.md) · Next: [R, the terminal and code](r-and-code.md)

## A step failed

The Runs tab marks the run **Failed at step N of M**, with a red strip, one part per step, and says in a line what happened. The bell says so too, and so does a notification if the window is not in front.

Click the failed step to see why. BioFlow reads Slurm's record of the job and the end of its log, and says what happened in plain words, then what to do. For example:
- "It ran out of memory: it used 7.6 GB of the 8 GB it asked for."
- "It ran out of time: Slurm stopped it at its limit of …"
- "A file it reads is not there: …"
- "The trait … is not a column of the phenotype table."

**What this is based on**, under it, shows Slurm's line for the job and the last lines of its log.

**What to do about it:**
- **A one-click fix**, where one change would let it run: for example **Memory 8 → 16 GB, and re-run**, or **Time 24 → 36 h, and re-run**. It changes the step's setting, then runs it again. When only some chromosomes failed, it retries only those ("…, and retry the 3 failed tasks").
- **Take me there** opens the setting the explanation names, and changes nothing until you do.
- **Re-run from here** runs that step and the steps after it again, reusing the finished steps before it. When that means re-running every step on a cluster, hold it for a second (**Hold to re-run**); letting go early runs nothing.
- **Debug this step** opens a shell on a compute node, in the Terminal, with the job's size, folder, modules and script ready, to try its commands by hand.
- **Show what to do**, at the top of the Runs tab, goes to the step whose failure needs a change first.

**Not sure whether a step finished?** If Slurm has forgotten a job (clusters keep its record only a few days) and BioFlow last looked before it ended, BioFlow reads the step's own record in the run's folder. When that can't tell either, the step says it can't tell, never that it failed: **Refresh**, in the run's **⋯** menu, looks again, or **Re-run from here** runs it again.

## Tell us

Choose **Help ▸ Report a problem…**, or **Report a problem…** under a failed step's explanation (it then says where it came from).

1. Say what you did, what you expected and what happened instead. **Include BioFlow's log of the last 24 hours** is ticked; leave it ticked unless you'd rather not.
2. The dialog shows **Exactly what the file holds**: what you wrote, the app's version, your computer's system, the app's state (steps, statuses and settings, not their values) and the log. Paths, host names, user names, e-mail addresses and keys are taken out, and nothing from your files, previews or jobs' output is in it. Read it first: nothing leaves your computer until you press the button.
3. **Post a public GitHub issue** writes the report into your Downloads folder and opens a new issue on this repository in your browser, with your description, the version, your system and a one-line summary filled in. Drag the file into the issue, then submit it.

You need a GitHub account to file an issue. **Issues here are public:** never paste data, file contents or anything about people into one. For anything that isn't for a public page, ask the person who invited you.

If the app itself won't start or freezes, file an issue by hand from [the issues page](https://github.com/nkkoran/bioflow-releases/issues/new/choose). Give the version (**Settings ▸ About**, or **BioFlow Studio ▸ About BioFlow Studio** on a Mac) and your operating system. BioFlow's own logs are in the folder **Settings ▸ Folders ▸ Logs** shows.

Known problems, and what to do meanwhile, are in [KNOWN-ISSUES.md](../KNOWN-ISSUES.md).

Next: [R, the terminal and code](r-and-code.md).
