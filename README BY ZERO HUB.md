# ⚡ ZeroX UI

UI สำหรับสคริปต์ Roblox ของทีม ZeroX
แถบหมวดอยู่ด้านบน การ์ดจัดเรียงเองตามขนาดจอ และใช้ได้ทั้งมือถือและ PC

```lua
local UI = loadstring(game:HttpGet("https://raw.githubusercontent.com/ZeroHubX2/TEST1/refs/heads/main/Test%2011"))()
```

---

## ✨ มีอะไรในกล่อง

- 📱 **ปรับตามจอเอง:** การ์ดเรียง 3, 2 หรือ 1 คอลัมน์ตามความกว้าง จอเตี้ยจะย่อส่วนหัวลงให้ หน้าต่างไม่ล้นจอ
- 🧭 **แถบหมวดด้านบน:** มีแคปซูลสีบอกหมวดที่เลือก ลากเลื่อนได้ มีลูกศรตอนหมวดล้นแถบ
- 🎚️ **ตัวควบคุมครบ:** Toggle, Slider (มีปุ่ม `-` `+` และพิมพ์ตัวเลขได้), Dropdown (เลือกได้ทีละอันหรือหลายอัน), Input, Keybind และปุ่ม
- 🎮 **การ์ดสำเร็จรูป:** การ์ดข้อมูลเกม, การ์ดสรุปการรัน, ตัวเลขสถิติ, กราฟ และปุ่มลัด
- 📌 **แถบสถานะลอย:** บอกจำนวนฟังก์ชันที่เปิดอยู่ FPS ping เวลา และเวลาที่รัน ลากย้ายได้
- 💾 **Config ในตัว:** บันทึกและโหลดค่าทุกตัวเลือกเป็น JSON เปิดบันทึกอัตโนมัติได้
- 🌈 **อนิเมชันและเอฟเฟกต์:** แสงวิ่งรอบขอบ จุดแสงลอย ripple ตอนกด และการเปลี่ยนหน้าแบบนุ่มๆ ปิดได้ทั้งหมดด้วยคำสั่งเดียว

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

แค่นี้ก็ได้หน้าต่างที่มีหมวด Main การ์ด Farm และสวิตช์ Auto Farm แล้ว

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
    Logo = "rbxassetid://132023049848714",
    LogoText = "ZH",
    ToggleKey = Enum.KeyCode.RightControl,
    ConfigFolder = "Zero Hub/Anime Zero",
    CloseNote = "Auto farm stops and the window closes.",
})
```

- `Title`: ชื่อฮับ ใช้เป็นหัวแจ้งเตือนและในกล่องยืนยันตอนกดปิด
- `SubTitle`: ข้อความเล็กข้างช่องค้นหา
- `Logo` / `LogoText`: รูปโลโก้ และตัวอักษรที่จะโชว์แทนถ้ารูปโหลดไม่ขึ้น
- `ToggleKey`: ปุ่มลัดซ่อน/แสดงหน้าต่างบน PC
- `ConfigFolder`: โฟลเดอร์ที่เก็บไฟล์ config
- `CloseNote`: ข้อความเตือนตอนกดปุ่ม ✕
- `Width` / `Height`: ขนาดเริ่มต้นบน PC ถ้าไม่ใส่จะเป็น 1000×640 ส่วนมือถือจะใช้เกือบเต็มจอเอง

### ใช้ Window ทำอะไรได้บ้าง

```lua
Window:AddSection("Automation")
local Farm = Window:AddTab({ Title = "Farm", Icon = "swords", Description = "Targeting and movement" })
Window:SetProfile("Playing Naruto")
```

- `Window:AddSection(name)`: ใส่เส้นคั่นกลุ่มในแถบหมวด ตัวที่เรียกก่อนหมวดแรกจะไม่แสดงอะไร
- `Window:AddTab(cfg)`: สร้างหมวดใหม่ ใส่ `Title`, `Icon` และ `Description` ที่จะโชว์ใต้ชื่อหมวด
- `Window:SetProfile(text)`: เปลี่ยนข้อความข้างช่องค้นหา
- `Window.Minimized`: เป็น `true` ตอนหน้าต่างถูกซ่อน

---

## 🧩 ชิ้นส่วนในการ์ด

### 🔘 Toggle: สวิตช์เปิด/ปิด

```lua
Farm:AddToggle("AutoFarm", {
    Title = "Auto Farm",
    Description = "Clears every wave for you",
    Default = false,
    Callback = function(on) end,
})
```

### 🎚️ Slider: แถบเลื่อนตัวเลข

```lua
Farm:AddSlider("Distance", {
    Title = "Distance (studs)",
    Description = "Gap between you and the target",
    Min = 0, Max = 30, Default = 8, Rounding = 0,
    Callback = function(v) end,
})
```

- ใส่หน่วยไว้ในวงเล็บท้ายชื่อ เช่น `(studs)` ช่องตัวเลขจะโชว์เป็น `8 studs`
- `Rounding` คือจำนวนทศนิยม ใส่ `0` ได้จำนวนเต็ม ใส่ `1` ได้ทศนิยม 1 ตำแหน่ง
- ปุ่ม `-` `+` เปลี่ยนค่าทีละ 1 ถ้าตั้ง `Rounding = 1` จะเปลี่ยนทีละ 0.1 กดค้างเพื่อเปลี่ยนต่อเนื่องได้
- แตะที่ช่องตัวเลขเพื่อพิมพ์ค่าเองได้ ถ้าพิมพ์เกินขอบเขต จะถูกบีบให้อยู่ในช่วง `Min`–`Max`

### 📋 Dropdown: เมนูเลือก

```lua
Farm:AddDropdown("Target", {
    Title = "Target",
    Values = { "Nearest", "Lowest HP", "Boss First" },
    Default = "Nearest",
})

Farm:AddDropdown("Skills", {
    Title = "Skills to use",
    Values = { "Skill 1", "Skill 2", "Skill 3", "Ultimate" },
    Multi = true,
    Default = { "Skill 1", "Ultimate" },
})
```

- `Default` ใส่เป็นลำดับ เช่น `1` หรือใส่เป็นค่า เช่น `"Nearest"` ก็ได้
- `Multi = true`: เลือกได้หลายอัน ค่าที่ได้จะเป็น `{ ["Skill 1"] = true, ["Ultimate"] = true }`
- ถ้ามีมากกว่า 8 ตัวเลือก ในเมนูจะมีช่องค้นหาให้
- `Options.Target:SetValues({...})`: เปลี่ยนรายการตัวเลือกใหม่ ถ้าค่าที่เลือกไว้ยังมีอยู่ในรายการใหม่ จะคงไว้ให้

### ⌨️ Input: ช่องพิมพ์

```lua
Farm:AddInput("StopFloor", {
    Title = "Floor to stop at",
    Numeric = true, Min = 1, Max = 1000,
    Default = 200, Placeholder = "200",
})
```

- `Numeric = true`: รับแต่ตัวเลข และบีบค่าให้อยู่ในช่วง `Min`–`Max`

### 🖱️ Button: ปุ่มกด

```lua
local Btn = Farm:AddButton({
    Title = "Teleport to spawn",
    Description = "Go back to where you started",
    ButtonText = "Go",
    Callback = function() end,
})
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

### Game Card: ข้อมูลเกม

ดึงรูปเกม ชื่อเกม ชื่อผู้สร้าง และ ID ให้เอง ใส่ปุ่มได้ตามต้องการ

```lua
local Game = Home:AddGameCard({
    Buttons = {
        { Title = "Rejoin", Callback = rejoin },
        { Title = "Server Hop", Callback = hop },
        { Title = "Leave Game", Callback = leave, Danger = true },
    },
})
Game:Set({ players = "12/22", ping = 56, pingColor = UI.Colors.Good })
```

### Hero: สรุปการรันพร้อมแถบเปอร์เซ็นต์

```lua
local Hero = Home:AddHero({ Title = "Current run" })
Hero:Set({ main = "Wave 4", sub = "Shibuya", badge = "ACTIVE", badgeColor = UI.Colors.Good })
Hero:SetBar(1, "Health", 82, UI.Colors.Good)
Hero:SetBar(2, "Ultimate", 40, UI.Colors.Warn)
```

### Stats และ Graph: ตัวเลขกับกราฟ

```lua
local Stats = Home:AddStats({ { "fps", "Framerate" }, { "ping", "Latency" } })
Stats:Set("fps", 60, "Smooth", UI.Colors.Good)

local Graph = Home:AddGraph({ Title = "Frame rate", Points = 40, Max = 60 })
Graph:Push(UI.FPS, UI.FPS .. " FPS")
```

### Actions: ปุ่มลัด

```lua
Home:AddSection("Quick actions")
Home:AddActions({
    { Title = "Auto Farm", Bind = "AutoFarm", OnText = "On - farming", OffText = "Off" },
    { Title = "Retry", Description = "On the end screen", ButtonText = "Go", Callback = retry },
})
```

- ถ้าใส่ `Bind`: แถวนั้นจะเป็นสวิตช์ที่ผูกกับ Toggle ตัวที่มี id นั้น เปิดที่ไหนอีกฝั่งก็เปิดตาม
- ถ้าไม่ใส่ `Bind`: แถวนั้นจะเป็นปุ่มกด

---

## 🎛️ คุม UI จากโค้ด

**หน้าต่าง**
- `UI:ToggleUI()`: ซ่อนหรือแสดงหน้าต่าง
- `UI:Destroy()`: ปิด UI ทั้งหมดและตัดทุก connection
- `UI.Unloaded`: เป็น `true` หลังปิด UI ใช้เป็นเงื่อนไขหยุด loop
- `UI.OnDestroy = function() end`: ฟังก์ชันที่จะทำงานหลัง UI ถูกปิด

**หน้าตา**
- `UI:SetAccent("Purple")`: เปลี่ยนสีหลัก มี Blue, Sky, Purple, Pink, Red, Orange, Green และ Teal ดูรายชื่อได้ที่ `UI.AccentNames`
- `UI:SetGlass(true)`: พื้นหลังใส มองเห็นเกม ถ้าใส่ `false` จะเป็นพื้นทึบ
- `UI:SetEffects(false)`: ปิดอนิเมชันกับเอฟเฟกต์ทั้งหมดเพื่อเพิ่ม FPS
- `UI:SetStatusBar(false)`: ซ่อนแถบสถานะลอย
- `UI:SetStatusScale(0.8)`: ย่อหรือขยายแถบสถานะ
- `UI.StatusIgnore = { FreeMouse = true }`: กำหนด id ของ Toggle ที่ไม่ต้องนับใน `ACTIVE`

**แจ้งเตือนและถามยืนยัน**

```lua
UI:Notify({ Title = "Saved", Content = "Config saved", Duration = 3 })

UI:Confirm({
    Title = "Leave the game?",
    Content = "Roblox closes right away.",
    Button = "Leave",
    Callback = function() game:Shutdown() end,
})
```

**Config**
- `UI:SaveConfig("config")`: บันทึกค่าทุกตัวเลือกลงไฟล์
- `UI:LoadConfig("config")`: โหลดค่าจากไฟล์แล้วใส่ให้ทุกตัวเลือก
- `UI:ReadConfig("config")`: อ่านไฟล์เป็น table โดยยังไม่ใส่ค่าให้
- `UI:ApplyConfig(data)`: ใส่ค่าจาก table ให้ทุกตัวเลือก
- `UI.AutoSave = true`: บันทึกเองทุกครั้งที่ค่าเปลี่ยน รอ 1 วินาทีก่อนบันทึก
- ไฟล์จะอยู่ที่ `ConfigFolder/config.json` ขนาดและตำแหน่งของหน้าต่าง ปุ่มโลโก้ และแถบสถานะ ถูกบันทึกไปด้วย

**ค่าที่อ่านได้**
- `UI.FPS`, `UI.Ping`: FPS และ ping เป็น ms อัปเดตทุกวินาที
- `UI.StartedAt`: เวลาที่เริ่มรัน เทียบกับ `os.clock()`
- `UI.Colors`: สีของธีม เช่น `Text`, `Sub`, `Dim`, `Good`, `Warn`, `Bad`
- `UI.Conns`: ใส่ connection ของคุณเข้าไป แล้วจะถูกตัดให้อัตโนมัติตอน `Destroy`

---

## 📦 Options

ทุก Toggle, Slider, Input และ Dropdown ที่ใส่ id จะเข้าไปอยู่ใน `UI.Options`

```lua
local Opt = UI.Options.AutoFarm

print(Opt.Value)
Opt:SetValue(true)
Opt:OnChanged(function(v) print("now", v) end)
Opt.NoSave = true
```

- `Value`: ค่าปัจจุบัน
- `SetValue(v)`: ตั้งค่าจากโค้ด และ Callback จะทำงานด้วย
- `OnChanged(fn)`: เพิ่มฟังก์ชันที่ทำงานทุกครั้งที่ค่าเปลี่ยน
- `NoSave = true`: ไม่บันทึกค่านี้ลงไฟล์ config
- `Values`, `SetValues(list)`: รายการตัวเลือกของ Dropdown

---

## 🎨 ไอคอน

ใส่ชื่อไอคอนใน `Icon` ของ Tab

`home` · `swords` · `crosshair` · `shield` · `flag` · `play` · `list-checks` · `scroll` · `settings` · `user` · `git-branch` · `roll` · `evolution` · `bolt` · `flame` · `target` · `cart` · `gift` · `upgrade` · `tag` · `bag` · `cursor` · `run` · `cpu` · `people` · `clock` · `timer` · `trophy` · `palette` · `chart` · `info` · `sparkles`

ส่วนไอคอนบนการ์ด จะถูกเลือกให้เองจากชื่อ Section เช่น ชื่อที่มีคำว่า `Timing` ได้นาฬิกาจับเวลา, `Movement` ได้คนวิ่ง และ `Shop` ได้รถเข็น

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

**ใส่ connection ให้ถูกตัดเองตอนปิด UI**

```lua
table.insert(UI.Conns, game:GetService("RunService").Heartbeat:Connect(function() end))
```

---

## ❓ เจอปัญหา

- **UI ไม่ขึ้นเลย:** ลองเปิดลิงก์ loadstring ในเบราว์เซอร์ ถ้าขึ้น 404 แปลว่าไฟล์บน GitHub ไม่ถูกชื่อหรือไม่อยู่ที่นั้น
- **มือถือกระตุก:** ปิดเอฟเฟกต์ด้วย `UI:SetEffects(false)`
- **หน้าต่างเล็กหรือใหญ่ผิดปกติ:** ขนาดเก่าถูกบันทึกไว้ในไฟล์ config ลากมุมขวาล่างของหน้าต่างเพื่อปรับใหม่ หรือลบไฟล์ `config.json`
- **แถบสถานะหายไป:** มันจะซ่อนเองตอนหน้าต่างหลักบังอยู่ ลองย้ายหน้าต่างลง หรือลากแถบไปไว้ที่อื่น

---

Made with ⚡ by **Zero Hub**
