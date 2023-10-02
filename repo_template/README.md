# Placeholder

[![GitHub all releases](https://img.shields.io/github/downloads/InsultingPros/placeholder/total)](https://github.com/InsultingPros/placeholder/releases)

Bla bla, general info.

<details>
  <summary>Don't touch this!</summary>

  Spoiler text. Note that it's important to have a space after the summary tag. You should be able to write any markdown you want inside the `<details>` tag... just make sure you close `<details>` afterward.

  ![img](docs/media/example.png)

  ```unrealscript
  log("I'm a pepe!");
  ```

</details>

## Installation

> **Note** maybe some notes?

```ini
Mutator=placeholder.placeholder
```

## Building

Use [KF Compile Tool](https://github.com/InsultingPros/KFCompileTool) for easy compilation.

```ini
add dependencies!
EditPackages=placeholder
```

## Steam workshop

link to workshop?

## Reminder about releases (delete me!)

### Directory style (delete me!)

```text
📦 MyModPackageName.zip
├── 📁 System
│   ├── 📄 *.u
│   ├── 📄 *.ucl
│   ├── 📄 *.int
│   └── ⚙️ *.ini
├── 📁 Animations
│   └── 📄 *.ukx
├── 📁 Sounds
│   └── 📄 *.uax
├── 📁 StaticMeshes
│   └── 📄 *.usx
├── 📁 Textures
│   └── 📄 *.utx
└── 📁 Redirect
    └── 📄 *.uz2
```

### How to archive (delete me!)

Preferable option is [7zip](https://www.7-zip.org/) with following settings:

|Variable           |Value    |
|---                |---      |
|Archive format     |zip      |
|Compression level  |Ultra    |
|Compression method |Deflate  |
|Dictionary size    |32 KB    |
|Word size          |258      |

This allow archives to be opened in windows explorer. I could go for `*.rar` or `*.7z` instead, but size savings are not that significant, and end users must have 3rd party apps to open them.
