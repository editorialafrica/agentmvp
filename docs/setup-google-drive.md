# Google Drive Setup

## Purpose

Google Drive serves as the central repository for generated EditorialAfrica artifacts.

The MVP uses manual uploads. Future milestones will automate this process.

---

## Recommended Folder Structure

EditorialAfrica/

    Nigeria/

        2026/

            2026-07-18/

            2026-07-19/

---

Each production date contains:

Analysis/

Scripts/

Social/

Reports/

---

## Upload Process

1. Run the EditorialAfrica production workflow.
2. Verify the execution report.
3. Create the dated folder if it does not exist.
4. Upload generated artifacts into their respective subfolders.
5. Confirm all required outputs are present.

---

## Naming Convention

Use the filenames defined in:

config/filenames.json

---

## Future Automation

Planned enhancements include:

- Automatic folder creation
- Automatic artifact uploads
- Execution report synchronization
- Version history
- Scheduled production runs