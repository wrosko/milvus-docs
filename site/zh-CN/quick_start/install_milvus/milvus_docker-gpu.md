---
id: milvus_docker-gpu.md
label: GPU 版 Milvus
order: 1
group: distribution
---


# 安装、启动 Milvus 服务

{{tab}}

## 安装前提

#### 操作系统

| 操作系统    | 版本      |
| -------------- | ------------ |
| CentOS         | 7.5 或以上    |
| Ubuntu LTS     | 18.04 或以上  |

#### 硬件

| 硬件  | 建议配置                               |
| ---- | ------------------------------------- |
| CPU  | Intel CPU Sandy Bridge 或以上          |
| CPU 指令集 | <ul><li>SSE42</li><li>AVX</li><li>AVX2</li><li>AVX512</li></ul> |
| GPU  | NVIDIA Pascal 或以上                   |
| 内存  | 8 GB 或以上（取决于具体向量数据规模）     |
| 硬盘  | SATA 3.0 SSD 或以上                    |

#### 软件

| 软件            | 版本                                |
| -------------- | -------------------------------------- |
| Docker         | 19.03 或以上                            |
| NVIDIA driver  | 418 或以上                              |
| NVIDIA Container Toolkit  | [NVIDIA-Container-Toolkit](https://github.com/NVIDIA/nvidia-docker)                              |

## 确认 Docker 状态

确认 Docker daemon 正在运行：

```shell
$ sudo docker info
```

<div class="alert note">
<ul>
<li>如果无法正常打印 Docker 相关信息，请启动 Docker daemon。</li>
<li>在 Linux 上需要使用 <code>sudo</code> 执行 Docker 命令。若要在没有 <code>sudo</code> 的情况下运行 Docker 命令，请创建 <code>docker</code> 组并添加用户，详见 <a href="https://docs.docker.com/install/linux/linux-postinstall/">Linux 安装步骤</a>。</li>
</ul>
</div>

## 拉取 Milvus 镜像

拉取支持 GPU 的镜像：

```shell
$ sudo docker pull milvusdb/milvus:{{var.gpu_milvus_docker_image_version}}
```

{{fragments/tar_workaround.md}}

## 下载并修改配置文件

```shell
$ mkdir -p /home/$USER/milvus/conf
$ cd /home/$USER/milvus/conf
$ wget http://raw.githubusercontent.com/milvus-io/milvus/{{var.release_version}}/core/conf/demo/server_config.yaml
```

<div class="alert note">
如果无法通过 <code>wget</code> 命令正常下载，你也可以在 <b>/home/$USER/milvus/conf</b> 目录下创建 <b>server_config.yaml</b> 文件，然后将 <a href="https://github.com/milvus-io/milvus/blob/{{var.release_version}}/core/conf/demo/server_config.yaml">server config 文件</a> 的内容复制到你创建的配置文件中。
</div>

配置文件下载完成后，你需要将 **server_config.yaml** 中的 `gpu` 区域的 `enable` 参数设置为 `true`。

## 启动 Milvus Docker 容器

<div class="alert note">
启动 Docker 容器之前，你必须将 <b>server_config.yaml</b> 中 <code>gpu</code> 部分的 <code>enable</code> 设为 <code>true</code>。
</div>

启动 Docker 容器，将本地的文件路径映射到容器中：

```shell
$ sudo docker run -d --name milvus_gpu_{{var.release_version}} --gpus all \
-p 19530:19530 \
-p 19121:19121 \
-v /home/$USER/milvus/db:/var/lib/milvus/db \
-v /home/$USER/milvus/conf:/var/lib/milvus/conf \
-v /home/$USER/milvus/logs:/var/lib/milvus/logs \
-v /home/$USER/milvus/wal:/var/lib/milvus/wal \
milvusdb/milvus:{{var.gpu_milvus_docker_image_version}}
```

上述命令中用到的参数定义如下：

- `-d`: 在后台运行容器。
- `--name`: 为容器指定一个名字。
- `--gpus`: 指定可用的 GPU。如未填写任何值，则所有 GPU 都可用。
- `-p`: 指定端口映射。
- `-v`: 将宿主机路径挂载至容器。

最后，确认 Milvus 运行状态：

```shell
$ sudo docker ps
```

如果 Milvus 服务没有正常启动，执行以下命令查询错误日志：

```shell
$ sudo docker logs milvus_gpu_{{var.release_version}}
```

## 常见问题

<details>
<summary><font color="#4fc4f9">可以在 Windows 上安装 Milvus 吗？</font></summary>
{{fragments/faq_install_windows.md}}
</details>
<details>
<summary><font color="#4fc4f9">为什么 Milvus 在启动时返回 <code>Illegal instruction</code>？</font></summary>
{{fragments/faq_illegal_instruction_set.md}}
</details>
<details>
<summary><font color="#4fc4f9">Milvus 中如何实现数据迁移？</font></summary>
{{fragments/faq_data_migration.md}}
</details>
<details>
<summary><font color="#4fc4f9">Milvus 只能使用 Docker 部署吗？</font></summary>
{{fragments/faq_install_from_source.md}}
</details>




## 接下来你可以

- 如果你刚开始了解 Milvus：

  - [运行示例程序](example_code.md)
  - [了解更多 Milvus 操作](milvus_operation.md)
  - [体验 Milvus 在线训练营](https://github.com/milvus-io/bootcamp)

- 如果你已准备好在生产环境中部署 Milvus：

  - 创建 [监控与报警系统](monitor.md) 实时查看系统表现
  - [设置 Milvus 参数](milvus_config.md)
  
- 如果你想在仅有 CPU 的环境下使用 Milvus：

  - [安装仅需 CPU 的 Milvus](milvus_docker-cpu.md)
