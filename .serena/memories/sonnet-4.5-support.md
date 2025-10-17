# Sonnet 4.5 Support Implementation

## 變更摘要
已成功添加 Claude Sonnet 4.5 (claude-sonnet-4-5-20250929) 支援到 agent setup。

## 修改的檔案

### 核心配置
1. **packages/core/src/models.ts**
   - 添加 `SONNET_4_5: "claude-sonnet-4-5-20250929"`
   - 添加顯示名稱: "Claude Sonnet 4.5"
   - 添加短名稱: "claude-sonnet-4.5"

2. **packages/types/src/agent.ts**
   - 更新 `ALLOWED_MODELS` 陣列，添加 `SONNET_4_5`

3. **packages/agents/src/discovery.ts**
   - 更新快捷映射邏輯：
     - "sonnet" → SONNET_4_5 (最新版本)
     - "sonnet-4" → SONNET_4 (向後兼容)
     - "sonnet-4.5" → SONNET_4_5 (明確指定)

4. **apps/tui/src/main.ts**
   - 更新 CLI modelMap 添加 "sonnet-4.5" 選項
   - 更新幫助訊息顯示所有可用模型

### UI 增強
5. **packages/dashboard-web/src/components/charts/ModelPerformanceComparison.tsx**
   - 添加 Sonnet 4.5 顏色映射

6. **packages/dashboard-web/src/components/charts/ModelTokenSpeedChart.tsx**
   - 添加 Sonnet 4.5 顏色映射

7. **packages/dashboard-web/src/components/charts/MultiModelChart.tsx**
   - 添加 Sonnet 4.5 顏色映射

## 使用方式

### Agent 配置檔案
```yaml
---
model: sonnet        # 使用最新的 Sonnet 4.5
model: sonnet-4.5    # 明確指定 Sonnet 4.5
model: sonnet-4      # 使用 Sonnet 4
---
```

### CLI 命令
```bash
ccflare --set-model sonnet-4.5
```

## 測試結果
✅ Lint 通過
✅ TypeCheck 通過
