Zzen.lua

A modern, customizable Roblox UI Library for Luau.

Zzen.lua provides a collection of UI components including Tabs, Sections, Toggles, Sliders, Dropdowns, Inputs, Colorpickers, Keybinds, Checkboxes, Steppers, Accordions, Notifications, Dialogs and more.

---

Features

- Modern Roblox UI
- Multiple built-in themes
- Tabs and Sections
- Toggle
- Slider
- Dropdown
- Multi Dropdown
- Input
- Colorpicker
- Keybind
- Checkbox
- Radio Group
- Number Input
- Action Button
- Button Group
- Quick Actions
- Divider
- Separator
- Status Indicator
- Counter Button
- Stepper
- Toggle Group
- Accordion
- Chip
- Live Label
- Notifications
- Dialogs
- Presets
- Theme management
- Accent color management
- Save/Load configuration support

---

Load

Load Zzen.lua directly from GitHub:

local Zzen = loadstring(game:HttpGet(
    "https://raw.githubusercontent.com/KUYKUBZ/ProjectX/refs/heads/main/Zzen.lua"
))()

---

Basic Structure

The basic structure is:

Zzen
 └── Window
      ├── Tab
      │    ├── Section
      │    │    ├── Toggle
      │    │    ├── Slider
      │    │    ├── Dropdown
      │    │    └── ...
      │    │
      │    └── Elements
      │
      └── Tab

The normal flow is:

Load Library
      ↓
Create Window
      ↓
Create Tab
      ↓
Create Section
      ↓
Create Element

---

Create Window

local Window = Zzen:CreateWindow({
    Title = "My Script",
    SubTitle = "Zzen Example",

    Size = UDim2.fromOffset(600, 450),

    Theme = "Dark"
})

Window Options

Common options include:

local Window = Zzen:CreateWindow({
    Title = "My Script",
    SubTitle = "Example",

    Size = UDim2.fromOffset(600, 450),

    Theme = "Dark",

    Search = true,

    MinimizeKey = Enum.KeyCode.RightControl
})

---

Create Tab

local Main = Window:AddTab({
    Title = "Main",
    Icon = "home"
})

Create multiple tabs:

local Main = Window:AddTab({
    Title = "Main",
    Icon = "home"
})

local Player = Window:AddTab({
    Title = "Player",
    Icon = "user"
})

local Settings = Window:AddTab({
    Title = "Settings",
    Icon = "settings"
})

---

Select Tab

Window:SelectTab(Main)

Example:

local Main = Window:AddTab({
    Title = "Main",
    Icon = "home"
})

local Settings = Window:AddTab({
    Title = "Settings",
    Icon = "settings"
})

Window:SelectTab(Settings)

---

Section

Create a section inside a Tab:

local Section = Main:AddSection(
    "Main Features",
    "zap"
)

Then add elements to the Section:

Section:AddToggle("Enabled", {
    Title = "Enable",
    Default = false
})

A Section is useful for grouping related options.

---

Toggle

Create a Toggle:

local Toggle = Main:AddToggle("MyToggle", {
    Title = "Enable Feature",
    Description = "Enable or disable the feature",

    Default = false,

    Callback = function(Value)
        print("Toggle:", Value)
    end
})

Set Value

Toggle:SetValue(true)

Disable:

Toggle:SetValue(false)

Listen for Changes

Toggle:OnChanged(function(Value)
    print("Changed:", Value)
end)

Destroy

Toggle:Destroy()

---

Slider

local Slider = Main:AddSlider("Speed", {
    Title = "Speed",

    Default = 50,

    Min = 0,
    Max = 100,

    Rounding = 0,

    Callback = function(Value)
        print("Speed:", Value)
    end
})

Set Value

Slider:SetValue(75)

Listen for Changes

Slider:OnChanged(function(Value)
    print("Slider:", Value)
end)

Destroy

Slider:Destroy()

---

Dropdown

Create a normal single-selection Dropdown:

local Dropdown = Main:AddDropdown("Mode", {
    Title = "Mode",

    Values = {
        "Normal",
        "Fast",
        "Extreme"
    },

    Multi = false,

    Default = "Normal",

    Callback = function(Value)
        print("Selected:", Value)
    end
})

Multi Dropdown

local Dropdown = Main:AddDropdown("Modes", {
    Title = "Modes",

    Values = {
        "A",
        "B",
        "C",
        "D"
    },

    Multi = true,

    Default = {
        "A",
        "C"
    },

    Callback = function(Value)
        print("Selected:", Value)
    end
})

Dropdown API

Dropdown:Open()

Dropdown:Close()

Dropdown:Display()

Dropdown:GetActiveValues()

Dropdown:SetActiveValues(...)

Dropdown:SetValue(...)

Dropdown:OnChanged(function(Value)
    print(Value)
end)

Dropdown:Destroy()

---

Colorpicker

local Color = Main:AddColorpicker("MyColor", {
    Title = "Color",

    Default = Color3.fromRGB(255, 0, 0),

    Callback = function(Value)
        print("Color:", Value)
    end
})

Set Color

Color:SetValueRGB(
    Color3.fromRGB(0, 255, 0)
)

With transparency:

Color:SetValueRGB(
    Color3.fromRGB(0, 255, 0),
    0.5
)

Listen for Changes

Color:OnChanged(function(Value)
    print("Color changed:", Value)
end)

Destroy

Color:Destroy()

---

Keybind

local Keybind = Main:AddKeybind("MyKeybind", {
    Title = "Toggle Key",

    Default = "RightShift",

    Callback = function(Value)
        print("Key:", Value)
    end
})

Set Key

Keybind:SetValue("F")

Listen for Changes

Keybind:OnChanged(function(Value)
    print("New key:", Value)
end)

Destroy

Keybind:Destroy()

---

Input

local Input = Main:AddInput("Username", {
    Title = "Username",

    Placeholder = "Type something...",

    Callback = function(Value)
        print("Input:", Value)
    end
})

Default Value

local Input = Main:AddInput("Username", {
    Title = "Username",

    Default = "Player",

    Callback = function(Value)
        print(Value)
    end
})

Numeric Input

local Input = Main:AddInput("Number", {
    Title = "Number",

    Numeric = true,

    Callback = function(Value)
        print("Number:", Value)
    end
})

Finished

Use "Finished = true" when you want the callback to run after finishing the input.

local Input = Main:AddInput("Username", {
    Title = "Username",

    Finished = true,

    Callback = function(Value)
        print("Finished:", Value)
    end
})

Set Value

Input:SetValue("Hello")

Listen for Changes

Input:OnChanged(function(Value)
    print(Value)
end)

Destroy

Input:Destroy()

---

Paragraph

Paragraphs are useful for displaying information.

Main:AddParagraph({
    Title = "Information",

    Content = "This is an example paragraph."
})

Example:

Main:AddParagraph({
    Title = "About",

    Content = "Zzen.lua is a customizable Roblox UI Library."
})

---

Checkbox

local Checkbox = Main:AddCheckbox("MyCheckbox", {
    Title = "Enable Option",

    Default = false,

    Callback = function(Value)
        print("Checkbox:", Value)
    end
})

Set Value

Checkbox:SetValue(true)

Listen for Changes

Checkbox:OnChanged(function(Value)
    print(Value)
end)

Destroy

Checkbox:Destroy()

---

Radio Group

local Radio = Main:AddRadioGroup("Difficulty", {
    Title = "Difficulty",

    Options = {
        "Easy",
        "Normal",
        "Hard"
    },

    Default = "Normal",

    Callback = function(Value)
        print("Difficulty:", Value)
    end
})

Multiple Selection

local Radio = Main:AddRadioGroup("Modes", {
    Title = "Modes",

    Options = {
        "A",
        "B",
        "C"
    },

    Multi = true,

    Default = {
        "A",
        "C"
    },

    Callback = function(Value)
        print(Value)
    end
})

API

Radio:SetValue("Hard")

Radio:OnChanged(function(Value)
    print(Value)
end)

Radio:Destroy()

---

Number Input

NumberInput is useful for entering numeric values.

local Number = Main:AddNumberInput("Amount", {
    Title = "Amount",

    Default = 10,

    Step = 1,

    Min = 0,

    Max = 100,

    Callback = function(Value)
        print("Amount:", Value)
    end
})

Set Value

Number:SetValue(50)

Listen for Changes

Number:OnChanged(function(Value)
    print(Value)
end)

Destroy

Number:Destroy()

---

Action Button

«Important: In the current Zzen.lua source, use "AddActionButton()" rather than "AddButton()".»

Main:AddActionButton("TestButton", {
    Title = "Test Button",

    ButtonText = "Click",

    Callback = function()
        print("Clicked!")
    end
})

Description

Main:AddActionButton("TestButton", {
    Title = "Test Button",

    Description = "Press the button to test it.",

    ButtonText = "Click",

    Callback = function()
        print("Clicked!")
    end
})

Copy Button

local Button = Main:AddActionButton("Copy", {
    Title = "Copy Text",

    ButtonText = "Copy",

    CopyText = "Hello World",

    CopiedText = "Copied!",

    ResetDelay = 1.5,

    Callback = function()
        print("Copied")
    end
})

Button API

Button:SetCopyText("New Text")

Button:SetButtonText(
    "Copy",
    "Copied!"
)

Button:Destroy()

---

Button Group

Create multiple buttons in one group.

Main:AddButtonGroup("Actions", {
    Title = "Actions",

    Buttons = {
        {
            Text = "Start",

            Callback = function()
                print("Start")
            end
        },

        {
            Text = "Stop",

            Callback = function()
                print("Stop")
            end
        }
    }
})

Example with three buttons:

Main:AddButtonGroup("Controls", {
    Title = "Controls",

    Buttons = {
        {
            Text = "Start",

            Callback = function()
                print("Started")
            end
        },

        {
            Text = "Pause",

            Callback = function()
                print("Paused")
            end
        },

        {
            Text = "Stop",

            Callback = function()
                print("Stopped")
            end
        }
    }
})

---

Quick Actions

QuickActions are useful for creating compact action controls.

Main:AddQuickActions("QuickActions", {
    Title = "Quick Actions",

    Actions = {
        {
            Text = "Start",

            Icon = "play",

            Callback = function()
                print("Start")
            end
        },

        {
            Text = "Stop",

            Icon = "square",

            Callback = function()
                print("Stop")
            end
        }
    }
})

---

Mini Bar

local Bar = Main:AddMiniBar("Progress", {
    Title = "Progress",

    Min = 0,

    Max = 100,

    Default = 50,

    Callback = function(Value)
        print("Progress:", Value)
    end
})

Set Value

Bar:SetValue(80)

Listen for Changes

Bar:OnChanged(function(Value)
    print(Value)
end)

Destroy

Bar:Destroy()

---

Divider

Create a simple divider:

Main:AddDivider()

With a label:

Main:AddDivider({
    Label = "Advanced Settings"
})

Custom height:

Main:AddDivider({
    Height = 2
})

---

Separator

Simple separator:

Main:AddSeparator()

With a label:

Main:AddSeparator({
    Label = "Settings"
})

---

Status Indicator

local Status = Main:AddStatusIndicator("ServerStatus", {
    Title = "Server",

    Status = "offline",

    Label = "Offline"
})

Change Status

Status:SetStatus(
    "online",
    "Online"
)

Example:

Status:SetStatus(
    "running",
    "Running"
)

Available status types:

online
offline
running
stopped
warning

Destroy

Status:Destroy()

---

Counter Button

local Counter = Main:AddCounterButton("Count", {
    Title = "Count",

    Default = 1,

    Min = 1,

    Max = 99,

    Step = 1,

    Callback = function(Value)
        print("Count:", Value)
    end
})

Set Value

Counter:SetValue(10)

Listen for Changes

Counter:OnChanged(function(Value)
    print(Value)
end)

Destroy

Counter:Destroy()

---

Stepper

Stepper provides numeric controls with increment/decrement functionality.

local Stepper = Main:AddStepper("Speed", {
    Title = "Speed",

    Default = 10,

    Step = 1,

    Min = 0,

    Max = 100,

    Callback = function(Value)
        print("Speed:", Value)
    end
})

Full Mode

local Stepper = Main:AddStepper("Speed", {
    Title = "Speed",

    Default = 10,

    Step = 1,

    Min = 0,

    Max = 100,

    Mode = "Full",

    Callback = function(Value)
        print(Value)
    end
})

Compact Mode

local Stepper = Main:AddStepper("Speed", {
    Title = "Speed",

    Default = 10,

    Step = 1,

    Min = 0,

    Max = 100,

    Mode = "Compact",

    Callback = function(Value)
        print(Value)
    end
})

Suffix

local Stepper = Main:AddStepper("Speed", {
    Title = "Speed",

    Default = 10,

    Min = 0,

    Max = 100,

    Step = 1,

    Suffix = " km/h",

    Callback = function(Value)
        print(Value)
    end
})

API

Stepper:SetValue(50)

Stepper:OnChanged(function(Value)
    print(Value)
end)

Stepper:Destroy()

---

Toggle Group

ToggleGroup is useful when you want several choices displayed together.

local Mode = Main:AddToggleGroup("Mode", {
    Title = "Mode",

    Options = {
        "Normal",
        "Fast",
        "Extreme"
    },

    Default = "Normal",

    Callback = function(Value)
        print("Mode:", Value)
    end
})

Set Value

Mode:SetValue("Fast")

Listen for Changes

Mode:OnChanged(function(Value)
    print(Value)
end)

Destroy

Mode:Destroy()

---

Accordion

Accordion creates a collapsible container.

local Accordion = Main:AddAccordion("Information", {
    Title = "Information",

    Description = "Click to expand.",

    Open = false,

    Icon = "info"
})

You can add elements inside an Accordion.

local Accordion = Main:AddAccordion("Settings", {
    Title = "Settings",

    Open = false
})

Accordion:AddParagraph({
    Title = "Info",

    Content = "Settings are inside this Accordion."
})

You can also add controls:

Accordion:AddToggle("InsideToggle", {
    Title = "Enable",

    Default = false,

    Callback = function(Value)
        print(Value)
    end
})

Accordion API

Accordion:Open()

Accordion:Close()

Accordion:Toggle()

Accordion:Destroy()

---

Chip

Chip elements can be used for compact selections.

local Chip = Main:AddChip("Colors", {
    Title = "Colors",

    Items = {
        "Red",
        "Green",
        "Blue"
    },

    Multi = true,

    Default = {
        "Red"
    },

    Callback = function(Value)
        print(Value)
    end
})

Set Value

Chip:SetValue({
    "Green",
    "Blue"
})

Listen for Changes

Chip:OnChanged(function(Value)
    print(Value)
end)

Destroy

Chip:Destroy()

---

Live Label

LiveLabel is useful for displaying values that change frequently.

local Status = Main:AddLiveLabel("Status", {
    Title = "Status",

    Text = "Loading...",

    Type = "info"
})

Available types:

default
info
success
warning
error

Change Text

Status:SetText("Loaded!")

Change Type

Status:SetType("success")

Example:

Status:SetText("Everything is ready!")
Status:SetType("success")

---

Notification

Display a notification:

Zzen:Notify({
    Title = "Success",

    Content = "Loaded successfully!",

    Duration = 3
})

With SubContent:

Zzen:Notify({
    Title = "Information",

    Content = "The script has loaded.",

    SubContent = "Everything is ready.",

    Duration = 5
})

---

Dialog

Create a confirmation dialog:

Window:Dialog({
    Title = "Confirm",

    Content = "Do you want to continue?",

    Buttons = {
        {
            Title = "Yes",

            Callback = function()
                print("Yes")
            end
        },

        {
            Title = "No",

            Callback = function()
                print("No")
            end
        }
    }
})

---

Themes

Zzen.lua includes the following themes:

Dark
Darker
AMOLED
Light
Aqua
Amethyst
Rose
Midnight
Ocean
Emerald
Sapphire
Minecraft

---

Change Theme

Zzen:SetTheme("Ocean")

Another example:

Zzen:SetTheme("AMOLED")

Minecraft:

Zzen:SetTheme("Minecraft")

---

Accent Color

Change the accent color:

Zzen:SetAccentColor(
    Color3.fromRGB(255, 0, 0)
)

Example:

Zzen:SetAccentColor(
    Color3.fromRGB(0, 170, 255)
)

Reset Accent Color

Zzen:ResetAccentColor()

---

Window Transparency

Zzen:SetWindowTransparency(0)

Example:

Zzen:SetWindowTransparency(1)

The library clamps the value to its supported range.

---

Presets

Zzen.lua includes a preset system.

Save Preset

Zzen:SavePreset("MyPreset")

Load Preset

Zzen:LoadPreset("MyPreset")

Delete Preset

Zzen:DeletePreset("MyPreset")

Get Preset Names

local Presets = Zzen:GetPresetNames()

for _, Name in ipairs(Presets) do
    print(Name)
end

---

SaveManager

If your environment supports the required file APIs, SaveManager can be used for configuration files.

Set the library:

SaveManager:SetLibrary(Zzen)

Set a folder:

SaveManager:SetFolder("MyScript")

Save a configuration:

SaveManager:Save("Config")

Load a configuration:

SaveManager:Load("Config")

Ignore specific options:

SaveManager:SetIgnoreIndexes({
    "MyToggle",
    "MySlider"
})

Example:

SaveManager:SetLibrary(Zzen)

SaveManager:SetFolder("MyScript")

SaveManager:Save("Default")

---

InterfaceManager

InterfaceManager can be used for interface-related settings.

InterfaceManager:SetLibrary(Zzen)

Example:

InterfaceManager:SetLibrary(Zzen)

InterfaceManager:SetTheme("Ocean")

Save settings:

InterfaceManager:SaveSettings()

Load settings:

InterfaceManager:LoadSettings()

Build an interface section:

InterfaceManager:BuildInterfaceSection(Settings)

---

Destroy UI

Destroy the entire UI:

Zzen:Destroy()

---

Complete Example

The following example combines several Zzen.lua components.

local Zzen = loadstring(game:HttpGet(
    "https://raw.githubusercontent.com/KUYKUBZ/ProjectX/refs/heads/main/Zzen.lua"
))()

local Window = Zzen:CreateWindow({
    Title = "My Script",

    SubTitle = "Zzen Example",

    Size = UDim2.fromOffset(650, 500),

    Theme = "Ocean",

    Search = true,

    MinimizeKey = Enum.KeyCode.RightControl
})

local Main = Window:AddTab({
    Title = "Main",

    Icon = "home"
})

local Settings = Window:AddTab({
    Title = "Settings",

    Icon = "settings"
})

local MainSection = Main:AddSection(
    "Main Features",
    "zap"
)

MainSection:AddToggle("Enabled", {
    Title = "Enable Feature",

    Description = "Enable or disable the feature.",

    Default = false,

    Callback = function(Value)
        print("Enabled:", Value)
    end
})

MainSection:AddSlider("Speed", {
    Title = "Speed",

    Default = 50,

    Min = 0,

    Max = 100,

    Rounding = 0,

    Callback = function(Value)
        print("Speed:", Value)
    end
})

MainSection:AddDropdown("Mode", {
    Title = "Mode",

    Values = {
        "Normal",
        "Fast",
        "Extreme"
    },

    Multi = false,

    Default = "Normal",

    Callback = function(Value)
        print("Mode:", Value)
    end
})

MainSection:AddInput("Text", {
    Title = "Input",

    Placeholder = "Type something...",

    Callback = function(Value)
        print("Input:", Value)
    end
})

MainSection:AddColorpicker("Color", {
    Title = "Color",

    Default = Color3.fromRGB(0, 170, 255),

    Callback = function(Value)
        print("Color:", Value)
    end
})

MainSection:AddKeybind("Keybind", {
    Title = "Keybind",

    Default = "RightShift",

    Callback = function(Value)
        print("Key:", Value)
    end
})

MainSection:AddCheckbox("Checkbox", {
    Title = "Checkbox",

    Default = false,

    Callback = function(Value)
        print("Checkbox:", Value)
    end
})

MainSection:AddActionButton("TestButton", {
    Title = "Test Button",

    ButtonText = "Click",

    Callback = function()
        Zzen:Notify({
            Title = "Success",

            Content = "Button clicked!",

            Duration = 3
        })
    end
})

MainSection:AddParagraph({
    Title = "Information",

    Content = "Zzen.lua UI Library Example"
})

Zzen:Notify({
    Title = "Zzen",

    Content = "UI Loaded Successfully!",

    Duration = 5
})

---

Available Elements

Element| API
Toggle| "AddToggle()"
Slider| "AddSlider()"
Dropdown| "AddDropdown()"
Colorpicker| "AddColorpicker()"
Keybind| "AddKeybind()"
Input| "AddInput()"
Paragraph| "AddParagraph()"
Checkbox| "AddCheckbox()"
Radio Group| "AddRadioGroup()"
Number Input| "AddNumberInput()"
Action Button| "AddActionButton()"
Button Group| "AddButtonGroup()"
Quick Actions| "AddQuickActions()"
Mini Bar| "AddMiniBar()"
Separator| "AddSeparator()"
Divider| "AddDivider()"
Status Indicator| "AddStatusIndicator()"
Counter Button| "AddCounterButton()"
Stepper| "AddStepper()"
Toggle Group| "AddToggleGroup()"
Accordion| "AddAccordion()"
Chip| "AddChip()"
Live Label| "AddLiveLabel()"

---

Common Element API

Many value-based elements provide the following methods:

Element:SetValue(...)

Listen for changes:

Element:OnChanged(function(Value)
    print(Value)
end)

Destroy:

Element:Destroy()

The exact methods available depend on the element type.

---

Common Callback Pattern

Most interactive elements use:

Callback = function(Value)

    print(Value)

end

For buttons:

Callback = function()

    print("Clicked")

end

---

Example: Multiple Features Together

local Enabled = false
local Speed = 50
local Mode = "Normal"

Main:AddToggle("Enabled", {
    Title = "Enabled",

    Default = false,

    Callback = function(Value)
        Enabled = Value

        print("Enabled:", Enabled)
    end
})

Main:AddSlider("Speed", {
    Title = "Speed",

    Default = 50,

    Min = 1,

    Max = 100,

    Rounding = 0,

    Callback = function(Value)
        Speed = Value

        print("Speed:", Speed)
    end
})

Main:AddDropdown("Mode", {
    Title = "Mode",

    Values = {
        "Normal",
        "Fast",
        "Extreme"
    },

    Default = "Normal",

    Callback = function(Value)
        Mode = Value

        print("Mode:", Mode)
    end
})

---

Important: AddButton vs AddActionButton

If you receive this error:

attempt to call missing method 'AddButton' of table

Do not use:

Main:AddButton({
    Title = "Button"
})

The current Zzen.lua source uses:

Main:AddActionButton("Button", {
    Title = "Button",

    ButtonText = "Click",

    Callback = function()
        print("Clicked")
    end
})

This is one of the most important differences when using the current version of Zzen.lua.

---

Troubleshooting

Error: AddButton is missing

Wrong:

Main:AddButton({
    Title = "Test"
})

Correct:

Main:AddActionButton("Test", {
    Title = "Test",

    ButtonText = "Click",

    Callback = function()
        print("Clicked")
    end
})

---

Error: Element is nil

Make sure the Tab exists before adding elements.

Correct:

local Main = Window:AddTab({
    Title = "Main"
})

Main:AddToggle("Test", {
    Title = "Test"
})

---

Error: Wrong object

The normal hierarchy is:

Zzen
 ↓
Window
 ↓
Tab
 ↓
Element

For example:

local Window = Zzen:CreateWindow({
    Title = "Test"
})

local Main = Window:AddTab({
    Title = "Main"
})

Main:AddToggle("Test", {
    Title = "Test"
})

---

Minimal Template

Use this as a starting point for a new script:

local Zzen = loadstring(game:HttpGet(
    "https://raw.githubusercontent.com/KUYKUBZ/ProjectX/refs/heads/main/Zzen.lua"
))()

local Window = Zzen:CreateWindow({
    Title = "My Script",
    SubTitle = "My UI",
    Theme = "Dark"
})

local Main = Window:AddTab({
    Title = "Main",
    Icon = "home"
})

Main:AddToggle("Enabled", {
    Title = "Enabled",
    Default = false,

    Callback = function(Value)
        print(Value)
    end
})

Main:AddActionButton("Test", {
    Title = "Test Button",

    ButtonText = "Click",

    Callback = function()
        print("Clicked")
    end
})

Zzen:Notify({
    Title = "Loaded",
    Content = "UI Loaded!",
    Duration = 3
})

---

Credits

Zzen.lua

GitHub:

https://github.com/KUYKUBZ/ProjectX

Source:

https://raw.githubusercontent.com/KUYKUBZ/ProjectX/refs/heads/main/Zzen.lua

---

License

See the repository for the project's current license and usage terms.

---

Documentation Status

This README documents the public-facing UI APIs and examples available in the current Zzen.lua source.

For the most up-to-date implementation, always compare this documentation with the current source file in the repository.