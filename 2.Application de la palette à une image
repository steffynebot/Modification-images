# Load the original brain floral image
brain_image_path = "/mnt/data/ChatGPT Image 10 avr. 2025, 22_08_01.png"
brain_image = Image.open(brain_image_path).convert("RGB")

# Resize for consistent processing
brain_array = np.array(brain_image)
reshaped_brain = brain_array.reshape(-1, 3)

# Map the dominant SVG colors onto the brain image colors using KMeans
kmeans_brain = KMeans(n_clusters=5, random_state=1).fit(reshaped_brain)
brain_colors = kmeans_brain.cluster_centers_.astype(int)

# Create a color mapping from brain image dominant colors to SVG colors
color_mapping = {tuple(brain_colors[i]): tuple(colors[i]) for i in range(5)}

# Apply the color mapping to the image
def map_color(pixel):
    pixel_tuple = tuple(pixel)
    for original, new_color in color_mapping.items():
        if np.allclose(pixel_tuple, original, atol=30):  # allow small variation
            return new_color
    return pixel_tuple

# Vectorized mapping is complex due to conditionals; use loop for clarity
new_pixels = []
for pixel in reshaped_brain:
    new_pixels.append(map_color(pixel))

# Reshape to original image dimensions
new_image_array = np.array(new_pixels, dtype=np.uint8).reshape(brain_array.shape)
new_image = Image.fromarray(new_image_array)

# Save the modified image
output_path = "/mnt/data/brain_flower_recolored.png"
new_image.save(output_path)

new_image.show()
