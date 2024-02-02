---
title: Rime
tags:
  - Rime
  - Software
---

# Rime

> 奉送原甫侍讀出守永興
>
> 歐陽修
>
> 酌君以荊州魚枕之蕉，贈君以宣城鼠須之管。
>
> 酒如長虹飲滄海，筆若駿馬馳平坂。
>
> 愛君尚少力方豪，嗟我久衰歡漸鮮。
>
> 文章驚世知名早，意氣論交相得晚。
>
> 魚枕蕉，一舉十分當覆盞。
>
> 鼠須管，為物雖微情不淺。
>
> 新詩醉墨時一揮，別後寄我無辭遠。

## Install Rime on macOS

---

```shell
brew install --cask squirrel
# 可能需要重启才能在设置中看到，并不需要加载系统扩展或者内核扩展
# 或者可能需要注销当前登录的会话之后才可以在系统输入法配置里面找到
```

## Install Rime on iOS

---

[:fontawesome-brands-app-store-ios:仓输入法](https://apps.apple.com/cn/app/仓输入法)

## macOS 配置 Rime

---

### 配置文件说明

数据文件位置

共享资料夹：`/Library/Input Methods/Squirrel.app/Contents/SharedSupport/`

用户资料夹：`~/Library/Rime/`

共享目录下放置的是 Rime 的预设配置，在软件版本更新时候，也会自动更新该目录下的文件。所以请不要修改该目录下的文件。用户目录则放置用户自定义的配置文件。我们要做的修改都放在用户目录下。

### 自定义配置

自定义全局配置 `touch ~/Library/Rime/default.custom.yaml`

`default.custom.yaml` 会覆盖 `default.yaml` 中的配置

文件参考 [rime-ice/default.yaml](https://github.com/iDvel/rime-ice/blob/main/default.yaml)

自定义外观设置 `touch ~/Library/Rime/squirrel.custom.yaml`

文件参考 [rime-ice/squirrel.yaml](https://github.com/iDvel/rime-ice/blob/main/squirrel.yaml)

### 拉取雾凇拼音

#### 从头设置

拉取雾凇拼音并创建自定义配置

```sh
cd ~/Library

git clone https://github.com/iDvel/rime-ice.git Rime && cd Rime
```

编辑 `default.yaml` 和 `squirrel.yaml` 文件，直接将上面的文件参考两个文件覆盖过来即可

## iOS 配置 Rime

---

首先开启 iCloud 同步，编辑 iCloud 中的配置，然后在设置中的 Rime 菜单中点击重新部署即可。

## 配置文件同步

---

### 通过 iCloud 同步

只同步了输入法自动生成的用户数据

`installation.yaml` 添加 `installation_id` 和 `sync_dir`

其中仓输入法的 `sync_dir=/private/var/mobile/Library/Mobile Documents/iCloud~dev~fuxiao~app~hamsterapp/Documents/sync`

那 macOS 上的 Rime 中配置的 `sync_dir: "~/Library/Mobile Documents/iCloud~dev~fuxiao~app~hamsterapp/Documents/sync"`

!!! note
    注意替换上文中的 `${HOME}` 变量

## 删除英文模式

---

进入每个输入方案的 `xxxx.schema.yaml`，注释掉 `engine/processors/ascii_composer` 和 `engine/segmentors/ascii_segmentor` 即可

## Source Link

---

- [:material-github: iDvel/rime-ice](https://github.com/iDvel/rime-ice)
- [安装及配置 Mac 上的 Rime 输入法——鼠鬚管 (Squirrel)](https://www.dreamxu.com/install-config-squirrel/)
- [:material-github: Lucius-Wang/rime-config](https://github.com/Lucius-Wang/rime-config/tree/master)
- [高效同步，便捷备份：我的 Rime 输入法 Mac 与 i(Pad)OS 多设备使用方案](https://utgd.net/article/20231)
- [:material-github: 如何删除鼠须管的英文模式？ #221](https://github.com/rime/squirrel/issues/221)
