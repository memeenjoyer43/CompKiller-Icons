# CompKiller UI Document

## Using Library
```lua
local Compkiller = loadstring(game:HttpGet("https://raw.githubusercontent.com/4lpaca-pin/CompKiller/refs/heads/main/src/source.luau"))();
```

## Creating Notification
```lua
local Notifier = Compkiller.newNotify();
```

### Send Notification
```lua
Notifier.new({
	Title = "Notification",
	Content = "Compkiller",
	Duration = 10,
	Icon = "rbxassetid://120245531583106"
});
```

## Loading UI
```lua
Compkiller:Loader("rbxassetid://120245531583106" , 1.5).yield();
```

## Creating Window
```lua
local Window = Compkiller.new({
	Name = "COMPKILLER",
	Keybind = "Insert",
	Logo = "rbxassetid://120245531583106",
	Scale = Compkiller.Scale.Window, -- Leave blank if you want automatic scale [PC, Mobile].
	TextSize = 15,
});
```

## Creating Watermark
```lua
local Watermark = Window:Watermark();
```

### Creating Text
```lua
local Time = Watermark:AddText({
	Icon = "timer",
	Text = "TIME",
});
```

### Editing Text
```lua
Time:SetText(Compkiller:GetTimeNow());
```

## Creating Tab Category
```lua
Window:DrawCategory({
	Name = "Category"
});
```

## Creating Tab (Normal)
```lua
local NormalTab = Window:DrawTab({
	Name = "Example Tab",
	Icon = "apple",
});
```

## Creating Tab (Single)
```lua
local NormalTab = Window:DrawTab({
	Name = "Example Tab",
	Icon = "apple",
	Type = "Single",
});
```

## Creating Container Tab
```lua
local ContainerTab = Window:DrawContainerTab({
	Name = "Extract Tabs",
	Icon = "contact",
});

-- Creating Tab (Normal) --
local ExtractTab = ContainerTab:DrawTab({
	Name = "Tab 1",
	Type = "Double"
});

-- Creating Tab (Single) --
local SingleExtractTab = ContainerTab:DrawTab({
	Name = "Tab 2",
	Type = "Single",
});
```

## Creating Section
```lua
local NormalSection = NormalTab:DrawSection({
	Name = "Section",
	Position = 'left'	
});
```

## Creating Toggle
```lua
local Toggle = NormalSection:AddToggle({
	Name = "Toggle",
	Flag = "Toggle_Example", -- Leave it blank will not save to config (ALL ELEMENTS)
	Default = false,
	Callback = function(value) -- value = false / true
		print(value)
	end,
});

Toggle:SetValue(true) -- settings a toggle value by code, argument must be a boolean
print(Toggle:GetValue()) -- getting a toggle current value
Toggle:SetText("CoolToggle") -- modifying a toggle Name by code, if argument is nil then it'll set the current Name to name default Name
print(Toggle:GetText()) -- getting a toggle current name
```

### Element Link
Link is available for Toggle, Slider, Keybind and Color Picker

### Link Keybind
```lua
-- documentation below link section
Element.Link:AddKeybind({
	Default = "E",
	Flag = "Option_Keybind",
	OnChangedCallback = print
	InputBeganCallback = print
	InputEndedCallback = print
});
```

### Link Helper
```lua
Element.Link:AddHelper({
	Text = "Helper Text"
})
```

### Link Color-Picker
```lua
-- documentation below slider documentation
Element.Link:AddColorPicker({
	Default = Color3.fromRGB(255,255,255),
	Callback = print
})
```

### Link Option
Link Option is Section but in Link
```lua
local Option = Toggle.Link:AddOption()

Option:AddToggle({
	Name = "Toggle in option!",
	Callback = print
})
```

## Creating Keybind
```lua
local keybind = NormalSection:AddKeybind({
	Name = "Keybind",
	Default = "LeftAlt",
	Flag = "Keybind_Example",
	OnChangedCallback = function(value) -- value = keybind the client set, example : E, R. T, B. Triggered on keybind change
		print(value)
	end,
	InputBeganCallback = function(value) -- value = keybind the client set, example : E, R. T, B. Triggered on keybind press
		print(value)
	end,
	InputEndedCallback = function(value) -- value = keybind the client set, example : E, R. T, B. Triggered on keybind release
		print(value)
	end,
});
keybind:SetValue("E") -- set the Keybind current key to the argument(MUST BE A STRING, Enum.KeyCode enums name OR Enum.UserInputType enums name)
print(keybind:GetValue()) -- get the Keybind current key 
```

## Creating Slider
```lua
NormalSection:AddSlider({
	Name = "Slider",
	Min = 0,
	Max = 100,
	Default = 50,
	Round = 0,
	Flag = "Slider_Example",
	Callback = print
});
```

## Creating ColorPicker
```lua
NormalSection:AddColorPicker({
	Name = "ColorPicker",
	Default = Color3.fromRGB(0, 255, 140),
	Flag = "Color_Picker_Example",
	Callback = print
})
```

## Creating Dropdown
```lua
NormalSection:AddDropdown({
	Name = "Single Dropdown",
	Default = "Head",
	Flag = "Single_Dropdown",
	Values = {"Head","Body","Arms","Legs"},
	Callback = print
})
```

### Multi Dropdown
```lua
NormalSection:AddDropdown({
	Name = "Multi Dropdown",
	Default = {"Head"},
	Multi = true,
	Flag = "Multi_Dropdown",
	Values = {"Head","Body","Arms","Legs"},
	Callback = print
})
```

## Creating Button
```lua
NormalSection:AddButton({
	Name = "Button",
	Callback = function()
		print('PRINT!')
	end,
})
```

## Creating Paragraph
```lua
local paragraph = NormalSection:AddParagraph({
	Title = "Paragraph",
	Content = "Very cool paragraph"
})
paragraph:SetTitle("Replaced paragraph")
paragraph:SetContent("The content are replaced!!!")
```

## Creating Textbox
```lua

NormalSection:AddTextBox({
	Name = "Textbox",
	Placeholder = "Placeholder",
	Default = "Hello, World",
  	Flag = "TextBoxExample",
	Callback = print
})
```

## Creating Config Tab
```lua
local ConfigUI = Window:DrawConfig({
	Name = "Config",
	Icon = "folder",
	Config = ConfigManager, -- Config Manager (required)
});

ConfigUI:Init();
```

# Config Manager
## Write Config
write current value to config
```lua
ConfigManager:WriteConfig({
	Name = "Config Name",
	Author = "Creator Name"
})
```

## Read Info
read config info. Ex: Author and Created date
```lua
ConfigManager:ReadInfo("<Config Name>")
```

## Load Config
Load the config in directory
```lua
ConfigManager:LoadConfig("<Config Name>")
```

## Delete Config
Delete the config in directory
```lua
ConfigManager:DeleteConfig("<Config Name>")
```

## Get Configs
get all configs in directory
```lua
ConfigManager:GetConfigs()
```

## Directory Path
config directory path
```lua
ConfigManager.Directory
```

# User Settings
## Create
```lua
local UserSettings = Window.UserSettings:Create();
```

## Example
```lua
UserSettings:AddColorPicker({
	Name = "Menu Color",
	Default = Compkiller.Colors.Highlight,
	Callback = function(f)
		Compkiller.Colors.Highlight = f;
		
		Compkiller:RefreshCurrentColor();
	end,
});

UserSettings:AddKeybind({
	Name = "Menu Key",
	Default = MenuKey,
	OnChangedCallback = function(f)
		MenuKey = f;
		
		Window:SetMenuKey(MenuKey)
	end,
});

UserSettings:AddDropdown({
	Name = "Menu Language",
	Values = {"English","Russian","Chinese"},
	Default = "English",
	Callback = print
});

UserSettings:AddDropdown({
	Name = "Menu Theme",
	Values = {
		"Default",
		"Dark Green",
		"Dark Blue",
		"Purple Rose",
		"Skeet"
	},
	
	Default = "Default",
	
	Callback = function(f)
		Compkiller:SetTheme(f)
	end,
});

UserSettings:AddDropdown({
	Name = "Visible Widgets",
	Values = {"Watermark","Keybinds","Double Tab"},
	Multi = true,
	Default = {"Watermark"},
	Callback = function(f)
		print(f)
	end,
});
```
