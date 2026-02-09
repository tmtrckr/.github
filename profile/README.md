# Time Tracker

## Table of Contents
1. [Organization](#organization)
2. [The Application](#the-application)
3. [Plugin Registry](#plugin-registry)
4. [Plugin Template](#plugin-template)

---

## Organization

The Time Tracker ecosystem is organized into a collection of repositories, each serving a specific purpose.

---

### 📦 Repository Structure

| 🏗️ **Repository Type** | 📋 **Purpose** |
|:----------------------:|:--------------:|
| **Main Application** | Core desktop application |
| **Plugin SDK** | Development toolkit for plugin creators |
| **Plugin Repositories** | Individual plugins (one per repository) |
| **Plugin Registry** | Central hub for plugin discovery |

---

### ✨ Key Benefits

<div align="center">

| | |
|:---:|:---:|
| ✨ **Modularity**<br/>*Each component lives independently* | 🚀 **Flexibility**<br/>*Plugins evolve at their own pace* |
| 🔍 **Discoverability**<br/>*Easy to find and install plugins* | 👥 **Collaboration**<br/>*Community contributions without core changes* |

</div>

---

<div align="center">

> 💡 **Note:** For detailed repository structure, naming conventions, and development guidelines, see the README files in each repository.

</div>

### Project Structure

The Time Tracker application follows a modular architecture with clear separation between frontend, backend, and plugin systems:

```
time-tracker-app/
├── backend/                   # Rust backend (Tauri)
│   ├── src/
│   │   ├── main.rs           # Application entry point
│   │   ├── database.rs       # SQLite database operations
│   │   ├── tracker.rs        # Core tracking logic
│   │   ├── commands.rs       # IPC commands for frontend
│   │   └── plugin_system/    # Plugin infrastructure
│   │       ├── registry.rs   # Plugin registry
│   │       ├── api.rs        # Plugin API interface
│   │       ├── extensions.rs # Extension system
│   │       ├── loader.rs     # Dynamic plugin loading
│   │       └── discovery.rs  # Plugin discovery
│   └── Cargo.toml
│
├── frontend/                  # React frontend
│   ├── components/           # UI components
│   ├── hooks/                # React hooks
│   ├── services/             # Tauri IPC calls
│   ├── store/                # Zustand state management
│   └── types/                # TypeScript types
│
├── plugin-sdk/               # Plugin SDK crate
│   ├── src/
│   │   ├── plugin.rs         # Plugin trait definition
│   │   ├── api.rs            # Plugin API interface
│   │   ├── extensions.rs     # Extension types
│   │   └── ffi.rs            # FFI bindings for dynamic loading
│   └── Cargo.toml
│
└── README.md
```

### Key Architectural Principles

1. **Separation of Concerns**: Clear boundaries between frontend (React/TypeScript), backend (Rust/Tauri), and plugins (Rust dynamic libraries)

2. **Plugin System**: Extensible architecture allowing plugins to:
   - Extend database schema
   - Add new data models
   - Register custom commands
   - Provide UI components
   - Hook into data processing

3. **Type Safety**: Strong typing throughout with Rust on the backend and TypeScript on the frontend

4. **IPC Communication**: Frontend communicates with backend via Tauri IPC commands

5. **Dynamic Loading**: Plugins are loaded as dynamic libraries at runtime

---

## The Application

Time Tracker is a powerful desktop application that automatically tracks your time and provides deep insights into how you spend your workday. Built with performance and privacy in mind, it runs seamlessly in the background while you work.

---

### 🎯 Core Features

#### ⚡ Automatic Time Tracking
Never manually log your time again. Time Tracker monitors your active applications and windows automatically, giving you a complete picture of where your time goes—without any effort on your part.

#### 🧠 Smart Idle Detection
When you step away, Time Tracker intelligently detects idle time and prompts you to classify it. No more guessing whether you were working or taking a break.

#### ✍️ Quick Manual Entry
Forgot to track a meeting or call? Add time entries instantly from the system tray. Perfect for offline meetings, thinking sessions, breaks, or any activity that needs manual logging.

#### 🏷️ Intelligent Categorization
Automatically categorize your activities with customizable rules. Set patterns for apps, websites, or window titles, and watch your time organize itself.

#### 📊 Powerful Reports & Analytics
Get insights with beautiful charts and breakdowns. View your time by day, week, or month. See which apps you use most, track productivity trends, and identify time-wasting patterns.

#### 💾 Export Your Data
Export your time data as CSV or JSON for external analysis, invoicing, or reporting. CSV exports include UTF-8 BOM for perfect Excel compatibility.

---

### 💼 Professional Features

#### 📁 Project & Task Management
Organize your work with projects and tasks. Assign time entries to specific projects, track progress, and see exactly where your effort goes.

#### 💰 Billable Time Tracking
Mark projects and categories as billable, set hourly rates, and automatically calculate revenue. Perfect for freelancers and consultants who need accurate billing.

#### 🌐 Website & Domain Tracking
See which websites you visit most. Time Tracker automatically extracts domains from browser activity, helping you understand your browsing habits and stay focused.

#### 🍅 Pomodoro Timer
Boost productivity with built-in Pomodoro timer. Track focus sessions, take breaks, and integrate with your projects and tasks.

#### 🎯 Goal Setting & Alerts
Set daily, weekly, or monthly time goals. Get alerts at 80% progress and celebrate when you hit 100%. Stay motivated and on track.

---

### 🎨 User Experience

#### ⌨️ Keyboard Shortcuts
Navigate quickly with keyboard shortcuts. Jump to Dashboard (`Ctrl+1`), Reports (`Ctrl+3`), or create a manual entry (`Ctrl+N`) in seconds.

#### 🔔 System Tray Integration
Minimize to tray and access everything you need with a right-click. Pause tracking, create entries, or navigate to any view—all without opening the main window.

#### 🚀 Autostart
Start tracking automatically when your computer boots. Never forget to start tracking again.

#### 🎯 Thinking Mode
Track focused thinking and planning time separately with one click. Perfect for deep work sessions that don't involve active application use.

---

### ✨ Key Benefits

| Problem | Solution |
|:-------:|:--------:|
| Don't know where time goes | Automatic tracking of active applications |
| "No mouse = slacking" | Smart idle detection + manual classification |
| Offline meetings not tracked | Quick entry from tray |
| Thinking ≠ work | Dedicated thinking mode |
| Need to bill clients | Billable time tracking with revenue calculations |
| Want to improve focus | Pomodoro timer with goal tracking |

---

### 🔒 Privacy & Performance

- **100% Local**: All data stays on your computer. No cloud sync, no external servers.
- **Lightweight**: Uses less than 50MB RAM and minimal CPU resources.
- **Fast**: Native OS APIs make tracking 10-100x faster than alternatives.
- **Private**: Your activity data never leaves your device.

---

## Plugin Registry

The Plugin Registry is the central hub for discovering and managing Time Tracker plugins. It provides a curated marketplace where users can browse, install, and update plugins that extend the application's functionality.

### Key Features

- **Centralized Discovery**: Browse all available plugins in one place
- **Easy Installation**: One-click install from the marketplace
- **Version Management**: Automatic updates and compatibility checking
- **Plugin Verification**: Verified plugins marked for trust and quality

### Available Plugins

The registry includes a growing collection of plugins:

| Plugin | Description | Repository |
|:------:|:-----------:|:----------:|
| **Projects & Tasks** | Project and task management with activity linking | [plugin-projects-tasks](https://github.com/tmtrckr/plugin-projects-tasks) |
| **Billing** | Billable time tracking with hourly rates and revenue calculations | [plugin-billing](https://github.com/tmtrckr/plugin-billing) |
| **Pomodoro** | Focus session tracking with Pomodoro timer | [plugin-pomodoro](https://github.com/tmtrckr/plugin-pomodoro) |
| **Goals** | Time goals with progress tracking and alerts | [plugin-goals](https://github.com/tmtrckr/plugin-goals) |

### Registry Repository

For plugin developers and contributors:

- **Registry Repository**: [plugins-registry](https://github.com/tmtrckr/plugins-registry)
  - Submit your plugin to the registry
- **Plugin Template**: [plugin-template](https://github.com/tmtrckr/plugin-template)
  - Start building your own plugin

> 💡 **For Developers**: See the [plugins-registry repository](https://github.com/tmtrckr/plugins-registry) for detailed information about adding plugins, registry structure, and contribution guidelines.

---

## Plugin Template

The Plugin Template provides everything you need to create your own Time Tracker plugin. It includes a complete starter project with Rust backend, React frontend, build system, and comprehensive documentation.

### What's Included

- **Rust Backend**: Complete plugin structure with SDK integration
- **React Frontend**: UI component templates
- **Build System**: GitHub Actions for cross-platform builds
- **Plugin Manifest**: Configuration file for plugin metadata
- **Documentation**: Step-by-step guides and examples

### Quick Start

1. **Use the Template**: Click "Use this template" on GitHub or clone the [plugin-template repository](https://github.com/tmtrckr/plugin-template)

2. **Configure Your Plugin**: Edit `plugin.toml` with your plugin information

3. **Implement Your Logic**: Add your plugin functionality using the provided structure

4. **Build & Release**: Use the included GitHub Actions workflow for automated builds

### Plugin Capabilities

Plugins can extend Time Tracker with:

- **Database Extensions**: Add custom tables and columns
- **Data Models**: Extend core entities with new fields
- **Custom Commands**: Add new functionality accessible via API
- **UI Components**: Create custom React components for the interface
- **Data Hooks**: Process and transform data during operations

### Example Plugins

See real-world implementations:

- **[Projects & Tasks Plugin](https://github.com/tmtrckr/plugin-projects-tasks)**: Project management with activity linking
- **[Billing Plugin](https://github.com/tmtrckr/plugin-billing)**: Billable time tracking and revenue calculations
- **[Pomodoro Plugin](https://github.com/tmtrckr/plugin-pomodoro)**: Focus session tracking with timer
- **[Goals Plugin](https://github.com/tmtrckr/plugin-goals)**: Time goals with progress tracking

### Resources

- **Plugin Template**: [plugin-template](https://github.com/tmtrckr/plugin-template) - Complete starter project
- **Plugin SDK**: Included in the main [time-tracker-app](https://github.com/tmtrckr/time-tracker-app) repository
- **Registry**: Submit your plugin to [plugins-registry](https://github.com/tmtrckr/plugins-registry)

> 💡 **Ready to Build?** Visit the [plugin-template repository](https://github.com/tmtrckr/plugin-template) for detailed documentation, code examples, and step-by-step guides.

---

## Summary

Time Tracker is built on a modular, extensible architecture that enables:

- **Core Application**: Powerful time tracking with automatic monitoring and professional features
- **Plugin System**: Extensible architecture for adding new functionality
- **Plugin Registry**: Centralized marketplace for discovering and installing plugins
- **Plugin Template**: Complete starter kit for building custom plugins

### Key Repositories

| Repository | Purpose | Link |
|:----------:|:-------:|:----:|
| **Main Application** | Core Time Tracker desktop app | [time-tracker-app](https://github.com/tmtrckr/time-tracker-app) |
| **Plugin Template** | Starter template for plugin development | [plugin-template](https://github.com/tmtrckr/plugin-template) |
| **Plugin Registry** | Central registry for plugin discovery | [plugins-registry](https://github.com/tmtrckr/plugins-registry) |

### Available Plugins

- [Projects & Tasks](https://github.com/tmtrckr/plugin-projects-tasks) - Project management
- [Billing](https://github.com/tmtrckr/plugin-billing) - Billable time tracking
- [Pomodoro](https://github.com/tmtrckr/plugin-pomodoro) - Focus session timer
- [Goals](https://github.com/tmtrckr/plugin-goals) - Time goal tracking

---

> 💡 **Want to contribute?** Check out the [plugin-template](https://github.com/tmtrckr/plugin-template) to start building your own plugin, or browse the [plugins-registry](https://github.com/tmtrckr/plugins-registry) to see what's available.
