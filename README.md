noname key mod
====

针对无名杀棘手怀念摧毁懒人包键势力角色进行的史诗级增强。

---
> [!CAUTION]
> 本更改仅适用于 https://github.com/lieren2023/noname-for-dummies 。不适用于 https://github.com/libnoname/noname 或其他变体。

> [!CAUTION]
> 本更改会造成平衡性失衡！

> [!CAUTION]
> 本更改可能会导致游戏客户端损坏！

## 更改（由 LLM 生成）

### 📊 全局改动

- **体力值统一提升**：几乎所有角色基础体力从 3/4 提升至 **5**；  
  - `key_misa`：3 → **8**  
  - `key_kagari` / `key_doruji`：保持 **16**
- **势力统一**：所有角色势力设为 `"key"`，原 `"shen"`/`"shu"` 技能重写适配
- **技能频次放宽**：大量技能移除 `usable: 1` 或 `charlotte: true`，变为**无限频**
- **数值普遍×2~×4**：摸牌、回血、伤害、弃牌、手牌/体力上限等全面翻倍

---

### ✨ 新增技能（6 个）

| 技能 | 角色 | 效果 |
|------|------|------|
| `kagari_yuanyi`（远忆） | key_kagari | 回合开始/结束时，摸 X + 回 X（X = 游戏轮数，上限 9） |
| `mia_rujing`（入境） | key_mia | 手牌花色数变化时切换状态：<br>• 阴：被指定为目标时摸 X 牌并令牌无效<br>• 阳：使用牌需弃 X 牌，否则无效并掉 1 血 |
| `yuuki_wuxin`（无心） | key_yuuki | 转换技：<br>• 阴：你造成的伤害取消<br>• 阳：他人对你造成的伤害取消<br>• 每角色回合结束时，摸 = 其造成伤害数 |
| `yusa_zhumeng`（逐梦） | key_yusa | 转换技：<br>• 阴：判定阶段 → 摸牌阶段<br>• 阳：弃牌阶段 → 摸牌阶段<br>出牌阶段：<br>– 手牌 ≥ 体力：无次数<br>– 手牌 ≤ 体力：无距离<br>– 手牌 = 体力：**额外回合** |
| `misa_`（魂映） | key_misa | 受伤后转换：<br>• 阴：回 2 血 + 封印伤害来源所有技能至其回合结束<br>• 阳：摸 4 牌 + 下回合开始前防同类伤害 |
| `michiru_huzhu`（互助） | key_michiru | 游戏开始得 1 “米券”；花色变化时 +1 券 + 回 1 血；使用基本牌时消耗 1 券，摸 = 剩余券数 |

---

### 🔧 大改技能（机制重构）

| 技能 | 角色 | 改动 |
|------|------|------|
| `hina_shenshi` | key_hina | 势力 `"shen"` → `"key"`；摸 2 → **4** |
| `iriya_yinji` | key_iriya | `drawTo(17)` → **`draw(17)`** |
| `liyingxia_wumai` | db_key_liyingxia | 势力 `"shu"` → `"key"`；技能池全换；**永久获得技能**（非临时）；摸牌 +2 |
| `sasami_miaobian` | key_sasami | 条件反转：**hp ≥ X 才触发**；hp < 3 时：受伤回 1、失牌摸 2、用牌摸 2 |
| `yui_lieyin` | key_yui | 改为**转换技**：<br>• 阴：红牌=杀 + 无距离 + 伤害+1<br>• 阳：杀=决斗 + 用决斗摸 1 |
| `umi_qihuan` | key_umi | 回 X → **回 7 + 摸 7**；拿技能数 2 → **7**；<br>**无死亡角色时**：重置技能 + 全场手牌=7 + 拿弃牌 |
| `kud_qiaoshou` / `kud_buhui` | key_kud | 移除复杂声明流程 → **直给摸 4 + 回 2**；濒死回至 **7 血** |
| `erika_yousheng` | key_erika | 使命技重做：**增 4 上限 + 回 4 + 摸 4 + 16 护甲**；失败条件改为 **濒死才触发** |
| `kotori_huazhan` | key_kotori | 魔物当【树上开花】 → **【无中生有】** |
| `shizuru_nianli` / `kanade_benzhan` | key_shizuru / sp_key_kanade | 移除“每轮/每回合限 1 次”；效果 ×2（摸 2→4，伤 1→2） |
| `mio_tuifu` | key_mio | 同性伤害 → **任意角色受伤即摸牌** |
| `ao_shixin` | key_ao | 觉醒条件：3 花色 → **4 花色**；觉醒收益：回 1 → **回 2 + 摸 4** |
| `michiru_sheyuan` | key_michiru | 频率：每轮 1 次 → **每角色回合 1 次**；触发条件与“米券”联动 |

---

### 🔢 数值类小改（普遍×2~×4）

- **摸牌**：1~2 → **2~4**（如 `kamome_yangfan` 2→4，`nao_duyin` 1→4）
- **回血**：1 → **2~4**（如 `kyou_duanfa` 1→4，`misuzu_nongyin` +2）
- **伤害**：1 → **2~4**（如 `seira_xinghui` ×2，`hisako_yinbao` 1→4，`tomoya_wangjin` 2→4）
- **弃牌**：1~2 → **2~4**（如 `kanade_benzhan` 弃 2→4）
- **手牌/体力上限**：+1 → **+4**（如 `nao_shouqing` +1→+4）
- **初始摸牌**：`akane_jugu` 摸 X → **2X**；`yuzuru_wuxin`（原交心）失血摸 2 → **增上限+回1+摸2**

---

## 📥 安装

将 key.ts 重命名为 key.js 并移动到 /storage/emulated/0/Android/data/com.noname.shijiao/character 里即可。

## 🏛 许可证
遵循上游许可证。
