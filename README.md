# BioFlow Studio: releases

BioFlow Studio is a desktop app for setting up bioinformatics analyses (GWAS with PLINK 2 or REGENIE, polygenic scores, Mendelian randomization, quality control, fine-mapping and more) and running them as Slurm jobs on a cluster you sign in to, such as the Digital Research Alliance of Canada's.

This repository holds its releases and its issues. The code is elsewhere.

**It is a beta.** Expect rough edges, and please tell us about them (below).

## Download

Open the [latest release](https://github.com/nkkoran/bioflow-releases/releases) and download the file for your computer:

| Your computer | File | Then |
| --- | --- | --- |
| Mac (Apple silicon or Intel) | the `.dmg` | Open it and drag BioFlow Studio to Applications. |
| Windows 10 or 11 | the `Setup` `.exe` | Run it; it installs for your account only. |
| Linux (x86-64) | the `.AppImage`, or the `.deb` | Make the AppImage executable (`chmod +x`) and run it, or install the `.deb`. |

The `.zip`, `.yml` and `.blockmap` files are what the app's updater reads: you don't need them.

## The first time it opens

The betas are not signed yet, so your computer can't check who made them and will stop the first launch. This is expected.

**Mac:**
1. Double-click BioFlow Studio. macOS refuses to open it.
2. Open **System Settings → Privacy & Security** and scroll to Security.
3. Next to "BioFlow Studio was blocked", click **Open Anyway**, then confirm.

You do this once per version. If macOS says the app is **"damaged and can't be opened"**, run this in Terminal, then open it again:

```bash
xattr -cr "/Applications/BioFlow Studio.app"
```

The command removes macOS's download quarantine from this one app. Only run it on an app you downloaded from this page.

**Windows:** SmartScreen says "Windows protected your PC". Click **More info**, then **Run anyway**.

## Updates

- **Windows and the Linux AppImage** download a new version by themselves and install it when you next quit and reopen the app.
- **Mac** can't install updates into an unsigned app. When a new version is out, the app says so, and **Download** opens its page here. Replace the app in Applications with the new one, then repeat the first-launch steps.

## Report a bug or suggest something

[Open an issue](https://github.com/nkkoran/bioflow-releases/issues/new/choose). Say:
- the version (on a Mac, BioFlow Studio ▸ About BioFlow Studio; elsewhere, the name of the file you downloaded) and your operating system;
- what you did, what you expected and what happened instead.

A screenshot helps. **Never attach data files, logs from your analyses or anything with people's information in it.** Issues here are public.

## Your data

BioFlow Studio runs your analyses with your own account on the clusters you sign in to, and your files stay there. A few features look things up on public sites, and send them only:
- positions;
- gene names;
- trait words (for example, Ensembl for the genes near a peak, the GWAS Catalog for a trait's studies).

Mendelian randomization's clumping by the OpenGWAS server, when you choose it, sends the candidate variants' IDs and p-values.
