# Rule Center 业务梳理文档

## 📋 概述

Rule Center（规则中心）是 WMS 系统的核心配置模块，负责管理仓库运营中的各种业务规则和配置。该模块包含两个技术栈的实现：
- **Vue 2.x** (`src/views/rule-center/`) - 传统业务模块
- **React** (`src/react-app/pages/rule-center/`) - 新业务模块

---

## 🗂️ 业务模块分类

### 一、拣货相关规则 (Picking Rules)

#### 1.1 拣货规则 (Picking Rule)
- **路径**: `src/views/rule-center/picking-rule/`
- **功能**: 
  - 拣货规则配置（单拣/多拣、多容器、高价值、大件等）
  - 拣货技能配置
  - 拣货区域颜色配置
  - 多拣货员配置
- **主要组件**:
  - `components/picking-rule/` - 拣货规则主配置
  - `components/picking-skills/` - 拣货技能配置
  - `components/multi-picker/` - 多拣货员配置
  - `zone-color-config/` - 区域颜色配置

#### 1.2 流式拣货设置 (Flow Pick Setting)
- **路径**: `src/react-app/pages/rule-center/flow-pick-setting/`
- **功能**:
  - 流式拣货规则配置
  - 生产周期设置
  - 店铺选择配置
  - 阈值配置
  - 订单保留配置
- **主要组件**:
  - `edit/` - 编辑页面
  - `components/holding-order/` - 订单保留
  - `components/view-log-modal/` - 日志查看

#### 1.3 MTO 拣货规则 (MTO Picking Rule)
- **路径**: `src/react-app/pages/rule-center/picking-rule/mto-picking-rule/`
- **功能**: MTO（Make-to-Order）订单拣货规则配置

#### 1.4 拣货调度 (Picking Dispatch)
- **路径**: `src/react-app/pages/rule-center/picking-dispatch/`
- **功能**: 拣货任务分配和调度规则

---

### 二、上架相关规则 (Putaway Rules)

#### 2.1 上架规则 (Putaway Rule)
- **路径**: `src/views/rule-center/putaway-rule/`
- **功能**:
  - 上架位置限制规则
  - 上架位置建议规则
  - 入库上架规则
  - 货架转移上架规则
  - SKU-位置配对配置
- **版本**: v2, v3, v4 (多个版本并存)
- **主要组件**:
  - `components/location.vue` - 位置限制和建议
  - `components/inbound-rack-transfer.vue` - 入库和货架转移
  - `sku-location-pairing-config/` - SKU位置配对

#### 2.2 上架任务分配规则 (Putaway Task Assignment Rule)
- **路径**: `src/views/rule-center/putaway-task-assignment-rule/`
- **功能**:
  - 高优先级任务规则
  - 盘点任务分配规则
  - 货架转移任务分配规则

---

### 三、质检规则 (QC Rules)

#### 3.1 质检规则配置 (QC Rule Config)
- **路径**: `src/views/rule-center/qc-rule/`
- **功能**:
  - 质检规则配置
  - 质检清单配置
  - 退货入库规则配置
  - 供应商设置
  - 质检检查列表
- **主要组件**:
  - `qc-rule-config.vue` - 质检规则主配置
  - `qc-checklist-config.vue` - 质检清单配置
  - `return-inbound-rule-config.vue` - 退货入库规则
  - `components/` - 质检相关组件

---

### 四、发货规则 (Shipping Rules)

#### 4.1 发货规则 (Shipping Rule)
- **路径**: `src/views/rule-center/shipping-rule/`
- **功能**:
  - 分组发货规则 (Group Shipping)
  - One AWB 规则
  - Bypass TWS 规则
- **主要组件**:
  - `group-shipping.vue` - 分组发货
  - `hybrid.ts` - 混合规则处理

---

### 五、波次规则 (Wave Rules)

#### 5.1 波次规则 (Wave Rule)
- **路径**: `src/views/rule-center/wave-rule/` 和 `src/react-app/pages/rule-center/wave-rule/`
- **功能**:
  - 波次规则配置
  - 波次规则组配置
  - 自定义波次规则
  - 自动波次规则
  - 分组规则配置
- **主要组件** (Vue):
  - `components/wave-rule/` - 波次规则
  - `components/wave-group/` - 波次规则组
  - `components/custom-wave/` - 自定义波次
  - `components/grouping-rule/` - 分组规则
- **主要组件** (React):
  - `auto-wave-rule/` - 自动波次规则
  - `store-group-template/` - 店铺组模板

---

### 六、补货规则 (Replenishment Rules)

#### 6.1 补货规则 (Replenishment Rules)
- **路径**: `src/views/rule-center/replenishment-rules/`
- **功能**:
  - 每日销售配置 (Daily Sales Config)
  - SKU 配置 (SKU Config)
  - 转移类型配置 (Transfer Type)
- **主要组件**:
  - `components/dialy-sales-config/` - 每日销售配置
  - `components/sku-config/` - SKU配置
  - `components/transfer-type/` - 转移类型

#### 6.2 补货反向规则 (Replenishment Reverse)
- **路径**: `src/react-app/pages/rule-center/replenish-reverse/`
- **功能**: 补货反向规则配置

---

### 七、包装规则 (Packaging Rules)

#### 7.1 包装规则 (Packaging Rule)
- **路径**: `src/views/rule-center/packaging-rule/` 和 `src/react-app/pages/rule-center/packaging-rule/`
- **功能**:
  - 3PL 包装规则
  - 收集包装规则
  - FBS 包装服务规则
  - 包装推荐规则
- **主要组件**:
  - `thirdpl-packaging-rule.vue` - 3PL包装规则
  - `collect-packaging-rule.vue` - 收集包装规则
  - `fbs-packaging-service-rule.vue` - FBS包装服务规则
  - `packaging-recommendation-rule/` (React) - 包装推荐规则

#### 7.2 装箱规则 (Boxing Rule)
- **路径**: `src/react-app/pages/rule-center/boxing-rule/`
- **功能**:
  - 入库装箱规则
  - 补货反向装箱规则
  - MTO 拣货装箱规则

---

### 八、技能配置规则 (Skill Config Rules)

#### 8.1 技能配置规则 (Skill Config Rule)
- **路径**: `src/views/rule-center/skill-config-rule/` 和 `src/react-app/pages/rule-center/operator-skill/`
- **功能**:
  - 销售出库技能配置
  - 移库转移技能配置
  - 入库技能配置
  - 货架转移技能配置
  - 补货退货技能配置
  - 盘点技能配置
- **主要组件** (Vue):
  - `components/picking-rule/` - 拣货规则技能
  - `components/picking-skills/` - 拣货技能
  - `components/sorting-rule/` - 分拣规则
  - `components/multi-picker/` - 多拣货员
- **主要组件** (React):
  - `operator-skill/sales-outbound/` - 销售出库技能
  - `operator-skill/inbound/` - 入库技能
  - `operator-skill/move-transfer/` - 移库转移技能
  - `operator-skill/rack-transfer/` - 货架转移技能
  - `operator-skill/replenishment-return/` - 补货退货技能
  - `operator-skill/cycle-count/` - 盘点技能

---

### 九、分配规则 (Allocate Rules)

#### 9.1 分配规则 (Allocate Rule)
- **路径**: `src/views/rule-center/allocate-rule/`
- **功能**:
  - 销售出库分配规则
  - MT 出库分配规则
  - RTS 出库分配规则
  - 补货分配规则
  - 补货拣货分配规则
- **主要组件**:
  - `components/sales-outbound/` - 销售出库分配
  - `components/mt-outbound/` - MT出库分配
  - `components/rts-outbound/` - RTS出库分配
  - `components/replenishment-rule/` - 补货分配
  - `components/replenishment-picking-rule/` - 补货拣货分配

---

### 十、配额配置 (Quota Config)

#### 10.1 配额配置 (Quota Config)
- **路径**: `src/views/rule-center/quota-config/`
- **功能**:
  - ASN 配额列表 (ASN Quota List)
  - RTS 配额配置 (RTS Quota Config)
  - 批量编辑配额
- **主要组件**:
  - `asn-quota-list.vue` - ASN配额列表
  - `rts-quota-list.vue` - RTS配额列表
  - `rts-quota-config.vue` - RTS配额配置
  - `components/rts-edit.vue` - RTS编辑
  - `components/asn-mass-edit.vue` - ASN批量编辑

---

### 十一、规则组 (Rule Group)

#### 11.1 规则组 (Rule Group)
- **路径**: `src/views/rule-center/rule-group/`
- **功能**:
  - 规则组管理
  - UID 规则配置
  - 批量规则配置
- **主要组件**:
  - `rule-group.vue` - 规则组主页面
  - `rule-group-detail.vue` - 规则组详情
  - `uid-rule.vue` - UID规则
  - `batch-rule.vue` - 批量规则
  - `components/uid-rule-dialog.vue` - UID规则对话框

---

### 十二、其他业务模块

#### 12.1 SKU 标签 (SKU Tag)
- **路径**: `src/views/rule-center/sku-tag/` 和 `src/react-app/pages/rule-center/sku-tag/`
- **功能**: SKU 标签类型配置和管理

#### 12.2 尺寸类型 (Size Type)
- **路径**: `src/views/rule-center/size-type/` 和 `src/react-app/pages/rule-center/size-type/`
- **功能**:
  - SKU 尺寸配置
  - SKU 重量配置
  - 货位尺寸配置
  - 任务尺寸配置

#### 12.3 查询显示 (Query Display)
- **路径**: `src/views/rule-center/query-display/`
- **功能**: 查询显示规则配置

#### 12.4 报告访问 (Report Access)
- **路径**: `src/views/rule-center/report-access/`
- **功能**: 报告访问权限配置和日志查看

#### 12.5 班次配置 (Shift Config)
- **路径**: `src/views/rule-center/shift-config/`
- **功能**: 班次规则配置

#### 12.6 高价值配置 (High Value)
- **路径**: `src/views/rule-center/high-value/`
- **功能**: 高价值商品规则配置

#### 12.7 IBT 处理 (IBT Handling)
- **路径**: `src/views/rule-center/ibt-handling/`
- **功能**: IBT（Inter-Branch Transfer）处理规则

#### 12.8 库存路由 (Inventory Route)
- **路径**: `src/views/rule-center/inventory-route/`
- **功能**:
  - 入库路由
  - 补货路由
  - 反向路由

#### 12.9 生命周期规则 (Lifecycle Rule)
- **路径**: `src/views/rule-center/lifecycle-rule/`
- **功能**: 商品生命周期规则配置

#### 12.10 个人目标设置 (Individual Target Setting)
- **路径**: `src/views/rule-center/individual-target-setting/`
- **功能**: 个人目标设置和配置

#### 12.11 销售出库订单配置 (Sales Outbound Order Config)
- **路径**: `src/react-app/pages/rule-center/sales-outbound-order-config/`
- **功能**:
  - 生产周期配置
  - 紧急标识配置
  - 订单保留配置

#### 12.12 生产力评分规则 (Productivity Scoring Rule)
- **路径**: `src/react-app/pages/rule-center/productivity-scoring-rule/`
- **功能**: 生产力评分规则配置

#### 12.13 履约链配置 (Fulfillment Chain Config)
- **路径**: `src/react-app/pages/rule-center/fullfillment-chain-config/`
- **功能**: 履约链配置和管理

#### 12.14 履约链周转天数规则 (Fulfillment Chain Turnover Days Rule)
- **路径**: `src/react-app/pages/rule-center/fulfillment-chain-turnover-days-rule/`
- **功能**: 履约链周转天数规则配置

#### 12.15 ABC 级别 (ABC Level)
- **路径**: `src/views/rule-center/abc-level/`
- **功能**: ABC 分类级别配置

#### 12.16 盘点配置 (Cycle Count Config)
- **路径**: `src/views/rule-center/cycle-count-config/`
- **功能**: 盘点规则配置

#### 12.17 盘点频率 (Cycle Count Frequency)
- **路径**: `src/views/rule-center/cycle-count-frequency/`
- **功能**: 盘点频率配置

#### 12.18 盘点任务规则 (Cycle Count Task Rule)
- **路径**: `src/views/rule-center/cycle-count-task-rule/`
- **功能**: 盘点任务规则配置

#### 12.19 重新排列规则 (Rearrangement Rule)
- **路径**: `src/views/rule-center/rearragement-rule/`
- **功能**: 重新排列规则配置

#### 12.20 出库流程 (Outbound Process)
- **路径**: `src/views/rule-center/outbound-process/`
- **功能**: 出库流程设置和指导

#### 12.21 新 SKU 属性 (New SKU Attribute)
- **路径**: `src/views/rule-center/new-sku-attribute/`
- **功能**: 新 SKU 属性配置

#### 12.22 SKU 属性验证 (SKU Attributes Validation)
- **路径**: `src/views/rule-center/sku-attributes-validation/`
- **功能**: SKU 属性验证规则

#### 12.23 重量验证 (Weight Validation)
- **路径**: `src/views/rule-center/weight-validation/`
- **功能**: 重量验证规则配置

#### 12.24 操作员技能 (Operator Skill)
- **路径**: `src/views/rule-center/operator-skill/`
- **功能**: 操作员技能配置（Vue版本）

#### 12.25 邮件中心 (Email Center)
- **路径**: `src/views/rule-center/email-center/`
- **功能**: 邮件通知规则配置

---

## 🔌 API 接口梳理

### API 文件目录结构
```
src/api/rule-center/
├── abcLevel.ts                          # ABC级别
├── allocate-rule.ts                     # 分配规则
├── boxing-rule.ts                       # 装箱规则
├── cc-config.ts                         # 盘点配置
├── cc-frequency.ts                      # 盘点频率
├── cc-pool.ts                           # 盘点池
├── flow-picking-setting.ts              # 流式拣货设置
├── fulfillment-chain-config.ts          # 履约链配置
├── fulfillment-chain-daily-sales-rule.ts # 履约链每日销售规则
├── fulfillment-chain-turnover-days-rule.ts # 履约链周转天数规则
├── group-rule.ts                         # 规则组
├── ibt-handling.ts                      # IBT处理
├── individual-target-setting.ts         # 个人目标设置
├── inventory-route.ts                    # 库存路由
├── mto-picking-rule.ts                   # MTO拣货规则
├── multi-picker.ts                      # 多拣货员
├── packaging-rule.ts                     # 包装规则
├── picking-dispatch.ts                  # 拣货调度
├── picking-rule.ts                      # 拣货规则
├── process-guide.ts                      # 流程指导
├── putaway-location-definition.ts        # 上架位置定义
├── putaway-rule-v2.ts                   # 上架规则v2
├── query-display.ts                      # 查询显示
├── quota-multi-conf.ts                  # 配额多配置
├── replenishment-return.ts              # 补货退货
├── rts-quota.ts                         # RTS配额
├── sales-outbound-order-config.ts        # 销售出库订单配置
├── shipping-rule.ts                     # 发货规则
├── skill-management-rule.ts              # 技能管理规则
├── sku-attribute-collection.ts          # SKU属性收集
├── sku-attributes-validation.ts         # SKU属性验证
├── sku-location-pairing-config.ts        # SKU位置配对配置
├── sku-tag.ts                           # SKU标签
├── sorting-rule.ts                      # 分拣规则
├── sorting-skill.ts                     # 分拣技能
├── wave-rule.ts                         # 波次规则
└── weight-validation.ts                 # 重量验证
```

---

## 🏗️ 技术架构

### 技术栈分布

#### Vue 2.x 技术栈
- **位置**: `src/views/rule-center/`
- **特点**: 
  - 使用 Vue Class Component 语法
  - 使用 TypeScript
  - 使用 Element UI (s-table, s-button 等)
  - 使用 WMS 通用组件 (wms-table, wms-filter)

#### React 技术栈
- **位置**: `src/react-app/pages/rule-center/`
- **特点**:
  - 使用 React Hooks
  - 使用 TypeScript
  - 使用 react-pro-components
  - 使用 ssc-ui-react 组件库

### 路由配置

#### Vue 路由
- **配置文件**: `src/router/modules/rule-center.ts`
- **路由命名**: `ruleCenter.*`

#### React 路由
- **配置文件**: `src/react-app/routes/rule-center.tsx`
- **路由路径**: `/rulecenter/*`

---

## 📊 业务流程图

### 主要业务流程

1. **拣货流程**
   ```
   订单创建 → 波次规则 → 拣货规则 → 拣货任务分配 → 拣货执行 → 包装规则 → 发货规则
   ```

2. **入库流程**
   ```
   ASN创建 → 配额配置 → 上架规则 → 上架任务分配 → 上架执行
   ```

3. **补货流程**
   ```
   补货需求计算 → 补货规则 → 补货任务创建 → 补货执行
   ```

4. **质检流程**
   ```
   入库质检 → 质检规则 → 质检清单 → 质检执行 → 质检结果
   ```

---

## 🔑 核心业务概念

### 1. 规则优先级 (Priority)
- 多个规则可以同时生效，通过优先级决定执行顺序
- 优先级数字越小，优先级越高

### 2. 规则组 (Rule Group)
- 将多个规则组合在一起，便于管理和应用
- 可以按仓库、店铺等维度分组

### 3. 技能配置 (Skill Config)
- 定义操作员需要具备的技能
- 用于任务分配和匹配

### 4. 配额管理 (Quota)
- 限制每日/每时段的入库/出库数量
- 用于产能管理和资源分配

### 5. 波次规则 (Wave Rule)
- 将订单分组形成波次
- 优化拣货路径和效率

---

## 📝 权限体系

### 权限命名规范
```
PC.RuleCenter.{Module}.{Action}
```

### 常见权限
- `View` - 查看权限
- `Create` - 创建权限
- `Edit` - 编辑权限
- `Delete` - 删除权限
- `Export` - 导出权限

### 示例
- `PC.RuleCenter.PickingRule.PickingRule.View`
- `PC.RuleCenter.PickingRule.PickingRule.Create`
- `PC.RuleCenter.PickingRule.PickingRule.Edit`

---

## 🔄 数据流转

### 规则配置流程
1. **创建规则** → 填写规则参数 → 设置优先级 → 保存
2. **规则生效** → 系统根据规则匹配订单/任务
3. **规则执行** → 生成对应的任务或操作
4. **规则监控** → 查看规则执行日志和效果

### 规则变更流程
1. **编辑规则** → 修改规则参数
2. **查看差异** → 对比变更前后的差异
3. **提交变更** → 保存新的规则配置
4. **查看日志** → 记录变更历史

---

## 🎯 业务特点

### 1. 规则驱动
- 所有业务操作都通过规则配置驱动
- 规则可以灵活组合和调整

### 2. 多维度配置
- 支持按仓库、店铺、SKU、订单类型等多维度配置
- 支持优先级和条件匹配

### 3. 实时生效
- 规则配置后可以实时生效
- 支持规则的启用/禁用

### 4. 历史追溯
- 所有规则变更都有日志记录
- 支持查看历史版本和差异对比

### 5. 权限控制
- 细粒度的权限控制
- 支持按模块、操作类型控制权限

---

## 📌 注意事项

### 1. 技术栈差异
- Vue 和 React 两套实现并存
- 新功能优先使用 React 实现
- 旧功能逐步迁移到 React

### 2. 版本管理
- 部分模块存在多个版本（如 putaway-rule v2/v3/v4）
- 需要明确当前使用的版本

### 3. 依赖关系
- 规则之间存在依赖关系
- 修改规则需要考虑对其他规则的影响

### 4. 性能考虑
- 规则匹配需要高效算法
- 大量规则时需要考虑性能优化

### 5. 数据一致性
- 规则配置变更需要保证数据一致性
- 需要考虑并发修改的情况

---

## 🔍 代码结构示例

### Vue 组件结构
```vue
<template>
  <div class="rule-page">
    <wms-filter :filterConfig="filterConfig" />
    <wms-table :pagination="pagination">
      <s-table :data="tableData">
        <!-- 表格列定义 -->
      </s-table>
    </wms-table>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
// 组件逻辑
</script>
```

### React 组件结构
```tsx
import React, { FC } from 'react';
import { useRequest } from 'ahooks';
import { ProTable } from 'react-pro-components';

const RulePage: FC = () => {
  // Hooks 逻辑
  return (
    <div>
      {/* 组件内容 */}
    </div>
  );
};
```

---

## 📚 相关文档

- API 文档: `src/api/rule-center/`
- 类型定义: `src/types/rule-center/`
- 路由配置: `src/router/modules/rule-center.ts`
- React 路由: `src/react-app/routes/rule-center.tsx`

---

## 🎓 总结

Rule Center 是 WMS 系统的核心配置中心，涵盖了仓库运营的各个方面：
- **拣货、上架、质检、发货**等核心流程的规则配置
- **波次、补货、包装**等业务优化规则
- **技能、配额、分配**等资源管理规则
- **权限、日志、监控**等系统管理功能

通过规则配置，可以实现仓库运营的灵活管理和优化。

---

*文档生成时间: 2025-01-27*
*文档版本: v1.0*


