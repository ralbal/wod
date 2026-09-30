### Clone Repo
```bash
# Clone the repository and enter its root directory
git clone https://github.com/ralbal/wod.git
cd wod

# Open the 2D Detection directory
cd perception/2d_detection
```

### Build Docker Image and Start Docker Container
All Docker commands in this section must be run from the `perception/2d_detection` directory
```bash
# Build the Docker image
docker build \
  --platform linux/amd64 \
  -t waymo-base:1.6.1 \
  .

# Start the development container
docker run --rm -it \
  --name 2d_detection \
  --hostname 2d-detection \
  --platform linux/amd64 \
  -v "$PWD:/workspace" \
  waymo-base:1.6.1
```

### Verify the installation inside the running container
All Python commands in this section must be run from the `root@2d-detection:/workspace#` workspace

```bash
python - <<'PY'
# Core dependencies
import numpy as np
import tensorflow as tf
from google.protobuf import message

print("Core dependency imports: PASS")

# Core Waymo data formats
from waymo_open_dataset import dataset_pb2
from waymo_open_dataset import label_pb2

print("Waymo data format imports: PASS")

# Perception utilities
from waymo_open_dataset.utils import box_utils
from waymo_open_dataset.utils import camera_segmentation_utils
from waymo_open_dataset.utils import frame_utils
from waymo_open_dataset.utils import range_image_utils
from waymo_open_dataset.utils import transform_utils

print("Waymo perception utility imports: PASS")

# Detection metrics and submissions
from waymo_open_dataset.metrics.ops import py_metrics_ops
from waymo_open_dataset.protos import breakdown_pb2
from waymo_open_dataset.protos import metrics_pb2
from waymo_open_dataset.protos import submission_pb2

print("Waymo detection metric imports: PASS")

# Segmentation
from waymo_open_dataset.protos import segmentation_pb2
from waymo_open_dataset.protos import camera_segmentation_pb2
from waymo_open_dataset.protos import camera_segmentation_submission_pb2

print("Waymo segmentation imports: PASS")

# Motion
from waymo_open_dataset.protos import scenario_pb2
from waymo_open_dataset.protos import motion_metrics_pb2
from waymo_open_dataset.protos import motion_submission_pb2

print("Waymo motion imports: PASS")

# Occupancy flow
from waymo_open_dataset.protos import occupancy_flow_metrics_pb2
from waymo_open_dataset.protos import occupancy_flow_submission_pb2

print("Waymo occupancy-flow imports: PASS")

# Sim Agents
from waymo_open_dataset.protos import sim_agents_metrics_pb2
from waymo_open_dataset.protos import sim_agents_submission_pb2

print("Waymo Sim Agents imports: PASS")

print("=" * 50)
print("Waymo Open Dataset v1.6.1 installation: PASS")
print("=" * 50)
PY
```

### Run the project in the /workspace:waymo-2d-detection container, mounted in the `perception/2d_detection` directory
```bash
python src/example.py
```

### Exit the container

Exit the container with:

```bash
exit
```

### Starting the environment again

For future development sessions, Docker Desktop must be running.

Navigate to the challenge directory:

```bash
cd perception/2d_detection
```

Start the existing image:

```bash
docker run --rm -it \
  --name 2d_detection \
  --hostname 2d-detection \
  --platform linux/amd64 \
  -v "$PWD:/workspace" \
  waymo-base:1.6.1
```

The image does not need to be rebuilt for every session.

