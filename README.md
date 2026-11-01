# ⚡ ZeroHub UI

ไลบรารี UI สำหรับสคริปต์ Roblox ของทีม ZeroHub
ธีมมืดพร้อม 7 สไตล์ แถบหมวดอยู่ด้านบน การ์ดเรียงซ้าย-ขวา ใช้ได้ทั้งมือถือและ PC ฟอนต์ Builder Sans

```lua
local UI = loadstring(game:HttpGet("https://raw.githubusercontent.com/ZeroHubX2/TEST1/refs/heads/main/Test%2011"))()
```

> 📜 **ผลงานต้นฉบับของทีม Zero Hub** ลิขสิทธิ์เป็นของ Zero Hub แจกภายใต้ [MIT License](LICENSE) ใช้ฟรี แก้ได้ แจกต่อได้ แต่ห้ามลบลิขสิทธิ์หรืออ้างว่าเป็นของตัวเอง ดูรายละเอียดที่ [ไลเซนส์และเครดิต](#-ไลเซนส์และเครดิต)

---

## ✨ มีอะไรในกล่อง

- 👋 **หน้าทักทายตอนรัน:** รูปโปรไฟล์ คำทักทายตามเวลา ชื่อผู้เล่นพิมพ์ทีละตัว ชื่อฮับ ชื่อแมพ และแถบโหลด แตะเพื่อข้ามได้
- 📖 **เปิด/ปิดแบบหนังสือ:** ปกสีดำมีโลโก้ พลิกเปิดจากสันซ้าย และพลิกปิดกลับ พร้อมเสียง
- 🎨 **7 ธีม:** Crimson, Midnight, Neon Cyber, Gold Royal, Sakura, Toxic และ Mono เปลี่ยนแล้วสีทั้ง UI ไหลเปลี่ยน และจำไว้ใช้ครั้งหน้า
- 🧭 **แถบหมวดด้านบน:** กรอบสีเลื่อนตามแบบสปริง มีแสงวาบวิ่งผ่าน ถ้าหมวดน้อยปุ่มจะขยายเต็มแถบ ถ้าเยอะลากเลื่อนได้และมีลูกศร
- 🔎 **ค้นหาทุกหมวด:** ปุ่มแว่นขยายท้ายแถบหมวด (หรือ Ctrl+F) หาได้ทุกการตั้งค่า มีปุ่มกระโดดไปแต่ละหมวด และบอกค่าปัจจุบันของแต่ละอัน
- 🧱 **2 ฝั่ง:** การ์ดเรียงซ้าย-ขวา จอแคบเหลือคอลัมน์เดียว หน้าต่างย่อพอดีจอเสมอ
- ❔ **ปุ่ม ? คำอธิบาย:** ซ่อนคำอธิบายไว้หลังไอคอน ? ข้างชื่อ PC เอาเมาส์ชี้ มือถือแตะ
- 🎚️ **ตัวควบคุมครบ:** Toggle, Slider, Dropdown, Segment, Input, Color Picker, Keybind และปุ่ม
- 🎮 **การ์ดสำเร็จรูป:** การ์ดแมพ, ตัวเลขสด, สรุปการรัน, สถิติ, กราฟ, ปุ่มลัด, เลือกธีม และจัดการโปรไฟล์
- 📲 **แจ้งเตือนสไตล์ iPhone:** เด้งขึ้นจากมุมขวาล่าง จัดกลุ่มตามหมวด ซ้อนเป็นกอง แตะหรือปัดเพื่อปิด
- 📱 **Mini mode:** ย่อหน้าต่างเหลือแถบเล็กที่มีแค่สวิตช์สำคัญ
- 🔊 **เสียง UI:** เสียงป๊อปฟองสบู่ปรับ pitch ต่างกันในแต่ละการกระทำ
- 🌈 **เอฟเฟกต์:** แสงออโรร่า จุดแสงลอย แสงวิ่งรอบขอบ แสงตามเมาส์บนการ์ด ripple ตอนกด ปิดทั้งหมดได้ด้วยคำสั่งเดียว
- 💾 **Config ในตัว:** บันทึก/โหลดทุกตัวเลือกเป็น JSON มีบันทึกอัตโนมัติและหลายโปรไฟล์

---

## 🚀 เริ่มใน 30 วินาที

```lua
local UI = loadstring(game:HttpGet("https://raw.githubusercontent.com/ZeroHubX2/TEST1/refs/heads/main/Test%2011"))()

local Window = UI:CreateWindow({ Title = "Zero Hub", SubTitle = "My Game", ConfigFolder = "Zero Hub/My Game" })
local Main = Window:AddTab({ Title = "Main", Icon = "home", Description = "Everything you need" })

Main:AddSection("Farm")
Main:AddToggle("AutoFarm", { Title = "Auto Farm", Default = false })

task.spawn(function()
    while not UI.Unloaded do
        if UI.Options.AutoFarm.Value then
            print("farming...")
        end
        task.wait(1)
    end
end)
```

> ไฟล์ไลบรารีรันเดี่ยวๆ จะไม่มีอะไรขึ้น หน้าต่างจะขึ้นเมื่อสคริปต์เรียก `CreateWindow` และ `AddTab`

---

## 🧱 UI ประกอบกันยังไง

```
Window                 หน้าต่างหลัก
 ├─ Tab                หมวดในแถบด้านบน
 │   ├─ Section        การ์ด 1 ใบ (มีไอคอนกับหัวข้อ)
 │   │   ├─ Toggle     แถวในการ์ด
 │   │   ├─ Slider
 │   │   └─ ...
 │   └─ Section        การ์ดใบถัดไป
 └─ Tab
```

- ทุกแถวจะถูกใส่ลงในการ์ดใบล่าสุดของหมวดนั้น
- อยากขึ้นการ์ดใหม่ ให้เรียก `Tab:AddSection("ชื่อ")`
- ถ้าเพิ่มแถวก่อนจะมี Section จะได้การ์ดที่ไม่มีหัวข้อ

---

## 🪟 สร้างหน้าต่าง

```lua
local Window = UI:CreateWindow({
    Title = "Zero Hub",
    SubTitle = "Anime Zero",
    SubCaption = "NOW FARMING",
    Wordmark = "rbxassetid://105303733304739",
    WordmarkHeight = 40,
    Logo = "rbxassetid://132023049848714",
    Credit = "Made by Zero Hub",
    ToggleKey = Enum.KeyCode.RightControl,
    ConfigFolder = "Zero Hub/Anime Zero",
    CloseNote = "Auto farm stops and the window closes.",
})
```

| key | ค่าเริ่มต้น | ใช้ทำอะไร |
| --- | --- | --- |
| `Title` | `"Zero Hub"` | ชื่อฮับ ใช้ในแจ้งเตือน หน้าทักทาย ปกหนังสือ และมุมขวาล่าง |
| `SubTitle` | `""` | ชื่อแมพ โชว์บนหัวหน้าต่าง หน้าทักทาย และปกหนังสือ |
| `SubCaption` | `"NOW FARMING"` | ข้อความเล็กสีหลักเหนือชื่อแมพ |
| `Wordmark` | โลโก้ ZERO HUB | รูปชื่อฮับ (พื้นโปร่งใส) ไม่ใส่ก็ได้โลโก้ ZERO HUB ให้เอง ใส่ `false` เพื่อใช้ตัวหนังสือ `Title` แทน มีแสงวิ่งผ่านเองทุก 3 วินาที |
| `WordmarkHeight` / `WordmarkAspect` | `40` / `3` | ความสูงของรูป และสัดส่วนกว้าง÷สูง ใช้คำนวณความกว้าง |
| `Logo` / `LogoText` | โลโก้ Zero Hub | รูปบนปุ่มลอยซ่อน/แสดง และตัวอักษรแทนถ้ารูปโหลดไม่ขึ้น |
| `Credit` | `"Made by <Title>"` | ข้อความบนปกหนังสือ |
| `Footer` | `Title` | ข้อความมุมขวาล่างของหน้าต่าง |
| `ToggleKey` | `RightControl` | ปุ่มลัดซ่อน/แสดงบน PC |
| `ConfigFolder` | `"Zero Hub"` | โฟลเดอร์เก็บ config |
| `CloseNote` | - | ข้อความในกล่องยืนยันตอนกดปิด |
| `Welcome` | `true` | หน้าทักทายตอนรันครั้งแรก ใส่ `false` เพื่อปิด |
| `Width` / `Height` | `1000` / `660` | ขนาดเริ่มต้นบน PC มือถือจะใช้เกือบเต็มจอเอง |

**ปุ่มบนหัวหน้าต่าง (ขวาบน):** Mini mode · บันทึก config · จุดเทาซ่อนหน้าต่าง · จุดสีปิด UI (ถามยืนยันก่อน)

### ใช้ Window ทำอะไรได้บ้าง

```lua
Window:AddSection("Automation")
local Home = Window:AddTab({ Title = "Home", Icon = "home", Description = "Ready to farm", Greeting = true })
local Farm = Window:AddTab({ Title = "Farm", Icon = "swords", Description = "Targeting and movement" })
Window:SetProfile("Playing Naruto")
```

- `Window:AddSection(name)`: เส้นคั่นกลุ่มในแถบหมวด ตัวที่เรียกก่อนหมวดแรกจะไม่แสดงอะไร
- `Window:AddTab(cfg)`: สร้างหมวด ใส่ `Title`, `Icon`, `Description` ถ้าใส่ `Greeting = true` หัวหน้าจะเป็นคำทักทาย เช่น "Good evening, ชื่อผู้เล่น"
- `Window:SetProfile(text)`: ข้อความต่อท้ายชื่อผู้เล่นที่มุมซ้ายล่าง
- `Window.Minimized`: เป็น `true` ตอนหน้าต่างถูกซ่อน

---

## 🧩 ชิ้นส่วนในการ์ด

ทุกชิ้นที่มี `Description` จะซ่อนคำอธิบายไว้หลังไอคอน ? ข้างชื่อ

### 🔘 Toggle: สวิตช์เปิด/ปิด

```lua
Farm:AddToggle("AutoFarm", {
    Title = "Auto Farm",
    Description = "Clears every wave for you",
    Default = false,
    Pin = true,
    Callback = function(on) end,
})
```

- `Pin = true`: ให้สวิตช์นี้ไปโผล่ในแถบ Mini mode

### 🎚️ Slider: แถบเลื่อนตัวเลข

```lua
Farm:AddSlider("Distance", {
    Title = "Distance (studs)",
    Description = "Gap between you and the target",
    Min = 0, Max = 30, Default = 8, Rounding = 0,
    Callback = function(v) end,
})
```

- ใส่หน่วยในวงเล็บท้ายชื่อ เช่น `(studs)` จะโชว์เป็น `8 studs` และในป้ายตอนลาก
- `Rounding` คือจำนวนทศนิยม ใส่ `1` ได้ทศนิยม 1 ตำแหน่ง
- ปุ่ม `-` `+` เปลี่ยนทีละ 1 (หรือ 0.1 ถ้ามีทศนิยม) กดค้างได้ และแตะตัวเลขเพื่อพิมพ์เองได้

### 📋 Dropdown: เมนูเลือก

```lua
Farm:AddDropdown("Target", { Title = "Target", Values = { "Nearest", "Lowest HP", "Boss First" }, Default = "Nearest" })
Farm:AddDropdown("Skills", { Title = "Skills to use", Values = { "Skill 1", "Skill 2", "Ultimate" }, Multi = true, Default = { "Skill 1" } })
```

- `Default` ใส่เป็นลำดับ (`1`) หรือเป็นค่า (`"Nearest"`) ก็ได้
- `Multi = true`: เลือกได้หลายอัน ค่าที่ได้เป็น `{ ["Skill 1"] = true }` ในเมนูมีปุ่ม All / Clear
- มากกว่า 6 ตัวเลือก จะมีช่องกรอง
- `Options.Target:SetValues({...})`: เปลี่ยนรายการ ถ้าค่าเดิมยังอยู่จะคงไว้ให้
- `Images = { ["Nearest"] = "rbxassetid://..." }`: ใส่รูปหน้าตัวเลือก รูปโชว์ทั้งในเมนูและบนปุ่ม (เฉพาะแบบเลือกอันเดียว) เปลี่ยนทีหลังด้วย `Options.Target:SetImages({...})`

### 🔀 Segment: ปุ่มเลือกแบบแท็บ

```lua
Farm:AddSegment("Mode", { Title = "Target", Values = { "Nearest", "Lowest HP", "Boss" }, Default = 1 })
```

กดง่ายกว่า Dropdown บนมือถือ มีแถบสีเด้งไปตามตัวที่เลือก

### 🎨 Color Picker: เลือกสี

```lua
Visuals:AddColorPicker("EspColor", { Title = "ESP colour", Default = Color3.fromRGB(255, 60, 80) })
```

กดแล้วเปิดกล่องสี มีแถบ Hue และช่องพิมพ์ HEX ค่าที่ได้เป็น `Color3` (บันทึกเป็น `#RRGGBB`)

### ⌨️ Input: ช่องพิมพ์

```lua
Farm:AddInput("StopFloor", { Title = "Floor to stop at", Numeric = true, Min = 1, Max = 1000, Default = 200, Placeholder = "200" })
```

### 🖱️ Button: ปุ่มกด

```lua
local Btn = Farm:AddButton({ Title = "Teleport to spawn", Description = "Go back to where you started", ButtonText = "Go", Callback = function() end })
Btn:SetDesc("Done!")
```

### 📝 Paragraph: ข้อความ

```lua
local Status = Farm:AddParagraph({ Title = "Status", Content = "Idle" })
Status:SetDesc("Fighting 5 enemies")
```

### ⌨️ Keybind: ตั้งปุ่มลัดซ่อน/แสดง

```lua
Settings:AddKeybind({ Title = "Show / hide key", Default = Enum.KeyCode.RightControl })
```

---

## 🎮 การ์ดสำเร็จรูป

### Stat Tiles: ตัวเลขสด 4 ช่อง

```lua
Home:AddStatTiles()
```

- Playtime (`00:12:34.5`), Players, FPS และ Ping อัปเดตทุก 0.1 วินาที ตัวเลขวิ่งไหลไปหาค่าใหม่
- FPS นับจากเฟรมจริงใน 1 วินาทีล่าสุด Ping อ่านจาก Data Ping ของ Roblox
- ทำเองก็ได้: `Home:AddStatTiles({ Auto = false, Items = { { "kills", "Kills", "target" } } })` แล้ว `:Set("kills", 12)`

### Map: การ์ดแมพ

```lua
local Map = Home:AddGameCard({
    Buttons = {
        { Title = "Rejoin", Callback = rejoin },
        { Title = "Server Hop", Callback = hop },
        { Title = "Leave Game", Callback = leave, Danger = true },
    },
})
```

- แบนเนอร์รูปปกเกมจริงไล่จางไปทางซ้าย มีชื่อเกม ผู้สร้าง และแถว `SRV … / PlaceId` แตะเพื่อคัดลอก Job ID
- มิเตอร์ PLAYERS / PING / UPTIME อัปเดตเอง
- ปุ่มมีไอคอนตามชื่อ ปุ่ม `Danger = true` ต้องกดค้างเพื่อยืนยัน

### Hero, Stats, Graph, Actions

```lua
local Hero = Home:AddHero({ Title = "Current run" })
Hero:Set({ main = "Wave 4", sub = "Shibuya", badge = "ACTIVE", badgeColor = UI.Colors.Good })
Hero:SetBar(1, "Health", 82, UI.Colors.Good)

local Stats = Home:AddStats({ { "fps", "Framerate" } })
Stats:Set("fps", 60, "Smooth", UI.Colors.Good)

local Graph = Home:AddGraph({ Title = "Frame rate", Points = 40, Max = 60 })
Graph:Push(UI.FPS, UI.FPS .. " FPS")

Home:AddSection("Quick actions")
Home:AddActions({
    { Title = "Auto Farm", Bind = "AutoFarm", OnText = "On - farming", OffText = "Off" },
    { Title = "Retry", Description = "On the end screen", ButtonText = "Go", Callback = retry },
})
```

`Bind` ทำให้แถวนั้นเป็นสวิตช์ที่ผูกกับ Toggle id นั้น ถ้าไม่ใส่จะเป็นปุ่ม

### Themes: การ์ดเลือกธีม

```lua
Settings:AddThemePicker()
```

### Profiles: จัดการหลายชุดตั้งค่า

```lua
Settings:AddConfigManager()
```

ตั้งชื่อ บันทึก โหลด และลบโปรไฟล์ได้ (ต้องมี `listfiles` / `delfile` ใน executor)

---

## 🎛️ คุม UI จากโค้ด

**หน้าต่าง**
- `UI:ToggleUI()`: ซ่อน/แสดงหน้าต่าง (เล่นอนิเมชันหนังสือ)
- `UI:SetMini(true)`: เข้า Mini mode
- `UI:Destroy()`: ปิด UI ทั้งหมด ตัดทุก connection
- `UI.Unloaded`: เป็น `true` หลังปิด UI
- `UI.OnDestroy = function() end`: ทำงานหลัง UI ถูกปิด

**ธีมและหน้าตา**
- `UI:SetTheme("Midnight")`: เปลี่ยนธีม ดูรายชื่อที่ `UI.ThemeOrder`
- `UI:SetAccent("Red")`: เปลี่ยนเฉพาะสีหลัก ดูรายชื่อที่ `UI.AccentNames`
- `UI:SetEffects(false)`: ปิดอนิเมชันและเอฟเฟกต์ทั้งหมดเพื่อเพิ่ม FPS

**เสียง**

เสียงเปิดอยู่ตั้งแต่เริ่ม ใช้เสียงป๊อปฟองสบู่ตัวเดียว (`rbxassetid://6895079853`) ปรับ pitch ให้ต่างกันในแต่ละการกระทำ เล่นผ่าน `PlayLocalSound` จึงได้ยินแค่เราคนเดียว

| ชื่อเสียง | ดังตอนไหน |
| --- | --- |
| `click` | กดปุ่มต่างๆ กดปุ่มในการ์ด Map เข้า/ออก Mini mode |
| `tab` | สลับหมวด |
| `on` / `off` | เปิด/ปิด Toggle (รวมสวิตช์ใน Mini mode) และติ๊กตัวเลือกใน Dropdown แบบ Multi |
| `tick` | ลาก Slider (ดังเบาๆ ทุกครั้งที่ค่าเปลี่ยน) |
| `open` | เปิด Dropdown, Color Picker, ค้นหา |
| `select` | เลือกตัวเลือกใน Dropdown, Segment, ธีม, ผลค้นหา |
| `copy` | แตะแถว SRV เพื่อคัดลอก Job ID |
| `alert` | กล่องถามยืนยัน และตอนกดค้างปุ่ม Danger จนครบ |
| `notify` + `notify2` | แจ้งเตือนเด้งขึ้น และตอนหน้าทักทายขึ้น (ดัง 2 จังหวะ) |
| `uiOpen` + `uiOpen2` | เปิดหน้าต่าง (พลิกหนังสือเปิด) และตอนออกจากหน้าทักทาย |
| `uiClose` + `uiClose2` | ปิด/ซ่อนหน้าต่าง (พลิกหนังสือปิด) |
| `whoosh` | เสียงลมตอนปกหนังสือพลิก |

- `UI:SetSounds(false)`: ปิดเสียง UI ทั้งหมด (`true` เปิดกลับ)
- `UI:SetVolume(0.5)`: ความดัง 0 ถึง 2 ค่าเริ่มต้น `0.5`
- `UI:PlaySound("click")`: เล่นเสียงเองจากชื่อในตาราง ใส่ความดังเพิ่มได้ `UI:PlaySound("notify", 0.8)`
- `UI.SoundOn` / `UI.Volume`: อ่านค่าปัจจุบัน
- เสียงเดียวกันจะไม่ดังซ้ำถี่กว่า 0.05 วินาที กันเสียงรัวตอนลาก Slider

```lua
Settings:AddToggle("UISound", { Title = "UI sounds", Default = true, Callback = function(on) UI:SetSounds(on) end })
Settings:AddSlider("UIVolume", { Title = "Volume", Min = 0, Max = 2, Default = 0.5, Rounding = 1, Callback = function(v) UI:SetVolume(v) end })
```

**แจ้งเตือนและถามยืนยัน**

```lua
UI:Notify({ Title = "Saved", Content = "Config saved", Duration = 3, Icon = "save", Group = "System" })

UI:Confirm({
    Title = "Leave the game?",
    Content = "Roblox closes right away.",
    Button = "Leave",
    Callback = function() game:Shutdown() end,
})
```

- แจ้งเตือนจัดกลุ่มตาม `Group` ถ้าไม่ใส่จะใช้ชื่อหมวดที่เปิดอยู่ ใส่ `Color` เปลี่ยนสีไอคอนได้

**Config**
- `UI:SaveConfig("config")` / `UI:LoadConfig("config")`: บันทึก/โหลดทุกตัวเลือก
- `UI:ReadConfig("config")` / `UI:ApplyConfig(data)`: อ่านเป็น table / ใส่ค่าจาก table
- `UI.AutoSave = true`: บันทึกเองหลังค่าเปลี่ยน 1 วินาที
- ไฟล์อยู่ที่ `ConfigFolder/config.json` เก็บทั้งค่าตัวเลือก ธีม สีหลัก ขนาดและตำแหน่งหน้าต่าง และตำแหน่งปุ่มลอย
- **ธีมกับหน้าทักทาย:** ตอนรันครั้งใหม่ ธีมที่บันทึกไว้จะถูกใช้ก่อนสร้างทุกอย่าง หน้าทักทายและปกหนังสือจึงขึ้นมาเป็นสีธีมนั้นเลย (ต้องบันทึกหลังเปลี่ยนธีม: เปิด `AutoSave` หรือกดปุ่มบันทึก และใช้ `ConfigFolder` เดิม)

**ค่าที่อ่านได้**
- `UI.FPS`, `UI.Ping`: อัปเดตทุก 0.1 วินาที
- `UI.StartedAt`: เวลาที่เริ่มรัน เทียบกับ `os.clock()`
- `UI.Colors`: สีของธีมปัจจุบัน เช่น `Text`, `Sub`, `Dim`, `Good`, `Warn`, `Bad`
- `UI.Conns`: ใส่ connection ของคุณ แล้วจะถูกตัดตอน `Destroy`
- `UI.Version`: เวอร์ชันไลบรารี (เห็นที่มุมขวาบนของปกหนังสือ และใน console)
- `UI.Author`, `UI.Copyright`, `UI.Source`: เจ้าของ ข้อความลิขสิทธิ์ และลิงก์ต้นทางของไลบรารี

---

## 📦 Options

ทุก Toggle, Slider, Input, Dropdown, Segment และ Color Picker ที่ใส่ id จะอยู่ใน `UI.Options`

```lua
local Opt = UI.Options.AutoFarm
print(Opt.Value)
Opt:SetValue(true)
Opt:OnChanged(function(v) print("now", v) end)
Opt.NoSave = true
```

- `Value`: ค่าปัจจุบัน
- `SetValue(v)`: ตั้งค่าจากโค้ด Callback จะทำงานด้วย
- `OnChanged(fn)`: ทำงานทุกครั้งที่ค่าเปลี่ยน
- `NoSave = true`: ไม่บันทึกค่านี้
- `Values`, `SetValues(list)`: รายการตัวเลือกของ Dropdown

---

## 🎨 ไอคอน

ใส่ชื่อไอคอนใน `Icon` ของ Tab, Notify หรือปุ่มในการ์ด Map

`home` · `swords` · `crosshair` · `shield` · `flag` · `play` · `list-checks` · `scroll` · `settings` · `user` · `git-branch` · `roll` · `evolution` · `bolt` · `flame` · `target` · `cart` · `gift` · `upgrade` · `tag` · `bag` · `cursor` · `run` · `cpu` · `people` · `clock` · `timer` · `trophy` · `palette` · `chart` · `info` · `sparkles` · `gamepad` · `refresh` · `shuffle` · `exit` · `copy` · `bars` · `power` · `warn` · `help` · `folder` · `save` · `search` · `check`

ไอคอนบนการ์ดจะถูกเลือกให้เองจากชื่อ Section เช่น `Timing` ได้นาฬิกาจับเวลา, `Movement` ได้คนวิ่ง

---

## 💡 ทริค

**หยุด loop ตอนปิด UI**

```lua
task.spawn(function()
    while not UI.Unloaded do
        task.wait(0.5)
    end
end)
```

**โหลด config ตอนเปิดสคริปต์**

```lua
UI.AutoSave = true
UI:LoadConfig("config")
```

**อัปเดตรายการ Dropdown ตามของในเกม**

```lua
local names = {}
for _, p in ipairs(game.Players:GetPlayers()) do names[#names + 1] = p.Name end
UI.Options.Target:SetValues(names)
```

---

## ❓ เจอปัญหา

- **รันแล้วไม่มีอะไรขึ้น:** ไลบรารีไม่สร้างหน้าต่างเอง ต้องเรียก `UI:CreateWindow({...})` แล้วตามด้วย `Window:AddTab({...})` อย่างน้อย 1 หมวด ดูตัวอย่างที่หัวข้อ [เริ่มใน 30 วินาที](#-เริ่มใน-30-วินาที)
- **ขึ้น error `attempt to call a nil value` ตรง loadstring:** executor โหลดลิงก์ไม่ได้ ลองเช็กว่าก๊อปลิงก์มาครบ (ต้องลงท้ายด้วย `Test%2011`) และ executor รองรับ `game:HttpGet`
- **ดู console ว่าโหลดสำเร็จไหม:** ถ้าโหลดได้จะขึ้น `[ZeroHub UI] v... loaded` ถ้าไม่ขึ้นแปลว่ายังโหลดไลบรารีไม่สำเร็จ
- **รันสคริปต์ซ้ำ:** ไม่ต้องปิดของเดิมเอง ทุกครั้งที่โหลดไลบรารีใหม่ UI ตัวเก่าจะถูกปิดให้อัตโนมัติ แต่ลูปของสคริปต์เก่าต้องหยุดเองด้วย `UI.Unloaded` (ดูข้อ "ลูปยังทำงานหลังปิด UI" ด้านล่าง)
- **ค่าที่ตั้งไว้ไม่จำ:** เปิด `UI.AutoSave = true` หรือกดปุ่มบันทึกบนหัวหน้าต่าง แล้วเรียก `UI:LoadConfig("config")` ตอนเริ่มสคริปต์ ต้องใช้ `ConfigFolder` เดิมทุกครั้ง และ executor ต้องรองรับ `writefile` / `readfile`
- **ลูปยังทำงานหลังปิด UI:** ให้ลูปเช็ก `while not UI.Unloaded do` ตามหัวข้อ [ทริค](#-ทริค)
- **รูปโลโก้ไม่ขึ้น ขึ้นเป็นตัวหนังสือแทน:** รูปโหลดไม่สำเร็จภายใน 8 วินาที UI จึงใช้ตัวหนังสือ `Title` แทน เช็กว่า asset id ถูกและเป็นรูปที่เปิดสาธารณะ
- **ไม่มีเสียง:** เช็กว่าไม่ได้สั่ง `UI:SetSounds(false)` และเสียงในเกมไม่ได้ปิดอยู่
- **มือถือกระตุก:** ปิดเอฟเฟกต์ด้วย `UI:SetEffects(false)`
- **หน้าต่างเล็กหรือใหญ่ผิดปกติ:** ลากมุมขวาล่างเพื่อปรับ หรือลบไฟล์ `config.json` ในโฟลเดอร์ `ConfigFolder`

---

## 📜 ไลเซนส์และเครดิต

**ZeroHub UI เป็นผลงานต้นฉบับของทีม Zero Hub** ออกแบบและเขียนขึ้นเองทั้งหมด ลิขสิทธิ์เป็นของ Zero Hub แต่เพียงผู้เดียว (`Copyright (c) 2026 Zero Hub`) และเปิดให้ใช้ภายใต้ [MIT License](LICENSE)

**หลักฐานความเป็นเจ้าของ**
- ลิขสิทธิ์ฝังอยู่ในตัวไลบรารี: `UI.Author`, `UI.Copyright`, `UI.Source`
- ทุกครั้งที่โหลด console จะขึ้นข้อความนี้

```
[ZeroHub UI] v5.0 loaded
[ZeroHub UI] ZeroHub UI - Copyright (c) 2026 Zero Hub. Original work by Zero Hub. MIT License. https://github.com/ZeroHubX2/TEST1
```

- ประวัติ commit บน GitHub ยืนยันว่าทีม Zero Hub เผยแพร่ก่อน

**ใช้ได้**
- ✅ ใช้ฟรี ทั้งสคริปต์แจกฟรีและสคริปต์ขาย
- ✅ แก้ไข ดัดแปลง และแจกต่อได้

**เงื่อนไขที่ต้องทำตาม**
- 📌 ห้ามลบ `Copyright (c) 2026 Zero Hub` และเนื้อหา MIT License ออกจากโค้ดที่ก๊อปหรือแจกต่อ รวมถึง `Lib.Copyright` ในตัวไลบรารี
- 📌 ห้ามอ้างว่าเป็นผู้สร้าง ZeroHub UI การลบลิขสิทธิ์แล้วแจกหรือขายเป็นของตัวเองถือว่าละเมิดลิขสิทธิ์ ทีมจะแจ้งลบ (DMCA) และรีพอร์ตทุกช่องทาง
- ⚠️ ให้ใช้ตามสภาพที่เป็น ทีม Zero Hub ไม่รับผิดชอบความเสียหายที่เกิดจากการใช้

**ขอความร่วมมือ**

ถ้า UI นี้มีประโยชน์ ช่วยใส่เครดิต `UI by Zero Hub` ไว้ในที่ที่ผู้เล่นเห็น เช่น ใน `Credit` ของ `CreateWindow`, หมวด About หรือโพสต์ที่แจกสคริปต์

```lua
local Window = UI:CreateWindow({
    Title = "My Hub",
    SubTitle = "My Game",
    Credit = "UI by Zero Hub",
})

local About = Window:AddTab({ Title = "About", Icon = "info" })
About:AddParagraph({ Title = "Credits", Content = UI.Copyright })
```

---

Made with ⚡ by **Zero Hub**
