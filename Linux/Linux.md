# Linux

## Ubuntu

### 安装 NVIDIA GPU drivers

1. 更新系统
   参考命令: `sudo apt update && sudo apt upgrade -y`
2. 禁用开源驱动 Nouveau
   - 编辑文件`blacklist.conf`  
    参考方式  
    > `sudo nano /etc/modprobe.d/blacklist.conf`  
    >
    > 在文件中添加内容：  
    >
    > ```shell
    > blacklist nouveau
    > options nouveau modeset=0
    > ```
    >
    > 保存并退出文件  
    >
    > 应用设置并重启系统  
    > `sudo update-initramfs -u`  
    > `sudo reboot`

3. 清理原有残留  
    参考命令:  
    1. `sudo apt autoremove --purge nvidia-*`
    2. `sudo apt purge nvidia-*`
4. 安装 NVIDIA GPU drivers
   - 系统GUI 官方仓库
   - 系统CLI 配置  
    参考方式  
    > 添加官方 PPA 仓库并更新（不一定，这一步按需操作）  
    > `sudo add-apt-repository ppa:graphics-drivers/ppa`  
    > `sudo apt update`  
    >
    > 查看可用驱动版本（关注`recommended`标识的版本）  
    > `ubuntu-drivers devices`  
    >
    > 安装指定驱动版本
    > `sudo apt install nvidia-driver-<版本号>`
    >
    > 重启系统
    > `sudo reboot`

   - 手动安装
5. 验证  
   参考命令: `nvidia-smi`
