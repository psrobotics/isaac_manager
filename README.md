# Isaac Made Easy

Tested with:
* Ubuntu 22.04
* IsaacSim 5.0.0
* IsaacLab 2.2.0

## Conda

```bash
make
conda activate ilab
```

*assumes you have conda installed*

## UV


```bash
make uv
source ilab/bin/activate
```

## Available Targets

### Main Targets
- **`all`** - Run complete setup: deps → gitman → clean → setup
- **`deps`** - Install system dependencies and package managers
- **`gitman`** - Update git submodules
- **`clean`** - Clean up environments (uses selected package manager)
- **`setup`** - Setup development environment (uses selected package manager)

### Package Manager Specific Targets
- **`clean-conda`** - Remove conda environment
- **`clean-uv`** - Remove UV virtual environment
- **`setup-conda`** - Setup conda environment
- **`setup-uv`** - Setup UV virtual environment

### Convenience Targets
- **`conda`** - Force use of conda for all operations
- **`uv`** - Force use of UV for all operations

## Package Manager Selection

### Environment Variable
```bash
# Set UV as default for this session
export PACKAGE_MANAGER=uv

# Or specify per command
PACKAGE_MANAGER=uv make setup
```

### Command Line Override
```bash
# Use UV for this command only
make uv

# Use conda for this command only  
make conda
```

## Detailed Target Descriptions

### `deps` Target
- Updates system packages
- Installs build tools (gcc-11+ if needed)
- Installs UV if `PACKAGE_MANAGER=uv`
- Installs gitman for submodule management

### `gitman` Target
- Updates all git submodules in `resources/`
- Downloads Isaac Sim and IsaacLab repositories

### `clean` Target
- **Conda**: Deactivates and removes `ilab` environment
- **UV**: Removes `ilab` directory

### `setup` Target
- **Conda**: Creates `ilab` environment and installs IsaacLab
- **UV**: Creates virtual environment and installs package in editable mode