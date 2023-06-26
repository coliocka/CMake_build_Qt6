# Cmake_build_Qt6_project

#### 介绍
将CMakeList.txt文件拷贝到要编译的Qt项目当中，建立一个build文件夹
在build文件中执行 cmake .. 命令，生成对应的makefile文件
在执行 make -j32 命令，这里 -j32 是指电脑的线程数，具体看电脑配置
如不知怎么看，可以打开命令行执行 nproc 就可以看到当前电脑的线程数
最后再执行 ./可执行文件名称即可

#### 使用说明
在CMakeList.txt文件中，需要改动的地方是

# 设置Qt6开发工具包的安装路径
set(Qt6_SDK_PATH "/home/crucal/Qt")
# 查找Qt里的cmake.conf配置文件
set(Qt6_DIR /home/crucal/Qt/6.3.2/gcc_64/lib/cmake/Qt6)
# 指定外部库路径
set(CMAKE_PREFIX_PATH /home/crucal/Qt/6.3.2/gcc_64/)

这些里的路径改为本机Qt安装的对应路径即可

这样执行出来的执行文件为Server，如果想自定义的话，可以将
# 生成可执行文件
add_executable(Server ${SOURCES})

# 连接Qt里的模块
target_link_libraries(Server Qt6::Core Qt6::Widgets Qt6::Multimedia Qt6::Sql
                            Qt6::Network Qt6::Gui)

以上两处的Server改为自定义名称即可