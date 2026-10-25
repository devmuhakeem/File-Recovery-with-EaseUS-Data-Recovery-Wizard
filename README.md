# File Recovery with EaseUS Data Recovery Wizard

A hands-on lab demonstrating file recovery: intentionally deleting a folder to simulate accidental data loss, then using EaseUS Data Recovery Wizard to scan, locate, and restore it, with an eye toward why the recovery mechanism works at all.

## Scenario
Accidental deletion (user error, software crash, formatting, hardware failure) is a routine, recurring operational problem. This lab simulated that scenario directly — delete a folder, then recover it — to build the practical skill and understand the underlying filesystem behavior that makes recovery possible in the first place.

## What I did

### 1. Simulated an accidental deletion
- Confirmed a folder existed on a separate drive (F:), then deliberately deleted it to set up the recovery scenario

### 2. Installed EaseUS Data Recovery Wizard
- Ran the installer and completed setup

### 3. Ran the recovery process
- **Selected the correct location**: the F: drive specifically, where the deletion occurred
- **Scanned** the drive — the tool reads past the filesystem's "this space is free" markers to look for file data physically still present on disk
- **Filtered results to Deleted Files** to narrow the scan output to what was actually relevant
- **Chose a recovery destination separate from the original drive** — critical, since writing recovered files back onto the same drive being scanned risks overwriting other still-recoverable data
- Reviewed the resulting recovery report and navigated to the restored files, organized under a structure reflecting the original filesystem (NTFS)

## Key takeaways
- "Deleted" in most everyday filesystem operations means the space is marked available for reuse, not that the underlying data was overwritten — that gap is exactly why recovery tools work
- Recovery has a time sensitivity: the longer a drive continues being used after deletion, the more likely the freed space gets overwritten by something new, after which the data is genuinely, not just apparently, gone
- Recovering to a separate destination (never back onto the drive being scanned) is essential — otherwise the recovery process risks overwriting the very recoverable space it's reading from
- The same mechanism that makes accidental recovery possible is exactly why a standard delete (or even a quick format) is insufficient for genuinely destroying sensitive data — secure erasure requires deliberately overwriting the data, not just removing its filesystem entry
- Time works against both goals in the same direction: act quickly to recover data you want back, and act quickly (with a proper wipe) if the goal is making sure data is actually gone

## Tools
EaseUS Data Recovery Wizard (Free)

---
*Completed in an isolated training lab environment on a provisioned Windows VM.*
