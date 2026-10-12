# 有村ロミ

- GitHub：[@biyuehu](https://github.com/biyuehu)
- 感兴趣的方向：前端 / 后端
- 目前接触过：见下文

## 我想学什么

参加下文。经验最多的当属 Web 方向，尤其是前端。后端也有不同了解。技术了解广度应该还行。

目前写得最多也最爱的语言是 TypeScript，第二多第二爱的语言是 Rust，再然后是 Haskell。

热衷于了解不同编程语言之间的差距、各种新颖的现代化的编程语言设计。不固守某一语言、框架，不限制自己的眼界。

对函数式编程语言，以及程序语言理论、类型论等计算机科学理论领域尤为感兴趣。

## 我想做什么

见下文

## 一个想问的问题

<!-- TODO: ... -->

## 笔记

- 2026-10-06：[从 OOP 协逆变到类型极性、负递归和可终止性](https://i.arimuraromi.com/post/oop-rec-total)
- 2026-08-03：[Koka入门③：效果系统、效果处理、自定义控制流](https://i.arimuraromi.com/post/koka-learn-3)
- 2026-07-31：[比较编程①：enum与ADT的真相，以及广义代数数据类型](https://i.arimuraromi.com/post/compro-1-enum)
- 2026-07-27 ：[Koka入门①：副作用与错误处理史、现代语言困境、安装](https://i.arimuraromi.com/post/koka-learn-1)
- 2026-01-22：[Scala3 观察日志1：类、类型类、对象、隐式实例、函数式](https://i.arimuraromi.com/post/scala-observing-1)
- 2024-09-03：[代码变量/函数/方法/类/文件/项目命名规范](https://i.arimuraromi.com/post/33)
- 2023-07-01：[JS的原型、原型链、构造函数](https://i.arimuraromi.com/post/16)
- 2023-06-16：[Git笔记](https://i.arimuraromi.com/post/15)
- 2022-08-12：[HTML笔记](https://i.arimuraromi.com/post/3)
- 2022-08-09：[JavaScript笔记1-ES5~6语法](https://i.arimuraromi.com/post/2)
- 2020-12-05：[MarkDown基础语法](https://i.arimuraromi.com/post/1)

## 作品

> 标题加**粗**的为最重要的一批项目。

### 本月正在开发中

#### [ts-plus-plus](https://github.com/biyuehu/ts-plus-plus)

- 开始：2026.10

昨日在我朋友怂恿下拟定的一个小团体内共同开发项目，基于 TypeScript 的 `Release-6.0` 分支的全新编程语言，旨在扩展 TypeScript 的类型系统能力以及引入现代语言特性，相关设计方向可参考 `README`，拟定加入特性可参考 [提案](https://github.com/biyuehu/ts-plus-plus/issues/2)。

截至目前，已实现 HKT（Higher-kinded Types，高阶类型）与类型宇宙：

```ts
type Pair<A, B> = [A, B];
type Apply2<F: (Type0, Type0) => Type0, A, B> = F<A, B>;
type NamedAge = Apply2<Pair, string, number>;

type Arrays: Type0 => Type0 = Array;
interface Functor<F: Type0 => Type0> {
  map<A, B>(fa: F<A>, fn: (value: A) => B): F<B>;
}
const arrayFunctor: Functor<Arrays> = {
  map: (values, fn) => values.map(fn),
};
```

此刻正欲打算实现名义化类型（`newtype`）与代数数据类型（`data`）。

#### [MoPress](https://github.com/biyuehu/mopress)

- 开始：2026.6
- [函数式！强大的文档网站兼通用网站生成工具](https://www.bilibili.com/video/BV1gaKN6EEtc)
- [官网与文档](https://mo.himeno-sena.com/)
- 技术栈：MoonBit

MoPress 是一个基于 MoonBit 语言、面向 MoonBit 生态的现代文档与通用静态站点生成工具，设计上同时参考了 mdBook 与 Hakyll。它的核心使用嵌入式 DSL（Domain Specific Language）来声明配置和函数式的处理管线来表达构建流程，同时提供丰富的语言无关向插件系统与自定义能力，以满足各种需求。

```moonbit
///|
async fn main {
  @core.mopress([
    Glob(
      "**/*.md",
      Text(raw => {
        raw
        |> @core.set_extension(".html")
        |> @core.render_markdown_and_frontmatter
        |> @core.load_and_apply_template("templates/default.html")
        |> @core.use_js(["console.log('hi, moonbit! hi, mopress!')"])
        |> @core.unify
      }),
    ),
    Glob("styles/**/*", Copy),
  ])
}
```

为 MoonBit 2026 年 5~7 月开源大赛参数项目，现正作为持续维护项目参加 MoonBit 十月赛。

#### [MonadBeat](https://github.com/biyuehu/monadbeat)

- 开始：2026.9
- 技术栈：Python、FastAPI、UnoCSS、Solid、TypeScript
- 参考企划：[MonadBeat / 单子律动](https://gist.github.com/biyuehu/27f199e96e3345519784ca73b4b68549)

一个面向 Haskell 爱好者的刷题网站。区别于普通算法刷题网站(LeetCode、Codewars 等其实也支持 Haskell，但题目和判题方式跟其他语言没什么两样，只是"换个语言写算法题")，MonadBeat 专注做只有 Haskell / 类型系统语境下才有意义的题目——玩类型推导、玩惰性求值、玩代数结构定律，而不是刷普通算法题。

### 持续维护中项目

#### **[RomiNest](https://github.com/biyuehu/romi-nest)**

- 开始：2024.10
- 技术栈：Angular、TypeScript、Rust、Axum、Sea-ORM、Lit、UuoCSS、Bun
- 介绍文章：[耗时两年，我做了这个极致个人化的全栈博客系统](https://i.arimuraromi.com/post/this-site)
- 介绍视频：[极致个人化的全栈开源博客项目基于Rust与Angular！](https://www.bilibili.com/video/BV1P4tJ6eEYC)

[本人博客](https://i.arimuraromi.com/) 的核心系统，一个前后端一体的个人门户网站系统，前端负责展示和交互，后端提供 API 和 SSR 服务，整体部署在单一可执行程序上。

博客功能主导，但不只是博客：

- 还算简约（不是简陋？）不花里胡哨不重口 CSS 不八股拟态风的 UI 界面
- 支持文章、动态、歌单、一言、角色记录、番剧与视觉小说记录（后续会支持书籍与电影记录）
- 功能强大不臃肿的后端，支持账号系统与评论系统以及安全管理（后续会支持 GitHub 账号登录）
- 公开的、通用的 HTTP API
- 现代的开发工作流，现代的技术栈
- 基于 ReScript 自研的音乐播放器
- 有趣的主题配色系统与角色生日提醒（继承自 MoeHub）
- 极致个人：无论是内容上还是技术选型上

前端采用 Angular 作为主框架。引入 Lit 框架编写和 Angular 解耦、与具体界面框架无关的通用 UI 组件库。样式均使用 UnoCSS。

后端使用 Axum 作为 Web 框架。数据层通过 SeaORM 操作 MySQL。JsonWebToken 用于用户认证。后端同时负责 SSR：启动一个 Node.js 子进程渲染 Angular 页面，未命中 API 的请求会转发给 Node 进程处理，实现服务端渲染。还有实时任务负责角色生日提醒。

类型一致性：Rust 侧使用 ts-rs 将模型导出为 TypeScript 类型，前端 API 层直接引用这些类型，保证前后端数据结构一致。

#### [WebAgent](https://github.com/biyuehu/webagent)

- 开始：2026.8

一个轻量级、基于 DSL 驱动的 AI 工具，用于文件操作、代码修改和命令执行——为网页和客户端AI助手而设计。

Web Agent 与众不同：兼容任何网页AI——复制生成的提示，将其粘贴到浏览器的AI聊天中（Claude、ChatGPT、DeepSeek等），让 AI 返回 DSL 命令（基于 MarkDown）。零成本且免费，无需 API 调用，白嫖网页 AI 额度。即时，在本地使用 Bun 运行。透明，在执行前，你可以看到每一个文件变更和命令。它弥合了“浏览器中的AI”和“你机器上的文件”之间的差距。

#### **[KotoriBot](https://github.com/kotorijs/kotori)**

- 开始：2023.5
- 介绍视频：[基于 TS 与 Node 的新一聊天机器人框架，支持多平台](https://www.bilibili.com/video/BV19xsxeEEP9)、[基于Node.js的Kotori机器人插件开发教程](https://www.bilibili.com/video/BV1MCFTeoE98)
- [官网与文档](https://kotori.js.org/)

当年效仿 Koishi 的造轮。给了我很多第一次：第一次思考项目架构、学习设计模式、学习 AOP、Monorepo、复杂的构建流程、CICD、单元测试、包发版等。

一个多平台、功能强大的聊天机器人应用，通过安装不同模块为 Kotori 扩展功能、玩法和个性化配置等。同时，Kotori 为开发者提供了现成的 Cli 用于模块开发与 Kotori 二次开发。

- 跨平台：得益于模块化支持，通过编写各种模块实现不同的功能与聊天平台接入
- 解耦合：基于控制反转（IOC）与面向切面编程（AOP）思想，减少代码冗余与复杂度
- 现代化：使用现代化的 ECMAScript 语法规范与强大的 TypeScript 类型支持

确实挺大的，三十余个插件模块以及 WebUI 也是自己弄的，篇幅原因不展开了，感兴趣可自行看官网文档。

#### [HimenoSena](https://github.com/biyuehu/HimenoSena)

- 开始：2025.2
- 介绍文章：[我做了一个姬野星奏的专属网站](https://www.bilibili.com/video/BV17mKsezEcw)
- 介绍视频：[姬野星奏网站2026.6更新介绍](https://www.bilibili.com/video/BV1itE96bEDf)
- [himeno-sena.com](https://himeno-sena.com/)
- 技术栈：Deno、TypeScript、WebComponents、Lit

为老婆做的专属网站以及专属域名（宣誓主权说是）。有展示、留言的功能。第一次使用到 Deno 以及 Lit 库，Lit 很好，但 Deno 的迁移成本给我留下了不好的印象。总之是因爱而生的最特别项目，也是最用心的项目之一，无需多言。一开始是用了点 PHP 实现访问计数（很糟糕），后来在 RomiNest 侧中实现公用的统计 API，故重构为纯静态版。

#### [StarON](https://github.com/biyuehu/staron)

- 开始：2026.8

一个超轻量的 npm 库，作用是要求使用者登录 GitHub 账号然后判断该账户是否 Star 指定项目，未 Star 触发退出不让用（或者自定义钩子），适用于 CLI 工具。顺手为 WebAgent 项目做的。

值得一提的是对于 FailAction 用到了我最爱的代数数据类型建模：

```typescript
import { Block, Warn, Fn } from 'staron'

Block('Custom message')       // print message and exit(1)
Warn('Custom message')        // print message and continue
Fn((ctx) => { /* ... */ })    // fully custom handling
```

### 持续开发中项目

#### **[SenaLang](https://github.com/biyuehu/sena-lang)**

- 介绍视频：[自制编程语言之基于Rust的实验性支持一等类型多后端现代函数式语言](https://www.bilibili.com/video/BV1JaYrzEEpk)
- 开始：2024.12
- [在线使用](https://l.himeno-sena.com)

一门基于 Rust 开发的支持多后端、多范式、现代化的函数式编程语言。计划支持一等类型、类型类、列表推导式、代数效果系统、RankNTypes、FOmega（HKT）、LLVM / WASM / Native C 等后端。现已实现基本语法、代数数据类型、模式匹配、自定义中缀运算符、JS 后端、直接解释器、一等类型。

最不别具一格的设计是关于类型宇宙与依赖类型的取舍：[详情](https://github.com/biyuehu/sena-lang#advantages)。

计划是在完善类型理论、范畴论、程序语言理论的知识储备后（主要是指基本学完 *Types And Programming Language* 后），作为本科期间的长期开发作品。

本项目第一次接触到了编程语言的诞生过程与构造的基础知识（词法分析、语法分析、解释器、编译器等），也练习了 Rust。

#### [SenaMusic](https://github.com/biyuehu/sena-music)

- 开始：2026.5
- 技术栈：TypeScrip、Lit-html、WebComponents、Zod、tRPC、Android、Desktop、UnoCSS

一个轻量级的自托管音乐播放器，将来自多个来源的歌曲汇集到统一的播放列表中（以网易云音乐源作为主要来源播放列表）。你可以听需要 VIP 的歌曲或在大陆被禁播的歌曲。已支持 网易云音乐、QQ 音乐、BiliBili、YouTube 源获取。计划支持 Android、Windows、Web 三平台。

此外，真正亮点是：

前端为采用 Signal 与 lit-html 技术封装的一个轻量的、函数式的 WebComponents 库。架构上采用 parcel 的多页面开发机制。

后端为基于 Node.JS 的 http 包和 Monad 概念开发的一款类似于 tRPC 的、函数式的、类型安全的、前后端零距离的框架：

```typescript
// 后端
export type AppRouter = InferRouteToClientRoute<typeof appRoute>

export const setSongSourceHandler = Action.empty<AppState>()
  .use([
    new BodyExtracter(
      z.object({
        id: z.string(),
        source: songSourceTypeSchema,
        value: z.string()
      })
    )
  ] as const)
  .bind(async ([{ id, source, value }], { logger }) =>
  // 类型全部自动推断
    Data.load().match({
      Right: (playlist) => {
        const songIndex = playlist.findIndex((song) => song.id === id)

        if (songIndex === -1) {
          logger.warn(`Song with id ${id} not found`)
          return Left({ error: `Song with id ${id} not found` })
        }
        ...
      },
      Left: (err) => {
        logger.error('Failed to load playlist:', err)
        return Left({ error: `Failed to load playlist: ${stringifyCatchError(err)}` })
      }
    })
  )

const setSongSource = Api.new(
  setSongSourceHandler,
  z.object({ playlist: playListSchema }),
  standardJsonReturnErrorSchema,
  new JsonReturner()
)

...

// 前端
import { createClient } from '@/romi/client'
import type { AppRouter } from '../server/app'
import { Cache } from './cache'

export const httpClient = createClient<AppRouter>({
  baseUrl: Cache.get<string>('api-base-url').unwrapOrElse(() => '')
})
httpClient.setSongOrder({ id, order: newIndex }).then((res) => ...)
// 类型自动推断，基于 Proxy 技术
```

#### [SenaVN](https://github.com/biyuehu/vn-cli)

- 开始：2026.4
- 技术栈：Haskell、Rust、Sqlite、WinAPI、GHC、Cabal

基于 Haskell 编程语言主导、Rust 胶水对接的视觉小说计时、管理、云端数据同步工具，与前作 GalKeeper 最大不同的是：

市面上这几年烂大街的 GalGame 管理工具，技术栈单一毫无创新可言令人乏味（可见 Vibe 对开发门槛之打击），本项目专为程序员设计，无图形化界面的纯终端工具，请自行想象终端输入 `gal run xxx` 便可打开游戏的炫酷感与便捷感。同时，由于意识形态原因本项目仅打算支持 Windows。

此外，本项目将证明 Haskell 作为工程开发的完全可行性以及本人的 Haskell 经验积累。与前代的主要联系在 Rust 侧基于前代的 Tauri 代码迁移。等待时机继续开发中。

#### [SenaTab](https://github.com/biyuehu/sena-tab)

- 介绍文章：[一次艺术表演——我用四门函数式语言写了个全栈项目](https://i.arimuraromi.com/post/four-fp)
- 开始：2024
- 技术栈：React、TypeScript、UnoCSS、Tsukiko

看到某个精美的浏览器新标签页扩展心血来潮的造轮。简洁、大气、多语言的界面。用上了自己写的 Tsukiko 库，第一次了解到了 Chrome 扩展的制造流程。

### 意义重大项目

#### [GardenMansion](https://github.com/biyuehu/GardenMansion)

- 时间：2025.10 开始，2026.8 结束
- 介绍文章：[一次艺术表演——我用四门函数式语言写了个全栈项目](https://i.arimuraromi.com/post/four-fp)
- 介绍视频：[我用四门函数式语言写了一个CRUD项目](https://www.bilibili.com/video/BV1QZub6bEfz)
- 技术栈：PureScript、Elm、Haskell、Idris2、TypeScript、Python、DHall、LevelDB、Bun、Node.JS、UnoCSS

前端采用 Elm 编程语言与 Vite，后端采用自行用 PureScript 编程语言、基于 Node.JS 的 http 库与 Monad 变换器封装的核心（被 Monad 强大和恐怖吓哭），数据库采用 Idris2 编程语言基于 LevelDB 封装，通过 JS FFI 对接 PureScript 后端。前后端共同类型使用 Haskell 编程语言表示，Elm 与 PureScript 的代码生成通过 Python 脚本实现。前后端胶水代码使用微量 TypeScript、JavaScript、CSS、HTML。样式采用 UnoCSS。配置文件采用 DHall。开发工具采用 Bun、Just、

毫无疑问，这从未打算做成正经的项目给人用，它的功能本身就是 Demo 级的（实用性为零），但又绝对不同于任何低劣的 Demo。 想到如果它用正常的 TypeScript 写的话，很快就能做完甚至做得更强，但显然这业务本身是毫无趣点吸引我，而且简单至极，故前提不成立。 既然如此，我觉得有没有人用更无所谓了，毕竟最大乐趣已经漂移到过程本身了。

过程是异常有趣的，高度的精确至空行数量与结尾空行的代码洁癖姑且算是一股清流了。这绝不是一个面向工业的正经项目，但或许是一回有趣的过程体验，一个别样的行为艺术，一次独特的个人表达，一场无聊的炫技表演，或者说对人人都在追求 AI 高效率高节奏开发的时代潮流中最彻骨的叛逆。

对于过程，多少还是了能学到不少东西（重要程度降序）：

- 多种语言操作、FFI 对接
- 多语言构建流程搭建、调度、设计
- Monad Transform 的实际应用
- Async Monad 的封装
- 函数式的后端基本框架的封装
- 前端页面的响应式编程开发
- 超复杂 CICD 的搭建

#### [DiceScript](https://github.com/biyuehu/dice-script)

- [演示网站](dice-script.vercel.app)
- 介绍视频：[一款基于Idris类型安全强大的骰子表达式开源解析库](https://www.bilibili.com/video/BV14ui5BgEoj)
- 时间：2025.3
- 技术栈：Idris2、Bun、Python、Codeberg、Vite

基于 Idris2 编程语言实现的一个骰子表达式解释器，含完整的词法分析、语法分析、求值器三过程。支持高级用法（数学函数、Lambda）。支持 JS、ChezScheme、Ref C、Racket 多个编译后端。并且还用 Idris2 通过 JS FFI 实现了前端网页编写。是个人第一个使用 Idris2 主导完成的正式项目，感受到了 Idris2 这门依赖类型的现代函数式编程语言的惊艳（LSP 不是很好用就是了）。

#### [GalKeeper](https://github.com/biyuehu/gal-keeper-1.x)

- 介绍视频：[一款开源的视觉小说管理与数据同步工具](https://www.bilibili.com/video/BV1VFGE6uEeA)
- 时间：2025

一个基于 React、FluentUI、Tauri、Rust、UnoCSS、GitHub API 开发的视觉小说游戏计时、管理、云端同步工具（基于 GitHub 仓库进行云端数据存储）。主要是想用 FluentUI 玩玩，然后试试 TauriV2，再者是当时对自己来说属于刚需。吸取了不该随随便便用 LevelDB 作为数据库存储的教训，令人痛心。现已停止维护，请移步至后继者 SenaVN。

#### [Sirius2](https://github.com/biyuehu/sirius2) & [Sirius](https://github.com/biyuehu/sirius)

- 演示视频（v2）：[国际版Addon实现文件本地读写](https://www.bilibili.com/video/BV139Tqz4Exd)
- 时间：2025.1
- 技术栈：tsup、tsx、Rust、Salvo

基于原生 BDS 运行的下一代最全面的 Minecraft 基岩版 BDS 服务器基础&综合性功能插件。问基岩版 Addon 提供了文件操作、数据库操作的能力，同时有了成套的 TPA、HOME、LAND、HELPER 等非零散性的基础服务器插件。宗旨继承于 Sirius1，亮点我想是为五年前搞 MC 开发的我所在的那个地方传来了工程化开发的火种。不再持续维护。第一次学习到配置 tsup 工具打包 TypeScript 以及 tsx 这一运行工具。

Sirius1 则是基于 LeviLamina 运行的下一代最全面的 Minecraft 基岩版 BDS 服务器基础&综合性功能插件（然后 LeviLamina 死了，所以有了原生的 Sirius2）。动机是见其 BDS 服务器插件生态百花齐放，但也造就插件质量参差不齐，某个简简单单的功能却还要装多个插件，更不用提很多脚本插件（尤其是 JavaScript）的开发者并未有过工程化开发经历，致使其代码可靠性与可维护性不堪入目还不自知。同时，LeviLamina 不如曾经的 BedrockX 的预装插件就已提供了官方实现、安全可靠的 Tpa、Home、Warp、Menu、Gui、Money、Helper 等多个基础功能，而 Sirius 则正是为 LeviLamina 填补该空缺，此外有不少指令也模仿了 BedrockX 进行实现，意在向 BedrockX 这一经典项目致敬。不再维护。

#### [Tsukiko](https://github.com/biyuehu/tsukiko)

- 介绍视频：[基于TypeScript开发的运行时下动态类型检查](https://www.bilibili.com/video/BV11j421R7tL)
- 时间：2023.11
- 技术栈：pnpm、TypeScript、Jest

灵感来自于 Zod，类似的一个轻量级 TypeScript 运行时类型校验库。那会儿对 TypeScript 还属于开智阶段，又对运行时校验很好奇（毕竟本身也是个一直以来的痛点，对于后端返回数据的安全性），所以就自己尝试实现了一个。第一次感受到了类型体操的洗礼（但其实也没有太复杂的体操）在为了实现精准的类型推断时。印象中除了单元测试外，还用到了一个工具从 JSDoc 中自动生成文档。不再持续维护。

#### [MoeHub](https://github.com/biyuehu/moehub)

- 介绍文章：[个人向的角色收藏与管理网站系统](https://i.arimuraromi.com/post/30)
- 介绍视频：[开源的GAL/动漫角色收藏网站系统](https://www.bilibili.com/video/BV1mQxSerEzk)
- 时间：2024.6
- 技术栈：pnpm、TypeScript、Koa、Prisma、Inversify、React、BiomeJS

个人向的角色收藏与管理网站系统。起点很简单，想给二次元老婆一个家，每位都有一个独立页面。印象中是在这里第一次用到 BiomeJS（代替 ESLint、Prettier），想提前体验下 NestJS 框架的那种类似 SpringBoot 的装饰器、依赖注入、AOP 开发风格，于是自己用 Koa（其实可以用 Express，但已经用过所以换了个，Koa 有点坑其实）和 Inversify 库封装了一下。算是第一个有点规模且正式的全栈项目。印象中 React 第一次在这里用，为目录规划头疼了会儿。Prsima 这种 ORM 框架也是第一次用，十分好用，还有 JWT 处理也是在这里第一次。Monorepo 让共同类型问题变得简单，这项目一过，之后其实很少有前后端同时用 TypeScript 开发以至于类型通用的体验了（截止到 SenaMusic 项目），因为后面选后端框架都给了别的语言机会。还有就是通过 Corn 表达式实现了角色生日的邮件提醒。该项目基本不再维护，但其精神、核心以及生日提醒均在 RomiNest 中[复现并统一](https://i.arimuraromi.com/char)（也是在这之后决定自研开发博客系统）。

#### [HuliTOOL](https://github.com/biyuehu/hulitool)

- 介绍视频：[基于Vue3+Ts的纯前端工具箱应用网站](https://www.bilibili.com/video/BV1R44y1w7e3)
- 时间：2023.7
- 技术栈：Vue3、TypeScript、Vite、Pinia、MDUI
- [在线使用](https://foxtool.vercel.app/)

该项目是本人的第一个 Vue + TypeScript + Vite + Pinia 项目实践，主要用于 Vue 练手。通过 Vue、TypeScript 第一次进入到前端工程化开发的世界，当时觉得工程化一词很高级而震撼，Vue 也是本人学的第一个现代前端框架，本项目大致是仿效着写的，也震撼于原来有个叫 NPM 的平台有那么多的现成库啊。毕竟是三年前了，这里面一些东西也有点旧了，至于技术能力、代码品味更是不同往日，一直是希望有机会对此重构、修复顺带温习 Vue，但看起来有点忙呢。

#### [HULICore](https://github.com/biyuehu/hulicore)

- 时间：2022~2024。2026.8 入土归档。
- 技术栈：PHP、Layui、JQuery、JavaScript、Bootstrap、MySQL、PHPEmailer

基于原生 PHP 制造一整套框架，主要封装了数据库操作、伪静态路由、功能函数等功能，框架遵守 MVC 架构，应用实例由 Controller 控制器、Model 模型、View 视图三部分组成，并在一定基础上参考了 typecho，由着网站主题 Theme 与插件 Plugin 两样用户级的功能。

已过时，各种意义上。但作为初二时期对项目架构的一次探索意义不小。学到了 OOP 基础、模块化开发、SQL 数据库以及服务器、网站部署、域名等相关知识。此外，那会儿这玩意闭源，用源码赚了一点点小钱。

### 一次性小项目

#### [Mikoto](https://github.com/biyuehu/mikoto)

- 介绍视频：[Teal语言体验一次游，像素打乱工具网站Demo](https://www.bilibili.com/video/BV1VE8B6zEMS)
- 时间：2026.7
- [在线使用](https://mikoto-img.vercel.app/)

使用 Teal 编程语言开发的图片反审查库，用了某个像素打乱算法。顺带用 Teal to Lua 然后 Lua in JS 以及 TS to JS 的方式写了基于 Bun 的 CLI 版封装和基于 Vite 的网页样式。性能很差，主要是对接半天的过程很有趣，Teal 语言也很不错，感觉像 Lua 的 TypeScript。作为体验 Teal 语言的项目。

#### [KanaRhythm](https://github.com/biyuehu/kana-rhythm)

- 介绍视频：[基于MoonBit语言的日语假名练习游戏](https://www.bilibili.com/video/BV17ZtuzkEVN)
- 时间：2025.8

一个基于 MoonBit 语言开发的用语日语假名练习的网页音乐小游戏。作为体验 MoonBit 语言的项目，顺带开发途中尝试了那时刚出的 Zed 编辑器。

#### [TunCLI](https://github.com/biyuehu/TuneCLI)

- 介绍视频：[基于Swift的纯终端渲染开源音乐播放器](https://www.bilibili.com/video/BV1HWbGz4EuV)
- 时间：2025.8

基于 Swift 语言开发的终端 UI 音乐播放器应用。其中用到了某个忘了名字的 C 库作为 Windows 上播放、处理音频的对接。Swift 语言设计令人感到喜悦，在 Windows 也还算能用，其次则是了解了一些 TUI 的基本知识。作为体验 Swift 语言的项目。

#### [NeteaseLyricFetcher](https://github.com/biyuehu/NeteaseLyricFetcher)

- 介绍视频：[基于C语言实现的网易云多种歌词获取工具](https://www.bilibili.com/video/BV1NPt3ztE4v)
- 时间：2025.7

基于 C 语言和 WinForm 开发的网易云音乐多语言歌词获取工具（中文、译文、罗马音）。作为第一个 C 项目的尝试（尽管在一年后通过 OI 再次接触到 C 时还是感到新鲜），然后是熟悉了一下 WinForm 的基本使用。

#### [mcwss](https://github.com/biyuehu/mcwss)

- 时间：2021、2024
- 技术栈：TypeScript、pnpm、Node.JS、WebSocket、ESLint、Prettier

一个简单的 Minecraft Bedrock 的 WebSocket 服务器 API 封装库。V1 是个人最早的 Node.JS 项目（2021），使用 JavaScript 编写且很糟糕不堪，2024 年决定作为与过去的 MC 开发经历的告别，便用 TypeScript 重构成为一个正儿八经的 npm package。

#### [ResPlayer](https://github.com/biyuehu/resplayer)

- 时间：2026.8

基于 ResScript 语言开发的网页嵌入式音乐播放器，可传统嵌入、可作为 npm package。Vibe 为主。现用于 RomiNest 中。

#### [MathForge](https://github.com/biyuehu/mathforge)

- 时间：2026.8

一个基于本地题库的高考数学刷题桌面应用，用 WPF (.NET) 构建，内置 LaTeX 公式渲染。问就是想用用 C# 并且刚好在某处看到某人弄的题库数据，所以就做了，顺带送给朋友。Vibe 为主。
