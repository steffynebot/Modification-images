# Re-import necessary modules after code execution environment reset
from PIL import Image
import matplotlib.pyplot as plt
import numpy as np
import cairosvg
from io import BytesIO
from sklearn.cluster import KMeans

# Re-load files
svg_path = blob-scene-haikei.svg
brain_image_path = "/mnt/data/ChatGPT Image 10 avr. 2025, 22_08_01.png"

# Convert SVG to PNG
png_output = BytesIO()
cairosvg.svg2png(url=svg_path, write_to=png_output)
png_output.seek(0)
svg_image = Image.open(png_output).convert("RGB")

# Resize for faster processing and extract colors
small_svg = svg_image.resize((100, 100))
svg_pixels = np.array(small_svg).reshape(-1, 3)
kmeans_svg = KMeans(n_clusters=5, random_state=0).fit(svg_pixels)
svg_colors = kmeans_svg.cluster_centers_.astype(int)

# Load the brain floral image
brain_image = Image.open(brain_image_path).convert("RGB")
brain_array = np.array(brain_image)
reshaped_brain = brain_array.reshape(-1, 3)

# Get dominant brain image colors
kmeans_brain = KMeans(n_clusters=5, random_state=1).fit(reshaped_brain)
brain_colors = kmeans_brain.cluster_centers_.astype(int)

# Create color mapping from brain colors to svg colors
color_mapping = {tuple(brain_colors[i]): tuple(svg_colors[i]) for i in range(5)}

# Function to map colors with tolerance
def map_color(pixel):
    for original, new_color in color_mapping.items():
        if np.allclose(pixel, original, atol=30):  # tolerance for similar colors
            return new_color
    return pixel

# Apply color mapping
new_pixels = np.array([map_color(pixel) for pixel in reshaped_brain], dtype=np.uint8)
new_image_array = new_pixels.reshape(brain_array.shape)
new_image = Image.fromarray(new_image_array)

# Save and show the new image
output_path = "/mnt/data/brain_flower_recolored.png"
new_image.save(output_path)
new_image.show()
