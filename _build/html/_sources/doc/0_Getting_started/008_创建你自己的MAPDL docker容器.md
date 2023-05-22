# 创建你自己的 MAPDL docker 容器
```{admonition} 前提
您需要一个有效的 Ansys 许可证和一个 Ansys 帐户来执行本节中详细描述的步骤。
```

您可以按照本页给出的步骤创建自己的 MAPDL docker 容器。本指南将使用本地 Ubuntu 机器，通过先安装 Ansys产品，为MAPDL 容器生成所需的文件，然后将生成的文件复制到容器中。

## 规定
- Linux 机器，最好是 Ubuntu 18.04 或更高版本。CentOS Linux 发行版不再受支持。这台机器需要安装 [Docker](https://www.docker.com/)。
- 一个有效的 Ansys 帐户。您的 Ansys 经销商应该已经为您提供了一个。
- 所提供的档案如下:
  - [Dockerfile](https://github.com/pyansys/pymapdl/tree/main/docker/Dockerfile)
  - [.dockerignore](https://github.com/pyansys/pymapdl/tree/main/docker/.dockerignore)

## 程序
### 下载 Ansys MAPDL 安装文件
从客户门户下载最新的 AnsysMAPDL 版本([当前版本](https://download.ansys.com/Current%20Release))。您需要有一个可以访问产品下载的有效 Ansys 帐户。

如果您没有 Ansys 帐户，请与您的 IT 经理联系。

### 安装 Ansys MAPDL 产品
要在 Ubuntu 机器上安装 Ansys MAPDL 产品，如果你使用图形用户界面，你可以按照[安装 MAPDL ](https://mapdl.docs.pyansys.com/version/stable/getting_started/running_mapdl.html#install-mapdl) 的方法进行，如果使用命令行界面，可以按照[安装 Ansys 产品](https://mapdl.docs.pyansys.com/version/stable/getting_started/wsl.html#installing-ansys-in-wsl) 。后面的方法可以在持续集成工作流程中进行小的改动后重复使用。

要减小最终镜像文件的大小，您可能需要使用以下方法安装最小文件:
```
sh /path-to-mapdl-installer \
    -install_dir /path-to-install-mapdl/ \
    -nochecks -mechapdl -ansyscust -silent
```

这个命令安装 MAPDL (`-mechapdl`) 和自定义例程 (`- ansyscust`) ，如 UPF。

请注意您正在安装 ANSYS 的位置，因为在下面的部分中需要目录路径。

## 构建 Docker 镜像
要构建 Docker 镜像，您需要创建一个目录并复制镜像中所需的所有文件。

下面的脚本详细介绍了复制这些文件和构建映像的步骤，您应该对脚本进行修改以使其适应您的需要。

```
# Creating working directory
mkdir docker_image
cd docker_image

# Copying the docker files
cp ./path-to-pymapdl/pymapdl/docker/Dockerfile
cp ./path-to-pymapdl/pymapdl/docker/.dockerignore

# Creating env vars for the Dockerfile
export VERSION=222
export TAG="V222"
export MAPDL_PATH=/path_to_mapdl_installation/ansys_inc

# Build Docker image
sudo docker build  -t $TAG --build-arg VERSION=$VERSION --build-arg MAPDL_PATH=$MAPDL_PATH
```

请注意:
- `Path-to-PyMAPDL` 是 `PyMAPDL repository` 所在的路径。
- `Path_to_MAPDL_install` 是本地安装 ANSYS MAPDL 的路径。

并非所有的安装文件都会被复制，事实上，在复制过程中被忽略的文件在 [.dockerignore](https://github.com/pyansys/pymapdl/tree/main/docker/.dockerignore) 文件中有详细说明。

构建容器所需的 Docker 容器配置在 [Dockerfile](https://github.com/pyansys/pymapdl/tree/main/docker/Dockerfile) 中有详细说明。

## Summary
- Step 1: 从门户网站下载最新的 AnsysMAPDL 版本([当前版本](https://download.ansys.com/Current%20Release))。
- Step 2: 在一个已知的文件夹中安装 Ansys MAPDL。如果你的本地安装有更新，并且机器运行的 Ubuntu 版本与 targe Ubuntu docker 版本相同，你可以重复使用。
- Step 3: 使用提供的 Docker 配置文件和脚本构建 Docker 镜像。

