# 字体文件配置说明

## 概述

已将 Google Fonts 在线字体替换为本地字体文件，并分离了普通字体和等宽字体。

## 字体配置

### 等宽字体（Monospace）

- **字体名称**: JetBrains Mono
- **用途**: 代码、博客主体内容
- **CSS变量**: `var(--font-mono)`

### 普通字体（Sans-serif）

- **字体名称**: Harmony Sans
- **用途**: 普通文本内容
- **CSS变量**: `var(--font-base)`
- **Fallback**: 系统默认字体（-apple-system, BlinkMacSystemFont, Segoe UI, Roboto 等）

## 需要下载的字体文件

请下载以下字体文件并放置到 `assets/fonts/` 目录：

### JetBrains Mono（等宽字体）

1. JetBrainsMono-Thin.woff2 (100)
2. JetBrainsMono-ThinItalic.woff2 (100 italic)
3. JetBrainsMono-Light.woff2 (300)
4. JetBrainsMono-LightItalic.woff2 (300 italic)
5. JetBrainsMono-Regular.woff2 (400)
6. JetBrainsMono-Italic.woff2 (400 italic)
7. JetBrainsMono-Bold.woff2 (800)
8. JetBrainsMono-BoldItalic.woff2 (800 italic)

### Harmony Sans（普通字体）

1. HarmonyOS_Sans_Light.woff2 (300)
2. HarmonyOS_Sans_Regular.woff2 (400)
3. HarmonyOS_Sans_Italic.woff2 (400 italic)
4. HarmonyOS_Sans_Medium.woff2 (500)
5. HarmonyOS_Sans_Bold.woff2 (700)

## 下载方式

### 方式一：从 JetBrains 官网下载

访问：https://www.jetbrains.com/lp/mono/
下载完整字体包，解压后在 `fonts/webfonts/` 目录找到 `.woff2` 文件

### 方式二：从 GitHub 下载

#### JetBrains Mono

```bash
cd /home/quark/blog/assets/fonts
wget https://github.com/JetBrains/JetBrainsMono/releases/latest/download/JetBrainsMono.zip
unzip JetBrainsMono.zip
mv fonts/webfonts/*.woff2 .
rm -rf fonts JetBrainsMono.zip
```

#### Harmony Sans

```bash
cd /home/quark/blog/assets/fonts
# 从华为开源仓库下载
wget https://repo.harmonyos.com/harmonyos/os/font/harmonyos-sans.zip
unzip harmonyos-sans.zip
# 根据实际文件结构调整路径
mv HarmonyOS_Sans/*.woff2 .
rm -rf HarmonyOS_Sans harmonyos-sans.zip
```

### 方式三：使用 google-webfonts-helper

- JetBrains Mono: https://gwfh.mranftl.com/fonts/jetbrains-mono
- 选择需要的字重，下载 woff2 格式文件

### 方式四：手动转换字体

如果只有 TTF/OTF 格式，可使用在线工具转换为 woff2：

- https://cloudconvert.com/ttf-to-woff2
- https://everythingfonts.com/ttf-to-woff2

## 文件结构

修改后的文件结构：

```
assets/
├── css/
│   ├── blog.css      (已修改：引用 fonts.css)
│   ├── post.css      (已修改：引用 fonts.css)
│   ├── fonts.css     (新建：字体定义文件)
│   ├── common.css
│   └── syntax.css
└── fonts/            (新建目录)
    ├── JetBrainsMono-Thin.woff2
    ├── JetBrainsMono-ThinItalic.woff2
    ├── JetBrainsMono-Light.woff2
    ├── JetBrainsMono-LightItalic.woff2
    ├── JetBrainsMono-Regular.woff2
    ├── JetBrainsMono-Italic.woff2
    ├── JetBrainsMono-Bold.woff2
    ├── JetBrainsMono-BoldItalic.woff2
    ├── HarmonyOS_Sans_Light.woff2
    ├── HarmonyOS_Sans_Regular.woff2
    ├── HarmonyOS_Sans_Italic.woff2
    ├── HarmonyOS_Sans_Medium.woff2
    └── HarmonyOS_Sans_Bold.woff2
```

## 使用示例

在 CSS 中使用字体：

```css
/* 等宽字体（用于代码、特殊内容） */
.code,
pre,
code {
  font-family: var(--font-mono);
}

/* 普通字体（如需使用） */
.normal-text {
  font-family: var(--font-base);
}
```

## 优势

1. ✅ **性能提升**: 无需请求 Google Fonts API，加载更快
2. ✅ **隐私保护**: 不向第三方发送请求
3. ✅ **离线可用**: 无网络环境也能正常显示
4. ✅ **字体分离**: 等宽字体（JetBrains Mono）和普通字体（Harmony Sans）明确区分
5. ✅ **自定义灵活**: 可根据需要调整字体栈
6. ✅ **中文支持**: Harmony Sans 对中文显示效果优秀
7. ✅ **优雅降级**: 字体文件缺失时自动使用系统字体作为 fallback
