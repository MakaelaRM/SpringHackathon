We participated in a 21-hour hackathon hosted by NASA and the USDA, working on a team of four. Our project used LiDAR and NAIP imagery to train a U-Net model that automatically detects and maps trails. By applying computer vision techniques to geospatial data, we aimed to streamline the identification of trail networks for improved resource allocation and environmental monitoring.

Data Preparation

We extracted 256×256 raster patches from LiDAR-derived elevation data (including hillshade) and NAIP RGB tiles. The dataset was balanced so that 70% of the patches contained roads or trails and 30% did not, reducing false positives. Each patch provided five input channels (DEM, hillshade, and NAIP RGB), with road masks dilated to better capture thin trails. All data were stored in .npz format for efficient loading during training.

Model Training

Our U-Net segmentation approach utilized on-the-fly augmentation—random flips and 90° rotations—to enhance generalization to diverse terrain and road orientations. We employed a combo loss function, combining binary cross-entropy and Dice loss, which proved effective for the extreme class imbalance (roads and trails occupied less than 5% of each patch). Training progress was tracked using the Intersection over Union (IoU) metric, with early stopping and learning rate reduction to optimize model performance. This prototype demonstrates the potential of deep learning to accelerate trail detection and mapping.
