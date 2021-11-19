# Lua

The Saboteur contains Lua 5.1 scripting language, which was used for controlling flow of missions, controlling and spawning of peds, and various other parts of the game.

On the PC version, Lua seems to not be modified on PC platform, but there seems to be changes on Xbox platform.

## Hooking

For getting `LuaManager` class which manages the global Lua machine is following offset: `uintptr_t luamanager_ptr = *(uintptr_t*)0x0142D324;`

*TODO: Following statement needs to be verified*

For getting `LuaMachine` class, which contains Lua state is following offset of LuaManager: `uintptr_t luamachine_ptr = luamanager_ptr + 0x124;`

For getting `lua_State` pointer, following code is used: `uintptr_t lua_state = *((uintptr_t*)*(uintptr_t*)luamachine_ptr);`

### Executing Lua Commands

For executing Lua commands, we need to know location of two functions, `lua_pcall` and `luaL_loadstring`. There are offsets of following functions:

```cpp
uintptr_t luaL_loadstring_ptr = 0x4041B0;
uintptr_t lua_pcall = 0x401F90;
```

Afterwards, we can execute Lua command as following:

```cpp
__asm
{
    push command ; pointer to char* of your Lua command
    push lua_state
    call luaL_loadstring_ptr
    add esp, 0x8

    push    0
    push    0
    push    0
    push    lua_state
    call    lua_pcall
    add     esp, 0x10
}
```

### Enabling Lua's print function

In release version of The Saboteur, the game is deleting `print` function in Lua machine.

You can avoid this by nopping instruction located at `0x006FAB6B` (nop 5 bytes)
