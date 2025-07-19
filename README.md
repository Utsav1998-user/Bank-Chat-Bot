# Install Roboflow if not already installed
!pip install roboflow

# Import required libraries
from roboflow import Roboflow
from google.colab import files
from IPython.display import Image, display
import os

# Initialize Roboflow
rf = Roboflow(api_key="YOUR_API_KEY")

# Load project and model
project = rf.workspace("your-workspace-name").project("your-project-name")
model = project.version(1).model  # Replace 1 with your version number

# Upload image
uploaded = files.upload()

# Get the uploaded image filename
image_path = next(iter(uploaded))  # this gives the filename string

# DEBUG: Check if image path exists
if not os.path.exists(image_path):
    print("File not found:", image_path)
else:
    # Predict on the image
    result = model.predict(image_path)

    # Check if result is None
    if result is None:
        print("Prediction failed. Make sure the image path and model are correct.")
    else:
        prediction = result.json()
        print("Prediction JSON:")
        print(prediction)

        # Save the prediction image with overlays
        result.save("predicted.jpg")

        # Display the image
        display(Image("predicted.jpg"))







project = rf.workspace().project("cat-dog-image-predictor")
