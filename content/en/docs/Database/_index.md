---
title: "Database Overview"
linkTitle: "Database Overview"
simple_list: true
weight: 20
---

This article explains Flourish database structure, database relations, and gives an idea of how to get to work with databases. In addition, this article showshow the most commonly used Tables and Schemas are arranged and describe their structure in detail.

## Database levels concept

Flourish has three types of Databases: **Company Level**, **Facility Level**, and **Common**

**Example:** Client has 1 Cultivation Center and 2 Stores, in Flourish terminology, that means that client has 3 Facilities. Each facility has its own database, resulting in 3 **Facility Level** databases in total. However, there is a 4-th **Company Level** database. Company DB contains data thats spans across facilities, i.e `items`,`strains`, `customers`, etc.

**Common** database contains only static data that is shared between Facility and Company databases. It is used, for instance, to perform [Purchase Limits validation]()

Every *Facility Level* database has `VIEWS` to reference every table at the *Company Level.*

Let's say that we have the following:

```text
CompanyDB: ABC
CultivationFacility: DEF
StoreFacility: GHI
StoreFacility: JKL
```

The item table is defined in CompanyDB ABC, however, we have an `item` VIEW for `DEF`, `GHI`, `JKL`, which points to `ABC.item`, which means that following queries all return same data:

```sql
SELECT * from ABC.item;
SELECT * from DEF.item;
SELECT * from GHI.item;
SELECT * from JKL.item;
```

For development purposes use the following databases:

**Company:**  `58b9ae9c280e20ea24a126b8`

**Facility:** `58b9b09d280e20ea24a126bb`

## Facility level

### Grow module tables

- plant: one row per plant
- group_hdr: one row per group
- group_strain_dtl: one row per group / per strain
- metrc_plant_batch
- metrc_plant_batch_dtl
- harvest_hdr: one row per harvest
- harvest_strain_dtl: one row per harvest / per strain
- harvest_dtl: one row per weight entry (can be plant specific)
- group_harvest: relationship between group_hdr and harvest_hdr

### Group

Things to remember:

- A group is a grouping of plants that is tracked together;
- A group can only be in a single location/status at one time;
- Groups can contain multiple strains;

#### Tables

- group_hdr
- group_strain_dtl
- plant

#### Table Relationships

```sql
group_hdr (gh) -> plant (p)
gh.group_hdr_pk = p.group_hdr_pk*
group_hdr (gh) -> group_strain_dtl (gsd)
gh.group_hdr_pk = gsd.group_hdr_pk
group_strain_dtl (gsd) -> plant (p)
gsd.group_hdr_pk = p.group_hdr_pk AND gsd.strain_id = p.strain_id
group_strain_dtl.group_hdr_pk
```

### Plant batches

To accommodate METRC requirements, Flourish team has designed the concept of "plant batches", which represent subset of plants that were created at one period of time.

**Example:** Anytime someone goes through the process of creating plants Grow -> Clone -> Create Plants, a new plant batch is created.

**Things to know:**

- No changes will ever be required to the plant batches design idea;
- Created batches are stored in the `metrc_plant_batch` table.
- Once a plant is associated with a plant batch, its association cannot be changed.
- Plants can move around and group can be split or combined, so we keep a record of which plant batches belong to which groups using the `metrc_plant_batch_group` tables.

#### Tables

- metrc_plant_batch
- metrc_plant_batch_group

#### Table Relationships

```sql
plant (p) -> metrc_plant_batch (mpb)
p.metrc_plant_batch_id = mpb.metrc_plant_batch_id
metrc_plant_batch (mpb) -> metrc_plant_batch_group
mpb.metrc_plant_batch_id = mpbg.metrc_plant_batch_id
group_hdr (gh) -> metrc_plant_batch_group (mpb)
gh.group_hdr_pk = mpbg.group_hdr_pk
```

## Harvest

Harvests are similar to groups, they represent the same thing: a grouping of plants, the only difference is that they were all harvested together. Once a group is ready, it is then harvested

**Note:** Harvests are a different entity than groups.

**Things to know:**

- A harvest can contain multiple groups
- A harvest can contain multiple strains
- Weights are recorded on harvests and then packages can be created from these weights

#### Tables

- harvest_hdr
- harvest_strain_dtl
- harvest_dtl
- group_harvest

## Company Level

[TBA]