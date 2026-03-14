# `claude code`

## 1.登录

```bash
/login

or 

cc-switch
```

## 2.`claude code`的三种模式

`shift+tab `切换模式

* `? for shortcuts` 默认模式
* `accept edits on` 自动模式

* `plan mode` 规划模式

## 3.输入框换行

`ctrl+j` or `ctrl+enter`

## 4.输入框GUI升级

`ctrl+g` 输入框升级为记事本。

## 5.启动危险模式

```bash
claude --dangerously-skip-permissions
```

## 6.回滚

```bash
/rewind
```

or

两次`esc`

不要太依赖，而是选用`git`进行version control。

## 7.进入bash

```bash
!
```

## 8.后台任务

```bash
/tasks
```

## 9.恢复对话，继续对话

```bash
/resume
```

or

```
#恢复上一次的对话
claude -c
```

## 10.使用mcp

```bash
claude mcp add xx

/mcp
```

## 11.上下文管理

```bash
/compact xxxxxxxx

/clear
```

## 12.`CLAUDE.md`

```bash
/init
```

```bash
/memory
```

## 13.`/hooks`

## 14.`/skills`

```bash 
mkdir ./.claude/skills/xxxxxx

code ./.claude/skills/xxxxxx

# 写入SKILL.md

/skills

# 对话框 or

/xxxxxx <concrete_requests>
```

## 15.SubAgent

```bash
/agents
```

## 16.`SubAgent`和`agent skill`的区别

`SubAgent`是线程

`agent-skills`是进程

## 17.`/plugin`

