# LVGL Framebuffer Demo for Vending Machine

基于 LVGL 的自动售货机界面演示项目，配置为在 Linux 帧缓冲设备 `/dev/fb0` 上运行。

## 项目介绍

本项目是一个基于 LVGL（Light and Versatile Graphics Library）的嵌入式图形界面演示项目，专门为自动售货机应用场景设计。项目采用模块化架构，提供完整的自动售货机界面功能，包括商品展示、购物车管理、结账支付、用户登录等核心功能。

### 技术栈

- **LVGL**: 轻量级嵌入式图形库，支持多种显示驱动和输入设备
- **Linux Framebuffer**: 直接操作帧缓冲设备进行图形渲染
- **C语言**: 高性能嵌入式开发语言

### 主要特性

- 支持商品浏览和选择
- 购物车管理功能
- 多种支付方式支持
- 用户登录和信息管理
- 响应式界面设计
- 支持 Linux 帧缓冲设备

## 项目结构

```
.
├── figure_vending_machine/   # 自动售货机界面模块
│   ├── figure_vending_machine.c/h  # 模块入口
│   ├── checkout.c/h          # 结账界面
│   ├── goods_mangm.c/h       # 商品管理逻辑
│   ├── goods_mangm_con.c/h   # 商品管理界面
│   ├── login_screen.c/h      # 登录界面
│   ├── main_screen.c/h       # 主界面
│   ├── screen_objs.c/h       # 屏幕对象管理
│   └── user_info_mangm.c/h   # 用户信息管理
├── lvgl/                     # LVGL 图形库（submodule）
├── lv_drivers/               # LVGL 驱动模块（submodule）
├── eva_pic.c                 # 图片资源
├── led.h                     # LED 控制接口
├── lv_conf.h                 # LVGL 配置文件
├── lv_drv_conf.h             # LVGL 驱动配置
├── Makefile                  # 编译脚本
└── CMakeLists.txt            # CMake 配置
```

### 模块说明

| 模块 | 功能描述 |
|------|----------|
| `figure_vending_machine` | 自动售货机主模块，协调各子模块 |
| `checkout` | 结账界面，处理支付流程 |
| `goods_mangm` | 商品数据管理，维护商品列表 |
| `goods_mangm_con` | 商品管理界面，支持商品增删改查 |
| `login_screen` | 用户登录界面，身份验证 |
| `main_screen` | 主界面，商品展示和选择 |
| `screen_objs` | 屏幕对象统一管理 |
| `user_info_mangm` | 用户信息管理，账户信息维护 |

## 功能介绍

### 1. 主界面功能
- 商品分类展示
- 商品搜索和筛选
- 购物车快捷入口
- 用户状态显示

### 2. 商品管理功能
- 商品列表浏览
- 商品详情查看
- 加入购物车
- 商品库存管理

### 3. 购物车功能
- 已选商品列表
- 数量调整
- 价格计算
- 清空购物车

### 4. 结账功能
- 订单确认
- 多种支付方式
- 支付结果展示
- 订单记录

### 5. 用户管理功能
- 用户登录/注册
- 个人信息查看
- 账户余额管理
- 交易历史记录

## 构建方法

### 克隆项目

```bash
git clone <repository-url>
cd figure_vending_machine/
git submodule update --init --recursive
```

### 编译项目

#### 使用 Makefile

```bash
make
sudo make install
```

#### 使用 CMake

```bash
mkdir build && cd build
cmake ..
make
sudo make install
```

### 运行演示

```bash
demo
```

### 依赖要求

- **LVGL 库**: 通过 submodule 自动获取
- **LVGL Drivers**: 通过 submodule 自动获取
- **Linux 环境**: 需要 Linux 帧缓冲设备支持
- **编译工具链**: GCC 或 Clang 编译器

## 配置说明

### LVGL 配置

修改 `lv_conf.h` 文件可以配置 LVGL 的各项参数，包括：
- 显示缓冲区大小
- 颜色深度
- 字体设置
- 动画效果

### 驱动配置

修改 `lv_drv_conf.h` 文件配置输入输出设备：
- 帧缓冲设备路径（默认 `/dev/fb0`）
- 输入设备配置
- 显示分辨率设置

## 开发说明

### 代码风格

项目采用标准 C 语言编程风格，遵循以下规范：
- 函数和变量命名使用下划线分隔（snake_case）
- 代码缩进使用 4 个空格
- 头文件使用 include guard
- 函数参数和返回值清晰注释

### 调试方法

1. 确保开发环境已安装必要的调试工具
2. 使用 `make debug` 编译调试版本
3. 使用 GDB 进行断点调试
4. 查看帧缓冲输出验证界面效果

## 许可证

本项目采用 MIT 许可证，详细信息请查看 LICENSE 文件。