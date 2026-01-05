Key Changes Made:
1. Added Data Management Section

    Two new buttons: "Export Data" and "Import Data"

    Styled with clear colors (green for export, blue for import)

    Added to the bottom of the app below the color indicators

2. Export Feature

    Creates a JSON file with all grid data

    Includes metadata (export date, version)

    Auto-downloads as grid-tracker-backup-YYYY-MM-DD.json

    Provides visual feedback when clicked

3. Import Feature

    Hidden file input triggered by Import button

    Validates JSON file structure

    Asks for confirmation before overwriting current data

    Refreshes grid display after import

    Provides visual feedback

4. File Structure

```
{
  "gridData": { ... },  // All checkbox states
  "exportDate": "2024-01-15T10:30:00.000Z",
  "version": "1.0"
}
```
6. Usage

    Export: Click "Export Data" → Downloads backup file

    Import: Click "Import Data" → Select backup file → Confirm import

    Files are saved locally on user's device

7. Safety Features

    Confirmation dialog before import

    Basic validation of imported file

    No automatic overwriting

    Preserves original localStorage functionality

This maintains all existing functionality while adding simple backup/restore capability. Users can now:
- Save backups to their device
- Restore from backups if localStorage is cleared
- Transfer data between devices (manually via file transfer)
