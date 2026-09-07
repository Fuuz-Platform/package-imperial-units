# ImperialUnits — Fuuz Imperial Units of Measure Package

> **Beta concept — not an accelerator.** Published as a working concept to read, run
> and take the pattern from. It is not a supported deliverable, it carries no service
> level agreement, and it may change or be withdrawn without notice.

A Fuuz package containing Imperial (US Customary) units of measure, unit types, and unit conversions for the Fuuz platform.

## Description

`ImperialUnits@1.0.0.fuuz` is a Fuuz platform package that provides a complete set of **Imperial-only** units of measure for use in any Fuuz application. It seeds three core data models — **UnitType**, **Unit**, and **UnitConversion** — giving your application a US Customary / Imperial measurement system out of the box. This package excludes SI / metric units, making it ideal for environments that operate exclusively with the Imperial system.

## Package Contents

| Data Model | Record Count | Description |
|---|---|---|
| **UnitType** | 17 | Imperial unit categories plus Amount, Currency, Frequency, and Time |
| **Unit** | 83 | Individual Imperial units of measure across all unit types |
| **UnitConversion** | 364 | Conversion factors between Imperial units within the same type |

### Unit Types Included

| Category | Unit Type |
|---|---|
| Area | Area (Imperial) |
| Density | Density (Imperial) |
| Energy | Energy (Imperial) |
| Flow Rate | Flow Rate (Imperial) |
| Force | Force (Imperial) |
| Length | Length (Imperial) |
| Power | Power (Imperial) |
| Pressure | Pressure (Imperial) |
| Speed | Speed (Imperial) |
| Temperature | Temperature (Imperial) |
| Torque | Torque (Imperial) |
| Volume | Volume (Imperial) |
| Weight | Weight (Imperial) |
| **Standalone** | |
| Amount | Amount |
| Currency | Currency |
| Frequency | Frequency |
| Time | Time |

## When to Use This Package

Use this package when:

- You are setting up a **new Fuuz application** that requires a standardized set of **Imperial / US Customary units only**.
- You operate in a region or industry that exclusively uses the **Imperial system** and do not need SI / metric units.
- You want a **lighter-weight alternative** to the full AllUnits package (83 units vs. 164, 364 conversions vs. 1,720).
- You want to **replace the platform's default seed data** with a comprehensive Imperial unit system.

## How to Import

1. Download the `ImperialUnits@1.0.0.fuuz` file from this repository.
2. Open your Fuuz application in the platform.
3. **Drag and drop** the `.fuuz` file into the platform UI to import the package.

## Before You Import — Deleting Existing Seed Data

The Fuuz platform seeds default UnitConversion, Unit, and UnitType records into new applications. These **will conflict** with the package import. You must delete the existing seed data first by running the GraphQL mutations provided in [`deleteSeededUnitData.graphql`](deleteSeededUnitData.graphql).

**Mutations must be run in this order** (foreign key dependencies):

1. **`deleteUnitConversion`** — Remove seeded unit conversions first (they reference Units).
2. **`deleteUnit`** — Remove seeded units next (they reference UnitTypes).
3. **`deleteUnitType`** — Remove seeded unit types last.

The `deleteSeededUnitData.graphql` file contains all three mutations pre-built with the default seeded record IDs.

> **Note:** You may need to update the IDs in the mutations or add additional entries depending on your environment. If your application has had units modified, added, or removed since initial setup, the seeded record IDs may differ from the defaults provided.

## Package Metadata

| Field | Value |
|---|---|
| Package Name | `ImperialUnits` |
| Version | `1.0.0` |
| Spec Version | `2.0.0` |
| Platform Version | `2026.2.1.782` |
| Publisher | `fuuz` |

## Service levels

No service level agreement applies to anything published here. It becomes a supported
deliverable only once it has been implemented by a Fuuz services professional or an
approved Fuuz partner.
