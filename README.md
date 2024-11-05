##### -CNN
AN INTRODUCTION of Convolutional Nertural Network


import numpy as np
image = np.array([
    [10, 20, 30, 40, 50],
    [60, 70, 80, 90, 100],
    [110, 120, 130, 140, 150],
    [160, 170, 180, 190, 200],
    [210, 220, 230, 240, 250]
])

filter_kernel = np.array([
    [1, 0, -1],
    [1, 0, -1],
    [1, 0, -1]
])


def convolution2d(image, filter_kernel):
    # 获取图像和滤波器的尺寸
    image_height, image_width = image.shape
    filter_height, filter_width = filter_kernel.shape

    # 计算特征图的尺寸
    output_height = image_height - filter_height + 1
    output_width = image_width - filter_width + 1

    # 初始化特征图
    output = np.zeros((output_height, output_width))

    # 滑动滤波器并计算点积
    for i in range(output_width):
        for j in range(output_height):
            image_range = image[i:i + filter_height, j:j + filter_width]
            output[i,j] = np.sum(image_range*filter_kernel)
    return output
output_map = convolution2d(image, filter_kernel)
print(output_map)
