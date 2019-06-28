#  示例TensorFlow C API

![Example TensorFlow C API logo](logo.png)

Branch | Linux/OSX | Windows | License | Codacy
-------|-----------|---------|---------|-------
master |[![Build Status](https://travis-ci.org/Neargye/hello_tf_c_api.svg?branch=master)](https://travis-ci.org/Neargye/hello_tf_c_api)|[![Build status](https://ci.appveyor.com/api/projects/status/4js5recgpxp53q0v/branch/master?svg=true)](https://ci.appveyor.com/project/Neargye/hello-tf-c-api/branch/master)|[![License](https://img.shields.io/github/license/Neargye/hello_tf_c_api.svg)](LICENSE)|[![Codacy Badge](https://api.codacy.com/project/badge/Grade/65a8401ec7da4ff49a9d4603dfbb600a)](https://www.codacy.com/app/Neargye/hello_tf_c_api?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=Neargye/hello_tf_c_api&amp;utm_campaign=Badge_Grade)

示例如何在Windows，Linux和macOS（Darwin）上运行TensorFlow lib C API。

## [例子](https://github.com/Neargye/hello_tf_c_api/blob/master/src)

* [Hello TF](src/hello_tf.cpp)
* [Load graph](src/load_graph.cpp)
* [Create Tensor](src/create_tensor.cpp)
* [Allocate Tensor](src/allocate_tensor.cpp)
* [Run session](src/session_run.cpp)
* [Interface](src/interface.cpp)
* [Tensor Info](src/tensor_info.cpp)
* [Graph Info](src/graph_info.cpp)

## 构建示例

### Windows

```bash
git clone --depth 1 https://github.com/Neargye/hello_tf_c_api
cd hello_tf_c_api
mkdir build
cd build
cmake -G“Visual Studio 15 2017”-A x64 ..
cmake --build。 --config Debug
```

如果如上操作尝试运行编译结果报错，且报“无法找到tensorflow.dll”的错，请移步至[此](https://github.com/Neargye/hello_tf_c_api/issues/25).



### Linux和macOS（Darwin）

```bash
git clone --depth 1 https://github.com/Neargye/hello_tf_c_api
cd hello_tf_c_api
mkdir build
cd build
cmake -G“Unix Makefiles”..
cmake --build。
```

### 备注

* 构建之后，您可以在文件夹hello_tf_c_api/tensorflow/lib中找到TensorFlow库，在hello_tf_c_api/tensorflow/include中找到头文件。
* 存储库中的tensorflow以x64模式编译。确保该项目针对64位平台。
* 确保tensorflow lib位于输出目录中，或者位于％PATH％环境变量包含的目录中。

## 获取tensorflow lib

对于x64 CPU，您可以从<https://github.com/Neargye/tensorflow/releases>下载tensorflow.so，tensorflow.dll和tensorflow.lib。

或者通过CPU或GPU支持从源代码构建所需的lib版本。

### 链接tensorflow lib

#### CMakeLists.txt 

（根目录下的CMakelists.txt已经将依赖写好，理论上不需要自己修改。请自行学习如何使用cmake）

```bash
link_directories（yourpath / to / tensorflow）#pathorflow lib的路径
......＃other
target_link_libraries（<target> <PRIVATE | PUBLIC | INTERFACE> tensorflow）
```

#### Visual Studio

“项目” - >“属性” - >“配置属性” - >“链接器” - >“其他依赖项”，并将tensorflow.lib的路径添加为下一行。

"Project"->"Properties"->Configuration Properties"->"Linker"->"Additional Dependencies" and add path to your tensorflow.lib as a next line. （防止中英文找不到对照）

确保tensorflow.dll位于输出目录中（默认情况下，这是项目文件夹下的Debug \ Release），或者位于％PATH％环境变量包含的目录中。

### [准备模型的示例](https://github.com/Neargye/hello_tf_c_api/blob/master/doc/prepare_models.md)

要生成graph.pb文件，需要使用图形定义和一组检查点，并将它们一起冻结到一个文件中。

### [如何从tensorflow.dll for windows创建tensorflow.lib文件的示例]（https://github.com/Neargye/hello_tf_c_api/blob/master/doc/create_lib_file_from_dll_for_windows.md）

## Licensed under the [MIT License](LICENSE)