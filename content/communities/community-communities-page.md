---
uid: community-communities-page
---

# Communities page

The `Communities` page, accessible at **Data Management** > **Communities**, is the entry point for creating and participating in communities. Depending on your user roles and permissions, this page displays a different inventory of communities and options.

## Community list

Each community that your tenant participates in is listed on the `Communities` page. From this page, you can review high level details for the community and view if you have access to view data streams from the community.

The following table describes each field listed for a community:

| Field | Description |
|--|--|
| **Community Details** | Opens the `Community details` page for the community, displaying more information about the community. |
| **Tenants** | The number of tenants participating in the community. |
| **Sharing Status** | Indicates whether one or more tenant in the community is sharing data streams. Statuses include: <ul><li><img src="../_icons/custom/check-circle.svg" alt="Sharing Active"/> <strong>Sharing Active</strong>: No tenants in the community have paused sharing.</li><li><img src="../_icons/default/pause-circle.svg" alt="Sharing Paused"/> <strong>Sharing Paused</strong>: One or more tenant in the community has paused sharing their data streams. The total number of tenants that have sharing paused are also listed.</li></ul> |
| **Member Status** | Indicates whether you are [Community Member](xref:community-community-roles#community-member) and can view data shared to the community within `Sequential Data Store`. If the field displays a status of ![information](../_icons/branded/information.svg) **Cannot view shared data**, then you are not a Community Member. If you are a Community Member, this field is omitted.<br><br>For more information on adding a Community Member, see <xref:community-manage-users>. |

Select **Community Detail** to administrate the community or view more information about it. For more information on administrative actions, see the following topics:

- <xref:community-community-administration>
- <xref:community-tenant-administration>

You can also toggle between a card view and a list view.

| View | Icon | Description |
|-|-|-|
| **List view** | ![list view](../_icons/branded/view-list.svg) | Lists each community your tenant participates in as list items. |
| **Card view** | ![card view](../_icons/branded/view-grid.svg) | Lists each community your tenant participates in as cards. |

### Community list sorting

While in **Card view**, you can sort the community list by using the following sorting options:

| Option | Description |
|--|--|
| **Community Membership** | Sorts communities by whether you are a member or the community. |
| **Name** | Sorts communities alphabetically by name. |
| **Description** | Sorts communities alphabetically by description. |
| **Tenant Count** | Sorts communities numerically by the number of tenants in the community. |
| **Sharing Status** | Sorts communities alphabetically by its current sharing status: **Paused** or **Sharing Active**. |

Select the **Sort** ![Sort](../_icons/default/sort-ascending.svg) icon to sort the communities by ascending or descending order for the applied option.

While in **List view**, you can sort the community list by clicking each column header. The list is sorted by the last column header that you click.

## Community toolbar

Use the controls available in the toolbar to find, create, or manage a community.

| Control | Description |
|--------|-------------|
| **Filter Communities** | Type criteria to find a specific community. |
| **Add community**<sup>1</sup> | Creates a new community. For more information on this process, see <xref:community-workflow-create>. |
| **View invitations**<sup>1</sup> | View any invitations that your tenant has pending to join a community. For more information on pending invitations, see <xref:community-view-invitations>.
| **More options** ![More options](../_icons/default/dots-vertical.svg) > **Manage Default Community Administrators**<sup>1</sup> | Configures which roles are automatically added as the default Community Administrators while you are creating or joining a community. For more information, see <xref:communities-manage-default-admins>. |

<sup>1</sup>Requires [Community Administrator](xref:community-community-roles#community-administrators) permissions.

## Community details

When you select a community, additional details about the community open in a side pane. The following table lists each field that displays in the side pane:

| Field | Description |
|-------|-------------|
| **Id** | The identifier for the community. |
| **Name** | The name of the community. |
| **Date created** | The date that the community was created. |
| **Description** | The description of the community. |
| **Sharing Status** | Indicates whether one or more tenant in the community is sharing data streams. Statuses include: <ul><li><img src="../_icons/custom/check-circle.svg" alt="Sharing Active"/> <strong>Sharing Active</strong>: No tenants in the community have paused sharing.</li><li><img src="../_icons/default/pause-circle.svg" alt="Sharing Paused"/> <strong>Sharing Paused</strong>: One or more tenant in the community has paused sharing their data streams. The total number of tenants that have sharing paused are also listed.</li></ul> |
| **Total Streams Shared** | The number of streams shared into the community. If the field displays an **Information** ![information](../_icons/branded/information.svg) icon, then you are not a Community Member. For more information on adding a Community Member, see <xref:community-manage-users>.<br><br>**Tip:** Select the **Launch** ![launch](../_icons/branded/launch.svg) icon to view shared streams for the community in SDS Explorer.|

This pane also lists each tenant that holds membership in the community, along with its sharing status and contact email. Select a contact email to email the recipient. The tenant denoted with the **Crown** ![crown](../_icons/default/crown.svg) icon is the **Administrative Tenant** for the community.
