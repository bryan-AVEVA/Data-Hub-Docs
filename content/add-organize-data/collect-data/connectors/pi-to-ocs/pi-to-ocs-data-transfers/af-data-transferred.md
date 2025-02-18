---
uid: af-data-transferred
---

# AF data that can be transferred

You can transfer the following AF element data into AVEVA Data Hub:

* Dynamic AF attributes with PI point data references
* Static AF attributes (attributes with no data reference)

Supported dynamic AF attributes can reference a PI point via a Data Archive server name and tag name. This transferred data does not include any data retrieval qualifiers. The associated event data contains simple PI point attributes with the same historical and streaming transfer mechanism as explicit PI points. 

The table below lists the AF objects that can be included in a PI to Data Hub data transfer and what those objects appear as in AVEVA Data Hub.

| AF Object                                             | AVEVA Data Hub Object |
| ----------------------------------------------------- | --------------------- |
| Elements                                              | Assets |
| Dynamic AF attributes with PI point data references   | Asset stream reference properties |
| Static AF attributes<sup>1</sup>                      | Asset metadata properties |

<sup>1</sup>Static AF attributes configured as type 'Boolean' are not supported and will not be transferred.

These AF objects are not included in a PI to Data Hub data transfer:

* Analysis data reference attributes

* Attributes that reference a non-registered data source/Data Archive

* AF categories

* AF enumeration sets

* AF models/layers/connections/ports

* AF tables

* Custom units of measure (UOMs)

* Event frames 

* Excluded attributes

* Extended properties and annotations on assets not supporting AF versioning

* Formula data reference attributes 

* Implicit PI points with attributes that reference other attributes

* Implicit PI points with multiple attributes on an AF element (only one attribute will be transferred)

* PI point arrays

* String builder attributes

* Table lookup attributes

* Weakly referenced elements, composition elements, and element templates

When an AF element is transferred and a corresponding AVEVA Data Hub asset is created, if any attributes are undefined in the element but have default attribute values defined in the applicable AF element template, the default values will be shown in the Asset Explorer. 

## Units of Measure (UOM) transfer

An AF attribute can have two different UOMs set, both the [Default UOM](https://docs.osisoft.com/bundle/af-sdk/page/html/P_OSIsoft_AF_Asset_AFAttribute_DefaultUOM.htm) and the [Source UOM](https://docs.osisoft.com/bundle/af-sdk/page/html/P_OSIsoft_AF_Asset_AFAttribute_SourceUOM.htm) (also called DataReference UOM). AVEVA Data Hub only allows for one UOM. PI to Data Hub considers an attribute's UOM to be its Source UOM if set; otherwise, it uses the default UOM. If both are set and they are different UOM classes, PI to Data Hub logs a warning that they are mismatched, but still uses the Source UOM.

Multiple PI point data reference attributes can reference the same PI point. If multiple attributes reference the same PI point but have different UOMs, a stream UOM is not transferred. If you update your AF attributes to resolve the conflict, the UOM will be transferred.

Custom units of measure (UOMs) do not transfer.

## Performance metrics: AF data transfer

The average data transfer rate is approximately 120-150 assets per second, and 1,000 assets per minute. Streams are created first, followed by AF element and asset data. If you use the same stream for various elements, the transfer time may be shorter.

**Note:** There may be some variance to these numbers.