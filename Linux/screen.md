# Linux Screen Command Documentation

## Table of Contents

- [Linux Screen Command Documentation](#linux-screen-command-documentation)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Basic Usage](#basic-usage)
    - [Launch a New Screen Session](#launch-a-new-screen-session)
    - [Detach From a Screen Session](#detach-from-a-screen-session)
    - [List All Active Screen Sessions](#list-all-active-screen-sessions)
    - [Reattach to a Detached Screen Session](#reattach-to-a-detached-screen-session)
  - [Window Management](#window-management)
    - [Create a New Terminal Window](#create-a-new-terminal-window)
    - [Switch Between Windows](#switch-between-windows)
    - [View and Select From a List of All Active Windows](#view-and-select-from-a-list-of-all-active-windows)
    - [Rename a Window](#rename-a-window)
  - [Advanced Features](#advanced-features)
    - [Send Commands to a Detached Session](#send-commands-to-a-detached-session)
  - [Important Notes](#important-notes)

## Introduction

`screen` command in Linux provides the ability to launch and use multiple shell sessions from a single ssh session. When a process is started with ‘screen’, the process can be detached from session & then can reattach the session at a later time. When the session is detached, the process that was originally started from the screen is still running and managed by the screen itself. The process can then re-attach the session at a later time, and the terminals are still there, the way it was left. It's particularly useful for remote system administration, running long processes, and multitasking in the terminal.

## Basic Usage

### Launch a New Screen Session

To start a new screen session:

```
screen
```

To start a session with a custom name:

```
screen -S session_name
```

Example:
```
screen -S session1
```

### Detach From a Screen Session

To detach from a screen session and return to the original terminal:

```
Ctrl-a + d
```

The detached session keeps its processes running in the background.

### List All Active Screen Sessions

To list all active sessions:

```
screen -ls
```

This command shows all running Screen sessions, their detachment statuses, names, and process IDs.

### Reattach to a Detached Screen Session

To reattach to a running Screen session:

```
screen -r ID-name
```

Replace `ID-name` with the actual Screen session ID or name.

Examples:
```
screen -r 1268
screen -r session1
```

## Window Management

### Create a New Terminal Window

To create a new window within a screen session:

```
Ctrl-a + c
```

### Switch Between Windows

Use these shortcuts to switch between windows:

- `Ctrl-a + n`: Cycle to the next window
- `Ctrl-a + p`: Move to the previous window
- `Ctrl-a + [0-9]`: Switch to a specific window by number (0-9)
- `Ctrl-a + Ctrl-a`: Toggle between the current and previous windows

### View and Select From a List of All Active Windows

To see a list of all windows in the current session:

```
Ctrl-a + "
```

Use arrow keys to navigate and Enter to select.

To switch to a window by name:

```
Ctrl-a + '
```

Then enter the window name.

### Rename a Window

To rename a window:

1. Navigate to the desired window
2. Press `Ctrl-a + :` to enter command mode
3. Type: `title "New Window Name"`

## Advanced Features

### Send Commands to a Detached Session

To run a command in a detached session without reattaching:

```
screen -S session-name-or-id -X -p 0 command
```

Replace `0` with the window number if needed.

Example:
```
screen -S hostinger -X -p 0 echo "Test message"
```

## Important Notes

- To use Screen shortcuts, release `Ctrl + a` before pressing the next key.
- Commands are case-sensitive.
- To quit Screen, use the `exit` command in the last remaining window.