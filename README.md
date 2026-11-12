# Kosa Kata Sejarah 每日生字

Sejarah Tingkatan 1–5 马来文词汇每日练习网页（学生自学，老师不用监督）。

- 词库：T1–T5 共 47 章，每章 50 词，另有 112 个历史常用生字
- 学习流程：翻卡学新词 → 选意思 + 听写 → 间隔复习（每天最多复习 20 个旧词）
- 做完后生成「完成码」，学生用 WhatsApp 发给老师
- 老师页（需密码）：粘贴学生的完成码，查看全班记录
- 单一文件 `index.html`，不需要安装或构建，进度保存在学生浏览器里（localStorage）

## 修改

| 想改什么 | 在 `index.html` 里找 |
|---|---|
| 词库（新增或修改词） | `const DATA =`（每章最多读取前 50 个词；新词请加在每章最后，避免打乱学生已有进度） |
| 每天复习旧词的上限 | `.slice(0,20)`（在 `buildSession` 里） |
| 每天新词数量的选项 | `[5,8,10,15,20]` |
| 老师密码 | `PASS_HASH`（SHA-256，改密码要重新算哈希） |
| 完成码防伪盐值 | `SALT` |

## 发布到 GitHub Pages

1. 在 GitHub 新建仓库（例如 `sejarah-vocab`），把 `index.html`、`.nojekyll`、`README.md` 上传到仓库根目录。
2. 仓库 → Settings → Pages → Build and deployment → Source 选 **Deploy from a branch**，Branch 选 `main`、文件夹选 `/ (root)`，保存。
3. 等 1–2 分钟，网址是 `https://<你的GitHub用户名>.github.io/sejarah-vocab/`。

## 注意

- **进度按网址保存**：换了网址（例如从别的链接搬到 GitHub 网址），学生之前的进度不会跟过去。请先决定好正式网址再发给学生。
- 公开仓库里别人能看到全部源码，包括 `SALT` 和老师密码的哈希。密码请用够长、不好猜的。
