
# $\mathrm{S^{imple}_{ystem}}\TeX$

**$\mathrm{S^{imple}_{ystem}}\TeX$** 是一个基于 $\LaTeX3$ 构建, 专为撰写简约风格的高质量数学笔记/讲义设计的 $\LaTeX$ 宏包.

$\mathrm{S^{imple}_{ystem}}\TeX$ 提供了一套高度自动化的章节管理系统、经过显示优化的数学指令以及便捷的交叉引用功能. 尽管该宏包专为 Simple·System 系列讲义设计, 其也可以应用于其它结构化内容创作, 为创作者免去大量复杂的排版逻辑.

---

## 📖 目录

- [✨ 设计特色](#设计特色)
- [📦 依赖](#依赖)
- [📂 安装 & 文件结构](#安装&文件结构)
- [★ 主文件 (`[Project].tex`)](#主文件)
    - [导言区](#主文件#导言区)
        - [导入](#主文件#导言区#导入)
        - [样式设置](#主文件#导言区#样式设置)
    - [正文区](#主文件#正文区)
        - [常规控制命令](#主文件#正文区#常规控制命令)
            - [生成目录](#主文件#正文区#常规控制命令#生成目录)
            - [导入子文件](#主文件#正文区#常规控制命令#导入子文件)
            - [生成索引](#主文件#正文区#常规控制命令#生成索引)
            - [其它 $\LaTeX$ 语法](#主文件#正文区#常规控制命令#其它LaTeX语法)
        - [目录控制命令](#主文件#正文区#目录控制命令)
            - [分块标题](#主文件#正文区#目录控制命令#分块标题)
            - [其它 $\LaTeX$ 语法](#主文件#正文区#目录控制命令#其它LaTeX语法)
- [☆ 子文件 (`sec/.../[Section].tex`)](#子文件)
    - [区块 Block](#子文件#区块)
        - [定义 Definition | 定理 Theorem | 推论 Corollary](#子文件#区块#定义|定理|推论)
            - [用法](#子文件#区块#定义|定理|推论#用法)
            - [示例](#子文件#区块#定义|定理|推论#示例)
        - [证明 Proof](#子文件#区块#证明)
            - [用法](#子文件#区块#证明#用法)
            - [示例](#子文件#区块#证明#示例)
    - [交叉引用 Cross Reference](#子文件#交叉引用)
        - [区块 (Block) 链接](#子文件#交叉引用#区块链接)
            - [用法](#子文件#交叉引用#区块链接#用法)
            - [示例](#子文件#交叉引用#区块链接#示例)
        - [节 (Section) 链接](#子文件#交叉引用#节链接)
            - [用法](#子文件#交叉引用#节链接#用法)
            - [示例](#子文件#交叉引用#节链接#示例)
        - [章/子章 (Chapter/Subchapter) 链接](#子文件#交叉引用#章/子章链接)
            - [用法](#子文件#交叉引用#章/子章链接#用法)
            - [示例](#子文件#交叉引用#章/子章链接#示例)
    - [公式 Formulas](#子文件#公式)
        - [字母符号](#子文件#公式#字母符号)
        - [分隔符](#子文件#公式#分隔符)
        - [括号](#子文件#公式#括号)
        - [运算 & 函数](#子文件#公式#运算&函数)
            - [基本](#子文件#公式#运算&函数#基本)
            - [三角](#子文件#公式#运算&函数#三角)
            - [函数](#子文件#公式#运算&函数#函数)
            - [线性代数](#子文件#公式#运算&函数#线性代数)
        - [逻辑量词](#子文件#公式#逻辑量词)
        - [多行排版](#子文件#公式#多行排版)
- [ℹ︎ 其它说明](#其它说明)
    - [关于参数宏](#其它说明#关于参数宏)
    - [关于附加参数](#其它说明#关于附加参数)
        - [附加参数 A](#其它说明#关于附加参数#附加参数A)
        - [附加参数 B](#其它说明#关于附加参数#附加参数B)
- [📄 附录](#附录)
    - ️[样式默认值](#附录#样式默认值)
    - [主文件示例](#附录#主文件示例)

---

## ✨ 设计特色 {#设计特色}

- **自动化章节管理**：无需手动编写复杂的`\include`逻辑. 通过`\ImportSection`命令即可导入子文件, 并且可以通过`\MakeSimpleCatalog` `\MakeSimpleIndex`来自动构建目录和索引.
- **定制数学区块**：内置定义`\Definition`、定理`\Theorem`、推论`\Corollary`、等数学区块, 采用不同的颜色显示（深红褐色、橄榄色、棕色等）, 视觉层次分明.
- **海量数学公式宏**：预定义了大量常用的数学简写（如`\bfR` `\fder` `\norm`等）, 极大地提升了公式输入效率.
- **智能交叉引用**：通过`\link` `\seclink` `\cptlink`等命令实现到各区块和章节的快速跳转.
- **全面中文支持**：基于`ctex`宏包, 对中文排版进行了深度优化.

---

## 📦 依赖 {#依赖}

$\mathrm{S^{imple}_{ystem}}\TeX$ 依赖以下标准 $\LaTeX$ 宏包:

- `expl3`, `xcolor`, `xparse`, `xstring`, `amsmath`, `hyperref`, `tikz`

建议使用 **XeLaTeX** 进行编译.

---

## 📂 安装 & 文件结构 {#安装&文件结构}

直接将`simplesystem.sty`文件放置于项目根目录即可, 或者放置于本地 TEXMF 目录下.

$\mathrm{S^{imple}_{ystem}}\TeX$ 中所有独立的子文件称为 **节(Section)** , **章(Chapter)** 用于存放具有相同属性的节, 也可以根据需要设置 **子章(Subchapter)** 来对其进一步划分.

**标签** 是每个章/子章/节都具有的唯一标识符, 在导入子文件和交叉引用等命令中使用.

需要注意:

- 标签中不能包含特殊字符`#` `%` `:` `/` `\` `{` `}`.
- 每个章/子章的文件夹名必须与其标签保持一致.
- 每个节的文件名必须与其标签保持一致.

$\mathrm{S^{imple}_{ystem}}\TeX$ 依赖于特定的文件结构来管理章节, 因此请确保你的项目符合以下结构:

```
[Project]/
├── [Project].tex               # 项目主文件
├── simplesystem.sty            # SimpleSystemTeX 宏包 (或者 TEXMF 目录下)
└── sec/
    ├── [Chapter1]/             # 章 Chapter
    │   ├── [Subchapter1]/      # 子章 Subchapter
    │   │   └── [Section1].tex  # 节 Section
    │   └── [Section2].tex      # 节 也可直接放置于 章 下 (直属节)
```

`[]`中的内容为对应内容的标签, 你可以将其替换为任何合法名称.

---

## ★ 主文件 (`[Project].tex`) {#主文件}

$\mathrm{S^{imple}_{ystem}}\TeX$ 要求你的项目主文件采用特定的指令来实现排版控制, 尤其是[正文区](#主文件#正文区)中的部分, 你可以在附录中查看[主文件示例](#附录#主文件示例).

### 导言区 {#主文件#导言区}

#### 导入 {#主文件#导言区#导入}

使用如下命令来导入 $\mathrm{S^{imple}_{ystem}}\TeX$ 宏包:

`\usepackage{simplesystem}`

#### 样式设置 {#主文件#导言区#样式设置}

$\mathrm{S^{imple}_{ystem}}\TeX$ 对目录、索引、区块等部分的样式提供了默认设置, 你可以使用如下命令来修改这些样式:

`\FormatSetting{样式名称}{样式内容}`

- 下面是可供修改的`样式名称`:
    - 目录样式
        - `CatalogTitle` 目录 标题
        - `CatalogPartTitle` 目录 分块标题
        - `CatalogSection` 目录 常规条目
        - `CatalogIndex` 目录 索引条目
    - 索引样式
        - `IndexTitle` 索引 标题
        - `IndexSubchapter` 索引 子章标题
        - `IndexSection` 索引 条目
    - 文内样式
        - `SectionHeading` 节 标题
        - `DefinitionName` 定义区块 名称
        - `DefinitionContent` 定义区块 内容
        - `TheoremName` 定理区块 名称
        - `TheoremContent` 定理区块 内容
        - `CorollaryName` 推论区块 名称
        - `CorollaryContent` 推论区块 内容
        - `ProofName` 证明区块 名称
        - `ProofContent` 证明区块 内容
        - `BlockLink` 区块链接
        - `SectionLink` 节链接
        - `ChapterLink` 章链接
- 在`样式内容`中, 可以使用如下参数宏来控制参数的显示:
    - `\parttitlename` 分块标题名称
    - `\chaptername` 章名称
    - `\subchaptername` 子章名称
    - `\sectionname` 节名称
    - `\blockname` 区块名称
    - `\blockcontent` 区块内容
    - `\linktext` 链接显示文本
    - `\parameterA` 附加参数 A
    - `\parameterB` 附加参数 B
- 还可以使用下列控制宏来实现更复杂的样式控制:
    - `\ifempty{参数宏}{True}{False}` 用于判断参数宏是否为空

关于上述参数宏的具体用法, 请见[关于参数宏](#其它说明#关于参数宏).

你可以参考 $\mathrm{S^{imple}_{ystem}}\TeX$ 为这些样式预设的[默认值](#附录#样式默认值).

### 正文区 {#主文件#正文区}

在主文件的正文区中你应**仅使用**下列由 $\mathrm{S^{imple}_{ystem}}\TeX$ 提供的宏命令.

#### 常规控制命令 {#主文件#正文区#常规控制命令}

##### 生成目录 {#主文件#正文区#常规控制命令#生成目录}

`\MakeSimpleCatalog`

- 你可以通过修改样式`CatalogTitle`来自定义目录标题.

##### 导入子文件 {#主文件#正文区#常规控制命令#导入子文件}

`\ImportSection{章标签}[子章标签]{节标签}(节名称)<附加参数A>`

- `子章标签`为可选参数, 对于直属节无需使用这一参数.
- `节名称`为可选参数, 若无该参数则默认使用`节标签`作为节名称.
- `附加参数A`为可选参数, 你可以在[关于附加参数](#其它说明#关于附加参数#附加参数A)中了解更多.
- 章/子章以标签作为名称, 暂不支持修改章名称和子章名称.

##### 生成索引 {#主文件#正文区#常规控制命令#生成索引}

`\MakeSimpleIndex{章标签}[子章标签列表]<附加参数A>`

- `子章标签列表`为可选参数, 格式为`子章标签1,子章标签2,...,子章标签n`
    - 若无该参数则默认在索引中导入该章下的全部节, 否则仅导入在`子章标签列表`中被列出的子章中的节.
    - 可以在列表最前端加入`,`来在索引中导入该章的全部直属节.
- `附加参数A`为可选参数, 你可以在[关于附加参数](#其它说明#关于附加参数#附加参数A)中了解更多.
- 你可以通过修改样式`IndexTitle`来自定义索引标题.


##### 其它 $\LaTeX$ 语法 {#主文件#正文区#常规控制命令#其它LaTeX语法}

要应用其它 $\LaTeX$ 语法, 请使用如下命令:

`\TextCommand{LaTeX代码}`

其它任何 $\LaTeX$ 语法对文档产生的作用都会出现在产出 PDF 文档的起始部分.

#### 目录控制命令 {#主文件#正文区#目录控制命令}

目录控制命令仅作用于目录排版, 不会对其它部分产生任何影响.

##### 分块标题 {#主文件#正文区#目录控制命令#分块标题}

`\CatalogPart{分块标题名称}`

##### 其它 $\LaTeX$ 语法 {#主文件#正文区#目录控制命令#其它LaTeX语法}

要专门应用其它 $\LaTeX$ 语法于目录, 请使用如下命令:

`\CatalogCommand{LaTeX代码}`

---

## ☆ 子文件 (`sec/.../[Section].tex`) {#子文件}

在子文件中可以正常使用任何 $\LaTeX$ 语法, 此外 $\mathrm{S^{imple}_{ystem}}\TeX$ 还额外提供了一些宏命令.

$\mathrm{S^{imple}_{ystem}}\TeX$ 会自动为每个节生成标题, 因此**不必在子文件中手动编写节标题**, 你可以通过修改样式`SectionHeading`来自定义节标题的风格.

### 区块 Block {#子文件#区块}

#### 定义 Definition | 定理 Theorem | 推论 Corollary {#子文件#区块#定义|定理|推论}

##### 用法 {#子文件#区块#定义|定理|推论#用法}

```LaTeX
\Definition{区块标签}(区块名称)<附加参数B>{
    区块内容
}
\Theorem{区块标签}(区块名称)<附加参数B>{
    区块内容
}
\Corollary{区块标签}(区块名称)<附加参数B>{
    区块内容
}
```

- `区块标签`是用于交叉引用的唯一标识符. 请勿在同一个子章下使用相同的`区块标签`.
- `区块名称`为可选参数, 若无该参数则默认使用`区块标签`作为区块名称.
- `附加参数B`为可选参数, 你可以在[关于附加参数](#其它说明#关于附加参数#附加参数B)中了解更多.

##### 示例 {#子文件#区块#定义|定理|推论#示例}

```LaTeX
\Definition{对称&反对称矩阵}(对称\&反对称矩阵){
    设 $\bm A$ 是 $n$ 阶方阵, $\bm A$ 是
    \par\noindent • 对称矩阵, 当且仅当 $\bm A=\bm A^{\rmT}$ .
    \par\noindent • 反对称矩阵, 当且仅当 $\bm A=-\bm A^{\rmT}$ .
}

\Theorem{线性映射构成线性空间}($\mathcal{L}\braI{U\and V}$是线性空间){
    $\braI{\mathcal{L}\braI{U\and V}\and\bfF\and+\and\cdot}$ 是线性空间, 其中加法和数乘定义为
    \begin{align*}
        \Forall{S\and T}{\mathcal{L}\braI{U\and V}}
        S+T:\bm u\mapsto S\bm u+T\bm u\ ,\\[-16mm]
    \end{align*}
    \begin{align*}
        \ForallII{\lambda}{\bfF}{T}{\mathcal{L}\braI{U\and V}}
        \lambda\cdot T:\bm u\mapsto\lambda T\bm u\ .
    \end{align*}
}

\Corollary{Jordan标准型的性质}{
    设 $\bm J_{T}$ 是 $T$ 的Jordan标准型, 则
    \par\noindent 1. $\bm J_{T}$ 中对应于 $\lambda$ 的最大Jordan块阶数等于 $\lambda$ 的指数.
    \par\noindent 2. $\bm J_{T}$ 中对应于 $\lambda$ 的各Jordan块阶数之和等于 $\lambda$ 的代数重数.
    \par\noindent 3. $\bm J_{T}$ 中对应于 $\lambda$ 的Jordan块数量等于 $\lambda$ 的几何重数.
}
```

#### 证明 Proof {#子文件#区块#证明}

##### 用法 {#子文件#区块#证明#用法}

```LaTeX
\Proof{区块名称}{
    区块内容
}
```

- `区块名称`中不能包含不可打印的 $\LaTeX$ 特殊字符（例如`&`）
- 可以在`区块内容`末尾处使用下列命令来生成证明结束符号 $\square$ :
    - `\ProofEndT` 以文本结束.
    - `\ProofEndF` 以公式结束.（如`align*`环境）
- 暂不支持对证明区块使用交叉引用.

##### 示例 {#子文件#区块#证明#示例}

```LaTeX
\Theorem{规范正交性引理}{
    设 $(\bm e_{k})_{k=1}^{n}$ 是一个规范正交向量组, 则
    \begin{align*}
        \Forall{(a_{k})_{k=1}^{n}}{\bfF^{n}}
        \norm{\sum_{k=1}^{n}a_{k}\bm e_{k}}^{2}=\sum_{k=1}^{n}\braIV{a_{k}}^{2}\ .
    \end{align*}
}
\Proof{证明I}{
    \begin{align*}
        \norm{\sum_{k=1}^{n}a_{k}\bm e_{k}}^{2}
        = \braV{\sum_{k=1}^{n}a_{k}\bm e_{k}\and\sum_{k=1}^{n}a_{k}\bm e_{k}}
        = \sum_{i=1}^{n}\sum_{j=1}^{n}a_{i}\overline{a_{j}}\delta_{i,j}
        = \sum_{k=1}^{n}\braIV{a_{k}}^{2}\ .\ProofEndF
    \end{align*}
}
\Proof{证明II{\scriptsize（数学归纳法）}}{
    \par 当 $n=1$ 时. 我们有 $\norm{a_{1}\bm e_{1}}=\braIV{a_{1}}\norm{\bm e_{1}}=\braIV{a_{1}}$ .
    \par 假设 $n=m$ 时上述命题成立. 由\link{内积空间}[正交性]{勾股定理}有
    \begin{align*}
        \norm{\sum_{k=1}^{m+1}a_{k}\bm e_{k}}^{2}
        = \norm{\sum_{k=1}^{m}a_{k}\bm e_{k}}^{2}+\norm{a_{m+1}\bm e_{m+1}}^{2}
        = \sum_{k=1}^{m}\braIV{a_{k}}^{2}+\braIV{a_{m+1}}^{2}
        = \sum_{k=1}^{m+1}\braIV{a_{k}}^{2}\ ,
    \end{align*}
    于是 $n=m+1$ 时上述命题成立, 进而其对一切正整数 $n$ 成立.\ProofEndT
}
```

### 交叉引用 Cross Reference {#子文件#交叉引用}

#### 区块 (Block) 链接 {#子文件#交叉引用#区块链接}

##### 用法 {#子文件#交叉引用#区块链接#用法}

```LaTeX
\link{章标签}[子章标签]{区块标签}(链接显示文本)<附加参数B>
```

- `子章标签`为可选参数, 对于直属节中的区块无需使用这一参数.
- `链接显示文本`为可选参数, 你可以通过[修改样式](#主文件#导言区#样式设置)来使用它.
- `附加参数B`为可选参数, 你可以在[关于附加参数](#其它说明#关于附加参数#附加参数B)中了解更多.
- 此链接将跳转至该区块名称处.

##### 示例 {#子文件#交叉引用#区块链接#示例}

```LaTeX
\par 下面的定理是\link{内积空间}{余弦定理}的一个直接推论.

\Corollary{勾股定理}{
    设 $V$ 是一个内积空间, 则
    \begin{align*}
        \Forall{\bm v_{1}\and\bm v_{2}}{V}
        \bm v_{1}\perp\bm v_{2}\implies
        \norm{\bm v_{1}+\bm v_{2}}^{2}
        = \norm{\bm v_{1}}^{2}+\norm{\bm v_{2}}^{2}\ .
    \end{align*}
}
```

#### 节 (Section) 链接 {#子文件#交叉引用#节链接}

##### 用法 {#子文件#交叉引用#节链接#用法}

```LaTeX
\seclink{章名称}[子章名称]{节标签}(链接显示文本)<附加参数B>
```

- `子章标签`为可选参数, 对于直属节无需使用这一参数.
- `链接显示文本`为可选参数, 你可以通过[修改样式](#主文件#导言区#样式设置)来使用它.
- `附加参数B`为可选参数, 你可以在[关于附加参数](#其它说明#关于附加参数#附加参数B)中了解更多.
- 此链接将跳转至该节标题处.

##### 示例 {#子文件#交叉引用#节链接#示例}

```LaTeX
\par 在\seclink{有限维线性空间}[矩阵表示]{向量&线性映射}(向量\&线性映射的矩阵表示)中我们将看到:
线性空间的基选定后, 任何线性映射 $T$ 都可以用 $\dim V\times\dim U$ 型矩阵来唯一确定.
```

#### 章/子章 (Chapter/Subchapter) 链接 {#子文件#交叉引用#章/子章链接}

##### 用法 {#子文件#交叉引用#章/子章链接#用法}

```LaTeX
\cptlink{章名称}[子章名称](链接显示文本)<附加参数B>
```

- `子章标签`为可选参数, 如需直接跳转至章则无需使用这一参数.
- `链接显示文本`为可选参数, 你可以通过[修改样式](#主文件#导言区#样式设置)来使用它.
- `附加参数B`为可选参数, 你可以在[关于附加参数](#其它说明#关于附加参数#附加参数B)中了解更多.
- 此链接将跳转至该章/子章在索引中的位置

##### 示例 {#子文件#交叉引用#章/子章链接#示例}

```LaTeX
\par 作为两种特殊的线性映射, 从线性空间 $V$ 到其自身和其所在域的映射将被赋予特别的名称,
我们将在\cptlink{线性空间}[线性变换]和\cptlink{线性空间}[线性泛函]中详细讨论其性质.
```

### 公式 Formulas {#子文件#公式}

#### 字母符号 {#子文件#公式#字母符号}

- 全微分 `\rmd` $\boxed{\mathrm{d}}$
- 自然常数 `\rme` $\boxed{\mathrm{e}}$
- 虚数单位 `\rmi` $\boxed{\mathrm{i}}$
- 组合数 `\rmC` $\boxed{\mathrm{C}}$
- 共轭转置 `\rmH` $\boxed{\mathrm{H}}$
- 转置 `\rmT` $\boxed{\mathrm{T}}$
- 复数集 `\bfC` $\boxed{\mathbf{C}}$
- 域 `\bfF` $\boxed{\mathbf{F}}$
- 自然数集 `\bfN` $\boxed{\mathbf{N}}$
- 有理数集 `\bfQ` $\boxed{\mathbf{Q}}$
- 实数集 `\bfR` $\boxed{\mathbf{R}}$
- 整数集 `\bfZ` $\boxed{\mathbf{Z}}$
- (变体)希腊字母φ `\phi` $\boxed{\varphi}$
- (变体)希腊字母ε `\epsilon` $\boxed{\varepsilon}$
- (变体)空集 `\emptyset` $\boxed{\varnothing}$

#### 分隔符 {#子文件#公式#分隔符}

- 逗号 `\and` $\boxed{\,,\,}$
- 分号 `\by` $\boxed{\,;\,}$
- 且 `\AND` $\boxed{\quad\mathrm{and}\quad}$
- 或 `\OR` $\boxed{\quad\mathrm{or}\quad}$

#### 括号 {#子文件#公式#括号}

- 圆括号 `\braI{x}` $\boxed{(x)}$
- 方括号 `\braII{x}` $\boxed{[x]}$
- 花括号 `\braIII{x}` $\boxed{\{x\}}$
- 竖括号 `\braIV{x}` $\boxed{|x|}$
- 尖括号 `\braV{x}` $\boxed{\langle x\rangle}$
- 左圆右方括号 `\braVI{x}` $\boxed{(x]}$
- 左方右圆括号 `\braVII{x}` $\boxed{[x)}$
- 向上取整括号 `\ceil{x}` $\boxed{\lceil x\rceil}$
- 向下取整括号 `\floor{x}` $\boxed{\lfloor x\rfloor}$
- 双竖括号（范数）`\norm{x}` $\boxed{||x||}$

这些括号的大小会根据被包裹的内容自动调整.

#### 运算 & 函数 {#子文件#公式#运算&函数}

##### 基本 {#子文件#公式#运算&函数#基本}

- 符号 `\sgn` $\boxed{\operatorname{sgn}}$
- 实部 `\Re` $\boxed{\operatorname{Re}}$
- 虚部 `\Im` $\boxed{\operatorname{Im}}$

##### 三角 {#子文件#公式#运算&函数#三角}

- 双曲正割 `\sech` $\boxed{\operatorname{sech}}$
- 双曲余割 `\csch` $\boxed{\operatorname{csch}}$
- 反余切 `\arccot` $\boxed{\operatorname{arccot}}$
- 反正割 `\arcsec` $\boxed{\operatorname{arcsec}}$
- 反余割 `\arccsc` $\boxed{\operatorname{arccsc}}$
- 反双曲正弦 `\arsinh` $\boxed{\operatorname{arsinh}}$
- 反双曲余弦 `\arcosh` $\boxed{\operatorname{arcosh}}$
- 反双曲正切 `\artanh` $\boxed{\operatorname{artanh}}$
- 反双曲余切 `\arcoth` $\boxed{\operatorname{arcoth}}$
- 反双曲正割 `\arsech` $\boxed{\operatorname{arsech}}$
- 反双曲余割 `\arcsch` $\boxed{\operatorname{arcsch}}$

##### 函数 {#子文件#公式#运算&函数#函数}

- 二次方 `\fsq` $\boxed{^{2}}$
- 三次方 `\fcu` $\boxed{^{3}}$
- $n$ 次方 `\fnpow` $\boxed{^{n}}$
- 反函数 `\finv` $\boxed{^{-1}}$
- 一阶导数 `\fder` $\boxed{'}$
- 二阶导数 `\fdder` $\boxed{''}$
- 三阶导数 `\fddder` $\boxed{'''}$
- $n$ 阶导数 `\fnder` $\boxed{^{(n)}}$

这些符号经过特殊优化, 请将其放置在函数符号与括号之间, 例如`f\fder\braI{x}`.

##### 线性代数 {#子文件#公式#运算&函数#线性代数}

- 迹 `\tr` $\boxed{\operatorname{tr}}$
- 像 `\im` $\boxed{\operatorname{im}}$
- 秩 `\rank` $\boxed{\operatorname{rank}}$
- 张成空间 `\spn` $\boxed{\operatorname{span}}$

#### 逻辑量词 {#子文件#公式#逻辑量词}

- 全称量词 I `\Forall{x}{A}` $\boxed{\forall\ x\in A:\quad}$
- 全称量词 II `\ForallII{x}{A}{y}{B}` $\boxed{\forall\ x\in A\ ,\ y\in B:\quad}$
- 存在量词 I `\Exists{x}{A}` $\boxed{\exists\ x\in A:\quad}$
- 存在量词 II `\ExistsII{x}{A}{y}{B}` $\boxed{\exists\ x\in A\ ,\ y\in B:\quad}$

#### 多行排版 {#子文件#公式#多行排版}

- 分支 II `\casesII{a}{caseA}{行间距(mm)}{b}{caseB}` $$\boxed{\begin{cases}\ a&\mathrm{case\,A}\\\ b&\mathrm{case\,B}\end{cases}}$$
- 分支 III `\casesIII{a}{caseA}{行间距(mm)}{b}{caseB}{行间距(mm)}{c}{caseC}` $$\boxed{\begin{cases}\ a&\mathrm{case\,A}\\\ b&\mathrm{case\,B}\\\ c&\mathrm{case\,C}\end{cases}}$$
- 圆角矩阵 `\matrix{列格式}{内容}`（格式与`array`环境一致）
- 方角矩阵 `\sqmatrix{列格式}{内容}`（格式与`array`环境一致）
- 行列式 `\determinant{列格式}{内容}`（格式与`array`环境一致）

---

## ℹ︎ 其它说明 {#其它说明}

### 关于参数宏 {#其它说明#关于参数宏}

在[样式设置](#主文件#导言区#样式设置)中提到的参数宏用于在样式内容中引用特定的信息, 这些信息会根据样式应用的具体场合而变化.

- `\parttitlename`
    - 交叉引用: 指向内容在目录中对应的分块标题名称.
    - 目录: 当前内容所在的分块标题名称.
    - 其它内容: 当前内容在目录中对应的分块标题名称.
- `\chaptername`
    - 交叉引用/目录/索引: 指向内容所在的章名称.
    - 其它内容: 当前内容所在的章名称.
- `\subchaptername`
    - 交叉引用/目录/索引: 指向内容所在的子章名称.
    - 其它内容: 当前内容所在的子章名称.
- `\sectionname`
    - 交叉引用/目录/索引: 指向内容所在的节名称.
    - 其它内容: 当前内容所在的节名称.
- `\blockname`
    - 区块: 区块名称.
    - 交叉引用: 指向区块的名称.
- `\blockcontent`
    - 区块: 区块内容.
    - 交叉引用: 指向区块的内容.
- `\linktext`
    - 交叉引用: 链接显示文本

关于参数宏`\parameterA`和`\parameterB`, 请参考[关于附加参数](#其它说明#关于附加参数).

### 关于附加参数 {#其它说明#关于附加参数}

附加参数允许你向 $\mathrm{S^{imple}_{ystem}}\TeX$ 传递额外的信息, 这些信息可用于实现条件分支或者作为补充内容来显示. 附加参数根据引入场合和作用域分为如下两种.

#### 附加参数 A {#其它说明#关于附加参数#附加参数A}

- 附加参数 A 只能在导入子文件和生成索引时引入
- 附加参数 A 的作用域一直持续到其下个引入场合为止, 且适用于目录中的相应部分.
- 你可以将副标题等内容作为附加参数 A 引入, 并且通过[修改样式](#主文件#导言区#样式设置)来使用它.

#### 附加参数 B {#其它说明#关于附加参数#附加参数B}

- 附加参数 B 可在其它任何命令中引入
- 附加参数 B 的作用域仅限于该命令本身.
- 你可以将替用显示文本等内容作为附加参数 B 引入, 并且通过[修改样式](#主文件#导言区#样式设置)来使用它.

---

## 📄 附录 {#附录}

### 样式默认值 {#附录#样式默认值}

下面是 $\mathrm{S^{imple}_{ystem}}\TeX$ 为各个样式预设的默认值, 你可以参考这些默认值来编写自己的样式.

**`CatalogTitle`**
```LaTeX
\Large\bfseries
\begin{center}Content\end{center}
\bigskip
```

**`CatalogPartTitle`**
```LaTeX
\Large\parttitlename
\vspace{-5pt}
```

**`CatalogSection`**
```LaTeX
\ifempty\subchaptername {
    \,{\scriptsize\chaptername}\ |\ \sectionname
} {
    \,{\scriptsize\chaptername}\ \subchaptername\ |\ \sectionname
}
\vspace{-7.5pt}
```

**`CatalogIndex`**
```LaTeX
{\large\chaptername}\ \parameterA
\vspace{-7.5pt}
```

**`IndexTitle`**
```LaTeX
\noindent
\bfseries{\huge\chaptername}\ {\Large\parameterA}
\par
```

**`IndexSubchapter`**
```LaTeX
\ifempty\subchaptername{
    {\Large\chaptername}
} {
    {\normalsize\chaptername}\ {\Large\subchaptername}
}
\vspace{-5pt}
```

**`IndexSection`**
```LaTeX
\ifempty\subchaptername {
    \,{\scriptsize\chaptername}\ |\ \sectionname
} {
    \,{\scriptsize\chaptername}\ \subchaptername\ |\ \sectionname
}
```

**`SectionHeading`**
```LaTeX
\noindent
\bfseries
\ifempty\subchaptername {
    {\Large\chaptername}{\huge\;|\;\sectionname}
} {
    {\Large\chaptername}\ {\huge\subchaptername\;|\;\sectionname}
}
\par\bigskip
```

**`DefinitionName`**
```LaTeX
\vspace{4pt}\noindent
\color{purple}\bfseries\blockname
\quad
```

**`DefinitionContent`**
```LaTeX
\color{purple}\itshape\blockcontent
```

**`TheoremName`**
```LaTeX
\vspace{4pt}\noindent
\color{teal}\bfseries\blockname
\quad
```

**`TheoremContent`**
```LaTeX
\color{teal}\itshape\blockcontent
```

**`CorollaryName`**
```LaTeX
\vspace{4pt}\noindent
\color{brown}\bfseries\blockname
\quad
```

**`CorollaryContent`**
```LaTeX
\color{brown}\itshape\blockcontent
```

**`ProofName`**
```LaTeX
\par\noindent
\itshape\blockname
```

**`ProofContent`**
```LaTeX
\itshape\blockcontent
\par\smallskip
```

**`BlockLink`**
```LaTeX
\bfseries
\ifempty\linktext {
    \,\blockname\,
} {
    \,\linktext\,
}
```

**`SectionLink`**
```LaTeX
\bfseries
\ifempty\linktext {
    \ifempty\subchaptername {
        \,{\footnotesize\chaptername}\,|\,\sectionname\,
    } {
        \,{\footnotesize\chaptername}\;\subchaptername\,|\,\sectionname\,
    }
} {
    \,\linktext\,
}
```

**`ChapterLink`**
```LaTeX
\bfseries
\ifempty\linktext {
    \ifempty\subchaptername {
        \,\chaptername\,
    } {
        \,{\footnotesize\chaptername}\;\subchaptername\,
    }
} {
    \,\linktext\,
}
```

### 主文件示例 {#附录#主文件示例}

```LaTeX
% --------------------------------------------------
% | 导言区 | Preamble (XeLaTeX) |
% --------------------------------------------------

\documentclass[10pt]{article}
\usepackage{simplesystem,ctex}

% 字体 | Fonts

\newCJKfontfamily\HeavyFontC{方正春晚龙行体 简 Heavy}

% 样式设置 | Format Settings

\ExplSyntaxOn % 打开 expl3 编程层 防止换行产生空格

\FormatSetting {CatalogTitle} {
    \Large\HeavyFontC
    \begin{center}目录\quad\textbf{Content}\end{center}\bigskip
}
\FormatSetting {IndexTitle} {
    \noindent
    \HeavyFontC{\huge\chaptername}\ \textbf{\Large\parameterA}
    \par
}
\FormatSetting {SectionHeading} {
    \noindent
    \bfseries\HeavyFontC
    \ifempty\subchaptername {
        {\Large\chaptername}{\huge\;|\;\sectionname}
    } {
        {\Large\chaptername}\ {\huge\subchaptername\;|\;\sectionname}
    }
    \par\bigskip
}

\ExplSyntaxOff % 关闭 expl3 编程层

% --------------------------------------------------
% | 正文区 | Body |
% --------------------------------------------------

\begin{document}

    \pagestyle{plain}

    % 目录 | Catalog

    \MakeSimpleCatalog
    \TextCommand{\newpage}

    % 线性空间
    \CatalogPart{$\bm{\alpha_{1}}$}
    \ImportSection{线性空间}{定义}
    \ImportSection{线性空间}{基本性质}
    \ImportSection{线性空间}[子空间]{定义}
    \ImportSection{线性空间}[向量组]{张成空间}
    \ImportSection{线性空间}[向量组]{线性相关性}
    \ImportSection{线性空间}[向量组]{替换定理}
    \ImportSection{线性空间}{Hamel基}
    \ImportSection{线性空间}[子空间]{交&和}(交\&和)
    \ImportSection{线性空间}[子空间]{直和}
    \ImportSection{线性空间}[子空间]{商空间}
    \ImportSection{有限维线性空间}{定义}
    \ImportSection{有限维线性空间}{基&维数}(基\&维数)
    \ImportSection{有限维线性空间}{维数公式}

    % 线性映射
    \CatalogPart{$\bm{\alpha_{2}}$}
    \ImportSection{线性空间}[线性映射]{定义}
    \ImportSection{线性空间}[线性映射]{线性映射空间}
    \ImportSection{线性空间}[线性映射]{核&像}(核\&像)
    \ImportSection{线性空间}[线性映射]{复合}
    \ImportSection{线性空间}[线性映射]{逆}
    \ImportSection{有限维线性空间}{秩—零化度定理}(秩\—零化度定理)
    \CatalogCommand{\newpage}

    % 多重线性代数
    \CatalogPart{$\bm{\alpha_{3}}$}
    \ImportSection{线性空间}[多重线性型]{定义}
    \ImportSection{线性空间}[多重线性型]{对称型}
    \ImportSection{线性空间}[多重线性型]{交错型}
    \ImportSection{线性空间}[双线性型]{对称交错分解}

    % 矩阵&行列式
    \CatalogPart{$\bm{\beta}$}
    \ImportSection{域}[矩阵]{定义}
    \ImportSection{域}[矩阵]{积}
    \ImportSection{域}[行列式]{定义}
    \ImportSection{域}[行列式]{基本性质}

    % 特征值理论
    \CatalogPart{$\bm{\gamma_{1}}$}
    \ImportSection{线性空间}[线性变换]{特征值}
    \ImportSection{线性空间}[线性变换]{广义特征空间}
    \ImportSection{有限线性空间}[特征多项式]{定义}
    \ImportSection{有限维线性空间}[特征多项式]{基本性质}
    \ImportSection{有限维线性空间}[特征多项式]{代数重数}
    \ImportSection{线性空间}[最小多项式]{定义}
    \ImportSection{线性空间}[最小多项式]{基本性质}
    \ImportSection{有限维线性空间}[矩阵表示]{对角化}
    \CatalogCommand{\newpage}

    % 相似标准型
    \CatalogPart{$\bm{\gamma_{2}}$}
    \ImportSection{有限维线性空间}{广义特征空间分解}
    \ImportSection{线性空间}[线性变换]{循环空间}
    \ImportSection{有限维线性空间}{幂零循环空间分解}
    \ImportSection{有限维线性空间}[矩阵表示]{Jordan标准型}

    % 索引 | Index

    \CatalogCommand{\bigskip\bigskip}
    \TextCommand{\newpage}
    \MakeSimpleIndex{域}<Field>
    \TextCommand{\newpage}
    \MakeSimpleIndex{线性空间}<Linear Space>
    \TextCommand{\newpage}
    \MakeSimpleIndex{有限维线性空间}<Finite Dimensional Linear Space>
    \TextCommand{\newpage}
    \MakeSimpleIndex{赋范空间}<Normed Space>
    \TextCommand{\newpage}
    \MakeSimpleIndex{内积空间}<Inner Product Space>

\end{document}
```
