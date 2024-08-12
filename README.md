# Fashion-seg
Project to segment clothes from background.

1) Overview of the Solution:
This solution is designed to generate binary masks from images, where the garment is highlighted in white, and the background is black. The core of this solution revolves around a CVPR pre-trained segmentation  U-Net model, specifically a U-Net architecture with a timm-efficientnet-b3 encoder. This model is loaded with pre-trained weights and is used to perform segmentation on the input images.

The pipeline includes several key steps:

    Loading the Pre-trained Model: The model is loaded using a URL to the pre-trained weights. This model is set to inference mode and is moved to the GPU for faster processing.

    Image Preprocessing: The input image is padded to ensure compatibility with the model's input size and normalized.

    Inference: The model predicts a mask, which is then processed to create a binary mask.

    Post-processing: The predicted mask is unpadded to restore the original dimensions, and it is optionally overlaid on the original image for visualization.

    Saving the Result: The final binary mask is saved with an appropriate filename.

2) Instructions on How to Install and Run the Code:
Prerequisites:

    Python 3.7 or later
   
    GPU with CUDA support (optional but recommended)
Clone the Repository:

    `git clone https://github.com/Shreyas-Dongre/Fashion-seg.git`
   
    `cd Fashion-seg`
   

Once inside the folder, install required libraries. 

    `pip install -r ./requirements.txt`

Running the Code:

    Update the image_paths list in the script with paths to your images.
    
    Run the Script OR open the ipynb and run the cells. (adjust input image path accordingly!)
    
3) Assumptions or Decisions Made During Development:
   
  Pre-trained Model: The pre-trained U-Net model uses the timm-efficientnet-b3 encoder. It was chosen for its balance between accuracy and efficiency.

  Image Padding: Images are padded to ensure they are compatible with the model's input size, which is a multiple of 32. This decision was made to avoid resizing, which could distort the garment's appearance.

  Threshold for Binary Mask: A threshold of 0 was used to create the binary mask, which might need adjustment based on the specific garment and background characteristics.

  Use of GPU: The code assumes access to a CUDA-capable GPU. If not available, you can modify the code to run on the CPU by replacing model.to('cuda') with model.to('cpu'). On cpu each image will take 40-60 seconds because of cpu limitations! #USE GPU PREFERABLY!

    
