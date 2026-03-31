# 🛠️ 09 — 技術架構 Tech Architecture

> Phaser 3 + TypeScript + Vite
> 資料驅動設計：所有遊戲資料存於 JSON 可配置資料庫。

---

## 🏗️ 技術選型

| 項目 | 技術 | 版本 | 說明 |
|------|------|------|------|
| 遊戲引擎 | **Phaser 3** | ^3.70 | 成熟 2D 框架，社群大 |
| 語言 | **TypeScript** | ^5.x | 型別安全，適合大型專案 |
| 建構工具 | **Vite** | ^5.x | 快速 HMR，模組化友好 |
| 地圖工具 | **Tiled** | — | 匯出 JSON，Phaser 原生支援 |
| 虛擬搖桿 | **自製** | — | 基於 Phaser Input，無外部依賴 |
| 資料儲存 | **IndexedDB** | — | 大容量本地存檔 |
| 備用儲存 | **localStorage** | — | 簡易設定存檔 |
| 部署 | **GitHub Pages** | — | 靜態託管 |
| 套件管理 | **npm** | — | |

---

## 📂 專案目錄結構

```
GSWORD/
├── docs/                           # 設計文件（你看到的這些 MD）
│   ├── 01-GAME-OVERVIEW.md
│   ├── 02-CLASSES.md
│   ├── 03-COMBAT-SYSTEM.md
│   ├── 04-MONSTERS-DATABASE.md
│   ├── 05-MAP-DESIGN.md
│   ├── 06-QUEST-SYSTEM.md
│   ├── 07-EQUIPMENT-ITEMS.md
│   ├── 08-UI-HUD.md
│   ├── 09-TECH-ARCHITECTURE.md
│   ├── 10-ART-AUDIO.md
│   └── 11-DEVELOPMENT-ROADMAP.md
├── index.html                      # 遊戲入口頁面
├── package.json
├── tsconfig.json
├── vite.config.ts
├── public/
│   ├── favicon.ico
│   └── audio/                      # 音效資源（不經過 Vite 處理）
├── src/
│   ├── main.ts                     # 入口
│   │
│   ├── config/                     # 遊戲設定
│   │   ├── GameConfig.ts           # Phaser Config
│   │   └── Constants.ts            # 全域常數
│   │
│   ├── data/                       # 🗄️ 可配置資料庫（全 JSON/TS）
│   │   ├── ClassData.ts            # 9 職業基礎屬性與成長
│   │   ├── SkillData.ts            # 198 個技能數據
│   │   ├── MonsterData.ts          # 25+ 怪物數據
│   │   ├── BossData.ts             # 5 個 BOSS 數據
│   │   ├── EquipmentData.ts        # 裝備數據
│   │   ├── ItemData.ts             # 道具數據
│   │   ├── QuestData.ts            # 任務數據
│   │   ├── MapData.ts              # 地圖配置
│   │   ├── NPCData.ts              # NPC 對話/商店
│   │   ├── LevelCurve.ts           # 等級經驗曲線
│   │   ├── LootTable.ts            # 掉落表
│   │   └── BalanceData.ts          # 數值平衡總表
│   │
│   ├── scenes/                     # 遊戲場景
│   │   ├── BootScene.ts            # 資源預載
│   │   ├── PreloaderScene.ts       # 載入進度條
│   │   ├── MainMenuScene.ts        # 主選單
│   │   ├── CharSelectScene.ts      # 職業選擇
│   │   ├── VillageScene.ts         # 崑崙村落（安全區）
│   │   ├── WorldMapScene.ts        # 世界大地圖
│   │   ├── DungeonScene.ts         # 秘境通用場景
│   │   ├── BossScene.ts            # BOSS 戰專用場景
│   │   ├── UIScene.ts              # UI 覆蓋層
│   │   ├── InventoryScene.ts       # 背包介面
│   │   ├── EquipmentScene.ts       # 裝備介面
│   │   ├── StatusScene.ts          # 角色狀態介面
│   │   ├── SkillTreeScene.ts       # 技能樹介面
│   │   ├── QuestLogScene.ts        # 任務日誌
│   │   ├── ShopScene.ts            # 商店介面
│   │   ├── DialogueScene.ts        # 對話介面
│   │   └── GameOverScene.ts        # 結算/死亡畫面
│   │
│   ├── entities/                   # 遊戲實體
│   │   ├── Player.ts               # 玩家基類
│   │   ├── classes/                # 9 職業子類
│   │   │   ├── MartialArtist.ts    # 武術師
│   │   │   ├── Medic.ts            # 醫術師
│   │   │   ├── Alchemist.ts        # 藥術師
│   │   │   ├── Swordsman.ts        # 劍術師
│   │   │   ├── Bladesman.ts        # 刀術師
│   │   │   ├── ShadowCaster.ts     # 陰術師
│   │   │   ├── TalismanMaster.ts   # 符術師
│   │   │   ├── Assassin.ts         # 刺術師
│   │   │   └── Wanderer.ts         # 浪子
│   │   ├── Monster.ts              # 怪物基類
│   │   ├── monsters/               # 怪物子類
│   │   │   ├── FoxSpirit.ts
│   │   │   ├── MountainSpirit.ts
│   │   │   ├── PoisonScorpion.ts
│   │   │   ├── BatDemon.ts
│   │   │   ├── IceWraith.ts
│   │   │   ├── Zombie.ts
│   │   │   ├── GhostFlame.ts
│   │   │   ├── FireSalamander.ts
│   │   │   ├── StoneGolem.ts
│   │   │   └── ...                 # 更多怪物
│   │   ├── bosses/                 # BOSS 子類
│   │   │   ├── WolfKing.ts
│   │   │   ├── SnakeDemoness.ts
│   │   │   ├── FrostColossus.ts
│   │   │   ├── FlameDragon.ts
│   │   │   └── KunlunGuardian.ts
│   │   └── NPC.ts                  # NPC 基類
│   │
│   ├── systems/                    # 遊戲系統
│   │   ├── CombatSystem.ts         # 戰鬥（傷害、碰撞）
│   │   ├── SkillSystem.ts          # 技能管理（CD、施放）
│   │   ├── LevelSystem.ts          # 等級/經驗
│   │   ├── EquipmentSystem.ts      # 裝備穿脫/強化
│   │   ├── InventorySystem.ts      # 背包管理
│   │   ├── LootSystem.ts           # 掉落計算
│   │   ├── QuestSystem.ts          # 任務追蹤
│   │   ├── StatusEffectSystem.ts   # 狀態效果管理
│   │   ├── SpawnSystem.ts          # 怪物生成
│   │   ├── SaveSystem.ts           # 存檔/讀檔
│   │   ├── AudioSystem.ts          # 音效管理
│   │   └── ChiSystem.ts            # 氣值系統
│   │
│   ├── skills/                     # 技能實作
│   │   ├── Skill.ts                # 技能基類
│   │   ├── ProjectileSkill.ts      # 投射物技能
│   │   ├── AOESkill.ts             # 範圍技能
│   │   ├── BuffSkill.ts            # 增益技能
│   │   ├── DebuffSkill.ts          # 減益技能
│   │   ├── MeleeSkill.ts           # 近戰技能
│   │   ├── SummonSkill.ts          # 召喚技能
│   │   └── MusicSkill.ts           # 樂曲技能（浪子專用）
│   │
│   ├── ui/                         # UI 組件
│   │   ├── HUD.ts                  # HP/MP/氣/EXP 條
│   │   ├── SkillBar.ts             # 技能欄
│   │   ├── Joystick.ts             # 虛擬搖桿
│   │   ├── MobileButtons.ts        # 行動端按鈕
│   │   ├── DialogBox.ts            # 對話框
│   │   ├── DamageNumber.ts         # 飄血數字
│   │   ├── BossHealthBar.ts        # BOSS 血條
│   │   ├── MiniMap.ts              # 小地圖
│   │   ├── ItemTooltip.ts          # 道具提示框
│   │   └── NotificationToast.ts    # 通知提示
│   │
│   ├── map/                        # 地圖系統
│   │   ├── GridMap.ts              # 格子地圖渲染
│   │   ├── MapManager.ts           # 地圖載入/切換
│   │   ├── TileRegistry.ts         # 圖塊定義
│   │   ├── FogOfWar.ts             # 戰爭迷霧
│   │   └── WorldMap.ts             # 世界大地圖
│   │
│   ├── input/                      # 輸入控制
│   │   ├── InputManager.ts         # 輸入管理器
│   │   ├── KeyboardController.ts   # 鍵盤
│   │   └── TouchController.ts      # 觸控
│   │
│   ├── utils/                      # 工具函數
│   │   ├── MathUtils.ts            # 數學（角度、距離、碰撞）
│   │   ├── RandomUtils.ts          # 隨機（掉落、暴擊）
│   │   ├── DeviceDetect.ts         # 裝置檢測
│   │   ├── Formatter.ts            # 格式化（數字、時間）
│   │   └── Debug.ts                # 除錯工具
│   │
│   └── types/                      # TypeScript 型別定義
│       ├── GameTypes.ts            # 遊戲通用型別
│       ├── ClassTypes.ts           # 職業型別
│       ├── SkillTypes.ts           # 技能型別
│       ├── ItemTypes.ts            # 物品型別
│       ├── MonsterTypes.ts         # 怪物型別
│       └── MapTypes.ts             # 地圖型別
│
├── dist/                           # 編譯輸出
└── README.md
```

---

## 🗄️ 資料庫設計（Data-Driven）

### 設計原則

所有遊戲資料以 **TypeScript 常數物件 / JSON** 存儲，方便修改和擴展：

```
修改一個怪物的攻擊力？
→ 改 MonsterData.ts 裡的數值即可，不需改任何邏輯程式碼。

加一個新職業？
→ 在 ClassData.ts 加一個新物件，在 SkillData.ts 加技能即可。

加一個新裝備？
→ 在 EquipmentData.ts 加一個新物件即可。
```

### 資料檔案說明

| 檔案 | 內容 | 可配置項 |
|------|------|---------|
| ClassData.ts | 9 職業基礎屬性 | 名稱、基礎值、成長值、武器類型 |
| SkillData.ts | 198 個技能 | 名稱、MP/氣消耗、CD、傷害倍率、效果 |
| MonsterData.ts | 25+ 怪物 | 名稱、等級、屬性、AI 參數、掉落 |
| BossData.ts | 5 個 BOSS | 技能組、階段、機制、掉落表 |
| EquipmentData.ts | 所有裝備 | 屬性、品質、職業限制 |
| ItemData.ts | 所有道具 | 效果、價格、堆疊上限 |
| QuestData.ts | 所有任務 | 對話、目標、獎勵、前置條件 |
| MapData.ts | 所有地圖 | 大小、主題、怪物生成、物件 |
| NPCData.ts | 所有 NPC | 位置、功能、商品列表、對話 |
| LevelCurve.ts | 等級曲線 | 每級所需經驗 |
| LootTable.ts | 掉落表 | 物品 ID、機率、數量範圍 |
| BalanceData.ts | 平衡參數 | 傷害公式常數、經驗倍率 |

---

## 💾 存檔系統

### 存檔方式

```
主要：IndexedDB（大容量，結構化存儲）
備用：localStorage（簡易設定，如音量）

存檔欄位：3 個獨立存檔位
自動存檔：進入存檔點/切換地圖時
手動存檔：隨時可在選單中存檔
```

### 存檔資料結構

```typescript
interface SaveData {
  version: string;           // 存檔版本（用於遷移）
  timestamp: number;         // 存檔時間
  playTime: number;          // 遊戲時間（秒）

  player: {
    classId: string;         // 職業 ID
    level: number;
    exp: number;
    hp: number;
    mp: number;
    chi: number;
    gold: number;
    stats: PlayerStats;      // 當前屬性
    position: { mapId: string; x: number; y: number };
    skillLevels: Record<string, number>;  // 技能等級
    skillSlots: string[];    // 技能欄配置
    quickItems: string[];    // 快捷道具欄
  };

  inventory: {
    items: InventorySlot[];  // 背包物品
    maxSlots: number;        // 背包上限
  };

  equipment: {
    weapon: EquipmentInstance | null;
    helmet: EquipmentInstance | null;
    armor: EquipmentInstance | null;
    gloves: EquipmentInstance | null;
    boots: EquipmentInstance | null;
    accessory1: EquipmentInstance | null;
    accessory2: EquipmentInstance | null;
  };

  progress: {
    completedQuests: string[];
    activeQuests: Record<string, QuestProgress>;
    unlockedMaps: string[];
    defeatedBosses: string[];
    discoveredAreas: string[];
  };

  settings: {
    bgmVolume: number;
    sfxVolume: number;
    language: string;
  };
}
```

---

## 🎮 Phaser 場景流程

```
BootScene (資源預載)
    ↓
PreloaderScene (進度條)
    ↓
MainMenuScene (主選單)
    ├── [新遊戲] → CharSelectScene → VillageScene
    ├── [繼續遊戲] → 載入存檔 → 對應場景
    └── [設定] → SettingsScene
    
遊戲中場景關係：
    VillageScene ←→ WorldMapScene ←→ DungeonScene
                                       ↓
                                    BossScene
    
同時運行（覆蓋層）：
    UIScene（永遠在最上層，管理 HUD/技能欄）
```

### 場景管理策略

```typescript
// 使用 Phaser 的 Scene Manager
// 遊戲場景使用 scene.start()（替換）
// UI 場景使用 scene.launch()（疊加）

// 範例：
this.scene.start('DungeonScene', { mapId: 'map_1_1' });
this.scene.launch('UIScene');  // UI 覆蓋在遊戲場景上方
```

---

## 📐 遊戲視窗設定

```typescript
const gameConfig: Phaser.Types.Core.GameConfig = {
  type: Phaser.AUTO,          // 自動選擇 WebGL / Canvas
  width: 1280,                // 16:9
  height: 720,
  scale: {
    mode: Phaser.Scale.FIT,   // 自動適配螢幕
    autoCenter: Phaser.Scale.CENTER_BOTH,
    min: { width: 640, height: 360 },
    max: { width: 1920, height: 1080 },
  },
  physics: {
    default: 'arcade',        // 簡單物理（碰撞檢測）
    arcade: {
      gravity: { x: 0, y: 0 },  // 俯視角無重力
      debug: false,
    },
  },
  scene: [BootScene, PreloaderScene, MainMenuScene, ...],
  pixelArt: false,            // 手繪風不需要像素銳化
  backgroundColor: '#000000',
};
```

---

## 🔧 開發工具

| 工具 | 用途 |
|------|------|
| Vite HMR | 熱更新，即時看到程式碼修改效果 |
| Tiled Map Editor | 設計格子地圖，匯出 JSON |
| Chrome DevTools | 除錯 |
| Phaser Debug Plugin | 碰撞框/FPS 顯示 |
| ESLint + Prettier | 程式碼格式化 |

---

## ⚡ 效能考量

| 項目 | 策略 |
|------|------|
| 同時最大怪物數 | 30-50 隻（超過則不生成） |
| 投射物上限 | 100 個 |
| 飄血數字上限 | 50 個 |
| 粒子效果上限 | 200 個 |
| 資源載入 | 按場景/層級懶載入 |
| 地圖渲染 | 僅渲染可視範圍 ± 1 格 |
| 碰撞檢測 | 使用 Phaser Arcade 物理 |
| 物件池 | 怪物、投射物、特效使用物件池 |
| 精靈圖 | Sprite Sheet 合併圖，減少 HTTP 請求 |
