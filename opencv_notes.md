## 接口

1. cv2.split(m)

   - 用于将一个多通道的数组（如图像）分离成几个单通道的数组。具体来说，它通常用来将彩色图像分解为独立的颜色通道

   - 输入为输入的多通道数组或图像

   - 返回值: 与输入图像通道数相同的多个单通道数组。对于BGR图像，返回三个单通道数组；对于BGRA图像，返回四个单通道数组

   - eg：

     ```
     b, g, r = cv2.split(image)
     ```

   - 如果输入的是单通道图像，则 `cv2.split` 不会产生任何效果，并且返回一个包含原始图像的元组。

   - 这个函数会创建新的 NumPy 数组来存储分离后的通道数据，因此如果对性能有严格要求，应当谨慎使用，因为它可能会消耗较多内存和处理时间。

   - 若要合并这些单通道数组回一个多通道数组，可以使用 `cv2.merge()` 函数






## 细节知识

1. 像素值0为黑色
2. 



