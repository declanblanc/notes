I'm really interested in having a nice developer environment. I've always enjoyed making my computer feel like my own person space. 

Starting my neovim from scratch so I can hopefully learn more as I go instead. 
nvim looks in the .config/nvim directory for its config.

In this directory I'm creating a lua project where the "root" of the project is `.config/nvim/init.lua` 

Before much else, I'm going to be installing the Lazy package manager. This will allow me to install plugins in the future. I'm going with the "structured setup" they suggest in [the documentation](https://lazy.folke.io/installation) 
Okay woah woah slowing down just a second. I've copied and pasted a big ol chonk of code in, and I want to make sure I know what's going on here and I'm not just blindly following the docs in place of blindly following a tutorial. 


```plaintext title="structure"
~/.config/nvim
├── lua
│   ├── config
│   │   └── lazy.lua
│   └── plugins
│       ├── spec1.lua
│       ├── **
│       └── spec2.lua
└── init.lua
```

```lua title="~/.config/nvim/init.lua"
require("config.lazy")
```

```lua title="~/.config/nvim/lua/config/lazy.lua"
-- Bootstrap lazy.nvim
local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
if not (vim.uv or vim.loop).fs_stat(lazypath) then
	local lazyrepo = "https://github.com/folke/lazy.nvim.git"  
	local out = vim.fn.system({ "git", "clone", "--filter=blob:none", "--branch=stable", lazyrepo, lazypath })  
	if vim.v.shell_error ~= 0 then    
		vim.api.nvim_echo({      
			{ "Failed to clone lazy.nvim:\n", "ErrorMsg" },      
			{ out, "WarningMsg" },      
			{ "\nPress any key to exit..." },    
		}, true, {})    
		vim.fn.getchar()    
		os.exit(1)  
	end
end
vim.opt.rtp:prepend(lazypath)

-- Make sure to setup `mapleader` and `maplocalleader` before
-- loading lazy.nvim so that mappings are correct.
-- This is also a good place to setup other settings (vim.opt)
vim.g.mapleader = " "
vim.g.maplocalleader = "\\"
-- Setup lazy.nvim
require("lazy").setup({  
	spec = {    
		-- import your plugins    
		{ import = "plugins" },  
	},  
	-- Configure any other settings here. See the documentation for more details.  
	-- colorscheme that will be used when installing plugins.  
	install = { colorscheme = { "habamax" } },  
	-- automatically check for plugin updates  
	checker = { enabled = true },
})
```
Sounds like a lot of hoopla to make over a little config file, right? 

[WRONG](https://youtu.be/pqy6wKmWvV8)

---

The first big chunk under the "--Bootstrap lazy.nvim" comment is the "black magic" part that for the moment I'm choosing not to concern myself with all too much. All I need to know for now is that this bit checks if lazyvim is installed, and if it's not, installs it!

`vim.g.mapleader = " "` - this line sets a "leader key", the leader key acts as a sort of prefix for keyboard shortcuts. Rather than doing a shortcut like Ctrl+Shift+W to close all windows, you could map a shortcut like \<leader\>W which is nifty because you don't even need to hold the leader key! Just slap is, then slap a capital W and boom! The default it sets here is the space key which is what most people - myself included - seem to use.

`vim.g.maplocalleader = "//"` - this is quite similar to the "global" leader key except... local... sorry. 
I actually didn't know what this was so I looked it up using `:help localleader`:

> In a global plugin, \<Leader\> should be used and in a filetype plugin `<LocalLeader>`.
> 
> "mapleader" and "maplocalleader" can be equal. Although, if you make them different, there is a smaller chance of mappings from global plugins to clash with mappings for filetype plugins. For example, you could keep "mapleader" at the default backslash, and set "maplocalleader" to an underscore.

So it seems for the moment this won't affect me too much but if at some point I have filetype specific plugins I'll need to worry about it.

Okay this writing is taking much longer than anticipated so I'm going to speed it up a bit (the quality of writing is going to drop off dramatically in the interest of me actually getting something done 😎)

the last bit in this file runs the lazyvim setup, it accepts some different arguments for configuration but what I'll focus the most on is `spec = { {import = "plugins" }, }` which, wait for it.. imports plugins from `.config/nvim/lua/plugins`! 
How exciting! At the moment I don't have any plugins setup so when I launch nvim I get an error `No specs found for module "plugins"` 

---

It's crazy I feel like the docs assume so much prior knowledge that I simply do not have. After the Installation page they just jump to "Plugin Spec" with 0 explanation

Despite the lacking resources, I've successfully installed the monokai colorscheme!
It's a bit weird (and still not quite right) so I want to carefully walk through how this is working. 

`lua/config/lazy.lua`
	Initializes lazy.vim and tells it where to look for plugins
`lua/plugins/monokai.lua` returns a tuple that fits the [Plugin Spec](https://lazy.folke.io/spec) descrbied by neovim. This documentation page for plugin specs is very unclear to me but I think I've been able to infer some of what it's saying. 
"Spec Source"

this is too much for me atm, oy vey

