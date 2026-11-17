# H5 博客

暖纸杂志风的静态博客，页面是纯 HTML，目前发布在 Cloudflare Worker：

https://blog.htsgyag6.workers.dev

站点文件在 `dist/`：根目录是首页，每篇文章一个子目录（例如 `dist/cursor-pstack-skills/`）。

## 本地预览

在仓库根目录启动一个静态服务器，根路径指向 `dist/`，例如：

```sh
python3 -m http.server 8787 --directory dist
```

然后打开 http://127.0.0.1:8787/

## 部署

用 [Wrangler](https://developers.cloudflare.com/workers/wrangler/) 发布到名为 `blog` 的 Worker。请把 Cloudflare 的账号和 API token 放在本地环境变量里，不要提交进仓库。

```sh
export CLOUDFLARE_ACCOUNT_ID="你的账号 ID"
export CLOUDFLARE_API_TOKEN="你的 API token"
wrangler deploy ./dist --name blog --compatibility-date 2026-09-04
```

`wrangler.toml` 已指定 `[assets] directory = "./dist"`。

## 不会进仓库的内容

本地备份、镜像目录、以及任何 `.env` / token 都已写入 `.gitignore`。
