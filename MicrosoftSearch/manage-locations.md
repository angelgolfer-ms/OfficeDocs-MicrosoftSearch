---
title: "Manage locations"
ms.author: dawholl
author: dawholl
manager: kellis
ms.date: 05/30/2019
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
ms.assetid: 8ab9aa00-cd74-405f-8410-9a1c3cfacdb9
description: "Over time, you may need to update a location's status and content to keep it relevant."
---

# Manage locations

## Location
Location helps your users find addresses and locate your organization's buildings by providing an accurate location for offices, campuses, and buildings, along with directions and navigation. Administrators should add all important locations of your organization. Unlike Bookmarks and Q&A, the index is not refreshed immediately, and it can take several hours for new or changed locations to appear in search results.

### Add or edit a single location
1. Go to **Microsoft 365 admin center**.
1. In the navigation pane, go to **Settings** and select **Microsoft Search**.
1. Select **Locations** tab. By default, the **Bookmarks** tab is selected on the **Microsoft Search** page.
1. To add a new location, select **Add new**.
1. To edit a location, select the location in the relevant locations list.
1. As you add or edit the information, the preview automatically updates.
1. Save your changes.

### Bulk add or edit locations
Administrators can use the Import or Export feature to bulk add or edit locations. 

Use the import/export feature to:
1. Bulk add location - Add details in the location template file, and then import it. 
1. Bulk edit locations - Export locations to a .csv file, then edit the location details in the exported .csv file, and then import the updated .csv file.
1. Backups Locations – Export existing locations to a .csv file.

To export or import locations:
1. In the upper-right corner of the **Locations** tab, select **Import**.
Select **Export** to download the existing locations in a .csv file.
1. In the right pane, choose the option to import using a .csv file. 
Download ehe template file for a list of the required fields and details.
1. Add or edit location details in the template file, and then save it on your computer. 
1. In the **Import** locations pane, select **Browse**, and then the .csv file that you want to import.
1. Select **Import**.

Here are some important points regarding the template file:
- Never edit data in these fields: *Id*, *Last Modified*, and *Last Modified By*
- If you include the *Id* of an existing bookmark, it will be replaced with the information in the import file.
- If there is an existing bookmark with the same title or URL, the bookmark will be updated with information in the import file.
- Not all fields in the template file are required and required fields vary depending on the bookmark state.
- Based on the *State* field, bookmarks will be saved as draft, suggested, scheduled, or they will be published automatically.
- For partners who manage multiple organizations, you can export your bookmarks from one org and import them into another. But you must remove the data in the *Id* column before you import.

**Note:** You cannot import Locations if there are any errors in the template file. To prevent errors, make sure your import file is properly formatted and include all the required information. 

For more information on how to prevent error, see [Prevent import errors](manage-bookmarks.md#prevent-import-errors).
