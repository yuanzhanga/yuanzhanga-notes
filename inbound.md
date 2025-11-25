入库  inbound

订单    order

任务    

到货登记    arriving

入库装箱    boxing

质检    qc

标准上架    standard-putaway

批量上架    mass-putaway

入库人力计划    labour-planning

再加工  reprocess

交叉转运分拣    


arriving/
├── index.vue                  # 到货主页面
└── carton-validation.vue      # 纸箱验证

order/
├── index.vue                  # 订单管理主页面（Tab切换）
├── asn/                      # ASN（到货通知单）管理
│   ├── index.vue             # ASN列表
│   ├── create-asn.vue        # 创建ASN
│   ├── detail.vue            # ASN详情
│   └── components/           # ASN相关组件
├── asn-group/                # ASN组管理
├── tracking-id/              # 跟踪ID管理
├── queue-list/               # 队列列表
├── reprocess/                # 重处理订单
└── hybrid.ts                 # 混合类型定义

receiving/
├── receiving.vue             # 收货主页面
├── report-exception.vue      # 异常报告
└── components/
    ├── scan-uid.vue          # UID扫描组件
    └── working-list.vue      # 工作列表组件

qc/
├── index.vue                 # 质检主页面
├── qc.vue                    # 质检操作页面
├── qc-item.vue               # 质检项目页面
├── qc-lovito.vue             # Lovito品牌质检
├── qc-lovito-new.vue         # Lovito新质检页面
├── constant.ts               # 质检常量
└── components/               # 质检相关组件
    ├── checklist.vue         # 质检清单
    ├── exception-dialog.vue  # 异常对话框
    ├── sku-list.vue          # SKU列表
    └── ...                   # 其他质检组件

boxing/
├── index.vue                 # 装箱主页面
├── boxing.vue                # 装箱操作页面
├── boxing-new.vue            # 新装箱页面
├── boxing-conf.ts            # 装箱配置
├── constant.ts               # 装箱常量
├── type.ts                   # 装箱类型定义
└── components/               # 装箱相关组件
    ├── asn-sku-list.vue      # ASN SKU列表
    ├── exception-qty-dialog.vue # 异常数量对话框
    └── ...                   # 其他装箱组件


mass-putaway/
├── mass-putaway.vue          # 批量上架主页面
├── report-exception.vue      # 异常报告
└── components/
    └── abnormal-list.vue     # 异常列表

reprocess/
├── reprocess.vue             # 重处理主页面
└── components/
    ├── reprocess-operate.vue # 重处理操作
    ├── reprocess-scan.vue    # 重处理扫描
    └── ...                   # 其他重处理组件

labour-planning/
├── labour-planning.vue       # 人力规划主页面
└── components/
    ├── edit-shift-dialog.vue # 编辑班次对话框
    └── impact-factors.vue    # 影响因素

1. 到货登记 (arriving) 
   ↓
2. 订单管理 (order/ASN)
   ↓
3. 收货确认 (receiving)
   ↓
4. 质量检查 (qc)
   ↓
5. 数量清点 (counting)
   ↓
6. 装箱处理 (boxing)
   ↓
7. 上架操作 (standard-putaway/mass-putaway)