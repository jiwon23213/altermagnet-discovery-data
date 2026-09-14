# AI-Based Generative Search for New Altermagnetic Candidates with Large Spin Splitting

Data repository accompanying the manuscript *AI-Based Generative Search for
New Altermagnetic Candidates with Large Spin Splitting*.

## Dataset contents

- `generated_structures/generated_structures_51200.tar.gz`: 51,200
  MatterGen-generated CIFs, named `gen_<batch>_<generation_index>.cif`
- `screening/screening_master.csv`: structure-level records through the
  DFT validation stage
- `screening/low_probability_validation.csv`: identifiers, CIF filenames,
  MatAltMag probabilities, and DFT validation outcomes for the 40 candidates
  with `P < 0.9` included in the additional validation analysis
- `final_cifs/`: PBE-relaxed altermagnetic structures of the 8 final
  candidates, with `final_structures.csv` as an index
- `magnetic_configurations/`: site-resolved initial `AM`, `FM`, and `NM`
  configurations for the 9 structures entering DFT validation

The screening stages currently recorded in `screening_master.csv` are applied
in this order:

1. AI-based altermagnet screening with a probability threshold of `P > 0.9`
2. Single magnetic-element-type filter
3. Even magnetic-atom-count filter
4. Novelty filter
5. Uniqueness filter
6. Symmetry-based filter
7. DFT validation of the altermagnetic ground state

Filter-stage fields use `pass`, `fail`, or `not_evaluated`. The last value
means that the structure did not enter that stage because it failed an earlier
stage.

## Additional low-probability DFT validation

`screening/low_probability_validation.csv` lists the 40 candidates with
`P < 0.9` included in the additional DFT validation analysis reported in the
Supporting Information. The columns are:

| Column | Description |
|---|---|
| `structure_id` | Structure identifier matching `screening_master.csv`. |
| `cif_file` | Filename of the original generated structure in `generated_structures/generated_structures_51200.tar.gz`. |
| `ai_based_altermagnet_probability` | MatAltMag probability, identical to the value in `screening_master.csv`. |
| `dft_validation_status` | `pass` if the candidate satisfies the altermagnetic validation criterion used in the reported comparison; `fail` otherwise. |

The file contains 19 `pass` and 21 `fail` entries, corresponding to an
altermagnetic fraction of 47.5%.
