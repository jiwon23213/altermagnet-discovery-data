# Magnetic configurations

`magnetic_configurations.csv` contains the initial collinear magnetic
configurations used for the 9 structures entering DFT validation. Each row
specifies one atomic site in one configuration.

- `structure_id`: identifier used throughout the public dataset
- `configuration_id`: `AM`, `FM`, or `NM`
- `atom_index_1based`: one-based site index in the reference structure
- `cif_site_label`: `_atom_site_label` in the reference CIF
- `initial_magmom_muB`: corresponding initial `MAGMOM` in Bohr magnetons
- `reference_structure`: CIF defining the cell, positions, and site order

The one-based atom index is one greater than the numeric suffix of
`cif_site_label` (for example, `Fe0` corresponds to atom index 1). This label
provides an unambiguous mapping even if a CIF parser groups sites by element.

The `AM` configuration is the compensated antiferromagnetic arrangement that
passes the altermagnetic symmetry test. Each validation structure contains two
magnetic atoms, so no additional distinct collinear antiferromagnetic pattern
was used. Zero moments for the `NM` configuration are listed to make the
site-level representation explicit.

The same three initial configurations were used for PBE and the three
element-specific Dudarev `U_eff` values. The configuration table records each
distinct pattern once rather than duplicating it for the four interaction
settings.
