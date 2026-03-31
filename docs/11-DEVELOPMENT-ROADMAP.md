# 🚀 11 — 開發路線圖 Development Roadmap

> 分階段開發，每階段有明確交付物。
> 適合一個人長期開發，可隨時擴充模組。

---

## 📊 開發階段總覽

```
Phase 1 ─── 基礎架構（骨架）
Phase 2 ─── 角色與移動（能動起來）
Phase 3 ─── 戰鬥核心（能打怪）
Phase 4 ─── 職業與技能（能放技能）
Phase 5 ─── 怪物與 AI（怪物會反擊）
Phase 6 ─── 地圖與關卡（有地圖可探索）
Phase 7 ─── RPG 系統（裝備/背包/等級）
Phase 8 ─── 任務與 NPC（有故事可玩）
Phase 9 ─── UI 完善（介面好用）
Phase 10 ── 音效與美術（換上正式素材）
Phase 11 ── 平衡與打磨（好玩）
Phase 12 ── 部署與發布
```

---

## 🏗️ Phase 1：基礎架構

> 目標：專案跑起來，能看到空白畫面。

- [ ] `npm create vite` + Phaser 3 + TypeScript 初始化
- [ ] 設定 `vite.config.ts`（Phaser 3 相容設定）
- [ ] 設定 `tsconfig.json`
- [ ] 建立基礎目錄結構
- [ ] BootScene + PreloaderScene 載入流程
- [ ] MainMenuScene（主選單基本畫面）
- [ ] Phaser Scale Manager 16:9 響應式設定
- [ ] 裝置檢測（桌面 / 行動）
- [ ] ESLint + Prettier 設定

**交付物：** 可啟動的空白遊戲，主選單顯示

---

## 🏃 Phase 2：角色與移動

> 目標：角色能在格子地圖上移動。

- [ ] GridMap 格子地圖渲染器（仿 GVampireSurvivor）
- [ ] Player 基類（Placeholder 圓形）
- [ ] KeyboardController（WASD + 方向鍵）
- [ ] TouchController + Joystick（虛擬搖桿）
- [ ] InputManager（統一管理鍵盤/觸控）
- [ ] 攝影機跟隨（平滑 lerp）
- [ ] 基本碰撞（牆壁不可通過）
- [ ] 地圖邊界限制

**交付物：** 彩色圓形在格子地圖上可移動

---

## ⚔️ Phase 3：戰鬥核心

> 目標：能打到東西，東西會掉血。

- [ ] CombatSystem（傷害計算公式）
- [ ] 近戰攻擊判定（扇形碰撞）
- [ ] 投射物系統（直線飛行、碰撞消失）
- [ ] DamageNumber 飄血數字
- [ ] 受擊閃爍效果
- [ ] HP/MP/氣 資源管理
- [ ] ChiSystem（氣值累積與消耗）
- [ ] StatusEffectSystem（中毒/灼燒/減速等）
- [ ] 暴擊 / 閃避 / 格擋判定
- [ ] 基礎 HUD（HP/MP/氣 條）

**交付物：** 角色能攻擊假怪物，傷害數字飄出

---

## 🗡️ Phase 4：職業與技能

> 目標：9 個職業都能用，技能能放出來。

- [ ] 9 個職業子類（基礎屬性差異化）
- [ ] CharSelectScene（職業選擇介面）
- [ ] Skill 基類（冷卻、MP/氣消耗、動畫）
- [ ] MeleeSkill（近戰技能）
- [ ] ProjectileSkill（遠程投射技能）
- [ ] AOESkill（範圍技能）
- [ ] BuffSkill / DebuffSkill（增益/減益技能）
- [ ] SummonSkill（召喚技能）
- [ ] MusicSkill（浪子樂曲技能）
- [ ] SkillData.ts（198 個技能數據錄入）
- [ ] SkillBar UI（6 技能快捷欄）
- [ ] 技能冷卻顯示（灰色遮罩 + 倒計時）
- [ ] 技能拖曳配置

**交付物：** 所有職業可選，技能可施放並顯示 Placeholder 特效

---

## 👾 Phase 5：怪物與 AI

> 目標：怪物會動、會打人、會死。

- [ ] Monster 基類（Placeholder 紅圓）
- [ ] 怪物 AI 狀態機（巡邏→追蹤→攻擊→撤退）
- [ ] MonsterData.ts（25 種怪物數據錄入）
- [ ] SpawnSystem（怪物生成系統）
- [ ] 怪物攻擊行為（近戰/遠程）
- [ ] LootSystem（掉落計算）
- [ ] 經驗值掉落與收集
- [ ] 金幣掉落與收集
- [ ] 5 個 BOSS 獨特 AI（階段制、多技能）
- [ ] BOSS 血條 UI
- [ ] BossScene（BOSS 戰專用場景）

**交付物：** 怪物有 AI 行為，打死會掉東西

---

## 🗺️ Phase 6：地圖與關卡

> 目標：5 層秘境都能探索。

- [ ] MapManager（地圖載入/切換管理器）
- [ ] MapData.ts（所有地圖配置錄入）
- [ ] VillageScene（崑崙村落安全區）
- [ ] WorldMapScene（世界大地圖介面）
- [ ] 第一層：4 小關 + BOSS 房（共 5 張地圖）
- [ ] 第二層：5 小關 + BOSS 房（共 6 張地圖）
- [ ] 第三層：5 小關 + BOSS 房（共 6 張地圖）
- [ ] 第四層：6 小關 + BOSS 房（共 7 張地圖）
- [ ] 第五層：6 小關 + BOSS 房（共 7 張地圖）
- [ ] 地形機制（毒沼、冰面、熔岩、落石等）
- [ ] 傳送點 / 地圖出入口
- [ ] 存檔點
- [ ] 寶箱互動
- [ ] FogOfWar（戰爭迷霧 / 暗區）
- [ ] MiniMap（小地圖）

**交付物：** 完整 5 層秘境可通關

---

## 📊 Phase 7：RPG 系統

> 目標：有完整的升級、裝備、背包系統。

- [ ] LevelSystem（等級/經驗計算）
- [ ] LevelCurve.ts（經驗曲線數據）
- [ ] 升級特效 + 屬性提升
- [ ] 技能點分配
- [ ] SkillTreeScene（技能樹介面）
- [ ] EquipmentSystem（裝備穿脫）
- [ ] 裝備品質系統（白/綠/藍/紫/橙）
- [ ] 隨機屬性生成
- [ ] 裝備強化系統
- [ ] InventorySystem（背包管理）
- [ ] InventoryScene（背包介面）
- [ ] EquipmentScene（裝備介面）
- [ ] StatusScene（角色狀態介面）
- [ ] 商店系統（購買/出售）
- [ ] 金幣經濟系統
- [ ] SaveSystem（IndexedDB 存檔）
- [ ] 自動存檔 + 手動存檔

**交付物：** 完整 RPG 系統，升級、穿裝備、買東西、存檔

---

## 📜 Phase 8：任務與 NPC

> 目標：有故事、有任務、有 NPC 互動。

- [ ] NPC 基類（可互動、顯示對話）
- [ ] NPCData.ts（NPC 數據錄入）
- [ ] QuestSystem（任務追蹤、進度計算）
- [ ] QuestData.ts（所有任務數據錄入）
- [ ] DialogueScene（對話介面）
- [ ] DialogBox UI（對話框、文字逐字出現）
- [ ] 第零章任務（教學引導）
- [ ] 第一章至第五章任務
- [ ] 支線任務
- [ ] QuestLogScene（任務日誌介面）
- [ ] ShopScene（商店介面）
- [ ] NPC 商店互動
- [ ] 任務提示（感嘆號/問號標記）

**交付物：** 完整主線 + 支線任務，NPC 可對話、可交易

---

## 🎨 Phase 9：UI 完善

> 目標：介面好用、好看。

- [ ] HUD 最終版（HP/MP/氣/EXP/EXP10% 條）
- [ ] 角色面板（下方狀態區）
- [ ] 技能欄最終版（冷卻、拖曳、提示框）
- [ ] 道具快捷欄
- [ ] ItemTooltip（物品/裝備提示框）
- [ ] NotificationToast（通知提示）
- [ ] BOSS 血條最終版
- [ ] 小地圖最終版
- [ ] 世界地圖解鎖進度顯示
- [ ] 行動裝置 UI 優化
- [ ] 響應式佈局最終調整
- [ ] 全部 UI 繁體中文確認
- [ ] 遊戲設定介面（音量、控制）

**交付物：** 完整美觀的 UI，桌面和行動裝置都好用

---

## 🎵 Phase 10：音效與美術

> 目標：替換 Placeholder，加入正式美術和音效。

- [ ] 免費 BGM 收集與整合（11+ 首）
- [ ] 免費 SFX 收集與整合（48+ 個）
- [ ] AudioSystem（音效管理、音量控制）
- [ ] BGM 按場景切換
- [ ] SFX 按事件觸發
- [ ] 替換角色 Placeholder → ComfyUI 精靈圖
- [ ] 替換怪物 Placeholder → ComfyUI 精靈圖
- [ ] 替換技能特效 Placeholder → ComfyUI 特效圖
- [ ] 替換 UI 元素 → 正式美術
- [ ] 替換地圖裝飾 → 正式美術
- [ ] 加入角色動畫
- [ ] 加入技能動畫

**交付物：** 有正式美術和音效的遊戲

---

## ⚖️ Phase 11：平衡與打磨

> 目標：好玩、平衡、無明顯 bug。

- [ ] 全程通關測試（9 職業各一次）
- [ ] 傷害數值平衡
- [ ] 怪物難度調整
- [ ] BOSS 機制微調
- [ ] 裝備掉落率調整
- [ ] 經驗曲線調整
- [ ] 技能冷卻和傷害微調
- [ ] 效能優化（FPS、記憶體）
- [ ] 物件池化（怪物、投射物、特效）
- [ ] 資源懶載入優化
- [ ] Bug 修復
- [ ] 隱藏層（混沌虛空）無盡模式
- [ ] 隱藏層噩夢模式

**交付物：** 平衡、穩定、好玩的完整遊戲

---

## 🌐 Phase 12：部署與發布

> 目標：上線可玩。

- [ ] Vite build 優化（壓縮、tree-shaking）
- [ ] GitHub Pages 部署設定
- [ ] 首頁 / 說明頁面
- [ ] 分享圖 / favicon
- [ ] README 更新（附遊玩連結）
- [ ] 版本號標記（v1.0.0）

**交付物：** 可遊玩的線上版本

---

## 📅 預估時間（參考）

| Phase | 內容 | 預估工作量 |
|-------|------|-----------|
| 1 | 基礎架構 | 短 |
| 2 | 角色與移動 | 短 |
| 3 | 戰鬥核心 | 中 |
| 4 | 職業與技能 | 長（198 技能） |
| 5 | 怪物與 AI | 中 |
| 6 | 地圖與關卡 | 長（31+ 張地圖） |
| 7 | RPG 系統 | 長 |
| 8 | 任務與 NPC | 中 |
| 9 | UI 完善 | 中 |
| 10 | 音效與美術 | 依美術進度 |
| 11 | 平衡與打磨 | 長 |
| 12 | 部署與發布 | 短 |

> ⚠️ 建議開發順序：Phase 1-3 為最高優先，先做出能跑能打的原型，之後逐步加內容。

---

## 🔧 模組化擴充設計

Vite + TypeScript 的模組化架構支援長期擴充：

```
加新職業？
→ data/ClassData.ts 加屬性
→ entities/classes/ 加子類
→ data/SkillData.ts 加技能

加新怪物？
→ data/MonsterData.ts 加數據
→ entities/monsters/ 加子類（如有特殊行為）

加新地圖？
→ data/MapData.ts 加配置
→ DungeonScene 自動載入

加新裝備？
→ data/EquipmentData.ts 加數據

加新任務？
→ data/QuestData.ts 加數據

加新 NPC？
→ data/NPCData.ts 加數據

以上全部不需要修改核心邏輯程式碼，
僅需要新增/修改資料檔案。
這就是資料驅動設計的好處。
```

---

## 📋 最低可玩版本（MVP）

如果要先做一個最小可玩版本，只需完成：

- [x] Phase 1：基礎架構
- [x] Phase 2：角色與移動
- [x] Phase 3：戰鬥核心
- [ ] Phase 4 精簡：先做 1 個職業（劍術師），10 個技能
- [ ] Phase 5 精簡：先做 5 種怪物 + 1 個 BOSS
- [ ] Phase 6 精簡：先做第一層（4 小關 + BOSS）
- [ ] Phase 7 精簡：等級系統 + 簡易背包
- [ ] Phase 9 精簡：基礎 HUD

**MVP 範圍：1 職業、1 層秘境、1 個 BOSS，能升級能打怪**

之後再逐步擴充到完整版。
