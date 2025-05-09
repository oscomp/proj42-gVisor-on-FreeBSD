# proj42-gVisor-on-FreeBSD

在2018年开源的gVisor是为容器提供高效、多层防御的应用内核。作为一个容器运行时，它提供了云原生安全（防止容器逃逸）、弹性资源。gVisor向应用呈现的是Linux syscall APIs，现在只能运行在Linux内核上，但理论上host内核不必是Linux，通过其他系统内核（例如FreeBSD/Windows）也能实现同样的能力。这个项目旨在为gVisor增加Linux以外的操作系统支持。

当前项目实现源码：

* https://github.com/google/gvisor

### 所属赛道

2025全国大学生操作系统比赛的“OS功能设计”赛道

### 参赛要求
- 以小组为单位参赛，最多三人一个小组，且小组成员是来自同一所高校的本科生
- 如学生参加了多个项目，参赛学生选择一个自己参加的项目参与评奖
- 请遵循“2025全国大学生操作系统比赛”的章程和技术方案要求

### 项目导师

周介龙 jielong.zjl@antgroup.com
别体伟 tiwei.btw@antgroup.com

### 难度

中等

### 特征

- 用 Golang 语言实现
- 使用高级语言在用户态实现跨系统的应用内核

### 文档

- [gVisor doc](https://gvisor.dev/)
- [FreeBSD VMM](https://github.com/freebsd/freebsd-src/blob/main/sys/amd64/include/vmm_dev.h)

### License

- [Apache-2.0](https://opensource.org/licenses/Apache-2.0)

## 预期目标

### 注意：下面的内容是建议内容，不要求必须全部完成。选择本项目的同学也可与导师联系，提出自己的新想法，如导师认可，可加入预期目标

### 第一题：基础架构移植与开发

- 基于FreeBSD的VMM hypervisor为gVisor增加新的运行平台(platform)；
- 基于gVisor的go分支对gVisor进行改造，进行必要的移植使其能基于FreeBSD的系统调用工作；
(如果同学对Windows等其他系统内核有深入理解，也可以选择其他内核)

目标：能够支持在目标内核上使用gVisor运行简单的Linux程序，例如C的hello, world程序

### 第二题：syscall与内核功能支持与补充

- 完成对gVisor已支持的syscall接口和其他内核功能在FreeBSD上的移植，包括网络、文件系统操作等；

目标：能够在gVisor中运行主流的Linux程序，例如nginx、etcd等

### 第三题：gVisor功能增强

- gVisor没有支持最新版Linux内核的全部syscall，为gVisor添加缺失的Linux syscall的支持，例如renameat2, clone3, pidfd_open等。

目标：为gVisor添加缺失的Linux syscall的支持

### 第四题：gVisor隔离性增强

- 基于capsicum(4)在FreeBSD上实现gVisor的沙箱隔离；
- 基于rctl(4)在FreeBSD上实现gVisor的资源控制；

目标：实现沙箱隔离和资源控制
