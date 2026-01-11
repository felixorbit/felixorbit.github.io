---
title: "文本处理工作流 Text Flow"
date: 2026-01-11
lastmod: 2026-01-11
draft: false
project_tags: ["工具"]
status: "growing"
summary: "集成常见文本处理工具的工作流"
links:
    external_link:
        text: "体验地址"
        icon: "fas fa-external-link-alt"
        href: "https://felixorbit.github.io/text-flow"
        weight: 1
    another_link:
        text: "项目地址"
        icon: "fab alt brands fa-github"
        href: "https://github.com/felixorbit/text-flow"
        weight: 2
---

## Text Flow

Text Flow 是一个流式文本处理工具。用户可以使用 Text Flow 提供的丰富的文本处理模块灵活构建自己所需的文本处理工作流，完成复杂的文本处理任务。

文本是信息的重要载体，我们日常工作生活需要频繁地和文本打交道。文本自身有着丰富的形式，如特定格式，特定编码等等，很多时候我们需要将文本在不同形式之间转换。我使用过很多非常好用的文本处理工具，但他们往往只完成单一任务，当我需要完成多步处理时，通常的做法是在一个工具里处理完成，然后复制粘贴到另一个工具里，这过程可能需要跨越多个网页，非常繁琐。因此我想拥有一个类似“管道”的流式处理工具，在定义好整个流程之后，他会自己完成所有工作，给我最终结果。

Text Flow 首先预置了一系列常见的文本处理模块，如哈希，编码/解码，加密/解密，转义/去转义，json格式化/压缩，正则匹配等，每个模块独立，可以接受单个/多个输入或者输出单个/多个结果，通过一个友好的界面，用户可以创建包含多个节点的顺序或并行的工作流，每个节点包含一个处理模块，最后得到一个较复杂的文本处理器。

本项目是我使用 [Gemini CLI](https://geminicli.com/) 完成的，我所做的只是提出自己的想法和反馈意见，完全由它进行实现和更改。从试用来看，我觉得它完成的非常不错，整个过程中的体验也非常好，相比于前一个项目（Config UI）的开发过程有非常大的进步，我觉得有很大一部分得益于 Gemini 3 Pro 模型的能力提升。因此，我对 AI 将来可以达到的高度依然保持乐观。

