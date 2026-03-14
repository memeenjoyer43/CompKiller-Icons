# CompKiller

> This is a modified version of CompKiller to be able to preserve more lucide.dev icons, original version of CompKiller are [here](https://github.com/4lpaca-pin/CompKiller)\
> forked by memeenjoyer43

CompKiller UI For Roblox (https://compkiller.net)

- Mobile Friendly
- Smooth
- Stable

![image](https://github.com/user-attachments/assets/b1c3a6d2-ef1f-42eb-91fe-cbdc2ce17721) ![image](https://github.com/user-attachments/assets/014e077b-0064-4d56-b0b0-d12e989e64f2)

<img width="1818" height="898" alt="Screenshot 2025-10-20 091725" src="https://github.com/user-attachments/assets/c6e5f705-f36b-4353-9a80-e2e25478282f" />

# Usage
- [**[Documentation]**](https://cat-sus.gitbook.io/compkiller/documents/interface)
- [**[Example]**](https://github.com/memeenjoyer43/CompKiller-Icons/blob/main/examples/Full.luau)
- [**[Source Code]**](https://github.com/memeenjoyer43/CompKiller-Icons/blob/main/src/source.luau)

# Other Functions

### Icons
```lua
Compkiller:_GetIcon(<name : String>) -> Table {ImageRectSize : Vector2, ImageRectOffset : Vector2, Image : String} | String(rbxassetid://...) | nil
```
Icon from fontawesome
```lua
Compkiller:_GetIcon(<name : String> , true) -> Rbx AssetId : String
```

### Random String
```lua
Compkiller:_RandomString() -> CK=............. : String
```
