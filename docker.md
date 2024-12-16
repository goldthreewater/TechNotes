1. 检查镜像：

   ```
   sudo docker images
   ```

2. 提交容器状态为新镜像：

   ```
   sudo docker commit my_tf2_container tf-vq:v1
   ```

3. 停止容器：

   ```
   sudo docker stop my_tf2_container
   ```

4. 移除容器：

   ```
   sudo docker rm my_tf2_container
   ```

5. 重新启动容器：

   ```
   sudo docker start -ai vq-test
   ```

6. 删除镜像：

   ```
   docker rmi my-image:tag
   ```

7. 在已经运行的容器中执行命令：

   ```
   sudo docker exec -it vq-test3 /bin/bash
   ```

   - `-i`（interactive）：表示以交互模式运行容器，这样你就可以在容器内部输入命令并得到响应。
   - `-t`（tty）：为容器分配一个伪终端（pseudo - TTY），这使得命令行交互更加友好，就像你直接在一个终端中操作一样。

8. 创建并启动一个新的容器：

   ```
   docker run --name ov-dino-container \
              --gpus all \
              -it \
              --rm \
              nvidia/cuda:12.6.3-cudnn-devel-ubuntu20.04
   ```

   - `--name ov-dino-container`：为容器指定名称。
   - `--gpus all`：允许容器访问所有可用的GPU。如果你想限制到特定数量或ID的GPU，可以在这里指定。
   - `-it`：以交互模式运行容器，并分配一个伪TTY（通常用于保持容器在前台运行）。
   - `--rm`：当容器退出时自动移除容器。如果你希望保留容器以便之后再次使用，则可以省略此选项。
   - `nvidia/cuda:12.6.3-cudnn-devel-ubuntu20.04`：指定使用的Docker镜像。

9. 从主机复制目录到容器

   ```
   docker cp /home/jinm/OV-DINO ov-dino-container:/OV-DINO
   ```

   

   