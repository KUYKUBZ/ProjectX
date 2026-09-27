docs
https://footagesus.github.io/WindUI-Docs/

# SET UP
```lua
local Link = "https://raw.githubusercontent.com/KUYKUBZ/ProjectX/refs/heads/main/WindCustom/WindUI.luau"
local bytes = {}
for i = 1, #Link do
    table.insert(bytes, string.byte(Link, i))
end
print("{" .. table.concat(bytes, ", ") .. "}")
```
```lua
local function decodeUrl(bytes)
    local str = ""
    for i = 1, #bytes do
        str = str .. string.char(bytes[i])
    end
    return str
end
local bytes = decodeUrl({104, 116, 116, 112, 115, 58, 47, 47, 114, 97, 119, 46, 103, 105, 116, 104, 117, 98, 117, 115, 101, 114, 99, 111, 110, 116, 101, 110, 116, 46, 99, 111, 109, 47, 75, 85, 89, 75, 85, 66, 90, 47, 80, 114, 111, 106, 101, 99, 116, 88, 47, 114, 101, 102, 115, 47, 104, 101, 97, 100, 115, 47, 109, 97, 105, 110, 47, 87, 105, 110, 100, 67, 117, 115, 116, 111, 109, 47, 87, 105, 110, 100, 85, 73, 46, 108, 117, 97, 117})
local WindUI = loadstring(game:HttpGet(bytes))()
```
---
# CREATE WINDOW
```lua
local Window = WindUI:CreateWindow({
    Title = "ProtonUI",
    Author = "T0X1C",
    Folder = "ProtonDocs",
    Size = UDim2.fromOffset(620, 500),
    Icon = "sparkles",
    ModernLayout = true,
    BottomDragBarEnabled = true
})
```
# WINDOW WITH MACOS BUTTON + SIZE

```lua
local Window = WindUI:CreateWindow({
    Title = "Araiwa",
    Author = "gamename",
    Icon = "sparkles",
    Folder = "Araiwa",
    NewElements = true,
    Topbar = {
        Height = 44,
        ButtonsType = "Mac",
    },
    Size = UDim2.fromOffset(500, 230),
    MinSize = Vector2.new(500, 230),
    MaxSize = Vector2.new(850, 560),
    ModernLayout = false,
    BottomDragBarEnabled = false
})
```

---
## Multi Section

`MultiSection` is an expandable container with tabbed inner content.

### Create

```lua
local Multi = MainTab:MultiSection({
    Title = "Combat Modes",
    Desc = "Switch between profiles",
    Icon = "crosshair",
    Box = true,
    BoxBorder = true,
    Opened = true,
})
```

### Config

| Key | Type | Default | Notes |
| --- | --- | --- | --- |
| `Title` | `string` | `"Section"` | Header title |
| `Desc` | `string?` | `nil` | Header description |
| `Icon` | `string?` | `nil` | Header icon |
| `TextXAlignment` | `"Left" \| "Center" \| "Right"` | `"Left"` | Header text alignment |
| `TextSize` | `number` | `19` | Header title text size |
| `DescTextSize` | `number` | `16` | Header description text size |
| `Box` | `boolean` | `false` | Enables boxed background |
| `BoxBorder` | `boolean` | `false` | Shows outline when `Box=true` |
| `FontWeight` | `Enum.FontWeight` | `SemiBold` | Header title weight |
| `DescFontWeight` | `Enum.FontWeight` | `Medium` | Header desc weight |
| `TextTransparency` | `number` | `0.05` | Header title transparency |
| `DescTextTransparency` | `number` | `0.4` | Header desc transparency |
| `Hover` | `boolean` | `true` | Hover/press feedback |
| `Opened` | `boolean` | `false` | Starts opened |
| `Locked` | `boolean` | `false` | Starts locked |
| `LockedTitle` | `string?` | `nil` | Stored; no built-in label in this container |
| `HeaderSize` | `number` | `42` | Header base size |
| `IconSize` | `number` | `20` | Header icon size |
| `HeaderGap` | `number` | `10` | Horizontal spacing in header |
| `HeaderPaddingX` | `number` | dynamic | Horizontal header padding |
| `HeaderPaddingY` | `number` | dynamic | Vertical header padding |
| `TabGap` | `number` | `6` | Gap between tab chips |
| `TabPaddingX` | `number` | `12` | Tab chip horizontal padding |
| `TabPaddingY` | `number` | `8` | Tab chip vertical padding |
| `TabTextSize` | `number` | `15` | Tab title size |
| `TabDescTextSize` | `number` | `13` | Tab desc size |

### Multi Section Methods

| Method | Signature | Description |
| --- | --- | --- |
| `SetIcon` | `Multi:SetIcon(iconOrNil)` | Updates/removes header icon |
| `SetTitle` | `Multi:SetTitle(title)` | Updates header title |
| `SetDesc` | `Multi:SetDesc(descOrNil)` | Updates/removes description |
| `Lock` | `Multi:Lock()` | Locks header interaction and tab elements |
| `Unlock` | `Multi:Unlock()` | Unlocks interaction and tab elements |
| `SelectTab` | `Multi:SelectTab(tabValue, isInstant)` | Selects tab by object, index, or title |
| `GetSelectedTab` | `Multi:GetSelectedTab()` | Returns selected tab object |
| `GetTabs` | `Multi:GetTabs()` | Returns all tab objects |
| `Tab` | `Multi:Tab(tabConfig)` | Creates a tab inside this multi section |
| `Open` | `Multi:Open(isNotAnim)` | Opens content area |
| `Close` | `Multi:Close(isNotAnim)` | Closes content area |
| `Destroy` | `Multi:Destroy()` | Destroys container and all tab content |

### Tab Config (`Multi:Tab({...})`)

| Key | Type | Default | Notes |
| --- | --- | --- | --- |
| `Title` | `string` | `"Tab N"` | Tab title |
| `Desc` | `string?` | `nil` | Tab subtitle |
| `Icon` | `string?` | `nil` | Tab icon |
| `IconThemed` | `boolean?` | `nil` | Uses themed icon coloring |
| `Selected` | `boolean` | `false` | Select immediately |
| `Opened` | `boolean` | `false` | Alias for immediate select |

### Multi Section Tab Methods

| Method | Signature | Description |
| --- | --- | --- |
| `Select` | `Tab:Select(isInstant)` | Selects this tab |
| `Destroy` | `Tab:Destroy()` | Removes this tab and its elements |

Each tab also receives element constructors:
`Paragraph`, `Button`, `ButtonKeybind`, `Toggle`, `ToggleKeybind`, `Slider`, `Keybind`, `Input`, `Dropdown`, `Code`, `Colorpicker`, `Section`, `MultiSection`, `Divider`, `Space`, `Image`, `Group`, `Video`.

### Full Example (All Multi Section Methods)

```lua
local Multi = MainTab:MultiSection({
    Title = "Combat Modes",
    Desc = "Select your profile",
    Icon = "crosshair",
    Box = true,
    BoxBorder = true,
    Opened = true,
})

local Rage = Multi:Tab({
    Title = "Rage",
    Desc = "Aggressive settings",
    Icon = "flame",
    Selected = true,
})

local Legit = Multi:Tab({
    Title = "Legit",
    Desc = "Low profile settings",
    Icon = "shield-check",
})

Rage:Toggle({
    Title = "Silent Aim",
    Value = false,
})

Legit:Slider({
    Title = "FOV",
    Value = { Min = 10, Max = 250, Default = 80 },
})

Multi:SetIcon("swords")
Multi:SetTitle("Profiles")
Multi:SetDesc("Switch behavior quickly")

Multi:SelectTab("Legit", true)
Multi:SelectTab(1, false)
Multi:SelectTab(Rage)

local selected = Multi:GetSelectedTab()
print("Selected tab:", selected and selected.Title)

local allTabs = Multi:GetTabs()
print("Tab count:", #allTabs)

local temp = Multi:Tab({ Title = "Temporary" })
temp:Select(true)
temp:Destroy()

Multi:Open(true)
Multi:Close(false)
Multi:Lock()
Multi:Unlock()
```

## Divider

`Divider` creates horizontal or vertical separators, with optional title support for horizontal mode.

### Create

```lua
local Divider = MainTab:Divider({
    Title = "Combat Settings",
    TitleAlignment = "Center",
})
```

### Config

| Key | Type | Default | Notes |
| --- | --- | --- | --- |
| `Orientation` | `"Horizontal" \| "Vertical"` | dynamic | Defaults to `Vertical` in groups, otherwise `Horizontal` |
| `Title` / `Text` | `string` | `""` | Horizontal title |
| `Thickness` | `number` | `1` | Minimum `1` |
| `Inset` | `number` | `7` | Frame inset |
| `TitleSpacing` | `number` | `8` | Space around title |
| `TitleAlignment` | `"Left" \| "Center" \| "Right"` | `"Center"` | Title side/alignment |
| `Height` | `number` | auto | Horizontal frame height |
| `Width` | `number` | auto | Vertical frame width |
| `Size` | `UDim2` | auto | Overrides default size |
| `Color` | `string \| Color3` | theme `"Divider"` | Divider line color |
| `Transparency` | `number` | theme | Divider line transparency |
| `TitleColor` | `string \| Color3` | theme `"DividerLabel"` | Title color |
| `TitleTransparency` | `number` | theme | Title transparency |
| `TitleSize` | `number` | `13` | Title text size |

### Methods

| Method | Signature | Description |
| --- | --- | --- |
| `SetTitle` | `Divider:SetTitle(newTitle)` | Updates title text |
| `SetThickness` | `Divider:SetThickness(px)` | Updates line thickness |
| `SetTitleAlignment` | `Divider:SetTitleAlignment("Left" \| "Center" \| "Right")` | Updates title alignment |
| `SetTitleSpacing` | `Divider:SetTitleSpacing(px)` | Updates title spacing |

### Full Example (All Divider Methods)

```lua
local Divider = MainTab:Divider({
    Title = "Aimbot",
    TitleAlignment = "Center",
    Thickness = 1,
    TitleSpacing = 8,
    Color = "Divider",
    TitleColor = "DividerLabel",
})

Divider:SetTitle("Aimbot Controls")
Divider:SetThickness(2)
Divider:SetTitleAlignment("Left")
Divider:SetTitleSpacing(14)
```
