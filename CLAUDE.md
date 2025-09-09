# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Python implementation of the k-Full Tree (kFT) algorithm for geo-referenced time-series (GTS) data summarization. The project implements spatio-temporal data analysis using graph-based clustering and tree structures.

### Reference Implementation

This code is a reference implementation of the algorithm described in `oliver2012.pdf`. The implementation follows the methodology and examples presented in the paper, including the sample data structure shown in Figure 2.

## Architecture

### Core Components

- **`kft.py`**: Main implementation containing:
  - `STNode`: Spatio-temporal node data structure
  - `STFullTree`: Spatio-temporal full tree representation
  - `GeoReferencedTimeSeries`: GTS data structure with spatial-temporal graph
  - `KFullTree`: Main algorithm implementation with Voronoi Partition Assignment (VPA)

- **`main.py`**: Simple entry point with hello world functionality

### Key Algorithms

The implementation follows a two-phase approach:
1. **Voronoi Partition Assignment (VPA)**: Assigns nodes to partitions using distance-based clustering
2. **Summary Tree Update**: Recomputes optimal ST-full trees for each partition

### Graph Structure

- Uses NetworkX DiGraph for spatio-temporal neighbor relationships
- Nodes represent (spatial_location, time_period) pairs
- Edges follow spatio-temporal adjacency (spatial neighbors at consecutive time periods)

## Development Commands

### Running the Code
```bash
uv run kft.py           # Run full kFT algorithm example
uv run python test_kft.py  # Run comprehensive test suite
```

### Dependencies
- Uses `uv` for dependency management
- Core dependencies: `networkx>=3.5`, `numpy>=2.3.2`
- Python >=3.13 required

### Installation
```bash
uv sync                 # Install dependencies
```

## Code Structure Notes

- Algorithm uses BFS for tree construction with degree constraints
- Implements both basic and VPA-based node assignment strategies
- Tree validation ensures proper ST-full tree properties (uniform depth, exact degree branching)
- Example data matches Figure 2 from the referenced academic paper (oliver2012.pdf)