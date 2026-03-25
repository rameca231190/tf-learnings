# tf-learnings scripts

## Full parallel inventory (all files)

- Template: `scripts/templates/efs_usershome_inventory_parallel.sh.j2`
- Example playbook snippet: `scripts/collect_usershome_file_inventory_parallel_example.yaml`

This is the fastest version of the *full tree* walk, but it still stats every file under `base_path`.

## Extensions-only parallel inventory (recommended for speed)

- Template: `scripts/templates/efs_usershome_inventory_extensions_parallel.sh.j2`
- Example playbook snippet: `scripts/collect_usershome_file_inventory_extensions_parallel_example.yaml`

This avoids the slow extension-filter stage by only emitting candidate paths from `find` (supported extensions hardcoded in the template).

Both scripts:
- write one output line per file
- use `scan_location` inside the output filename
- run `mkdir -p` for output directories (including when `scan_location` contains `/`)

