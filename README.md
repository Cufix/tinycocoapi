# COCO metrics for any dataset

Based on [cocoapi](https://github.com/cocodataset/cocoapi)


## What's different?
For object detection, we define 6 different object sizes: micro, tiny, very-tiny, small, medium and large.
Relative threshold values are used for each of them. 


## What's the same?
Use the same syntax as with the official cocoapi and the same annotation files. 
You don't need to change anything.


### Usage
```python
cocoGt = COCO(gt_path)
cocoDt = cocoGt.loadRes(res_path)
imgIds = sorted(cocoGt.getImgIds())
cocoEval = COCOeval(cocoGt, cocoDt, 'bbox')
cocoEval.params.imgIds = imgIds
cocoEval.evaluate()
cocoEval.accumulate()
cocoEval.summarize()
```

### Sample output
```
Average Precision  (AP) @[ IoU=0.50:0.95 | area=   all | maxDets=100 ] = 0.362
Average Precision  (AP) @[ IoU=0.50      | area=   all | maxDets=100 ] = 0.643
Average Precision  (AP) @[ IoU=0.75      | area=   all | maxDets=100 ] = 0.355
Average Precision  (AP) @[ IoU=0.50:0.95 | area= micro | maxDets=100 ] = 0.023
Average Precision  (AP) @[ IoU=0.50:0.95 | area=v-tiny | maxDets=100 ] = 0.207
Average Precision  (AP) @[ IoU=0.50:0.95 | area=  tiny | maxDets=100 ] = 0.497
Average Precision  (AP) @[ IoU=0.50:0.95 | area= small | maxDets=100 ] = 0.525
Average Precision  (AP) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.504
Average Precision  (AP) @[ IoU=0.50:0.95 | area= large | maxDets=100 ] = 0.443
Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets=  1 ] = 0.468
Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets= 10 ] = 0.537
Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets=100 ] = 0.537
Average Recall     (AR) @[ IoU=0.50:0.95 | area= micro | maxDets=100 ] = 0.023
Average Recall     (AR) @[ IoU=0.50:0.95 | area=v-tiny | maxDets=100 ] = 0.428
Average Recall     (AR) @[ IoU=0.50:0.95 | area=  tiny | maxDets=100 ] = 0.625
Average Recall     (AR) @[ IoU=0.50:0.95 | area= small | maxDets=100 ] = 0.616
Average Recall     (AR) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.583
Average Recall     (AR) @[ IoU=0.50:0.95 | area= large | maxDets=100 ] = 0.486
```
