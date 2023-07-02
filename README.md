# SAMP-API.lua

SAMP-API.lua is a lua library for MoonLoader that adds structures and functions from SA:MP.

Currently supports versions `0.3.7-R1`, `0.3.7-R3-1` and `0.3.7-R5-1`.

## Installation

Copy the entire folder `sampapi` into the `moonloader/lib` directory.

## Example

Here is an example of a simple dialog hider:

```lua
local ffi = require 'ffi'
require 'moonloader'

local sampapi = require 'sampapi'
local dialog = sampapi.require('CDialog', true)

function main()
    if sampapi.GetBase() == 0 or sampapi.GetSAMPVersion() == ffi.C.SAMP_VERSION_UNKNOWN then
        return
    end

    while true do
        wait(0)

        if isKeyJustPressed(VK_HOME) then
            local ref = dialog.RefDialog()
            if ref then
                ref.m_bIsActive = 1
            end
        elseif isKeyJustPressed(VK_END) then
            local ref = dialog.RefDialog()
            if ref then
                ref.m_bIsActive = 0
            end
        end
    end
end
```