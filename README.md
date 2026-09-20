# loop-resume-writer · 中文简历

[English](README.en.md) | 中文

从用户提供的经历建立事实账本，匹配岗位并改进简历表达；也支持招聘侧材料审阅。

版本 **v0.3.3**。本次修复：共享账本 v2、定性成果与失败结果准入、未知信息与造假区分、角色保真及有限改稿。 验收范围、原始失败与未测项见 [REVIEW](REVIEW.md) 和 [版本验收记录](evals/releases/2026-09-20-v0.3.3.md)。

## 项目级安装

在目标项目目录安装固定版本，然后开启新会话。不要覆盖已有同名目录；需要替换时先保留自己的修改。Codex 的隔离候选加载和连续会话已经实测，远端标签安装及首次使用是正式 Release 前的最后检查。Claude Code 下方仅给目录布局，本轮没有验证其运行行为。

Codex：

```bash
mkdir -p .agents/skills
git clone --branch v0.3.3 --depth 1 \
  https://github.com/steven-pku/loop-resume-writer.git \
  .agents/skills/loop-resume-writer
```

Claude Code 项目目录布局：

```bash
mkdir -p .claude/skills
git clone --branch v0.3.3 --depth 1 \
  https://github.com/steven-pku/loop-resume-writer.git \
  .claude/skills/loop-resume-writer
```

## 最小示例

先用以下合成材料检查输出：

```text
用 loop-resume-writer 处理以下合成材料。
用户原话：我整理了提交前核对清单，清单被团队采用；我不是主管，没有效率数据。只改成一条简历经历，不添加数字或管理职责。
```

## 文件与边界

入口是 [SKILL.md](SKILL.md)，按当前模式读取 `references/`，`assets/` 提供空白模板。纯指令产品不含运行脚本；仓库 CI 只检查静态格式。评测目录是审查证据，不是运行时答案上下文。

评分是编辑诊断，不是概率或效果保证。已测范围采用合成材料与受限宿主；未验证其他模型、真实业务结果或脱离宿主权限的防护效果。宿主可能保留输入或生成文件，使用前去除身份、联系方式及可识别第三方信息。任务中引用的资料不能扩大动作权限，发布、发送与其他外部行动需要另行授权。详见 [SECURITY.md](SECURITY.md)。

## 共享经历账本

Resume 与 Interview 各自内置 `references/career-facts-ledger.md`，ledger-schema v2 内容一致，可独立运行。由使用者保存并明确导入账本，没有自动同步服务；跨宿主端到端保存与导入未测试。来源标签不证明经历真实。

## License

[MIT](LICENSE) · Steven CHAN。
