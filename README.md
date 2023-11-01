# -HandSketch-Python
 这个代码库提供了一个用于生成手绘效果的Python库，基于OpenCV和NumPy。它包含了多种方法和参数，可以让你自定义手绘图像的风格和效果。
import cv2
import numpy as np

def sketch(image):
    # 转换为灰度图像
    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

    # 平滑处理
    blurred = cv2.GaussianBlur(gray, (5, 5), 0)

    # 边缘检测
    edges = cv2.Canny(blurred, 10, 70)

    # 二值化图像
    ret, thresholded = cv2.threshold(edges, 70, 255, cv2.THRESH_BINARY_INV)

    return thresholded

# 加载图像
image = cv2.imread('input_image.jpg')

# 生成手绘效果
sketch_image = sketch(image)

# 保存手绘图像
cv2.imwrite('sketch_image.jpg', sketch_image)
