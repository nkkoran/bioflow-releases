# BioFlow Studio: releases

BioFlow Studio is a desktop app for setting up bioinformatics analyses (GWAS with PLINK 2 or REGENIE, polygenic scores, Mendelian randomization, quality control, fine-mapping and more) and running them as Slurm jobs on a cluster you sign in to, such as the Digital Research Alliance of Canada's.

This repository holds its releases and its issues. The code is elsewhere.

**It is a beta.** Expect rough edges, and please tell us about them (below).

- **[Getting started](GUIDE.md):** sign in, pick your files, run a GWAS and read its results, in about 15 minutes. It also says what the app sends where.
- **[Known issues](KNOWN-ISSUES.md):** what doesn't work yet, and what to do instead.

## Download

Open the [latest release](https://github.com/nkkoran/bioflow-releases/releases) and download the file for your computer:

| Your computer | File | Then |
| --- | --- | --- |
| Mac (Apple silicon or Intel) | the `.dmg` | Open it and drag BioFlow Studio to Applications. |
| Windows 10 or 11 | the `Setup` `.exe` | Run it; it installs for your account only. |
| Linux (x86-64) | the `.AppImage`, or the `.deb` | Make the AppImage executable (`chmod +x`) and run it, or install the `.deb`. |

The `.zip`, `.yml` and `.blockmap` files are what the app's updater reads: you don't need them.

## The first time it opens

**Mac:** the app is signed and notarized by Apple, so it opens normally.

**Windows:** the app is not signed yet. SmartScreen says "Windows protected your PC": click **More info**, then **Run anyway**. You do this once per version.

**Linux:** no extra step.

## Updates

The app checks for a new version each time it opens; **Check for Updates** (in the BioFlow Studio menu on a Mac, the Help menu elsewhere) checks now.
- **Mac, Windows and the Linux AppImage** download a new version by themselves and install it when you next quit and reopen the app.
- **The Linux `.deb`:** download the new `.deb` from the releases page and install it.

## Report a bug or suggest something

In the app, choose **Help ▸ Report a Problem…**. It writes a report you can read first (no data, and paths, host names and user names taken out), then opens a new issue here for you to attach it to. The [guide](GUIDE.md#when-something-goes-wrong) says more.

Or [open an issue](https://github.com/nkkoran/bioflow-releases/issues/new/choose) yourself. Say:
- the version (**Settings ▸ About** in the app) and your operating system;
- what you did, what you expected and what happened instead.

A screenshot helps. **Never attach data files, logs from your analyses or anything with people's information in it.** Issues here are public.

## Your data

BioFlow Studio runs your analyses with your own account on the clusters you sign in to, and your files stay there. A few features look things up on public sites, and send them only:
- positions;
- gene names;
- trait words (for example, Ensembl for the genes near a peak, the GWAS Catalog for a trait's studies).

Mendelian randomization's clumping by the OpenGWAS server, when you choose it, sends the candidate variants' IDs and p-values.

The app has no telemetry, analytics or crash reporting. Everything it sends, and when, is listed in the guide's [What BioFlow sends where](GUIDE.md#what-bioflow-sends-where).
