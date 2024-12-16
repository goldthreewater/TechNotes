## IOU

```python
def cal_iou(box1,box2):
    x1,y1,x2,y2=box1
    xx1,yy1,xx2,yy2=box2
    
    inner_x1=max(x1,xx1)
    inner_y1=max(y1,yy1)
    inner_x2=min(x2,xx2)
    inner_y2=min(y2,yy2)
    
    inner_w=max(0,inner_x2-inner_x1)
    inner_h=max(0,inner_y2-inner_y1)
    
    inner_area=inner_w*inner_h
    box1_area=(x2-x1)*(y2-y1)
    box2_area=(xx2-xx1)*(yy2-yy1)
    
    iou=inner_area/(box1_area+box2_area-inner_area)
    return iou
```

## NMS

```
def nms(boxes, scores, iou_threshold):
    """
    NMS算法
    :param boxes: numpy数组，形状为[N, 4]，每行是[x1, y1, x2, y2]
    :param scores: numpy数组，形状为[N]，每个框的置信度分数
    :param iou_threshold: float，IoU阈值
    :return: 保留框的索引列表
    """
    if len(boxes) == 0:
        return []

    # 按分数降序排序
    indices = np.argsort(scores)[::-1]
    keep = []

    while len(indices) > 0:
        current = indices[0]
        keep.append(current)

        # 计算IoU
        x1 = np.maximum(boxes[current, 0], boxes[indices[1:], 0])
        y1 = np.maximum(boxes[current, 1], boxes[indices[1:], 1])
        x2 = np.minimum(boxes[current, 2], boxes[indices[1:], 2])
        y2 = np.minimum(boxes[current, 3], boxes[indices[1:], 3])

        intersection = np.maximum(0, x2 - x1) * np.maximum(0, y2 - y1)
        area1 = (boxes[current, 2] - boxes[current, 0]) * (boxes[current, 3] - boxes[current, 1])
        area2 = (boxes[indices[1:], 2] - boxes[indices[1:], 0]) * (boxes[indices[1:], 3] - boxes[indices[1:], 1])

        iou = intersection / (area1 + area2 - intersection)

        # 保留IoU小于阈值的框
        indices = indices[1:][iou <= iou_threshold]

    return keep
```

