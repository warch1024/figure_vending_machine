# LVGL Framebuffer Demo for Vending Machine

基于 LVGL 的自动售货机界面演示项目，配置为在 Linux 帧缓冲设备 `/dev/fb0` 上运行。

## 项目结构

```
.
├── figure_vending_machine/   # 自动售货机界面模块
│   ├── checkout.c/h          # 结账界面
│   ├── goods_mangm.c/h       # 商品管理
│   ├── goods_mangm_con.c/h   # 商品管理界面
│   ├── login_screen.c/h      # 登录界面
│   ├── main_screen.c/h       # 主界面
│   ├── screen_objs.c/h       # 屏幕对象
│   └── user_info_mangm.c/h   # 用户信息管理
├── eva_pic.c                 # 图片资源
├── led.h                     # LED 控制
├── lv_conf.h                 # LVGL 配置
├── lv_drv_conf.h             # LVGL 驱动配置
├── Makefile                  # 编译脚本
└── CMakeLists.txt            # CMake 配置
```

## 克隆项目

```bash
git clone <repository-url>
cd lv_port_linux_frame_buffer/
git submodule update --init --recursive
```

## 构建项目

```bash
make
sudo make install
```

## 运行演示

```bash
demo
```

## 依赖

- LVGL 库（通过 submodule 管理）
- LVGL Drivers（通过 submodule 管理）
- Linux 帧缓冲设备支持