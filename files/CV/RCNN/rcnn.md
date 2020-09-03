Notes in ‘RCNN’


Notes in Workspace:

Excerpt:    Our object detection system consists of three modules.  The first generates category-independent region proposals. These proposals define the set of candidate detections avail-able to our detector. The second module is a large convolutional neural network that extracts a fixed-length feature vector from each region. The third module is a set of class-specific linear SVMs.
(RCNN, p.2)

Excerpt:    While R-CNN is agnostic to the particular region proposal method, we use selective search to enable a controlled comparison with prior  detection work
(RCNN, p.3)

Excerpt:    We extract a 4096-dimensional feature vector from each region proposal. We must first convert the image data in that region into a form that is compatible with the CNN (its architecture requires inputs of a fixed 227 × 227 pixel size). Of the many possible transformations of our arbitrary-shaped regions, we opt for the simplest. Regardless of the size or aspect ratio of the  candidate region, we warp all pixels in a tight bounding box  around it to the required size.
(RCNN, p.3)

Excerpt:    At test time, we run selective search on the test image  to extract around 2000 region proposals (we use selective  search’s “fast mode” in all experiments). We warp each  proposal and forward propagate it through the CNN in or-  der to compute features. Then, for each class, we score  each extracted feature vector using the SVM trained for that  class. Given all scored regions in an image, we apply a  greedy non-maximum suppression (for each class independently) that rejects a region if it has an intersection-over-union (IoU) overlap with a higher scoring selected region  larger than a learned threshold.
(RCNN, p.3)

Excerpt:    Aside from replacing the CNN’s ImageNet-  specific 1000-way classification layer with a randomly initialized (N + 1)-way classification layer (where N is the number of object classes, plus 1 for background), the CNN  architecture is unchanged.
(RCNN, p.3)


Excerpt:    We treat all region proposals with ≥ 0.5 IoU overlap with a ground-truth box as positives for  that box’s class and the rest as negatives. We start SGD at  a learning rate of 0.001 (1/10th of the initial pre-training  rate), which allows fine-tuning to make progress while not  clobbering the initialization. In each SGD iteration, we uniformly sample 32 positive windows (over all classes) and  96 background windows to construct a mini-batch of size  128. We bias the sampling towards positive windows be-  cause they are extremely rare compared to background.
(RCNN, p.4)
