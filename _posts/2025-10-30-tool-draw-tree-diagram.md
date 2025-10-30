---
layout: post
title: 'tool: draw tree diagram'
categories:
- tools
tags:
- tools
date: 2025-10-30 22:36 +0800
---
## Brief

This post will introduce the tool "draw-tree-diagram.sh" that make you generate tree diagram given paths.

[github repo](https://github.com/TUNGHUAYU/draw_tree_diagram)

## Usage

> usage

``` sh
# clone repository
$ git clone https://github.com/TUNGHUAYU/draw_tree_diagram.git
$ cd draw_tree_diagram/

# draw tree diagram
bash draw_tree.sh paths.txt 
📁 Directory Tree:
├── A/
│   ├── B/
│   │   └── C/
│   │       └── D
│   └── B1/
│       ├── C1
│       └── C2
└── C
```

> paths.txt

``` tex 
A/
A/B/C/D
A/B1/C1
A/B1/C2
C
```