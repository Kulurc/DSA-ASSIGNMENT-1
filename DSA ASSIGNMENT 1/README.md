# OpenGL + ImGui Boilerplate Setup Guide

This project uses **GLFW**, **GLEW**, and **Dear ImGui** for creating an OpenGL application with a GUI.

## Dependencies Setup

### 1. GLFW (Window Management)

1. Download from: https://www.glfw.org/download.html (Pre-compiled binaries for Windows)
2. Extract and copy:
   - `include/GLFW/` folder → `Dependencies/GLFW/include/GLFW/`
   - `lib-vc2022/glfw3.lib` → `Dependencies/GLFW/lib/glfw3.lib`

### 2. GLEW (OpenGL Extension Wrangler)

1. Download from: https://glew.sourceforge.net/ (Binaries for Windows)
2. Extract and copy:
   - `include/GL/` folder → `Dependencies/GLEW/include/GL/`
   - `lib/Release/x64/glew32s.lib` → `Dependencies/GLEW/lib/glew32s.lib`

> **Note:** We use the static library (`glew32s.lib`) with `GLEW_STATIC` defined.

### 3. Dear ImGui

1. Download from: https://github.com/ocornut/imgui (Releases or clone)
2. Copy these files to `Dependencies/imgui/`:
   - `imgui.cpp`
   - `imgui.h`
   - `imgui_demo.cpp`
   - `imgui_draw.cpp`
   - `imgui_internal.h`
   - `imgui_tables.cpp`
   - `imgui_widgets.cpp`
   - `imconfig.h`
   - `imstb_rectpack.h`
   - `imstb_textedit.h`
   - `imstb_truetype.h`
   - `backends/imgui_impl_glfw.cpp`
   - `backends/imgui_impl_glfw.h`
   - `backends/imgui_impl_opengl3.cpp`
   - `backends/imgui_impl_opengl3.h`
   - `backends/imgui_impl_opengl3_loader.h`

## Visual Studio Project Configuration

### Include Directories

Add to **C/C++ → General → Additional Include Directories**:

```
$(ProjectDir)Dependencies\GLFW\include
$(ProjectDir)Dependencies\GLEW\include
$(ProjectDir)Dependencies\imgui
```

### Library Directories

Add to **Linker → General → Additional Library Directories**:

```
$(ProjectDir)Dependencies\GLFW\lib
$(ProjectDir)Dependencies\GLEW\lib
```

### Libraries

Add to **Linker → Input → Additional Dependencies**:

```
glfw3.lib
glew32s.lib
opengl32.lib
```

### Preprocessor Definitions

Add to **C/C++ → Preprocessor → Preprocessor Definitions**:

```
GLEW_STATIC
```

### Source Files to Add

Add these files to your project:

- `main.cpp`
- `Dependencies/imgui/imgui.cpp`
- `Dependencies/imgui/imgui_demo.cpp`
- `Dependencies/imgui/imgui_draw.cpp`
- `Dependencies/imgui/imgui_tables.cpp`
- `Dependencies/imgui/imgui_widgets.cpp`
- `Dependencies/imgui/imgui_impl_glfw.cpp`
- `Dependencies/imgui/imgui_impl_opengl3.cpp`

## Folder Structure

```
DSA ASSIGNMENT 1/
├── Dependencies/
│   ├── GLFW/
│   │   ├── include/
│   │   │   └── GLFW/
│   │   │       └── glfw3.h
│   │   └── lib/
│   │       └── glfw3.lib
│   ├── GLEW/
│   │   ├── include/
│   │   │   └── GL/
│   │   │       ├── glew.h
│   │   │       ├── wglew.h
│   │   │       └── eglew.h
│   │   └── lib/
│   │       └── glew32s.lib
│   └── imgui/
│       ├── imgui.cpp
│       ├── imgui.h
│       ├── imgui_impl_glfw.cpp
│       ├── imgui_impl_glfw.h
│       ├── imgui_impl_opengl3.cpp
│       ├── imgui_impl_opengl3.h
│       └── ... (other imgui files)
├── main.cpp
└── DSA ASSIGNMENT 1.vcxproj
```

## Build & Run

1. Set configuration to **Debug x64** or **Release x64**
2. Build the solution (Ctrl+Shift+B)
3. Run (F5)

## Controls

- **ESC**: Close the application
- Use ImGui windows to interact with the UI
