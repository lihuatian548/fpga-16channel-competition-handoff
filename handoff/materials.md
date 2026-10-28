# 接手材料清单

## GitHub文档包建议内容

| 仓库相对位置 | 文件用途 | 是否本次上传 |
| --- | --- | --- |
| README.md | 指向本轮参赛稿和交接入口，记录版本与提交 | 是 |
| docs/competition-report.docx | 本轮最终Word，真实多级标题与导航，完成全页排版检查 | 是，根任务最终绑定 |
| docs/competition-report.md | 与Word正文同步的可读文本 | 可随文稿一起上传 |
| handoff/README.md | 已确认选择、架构、版本、验证组和接手顺序 | 是 |
| handoff/technical-status.md | 累计工程核验记录，独立于参赛正文 | 是 |
| handoff/project-facts.json | 60事实/35指标/14历史/34差异/12待确认/61来源/22映射的脱敏副本 | 是 |
| handoff/artifact-index.json | 六候选hash、源证据hash、前轮交付身份和本轮最终绑定 | 是 |
| handoff/source-map.example.json | 无真实个人绝对目录的定位占位 | 是 |
| handoff/file-manifest.json | 本轮实际上传文件的仓库路径、大小、SHA256 | 是，根任务最终生成 |
| handoff/materials.md | 本文件，说明上传范围和本地资料入口 | 是 |

不要为了“交接完整”自动上传完整Vivado/PCB工程、厂商IP/BSP/SDK、运行库、PC发布程序、旧ZIP、临时PDF/PNG、缓存、凭据或个人目录索引。本次用户授权范围是文档和交接资料；工程大文件以来源和hash索引保留，后续按明确需要再传。

## 本地继续工程工作时需要的既有资料

| 占位符/入口 | 材料 | 解决的问题 |
| --- | --- | --- |
| PROJECT_ROOT | 用户原输出和16通道研制报告根目录 | 取原报告、历轮交付和本地原始数据，不需要再次索要已给文件 |
| COMPETITION_TEMPLATE | 原赛事模板 | 保持章节、图片、限字和匿名要求 |
| VIVADO_PROJECT | 用户指定6237_Xilinx工程，含6236A standalone | 复核实际源和既有工程，原工程不覆盖 |
| PCB_PROJECT | 指定16通道PCB目录，采用PRJ/PRJ ACQ版 | 原理图/PCB/BOM和网络来源 |
| PC_YE7600 / PC_CONFIG / PC_BACKUP | 主PC、配置工具与备用程序目录 | 绑定实际可执行文件身份/配置和同次保存 |
| WORKSPACE/work/round8 | 最终R2候选、原基线、各类测试、route报告与发布记录 | 取完整工程和新bit/HDF/ELF/BOOT的可复算来源 |
| WORKSPACE/work/round9 | 抓包/保存/同次记录工具及原始自测记录 | 形成下一次真实试验的可追溯文件链 |
| R8离线候选附件 | 上述完整候选/验证归档 | 不在本次文档仓库重复收入 |
| R9离线验收附件 | 六候选、三初始化、Python工具、模板和验证记录 | 原档身份见版本索引；全部SYNTHETIC文件仍是人工夹具 |

完整项目重建需要原厂Vivado/SDK2018.3及相应工程来源，不应把文档仓库误当可直接编译的固件仓库。

## 常用离线入口

以下相对路径以原第9轮验收包解压目录为基准，或在本地WORKSPACE/work/round9使用；它们不表示脚本已经包含在本次GitHub文档包中。工具只需Python标准库，当前本机的运行时路径由本地映射记录，不提交个人运行时绝对目录。

```text
python session_tools/session.py verify-bundle --bundle bundle
python session_tools/session.py new --bundle bundle --parent sessions --id REAL_001
python session_tools/session.py add --session sessions/REAL_001 --role capture --file <实际原始抓包文件>
python session_tools/session.py audit --session sessions/REAL_001
python capture_tools/capture_check.py --input <实际PCAP或PCAPNG> --out <全新输出目录> --input-nature user-provided
python save_compare/compare_saved.py inventory <实际保存CSV>
python save_compare/compare_saved.py compare --manifest <已填写显式映射JSON> --out-dir <全新输出目录>
```

TDMS本轮未直接解析。若PC提供实际导出CSV，须同时保留原TDMS/索引、group/channel、单位、时间定义、导出工具版本及处理步骤；无法真实导出时不制造替代CSV。

## 进入首次上板时最小补充材料

1. 准确核心板型号/硬件版本、DDR芯片/组织及正式引脚表，解决候选高地址和通知映射。
2. X1实装料号/贴装记录或独立时基测量，解决配置条件与真实时钟对应。
3. 本次板号、JTAG线缆/在线目标、实际加载文件hash及完整初始化/运行日志，建立候选到板上身份。
4. 同次完整原始抓包、PC可执行文件和配置hash、所有保存分段、操作起止与时基定义，建立数字链/保存对应。
5. 通道/时间定义明确后再补逐路标定、短接噪声、扫频、同步和冷启动条件/原文件。最终展示照片按用户安排最后补。

## 本轮交付完成时根任务应回填

- 本轮最终Word及同步Markdown的实际仓库路径、大小、SHA256；Word页数、Heading导航检查和全页视觉QA结果。
- 上传前明确的仓库URL和分支；实际提交SHA；实际远端文件列表和字节/hash核对。仓库尚未确认或未实际上传时保留未完成状态。
- 新文档没有代表新固件，不更改R8候选hash或补写板上/性能通过结论。
