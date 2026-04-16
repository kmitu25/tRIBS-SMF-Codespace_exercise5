# tRIBS-SMF Workspace Instructions

## Project Overview

This is a teaching sandbox for GitHub Codespaces focused on hydrological modeling with tRIBS (Triangulated Irregular Network-based Real-time Integrated Basin Simulator) and SMF (Soil Moisture Flash flood) components. It combines:

- **tRIBS**: C++ simulator (pre-compiled)
- **pytRIBS**: Python API for model setup and analysis
- **Jupyter notebooks**: Interactive workflows for data preparation, simulation, and visualization

The workspace is pre-configured with all dependencies and data. It's designed for learning hydrological modeling, not for developing the tRIBS library itself.

See [README.md](README.md) for quick-start guide and troubleshooting.

## Architecture and Workflow

The modeling workflow follows a three-step process:

1. **Setup**: Generate meteorological forcing and build model inputs (mesh, parameters)
2. **Run**: Execute tRIBS simulation
3. **Analyze**: Parse and visualize results

Key components:
- `Project`: Manages metadata and directories
- `Mesh`: DEM processing and watershed delineation
- `Soil/Land/Met`: Parameterization classes
- `Model`: Combines inputs and writes tRIBS config files
- `Results`: Parses simulation outputs

## Key Conventions

- **Imports**: Use `from pytRIBS.classes import *` for core classes
- **Directory Structure**: Auto-generated via `proj.directories` dict
- **File Paths**: Relative to notebook location; data in `../smf_init_data/`
- **Parameters**: Dictionary-style assignment (e.g., `model.optlanduse['value'] = 0`)
- **IDs**: Integer-based soil/land IDs map to properties via lookup tables
- **Naming**: Three config variants: `SMF.in` (default), `SMF_longterm.in`, `SMF_100yr.in`

## Build and Run Commands

The environment is pre-built. To run simulations:

```bash
# From notebook or terminal
tRIBS <input_file>.in > <log_file>.log 2>&1
```

No build/test commands needed - this is a sandbox, not a development project.

## Common Pitfalls

- **Kernel Selection**: Use "Python 3.11.x" kernel in notebooks
- **Whitebox Errors**: "Could not create output settings.json" is non-fatal
- **File Dependencies**: Pre-generated mesh required; custom mesh generation is complex
- **Runtime**: Simulations take 5-30 minutes; results stored locally
- **Paths**: All relative paths assume running from notebook directory

If `tRIBS` is unavailable, rebuild container via "Codespaces: Rebuild Container".

## Exemplar Files

- [Make_SMF_Model.ipynb](workspaces/SMF_pytRIBS/smf_demo/Make_SMF_Model.ipynb): Complete model setup workflow
- [Run_Model.ipynb](workspaces/SMF_pytRIBS/smf_demo/Run_Model.ipynb): Simulation execution and analysis
- [SMF.in](workspaces/SMF_pytRIBS/smf_demo/SMF.in): tRIBS configuration reference
- [smf_assets/](workspaces/SMF_pytRIBS/smf_assets): Architecture diagrams

## For AI Agents

- Modify notebook cells, not standalone .py files
- Start every project with `Project(os.getcwd(), name, epsg)`
- Most errors are data/path issues, not code bugs
- Simulation is deterministic via .in file parameters</content>
<parameter name="filePath">/workspaces/tRIBS-SMF-Codespace_exercise5/.github/copilot-instructions.md