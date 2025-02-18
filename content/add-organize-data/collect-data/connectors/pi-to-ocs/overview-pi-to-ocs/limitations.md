---
uid: pi-to-ocs-limitations
---

# Limitations of PI to Data Hub

The following table lists the known limitations for PI to Data Hub.

| Issue | Restrictions | 
| ------------- | ----------------- | 
| Restrictions for PI point transfers | <ul><li>Point must belong to the classic or base point class.</li><li>Point type must be Float16, Float32, Float64, Int16, Int32, Digital, Timestamp, or String.</li><li>Must not be a future PI point.</li></ul> |
| High availability (HA) & collectives | <ul><li>PI to Data Hub does not support high availability (HA) features or connecting to a Data Archive collective.</li><li> AF elements or attributes that reference a collective name instead of one of the nodes are not supported.</li><li> AF Collectives are supported natively by PI to Data Hub.</li></ul> |
| PI to Data Hub Agent registration | <ul><li>Multiple PI to Data Hub Agents can connect to and transfer data from the same Data Archive if the agents are installed on different machines and assigned to different namespaces. Only one agent can be installed on each computer.</li></ul> |
| Data Archive | <ul><li>PI to Data Hub does not write events back to Data Archive from AVEVA Data Hub.</li></ul> |
| SDS streams indexes | <ul><li>Does not support multiple values at a given index.</li><li>If a Data Archive tag has multiple values at a given timestamp, AVEVA Data Hub will store the first value returned.</li></ul> |
| Custom UOM data | <ul><li>Custom units of measure (UOMs) that are not one of the predefined UOM classes in AVEVA Data Hub are not supported. During the transfer of AF element data, AF elements with custom UOMs will not have their corresponding asset's UOM property set.</li></ul> |
| PI Analysis Service | <ul><li>If you use PI to Data Hub with the PI Analysis Service, be sure to save analysis outputs to PI points.</li></ul> |
| Multiple UOMs | <ul><li>If multiple attributes reference the same PI point but have different UOMs, a stream UOM is not transferred.</li></ul> |
