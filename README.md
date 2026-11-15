# agent-skills

Claude CodeやCodexで使う、個人のAgent Skillsを管理するリポジトリです。

## 1. スキル一覧

- [write-technical-docs](skills/write-technical-docs/SKILL.md): README、仕様書、技術要件、設計文書をMarkdownで作成・更新する。

## 2. 導入手順

Node.js 22.20以降を用意し、PowerShellで次を実行します。

```powershell
Set-Location "$env:USERPROFILE/RiderProjects/agent-skills"
npx skills add ./ --global --agent codex --skill write-technical-docs
```

個人用のスキルとして導入すると、複数の開発リポジトリから利用できます。Claude Codeへ導入する場合は、`--agent codex`を`--agent claude-code`に変更します。

スキルを修正するときは、このリポジトリの編集元を更新します。導入先へ反映するには、同じ導入コマンドを再実行します。

コマンドの詳細は[skills CLIの導入手順](https://github.com/vercel-labs/skills/blob/main/docs/commands.md#skills-add)を参照してください。

## 3. スキルの追加方法

`skills/<スキル名>/`を作り、その中に`SKILL.md`を配置します。フォルダ名は英小文字・数字・ハイフンで付け、定義の`name`と揃えます。

```text
agent-skills/
├── README.md
└── skills/
    └── write-technical-docs/
        └── SKILL.md
```

スキル定義の冒頭には、名前と利用場面を記載します。

```yaml
---
name: skill-name
description: このスキルで行う作業と、使用する場面を記載する。
---
```

補足資料は各スキルの`references/`、繰り返し実行する処理は`scripts/`に置き、定義本文から参照します。追加後は、この文書のスキル一覧を更新します。
