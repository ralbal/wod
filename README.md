# Waymo Open Dataset Challenges

This repository contains separate solutions and development environments for Waymo Open Dataset perception and motion challenges.

A modular pipeline for developing, training, evaluating, and generating submission across Waymo Open Dataset Challenges

Each challenge is isolated in its own directory and includes its own:

- README
- Docker environment
- Dependencies
- Source code
- Tests
- Data preparation instructions
- Training and evaluation workflow
- Submission-generation workflow

## Getting started

### 1. Clone the repository

Clone this repository using GitHub Desktop or Git.

#### GitHub Desktop

1. Open GitHub Desktop.
2. Select **File → Clone Repository**.
3. Select this repository.
4. Choose a local path.
5. Click **Clone**.
6. Open the cloned repository in Visual Studio Code.

#### Command line

```bash
git clone https://github.com/ralbal/wod.git
cd wod
```

### 2. Install Docker Desktop

Install [Docker Desktop](https://www.docker.com/products/docker-desktop/) if it is not already installed.

Docker Desktop must be open and the Docker engine must be running before building or starting a challenge environment.

### 3. Select a challenge

Choose a challenge from the tables below and open its README.

Do not create one shared Python virtual environment at the repository root. Each challenge maintains its own isolated Docker environment and dependencies.



## Challenges

Each challenge is treated as an independent project.

### Perception challenges

| Challenge | Directory | Status |
|---|---|---|
| 2D Detection | [perception/2d_detection](perception/2d_detection/README.md) | Environment configured |

### Motion challenges

Motion challenge directories will be added here as development begins.

| Challenge | Directory | Status |
|---|---|---|
| No motion challenge added yet | — | Planned |

A challenge may use a different:

- Python version
- Waymo Open Dataset package version
- TensorFlow or PyTorch version
- Docker image
- Dependency list
- Data format
- Evaluation metric
- Submission format

For this reason, setup and execution commands belong in the challenge-specific README rather than the root README.

## Standard challenge workflow

Although implementation details may differ, each challenge should generally follow this workflow:

1. Open the challenge directory.
2. Read the challenge README.
3. Build its Docker image.
4. Start its development container.
5. Verify its dependencies.
6. Prepare or download the required dataset.
7. Run preprocessing.
8. Train or execute the solution.
9. Evaluate the results.
10. Generate the challenge submission.

## Data storage

Waymo dataset files are not committed to this repository.

Large files such as the following should remain outside Git:

- TFRecord files
- Extracted images
- Converted annotations
- Model checkpoints
- Training outputs
- Evaluation outputs
- Submission archives

Each challenge README should document where its local data is expected and how it is mounted into Docker.

## Current verified environment

The 2D Detection environment has been verified with:

- Linux x86-64 Docker
- Python 3.10
- TensorFlow 2.11
- Waymo Open Dataset v1.6.1
- CPU-only execution on Apple Silicon
- Waymo perception utilities
- Detection metrics
- Segmentation formats
- Motion formats
- Occupancy-flow formats
- Sim Agents formats