## 接口

1. `plt.subplots(nrows=1, ncols=1, sharex=False, sharey=False, squeeze=True, subplot_kw=None, gridspec_kw=None, **fig_kw)`

   可以指定行数和列数，并且它会返回一个图形对象和一个包含所有子图的轴对象数组

   - **参数**

     - **`nrows`**：指定子图的行数，默认值为 1。

     - **`ncols`**：指定子图的列数，默认值为 1。

     - **`sharex`**：控制所有子图是否共享 X 轴。可以是布尔值（`True` 或 `False`），也可以是更详细的设置如 `'col'` 或 `'row'`。

     - **`sharey`**：控制所有子图是否共享 Y 轴。与 `sharex` 类似。

     - **`squeeze`**：当只有一行或一列时，如果 `squeeze=True`，则返回单个 `AxesSubplot` 对象而不是数组；如果 `squeeze=False`，总是返回二维数组。

     - **`subplot_kw`**：字典，包含传递给每个子图的额外关键字参数。

     - **`gridspec_kw`**：字典，包含传递给 `GridSpec` 的关键字参数，用于更细粒度地控制布局。

     - **`fig_kw`**：其他关键字参数将传递给 `plt.figure()`，例如 `figsize` 来设定图形大小。

   - **返回值**

     - **`fig`**：`Figure` 对象，表示整个图形窗口。

     - **`axs`**：`AxesSubplot` 对象或对象数组，具体取决于 `nrows`、`ncols` 和 `squeeze` 参数。每个 `AxesSubplot` 对象代表一个子图。

   - 举例

     ```
     import matplotlib.pyplot as plt
     import cv2
     import numpy as np
     
     # 加载一些示例图像
     image1 = cv2.imread('path/to/image1.jpg')
     image2 = cv2.imread('path/to/image2.jpg')
     image3 = cv2.imread('path/to/image3.jpg')
     
     # 如果需要将BGR转换为RGB以正确显示颜色
     image1_rgb = cv2.cvtColor(image1, cv2.COLOR_BGR2RGB)
     image2_rgb = cv2.cvtColor(image2, cv2.COLOR_BGR2RGB)
     image3_rgb = cv2.cvtColor(image3, cv2.COLOR_BGR2RGB)
     
     # 创建一个2x2的网格，最后一个位置留空
     fig, axes = plt.subplots(nrows=2, ncols=2, figsize=(10, 8))
     axes = axes.ravel()  # 将2D数组展平为1D
     
     # 显示图像
     images = [image1_rgb, image2_rgb, image3_rgb]
     titles = ['Image 1', 'Image 2', 'Image 3']
     
     for ax, image, title in zip(axes, images + [None], titles + ['']):
         if image is not None:
             ax.imshow(image)
             ax.set_title(title)
             ax.axis('off')  # 关闭坐标轴
         else:
             fig.delaxes(ax)  # 删除多余的子图
     
     plt.tight_layout()
     plt.show()
     ```

     

​		