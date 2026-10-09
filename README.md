# 人生档案 Skill

可在支持 Agent Skills 的智能体中使用的个人档案工作流。用户显式调用且不带参数时默认归档当前对话；首次调用会先引导选择继续使用已有档案或创建新档案。访谈通过调用参数“访谈”启动。

## 安装

### 从 GitHub 安装到支持 `skills` CLI 的 Agent

```bash
npx skills add zhj022326-commits/life-archive-skill --skill life-archive --agent codex --global
```

这条命令会把 `life-archive` 安装到 Codex 的用户级技能目录。安装后开启新的 Codex 会话。使用其他支持 `skills` CLI 的 Agent 时，可替换 `--agent` 参数；也可省略该参数并按 CLI 提示选择。

### 手动安装

1. 在本仓库点击 **Code → Download ZIP** 并解压。
2. 将解压目录中的整个 `skills/life-archive/` 文件夹复制到目标 Agent 的技能目录。不要只复制 `SKILL.md`；`references/` 和 `assets/` 也要保留。
3. Codex 默认的用户级位置是 `%USERPROFILE%\.codex\skills\life-archive\`。项目级安装可放在项目的 `.agents/skills/life-archive/`。其他 Agent 请使用其文档指定的技能目录。
4. 确认最终路径中直接包含 `life-archive\SKILL.md`，不要多套一层 `skills/life-archive`；然后重启 Agent 或开启新会话。

### 豆包工作

在豆包工作里通过其技能安装入口引用公开 GitHub 仓库，并选择 `life-archive`。若当前安装方式要求本地文件，则按上面的“手动安装”说明导入 `skills/life-archive/`。安装后在技能列表中显式调用；如果宿主把“选中”与“执行”分成两个动作，需使用它的调用入口。

## 使用

- 显式空调用：归档当前对话。
- 调用时附加“访谈”：启动人生访谈。

首次调用时可选择输入已有档案的完整路径，或创建新档案。新档案会在所选位置下使用带随机后缀的文件夹名；安装版 `SKILL.md` 保存当前路径，公开仓库不保存个人路径。档案绑定后正常使用不更换路径；用户手动移动档案时，可明确要求重新定位，技能核对档案编号后更新路径。卸载重装并重新初始化可选择旧档案或新档案；单开新对话不会重置位置。云端运行环境必须能访问所选存储位置；它不能自动读写用户电脑上不可访问的本地盘符。

## 数据

本仓库只包含 Skill 指令、规则和空白模板，不包含任何个人档案。用户档案应保存在用户自己指定的位置，不要提交到本仓库。

## 结构

```text
skills/life-archive/
├── SKILL.md
├── agents/openai.yaml
├── references/
└── assets/archive-template/
```

## 许可

本仓库尚未附加开源许可证。发布者需在公开前决定是否授权他人复制、修改和再分发。
