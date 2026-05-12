# NeverBecomeYourDownstream

> A curated ASN blocklist project for filtering networks that should never appear in your downstream routing path.  
> 一个用于过滤永远不应该出现在你下游的 ASN 列表

---

## Introduction / 项目简介

`NeverBecomeYourDownstream` collects multiple categories of ASNs that are generally considered undesirable as downstreams.

`NeverBecomeYourDownstream` 收集了多个类别的 ASN，这些网络通常不应该出现在你的下游路由中。

---

# Categories / 分类说明

| Category | Description | Data Source |
|----------|-------------|-------------|
| **T1** | Tier1 carriers (fixed 25 ASNs) | `data/t1asn.txt` |
| **GOV** | Government organization ASNs | `tags-gov.csv` |
| **LARGE** | Large-scale networks (Hosts > 10K + Internet Critical Infrastructure) | `tags-a10k.csv` + `tags-icrit.csv` |
| **COMPANY** | Large enterprise/company ASNs | `tags-corp.csv` |
| **DSL** | DSL operator ASNs | `tags-dsl.csv` |
| **ALL** | Combined deduplicated list of all categories | All sources merged |

---

# Output Formats / 输出格式

Each category (including `ALL`) is exported in multiple formats.

每个分类（包括 `ALL` 总表）都会导出为多种格式。

| Directory | Description |
|-----------|-------------|
| `output/bird/` | BIRD router configuration format (`.conf`) |
| `output/txt_name/` | Plain text with ASN names (`.txt`) |
| `output/txt_plain/` | Plain text with ASN numbers only (`.txt`) |
| `output/csv_name/` | CSV format with ASN names (`.csv`) |
| `output/csv_plain/` | CSV format with ASN numbers only (`.csv`) |

---

# Generated Files / 输出文件

Each output directory contains:

每个输出目录中包含：

| File | Description |
|------|-------------|
| `all` | Combined deduplicated ASN list |
| `t1` | Tier1 ASN list |
| `gov` | Government ASN list |
| `large` | Large-scale network ASN list |
| `company` | Large company ASN list |
| `dsl` | DSL operator ASN list |

Example:

```text
output/
├── bird/
│   ├── all.conf
│   ├── t1.conf
│   ├── gov.conf
│   ├── large.conf
│   ├── company.conf
│   └── dsl.conf
├── txt_plain/
├── txt_name/
├── csv_plain/
└── csv_name/
```
---

# Data Source / 数据来源

ASN metadata is primarily derived from the following sources:

ASN 元数据主要来源于以下数据源：

- Original source / 原始来源：
  - bgp.tools

- Mirror database / 镜像数据库：
  - https://github.com/Alice39s/BGP.Tools-OpenDB

To avoid placing unnecessary load on the bgp.tools service, this project uses the mirrored `BGP.Tools-OpenDB` dataset instead of directly querying the original website.

为了避免对bgp.tools造成额外压力，本项目使用镜像数据库 BGP.Tools-OpenDB作为数据来源，而非直接请求原始网站
