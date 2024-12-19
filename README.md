# Colony Segmentation with Optimized Memory Management

This Colab notebook implements an image processing pipeline for segmenting bacterial colonies in images of petri dishes. It is designed to handle high-resolution images efficiently by incorporating several memory management techniques.

## Features

- **Patch-based Processing:** Large images are divided into overlapping patches to reduce memory footprint during processing. This allows the analysis of images that would otherwise exceed Colab's RAM limitations.
- **Optimized Patch Handling:** Patch coordinates are pre-calculated and stored to minimize redundant computations. Overlapping regions are blended smoothly using a Gaussian weight matrix to ensure seamless transitions between patches.
- **Illumination Correction:** Non-uniform illumination is corrected using a downsampling method, which reduces the memory required for background estimation.
- **Efficient Data Structures:** NumPy arrays are used extensively for image manipulation, leveraging their efficient memory management and vectorized operations.
- **Concurrent Image Saving:** High-resolution output images are saved concurrently using a ThreadPoolExecutor, minimizing the time spent on disk I/O.

## Memory Management Strategies

The following strategies are implemented to optimize memory usage:

1. **Patch-based processing:** By dividing the image into smaller patches, the algorithm avoids loading the entire image into memory at once. This significantly reduces the memory footprint, enabling the processing of very large images.
2. **Downsampling for illumination correction:** The illumination correction step uses a downsampled version of the image to estimate the background. This reduces the memory required for this step without significantly affecting the accuracy of the correction.
3. **Efficient data structures:** The code utilizes NumPy arrays, which are optimized for memory efficiency and performance. This helps to minimize memory usage and improve processing speed.
4. **Concurrent image saving:** The use of a ThreadPoolExecutor for saving images allows the program to save multiple images concurrently, reducing the time spent waiting for disk I/O. This helps to free up memory more quickly.

## Usage

1. **Mount Google Drive:** The code mounts your Google Drive to access input images and store results.
2. **Specify Input and Output Directories:** Update the `input_dir` and `output_dir` variables to point to the appropriate locations in your Drive.
3. **Run the Code:** Execute the code cells to process the images. The results will be saved in the specified output directory.

## Results

The pipeline produces several outputs:

- **Segmented Colonies:** A binary mask highlighting the segmented colonies.
- **Colored Mask:** A multicolor mask where each colony is assigned a unique color.
- **Overlay:** An overlay of the original image with the colored mask, providing a visualization of the segmentation results.

## Dependencies

- OpenCV
- NumPy
- SciPy
- PIL
- Matplotlib
- tqdm
- concurrent.futures
