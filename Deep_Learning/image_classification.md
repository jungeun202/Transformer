# Image Classification

Assign an image input to one of a fixed set of categories. 
<br> Problems: semantic gap, vietpoint variation, background clutter, illlumination challenges, etc. 
<br> Need a data-driven approach. 
```
def train (images, labels) return model
def predict (model, test_image) return test_label
```

# Nearest Neighbor 
Distance metric to compare images. 
1. L1 distance (Manhattan distance)
<br> $$d_{L1}(\mathbf{x}, \mathbf{y}) = \sum_{i=1}^n |x_i - y_i|$$
- testing the model takes O(N) to compare all images &rarr; BAD
2. L2 distance (Euclidean Distance)
<br> $$d_{L2}(\mathbf{x}, \mathbf{y}) = \sqrt{\sum_{i=1}^{n} (x_i - y_i)^2}$$
- coordinate frame free

### KNN
