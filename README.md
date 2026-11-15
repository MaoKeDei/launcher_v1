# 拾启｜LumeStart · 发布产物仓库

这个仓库只放**对外的发布产物**，不放源码。源码在私有仓库 `MaoKeDei/miao-ke-launcher`。

## 产物命名

```
LumeStart_<YYMMDD>_<arch>_<序号>.zip
```

例：`LumeStart_261115_x64_38.zip` = 2026-11-15 打的 x64 包，第 38 次对外发布。

- 程序显示名：**拾启｜LumeStart**
- 进程名与包内主程序：`LumeStart.exe`（ASCII，避免脚本与 URL 编码问题）
- 包内结构：根目录直接是 `LumeStart.exe` + `assets/`，**不含 `data/`**（玩家数据在本地，更新不覆盖）

## 每个 Release 必须写清

- 版本号 / 构建号（与云端台账一致）
- 文件名
- 字节数
- SHA256（上传前本地算、下载后回算一致）
- 更新说明（用户能看懂的一句话）

## 客户端更新方式

启动器 `GET …/api/launcher/check` 拿到下载地址后：下载 → SHA256 校验 → 整包 zip 解压（带 zip-slip 校验）→ 生成替换脚本 → 退出替换 → 重启。因此**发布物必须是 zip**，单个 exe 会导致更新失败。

## 校验

下载后请自行核对发布页里给出的 SHA256；不一致不要运行。
