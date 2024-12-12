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

