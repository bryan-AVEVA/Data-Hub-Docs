---
uid: data-view-link-fields
---

# Link data fields

Data items included in a data view may have slight differences in property naming, despite those properties representing the same logical thing. For example, data from one equipment manufacturer reports `Temperature`, while another reports `Temp` instead.

Data views can overcome property naming differences by linking these similar properties into a single data field. This applies to stream properties referenced by Id or by name, and to stream metadata keys. Asset properties can also be linked.

When data fields are linked, AVEVA Data Hub converts the data types in the linked fields into compatible data types. For more information, see <xref:data-view-data-type-conversion>.

## To link fields

To link data items, drag and drop one field onto another. Properties can only be linked to other properties of the same data type. Metadata can only be linked to other metadata of the same data type.

![Field sets: link fields](_images/link-fields.gif)

## To unlink fields

To unlink a linked field, select **More options** ![more options](../../_icons/branded/dots-vertical.svg) > ![unlink all](../../_icons/default/link-variant-off.svg) **Unlink All**.

## Developer documentation

Within the Developer Guide, the term "linking" is synonymous with "consolidating". For more information, see <xref:ConsolidateDataFields>.
