Notes in ‘Fast R-CNN’



Notes in Workspace:

Excerpt:    R-CNN is slow because it performs a ConvNet forward  pass for each object proposal, without sharing computation.  Spatial pyramid pooling networks (SPPnets) [11] were proposed to speed up R-CNN by sharing computation. The SPPnet method computes a convolutional feature map for  the entire input image and then classifies each object pro-posal using a feature vector extracted from the shared feature map. Features are extracted for a proposal by max-pooling the portion of the feature map inside the proposal  into a fixed-size output (e.g., 6 × 6). Multiple output sizes are pooled and then concatenated as in spatial pyramid pooling. SPPnet accelerates R-CNN by 10 to 100× at test time. Training time is also reduced by 3× due to faster proposal feature extraction.
(Fast R-CNN, p.1)

Excerpt:    The RoI pooling layer uses max pooling to convert the  features inside any valid region of interest into a small feature map with a fixed spatial extent of H × W (e.g., 7 × 7),  where H and W are layer hyper-parameters that are independent of any particular RoI. In this paper, an RoI is a  rectangular window into a conv feature map. Each RoI is  defined by a four-tuple (r, c, h, w) that specifies its top-left  corner (r, c) and its height and width (h,w). RoI max pooling works by dividing the h × w RoI window into an H × W grid of sub-windows of approximate  size h/H × w/W and then max-pooling the values in each  sub-window into the corresponding output grid cell. Pooling is applied independently to each feature map channel,  as in standard max pooling. The RoI layer is simply the  special-case of the spatial pyramid pooling layer used in  SPPnets [11] in which there is only one pyramid level. We  use the pooling sub-window calculation given in [11].
(Fast R-CNN, p.2)



