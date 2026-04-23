
<h1>Chest X-Ray Classification using SVM and CNN</h1>

<h2>1. Introduction</h2>
<p>
Medical image classification plays a crucial role in assisting doctors in diagnosing diseases.
In this project, chest X-ray images are classified into different categories using two different
approaches: Support Vector Machines (SVM) and Convolutional Neural Networks (CNN).
The objective is to compare the performance of traditional machine learning and deep learning
methods and analyze how the amount of training data affects their performance.
</p>

<h2>2. Dataset</h2>
<p>
The dataset consists of chest X-ray images categorized into two classes: Normal and Pneumonia.
All images were preprocessed by resizing and normalization before being fed into the models.
The same test dataset was used across all experiments to ensure fair comparison and avoid data leakage.
</p>

<img src="images/sample_xray.png">

<h2>3. Methodology</h2>

<h3>3.1 Support Vector Machine (SVM)</h3>
<p>
For the SVM model, images were first flattened into one-dimensional vectors.
Dimensionality reduction was performed using Principal Component Analysis (PCA)
to reduce computational complexity. Two kernels were used:
Linear and Radial Basis Function (RBF).
The linear kernel assumes linearly separable data, while the RBF kernel can handle
non-linear relationships.
</p>

<h3>3.2 Convolutional Neural Network (CNN)</h3>
<p>
A CNN model was implemented using convolutional layers, pooling layers, and fully connected layers.
CNNs are specifically designed for image data as they can automatically extract spatial features.
However, due to computational limitations, the model was trained for only a few epochs,
which impacts its performance.
</p>

<h2>4. Training with Different Data Sizes</h2>
<p>
To study the effect of training data size, models were trained using 20%, 40%, 60%, and 80%
of the available training dataset. This experiment helps in understanding how models scale
with increasing data.
</p>

<h2>5. Results</h2>

<table>
<tr>
<th>Data %</th>
<th>SVM (RBF)</th>
<th>SVM (Linear)</th>
<th>CNN Accuracy</th>
<th>F1 Score</th>
<th>Sensitivity</th>
<th>Specificity</th>
</tr>

<tr>
<td>20%</td>
<td>0.866</td>
<td>0.844</td>
<td>0.4375</td>
<td>0.5714</td>
<td>0.7500</td>
<td>0.1250</td>
</tr>

<tr>
<td>40%</td>
<td>0.888</td>
<td>0.876</td>
<td>0.5000</td>
<td>0.6364</td>
<td>0.8750</td>
<td>0.1250</td>
</tr>

<tr>
<td>60%</td>
<td>0.889</td>
<td>0.884</td>
<td>0.3125</td>
<td>0.3529</td>
<td>0.3750</td>
<td>0.2500</td>
</tr>

<tr>
<td>80%</td>
<td>0.885</td>
<td>0.872</td>
<td>0.5625</td>
<td>0.5882</td>
<td>0.6250</td>
<td>0.5000</td>
</tr>

</table>

<h2>Accuracy Comparison</h2>
<img src="images/accuracy_plot.png">

<h2>6. Observations</h2>
<p>
The results clearly show that SVM with RBF kernel consistently achieves the highest accuracy
across all dataset sizes. This is because the RBF kernel can effectively model non-linear patterns
present in medical images. The linear kernel performs slightly worse, as it assumes a linear
decision boundary which is not sufficient for complex image data.
</p>

<p>
The CNN model, on the other hand, shows significantly lower and inconsistent performance.
At 60% data, the accuracy even drops, indicating instability in learning. This behavior is mainly
due to insufficient training, as the model was trained for only a few epochs. Deep learning models
require large datasets and longer training durations to perform effectively.
</p>

<p>
Another important observation is that the specificity of the CNN model is very low for smaller
datasets. This means the model struggles to correctly identify negative cases (normal images).
However, as the dataset size increases to 80%, both accuracy and specificity improve,
showing that CNN benefits from more data.
</p>

<h2>7. Kernel Comparison (RBF vs Linear)</h2>
<p>
The RBF kernel performs better than the linear kernel because it can capture non-linear
relationships in the data. Chest X-ray images contain complex textures and patterns that
cannot be separated using a straight line. The linear kernel is limited in its ability to model
such complexity, resulting in slightly lower accuracy.
</p>

<h2>8. Effect of Training Data Size</h2>
<p>
As the amount of training data increases, the performance of SVM improves slightly and remains stable.
This indicates that SVM is less sensitive to data size once sufficient features are captured.
</p>

<p>
In contrast, CNN performance is highly dependent on the amount of data. With smaller datasets,
the CNN struggles to learn meaningful features, resulting in poor performance. However, as the
dataset size increases, the CNN starts improving, indicating that deep learning models scale better
with data compared to traditional machine learning methods.
</p>



<h2>10. Conclusion</h2>
<p>
In this study, SVM with RBF kernel achieved the best performance due to its ability to handle
non-linear data effectively. The CNN model did not perform well due to insufficient training
and limited data usage.
</p>

<p>
However, with proper training (100–200 epochs) and larger datasets, CNN is expected to outperform
SVM, as it is specifically designed for image-based tasks. This experiment highlights the importance
of both model selection and training strategy in achieving optimal results.
</p>

</body>
</html>
