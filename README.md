# GoldenDrop GEO 知识库 —— 优化文件包说明

以下是根据审计报告逐条修复后的文件。由于我没有你 GitHub 仓库的直接推送权限,这些是**待提交的替换内容**,请对照文件路径手动复制到仓库对应位置后 commit / push。

---

## 文件清单与对应修改

| 文件 | 对应原网站路径 | 修改内容 |
|---|---|---|
| `knowledge-base/products/water-timer/irrigation-timer-specifications.md` | `/knowledge-base/products/water-timer/irrigation-timer-specifications.html` | 修复损坏的规格表格（原来每行被拆成独立小表格） |
| `knowledge-base/products/water-timer/irrigation-timer-installation-guide.md` | `/knowledge-base/products/water-timer/irrigation-timer-installation-guide.html` | 修复故障排查表格；**删除了发布前遗留的内部质检备注**（"应在发布前与原始说明书核实"）——建议你在提交前用原始说明书核实第6节"Warnings"内容是否完整,确认无误后再上线 |
| `knowledge-base/products/water-timer/index.md` | `/knowledge-base/products/water-timer/index.html` | ① 删除"Battery Life: Up to 12 months"的未核实声明,改为"未官方指定"② 电源说明补充"(不含电池)"③ **顺带发现并修复了一个审计报告中未提到的新冲突**:索引页原写"Working Water Pressure: 0.2–8 bar",与规格页"0.5–8 Bar"不一致,已统一为 0.5–8 bar |
| `knowledge-base/products/wfm-1002/index.md` | `/knowledge-base/products/wfm-1002/index.html` | 防水等级统一为 IPX7,并加入与定时器页面一致的调和说明文字 |
| `knowledge-base/products/wfm-1002/specifications.md` | `/knowledge-base/products/wfm-1002/specifications.html` | 原来"以官方认证文件为准"的模糊表述,补全为明确的 IPX7 数值 |
| `knowledge-base/products/wfm-1002/product-identity.md` | `/knowledge-base/products/wfm-1002/product-identity.html` | **删除了"Dual-channel Bluetooth Wireless Irrigator"（双通道蓝牙无线灌溉器）的悬空引用**（见下方"需要你确认的事项"） |
| `products.md` | `/products.html` | 统一产品命名:WFM-1002 和 定时器均补充完整型号,定时器同时标注"Digital Water Timer (W-Timer1001)"与"Single Channel Irrigation Timer"两个名称对应关系 |
| `sitemap.xml` | `/sitemap.xml`（新文件） | 新增站点地图,包含全部17个页面 |
| `robots.txt` | `/robots.txt`（新文件） | 新增,明确允许所有爬虫（含AI爬虫）抓取全站,并指向 sitemap |
| `schema-snippets/*.html` | 插入各页面 `<head>` | 新增 JSON-LD 结构化数据（Organization / Product ×2 / FAQPage ×2），提升 AI 答案引擎抓取准确率 |

---

## ⚠️ 需要你确认/决定的事项

我不能替你做以下决定，因为需要真实数据或你的产品线信息：

1. **WFM-1002 的真实防水等级**：我在修复文件中统一采用了 **IPX7**（因为原网站的 `certification.html` 给出了明确的测试标准 IEC 60529，比另一处的 IPX6 更具体、更可信）。请务必与制造商核实这是否是正确数值。

2. **"Dual-channel Bluetooth Wireless Irrigator"（双通道蓝牙无线灌溉器）**：我直接删除了这处引用，因为网站上没有任何配套内容支撑它。如果这确实是一款真实存在或即将推出的产品，请提供以下信息，我可以帮你补建完整的产品页面：
   - 型号
   - 核心功能/连接方式
   - 规格参数
   - 是否已有认证/包装信息

3. **定时器电池续航时间**："Up to 12 months" 这个说法我已删除并标注为"未官方指定"。如果你有官方测试数据（例如具体使用场景下的续航月数），可以提供给我，我会用真实数据替换现在的占位说明。

4. **`sitemap.xml` 的另一种方案**：由于网站基于 Jekyll 构建，除了我提供的静态 `sitemap.xml`，你也可以选择在 `_config.yml` 中添加 `jekyll-sitemap` 插件让站点地图自动生成、自动更新（长期更省心，但需要你有权限修改 `_config.yml` 和 `Gemfile`）。

---

## 未处理项（需要更多信息才能推进）

- **价格 / 购买渠道页面**：未创建，需要你提供定价和购买链接。
- **保修/退换货政策页面**：未创建，需要你提供政策文本。
- **产品图片、可下载 PDF 说明书**：网站文字中多次提到"官方产品图片"，但没有实际图片链接，需要你提供素材。
- **文件夹命名统一**（`wfm-1002/specifications.html` vs `water-timer/irrigation-timer-specifications.html` 前缀不一致）：这涉及改变 URL 路径，会影响已被索引/分享的链接，建议单独评估是否值得改动，我这次没有动它。

---

如果你把这些文件替换进仓库后想让我再检查一遍渲染效果，可以把新的 live 链接发给我，我可以重新抓取核实。
