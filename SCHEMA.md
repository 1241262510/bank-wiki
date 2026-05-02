# Wiki Schema

## Domain
银行卡知识库 — 聚焦三大方向：外币银行卡、虚拟卡、国内银行卡。覆盖卡片产品、申请流程、费用、权益、使用策略等。

## Conventions
- File names: lowercase, hyphens, no spaces (e.g., `citic-credit-card.md`)
- Every wiki page starts with YAML frontmatter (see below)
- Use `**wikilinks**` to link between pages (minimum 2 outbound links per page)
- When updating a page, always bump the `updated` date
- Every new page must be added to `index.md` under the correct section
- Every action must be appended to `log.md`

## Frontmatter
```yaml
---
title: Page Title
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: entity | concept | comparison | query | summary
tags: [from taxonomy below]
sources: [raw/articles/source-name.md]
---
```

## 三大分类

### 一、外币银行卡（foreign/）
适合海淘、跨境消费、海外出行的银行卡产品。
- 多币种信用卡（全币种/双币种）
- 外币借记卡（境外取现/消费）
- 跨境支付方案
- 汇率、货币转换费、境外取现手续费对比

### 二、虚拟银行卡（virtual/）
纯数字发卡，无实体卡或虚拟卡号附加在实体卡上。
- 虚拟信用卡（Depay、OneKey Card、Nobe等）
- 虚拟预付卡（WildCard、Fomepay等）
- 银行自带虚拟卡号（招行、中信等）
- 用于海外订阅（ChatGPT、Netflix、AWS等）
- 加密货币充值类虚拟卡

### 三、国内银行卡（domestic/）
国内主流银行卡片产品。
- 信用卡（权益、年费、积分体系）
- 借记卡（账户管理、跨行转账）
- 联名卡（航司、电商、出行）
- 特色权益卡（贵宾厅、加油、超市返现）

## 目录结构
```
bank-wiki/
├── SCHEMA.md
├── index.md
├── log.md
├── foreign/              # 外币银行卡
│   ├── entities/         # 外币卡产品实体
│   ├── concepts/         # 外币卡概念（汇率、货币转换费等）
│   ├── comparisons/      # 外币卡对比
│   └── queries/          # 外币卡查询结果
├── virtual/              # 虚拟银行卡
│   ├── entities/         # 虚拟卡产品实体
│   ├── concepts/         # 虚拟卡概念（加密充值、风控等）
│   ├── comparisons/      # 虚拟卡对比
│   └── queries/          # 虚拟卡查询结果
├── domestic/             # 国内银行卡
│   ├── entities/         # 国内卡产品实体
│   ├── concepts/         # 国内卡概念（积分、提额等）
│   ├── comparisons/      # 国内卡对比
│   └── queries/          # 国内卡查询结果
├── raw/                  # 原始资料
│   ├── articles/
│   ├── papers/
│   ├── transcripts/
│   └── assets/
└── _archive/
```

## Tag Taxonomy

### 分类标签
foreign-card, virtual-card, domestic-card

### 外币卡专属
multi-currency, dual-currency, zero-forex-fee, overseas-withdrawal,
cross-border-payment, currency-conversion, exchange-rate, swift-transfer

### 虚拟卡专属
crypto-funded, prepaid-virtual, subscription-payment, ai-service-payment,
anonymous-card, usdt-funded, usdc-funded, virtual-card-number

### 国内卡专属
credit-card, debit-card, co-branded-card, platinum-card, diamond-card,
infinite-card, business-card

### 银行机构
bank-cmb (招商银行), bank-icbc (工商银行), bank-ccb (建设银行), bank-boc (中国银行),
bank-abc (农业银行), bank-citic (中信银行), bank-spdb (浦发银行), bank-cib (兴业银行),
bank-ceb (光大银行), bank-pab (平安银行), bank-comm (交通银行), bank-gdb (广发银行),
bank-ms (邮储银行), bank-hxb (华夏银行), bank-cmbc (民生银行)

### 虚拟卡平台
platform-depay, platform-onekey, platform-wildcard, platform-fomepay,
platform-nobe, platform-dupay

### 权益/功能
annual-fee, rewards, lounge-access, insurance, cashback, travel-benefits,
dining-benefits, shopping-benefits, medical-benefits

### 策略/知识
application-strategy, credit-score, limit-increase, points-strategy,
card-combination, fee-optimization, risk-management, kyc-verification,
refund-policy, account-freeze

### 元类型
comparison, beginner, advanced, controversy, timeline

Rule: every tag on a page must appear in this taxonomy. If a new tag is needed,
add it here first, then use it.

## Page Thresholds
- **Create a page** when a card/platform/concept appears in 2+ sources OR is central to one source
- **Add to existing page** when a source mentions something already covered
- **DON'T create a page** for passing mentions or minor details
- **Split a page** when it exceeds ~200 lines
- **Archive a page** when content is fully superseded — move to `_archive/`

## Entity Pages
One page per notable entity (card product, bank, virtual card platform). Include:
- Overview / what it is
- Key facts: fees, supported currencies, target use case
- Core benefits breakdown
- Application/registration requirements
- Relationships to other entities (**wikilinks**)
- Source references

## Concept Pages
One page per concept or topic. Include:
- Definition / explanation
- Practical guide
- Tips and pitfalls
- Related concepts (**wikilinks**)

## Comparison Pages
Side-by-side analyses. Include:
- What is being compared and why
- Dimensions of comparison (table format preferred)
- Verdict or recommendation by use case
- Sources

## Update Policy
When new information conflicts with existing content:
1. Check the dates — newer sources generally supersede older ones
2. If genuinely contradictory, note both positions with dates and sources
3. Mark the contradiction in frontmatter: `contradictions: [page-name]`
4. Flag for user review in the lint report
