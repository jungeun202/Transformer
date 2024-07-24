# Linear Classifier 
### Parametric Approach
- Input x ( image 32x32x3 from CIFAR 10 dataset ) &rarr; $f(x, W)$ **parameters W** (weights) &rarr; 10 numbers with their class scores
- Rely on parameters to make predictions.
1. Algebric Viewpoint
- $f(x,W) = Wx + b$
- eg: 2x2 image with 3 classes
<br> Flatten 2x2 image into 4x1 ; stretches pixels into column 
<br> Wx + b
<br> (3, 4) inner product (4,) + (3,) = (3,)
2. Visual Viewpoint
- One template per class ; template matching
- Problems: images that can collide between two different templates, images with different angles or poses. 
3. Geometric Viewpoint
- x, y axis are different pixel values
- Each category template will stay on that line, intercepting with x, y axis, and in high dimension it becomes hyperplane.

### Hard cases for a linear classifier
- When we can't draw linear decision boundaries among different categories.

### Good W
1. Use a loss function to quantify how good a W is.
2. Find W that minimizes loss function

### Loss Function
- Loss function quantify how good the classifier is.
- low loss is a good classifier
1. Cross Entropy Loss (Multinomial Losistic Regression)
  - Convert raw classifier scores into probabilities.
  - Score function: $s = f(x_i; W)$ ; produce a raw score (logit) for each class.
  - Softmax function : $P(Y = k \mid X = x_i) = \frac{\exp(s_k)}{\sum_j \exp(s_j)}$
  - Cross-entropy loss : $L_i = -\log P(Y = y_i \mid X = x_i)$ ; probabilities of predicted
  - $L_i = -\log \left( \frac{\exp(s_{y_i})}{\sum_j \exp(s_j)} \right) $
- Details
  1. Exponentiate all unnormalized log-probabilities (logits) so that probabilities can be $\ge$ 0.
  2. Nomalize them so that probabilities can be sum to 1.
  3. Do **cross-entropy loss** for maximum likelihood esimation, choosing weights to maximize the likelihood of the observed data.
     <br> Do **Kullback-Leibler (KL) divergence**
       - Compare the ground true labels with predictions
       - $D_{\text{KL}}(Q \parallel P) = \sum_{y} Q(y) \log \frac{Q(y)}{P(y)}$ ; Q is correct probs and P is predictions
2. Multiclass SVM loss
- While $s = f(x_i; W)$, $L_i = \sum_{j \neq y_i} \max(0, s_j - s_{y_i} + 1)$
  - $s_j$ is a predicted score for incorrect category.
  - $s_{y_i}$ is a predicted score for correct category.
  - +1 is a margin
- SVM is not differentiable at the hinge point. 
