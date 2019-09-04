---
description: >-
  Use PMQL to filter all records in your ProcessMaker Collection to find that
  one you need.
---

# Search Records in a Collection

## Search Records in a ProcessMaker Collection

Use the **Search** function to filter all ProcessMaker [Collections](../what-is-a-collection.md) from the **Collections** page based on your entered text.

{% hint style="info" %}
### ProcessMaker Package Required

The [Collections package](../../package-development-distribution/package-a-connector/collections.md) must be installed in your ProcessMaker instance. The Collections package is not available in the ProcessMaker open-source edition. Contact [ProcessMaker Sales](mailto:sales@processmaker.com) or ask your ProcessMaker sales representative how the Collections package can be installed in your ProcessMaker instance.

### Permissions Required

Your ProcessMaker user account or group membership must have the "Collections: View Collections" permission to view the list of ProcessMaker Collections unless your user account has the **Make this user a Super Admin** setting selected. See the ProcessMaker [Collections](../../processmaker-administration/permission-descriptions-for-users-and-groups.md#collections) permissions or ask your ProcessMaker Administrator for assistance.

Furthermore, your ProcessMaker user account or group membership must have the **View** record-level permission from a Collection's configuration to view that Collection's records. See [Configure a Collection](../manage-collections/configure-a-collection.md#configure-a-processmaker-collection) or ask the manager of that ProcessMaker Collection for assistance.
{% endhint %}

Follow these steps to search records in a ProcessMaker Collection:

1. [View the records for the ProcessMaker Collection](view-all-records-in-a-collection.md#view-all-records-in-a-collection) in which you want to search.
2. In the **PMQL** field, enter your ProcessMaker Query Language \(PMQL\) parameters that compose your record search. Refer to the following PMQL parameter syntax options that are not case sensitive to compose your PMQL search:

   * **Process\(es\):**
     * Use the following syntax as a guide to include one Process in your search criteria:

       `(request = "exact Process name including spaces")`

     * Use the following syntax as a guide to include two or more Processes in your search criteria:

       `(request = "Process name 1" OR request = "Process name 2")`
   * **Request information:**

     Use the following syntax as a guide to reference Request-related information in your search criteria.

     `data.RequestData`

     `data.` represents that what follows derives from Request information, as is used in JSON dot notation. To derive that Request information, view the [**Data** tab in the summary for a completed Request](../../using-processmaker/requests/request-details/summary-for-completed-requests.md#editable-request-data) to view the data from a completed Request, and then use the specific key name \(represented in red-colored text\) in place of `RequestData` in this syntax. Spaces are allowed between operators. Example: `data.last_name = "Canera"`. Note that your ProcessMaker user account or group membership must have the [Requests: Edit Request Data](../../processmaker-administration/permission-descriptions-for-users-and-groups.md#requests) permission. Ask your ProcessMaker Administrator if you do not see the **Data** tab in completed Requests.

   * **ProcessMaker Magic Variables:**

     Following the same syntax as referencing Request-related information, reference ProcessMaker [Magic Variables](../../designing-processes/reference-global-variables-in-your-processmaker-assets.md) in your search criteria. See [Magic Variable Descriptions](../../designing-processes/reference-global-variables-in-your-processmaker-assets.md#global-variable-descriptions).

   * **Status\(es\):** 
     * Use the following syntax as a guide to include one Request status in your search criteria:

       `(status = "In Progress")`

     * Use the following syntax as a guide to include two or more Request statuses in your search criteria:

       `(status = "Completed" OR status = "Canceled")`
   * **Requester\(s\):**
     * Use the following syntax as a guide to include one requester in your search criteria:

       `(requester = "Username1")`

     * Use the following syntax as a guide to include two or more requesters in your search criteria:

       `(requester = "Username1" OR requester = "Username2")`
   * **Participant\(s\):**
     * Use the following syntax as a guide to include one Request participant in your search criteria:

       `(participant = "Username3")`

     * Use the following syntax as a guide to include two or more Request participants in your search criteria:

       `(participant = "Username3" OR participant = "Username4")`
   * **Time Period\(s\):**
     * Use the following syntax as a guide to include a period of time in your search criteria:

       `updated_at < NOW -2 day`

       Use `updated_at < NOW` to represent how much time from the present the sought after Request is, then use `-` followed by an integer to specify that time. The units of time `second`, `minute`, `hour` and `day` are supported.
   * **Operators for use in and between search criterion:**

     * Equal to: `=`
     * Not equal to: `!=`
     * Less than: `<`
     * Greater than: `>`
     * Less than or equal to: `<=`
     * Greater than or equal to: `>=`
     * Use `AND` operators between each set of search criterion to search using multiple criteria.
     * Use the `AND` operator between criterion to search for multiple specified criterion.
     * Use the `OR` operator between criterion to search for either specified criterion.

     Spaces are allowed between operators. Example: `data.last_name = "Canera"`.

   Below is an example of a valid advanced Request search:

   `(request = "Process Name 1" OR request = "Process Name 2") AND (status = "Canceled" OR status = "Error") AND (requester = "Username1" OR requester = "Username2") AND (participant = "Username3" OR participant = "Username4" AND (updated_at < NOW -2 day)`

3. Click the **Search** button![](../../.gitbook/assets/request-task-search-button.png)to search the ProcessMaker Collection's records based on your entered criteria. If there is no search criteria in the **PMQL** field when the **Search** button is clicked, the following message displays: **Search query is empty. Please add search attributes or PMQL before saving.**
4. Optionally, if the [Save Searches package](../../package-development-distribution/package-a-connector/saved-searches-package.md) is installed in your ProcessMaker instance, save and share the record search by clicking the **Save Search** button![](../../.gitbook/assets/save-search-button-requests-tasks.png). See [Save and Share a Record Search](save-and-share-a-record-search.md).

## Related Topics


