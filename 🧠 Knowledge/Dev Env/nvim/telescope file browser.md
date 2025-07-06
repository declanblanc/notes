I've installed [telescope file browser](https://github.com/nvim-telescope/telescope-file-browser.nvim)! 
Previously I was using nvim-tree (I think), so it's an adjustment but I think I'll like it in the long run. 

I've mapped `<leader>t` to open the file browser: 
```lua
vim.keymap.set("n", "<space>t", ":Telescope file_browser path=%:p:h select_buffer=true<CR>")
```

This is taken directly from the "Mappings" section of the GitHub for the file browser. 

`?` while in Normal in the file browser displays the normal mode keybinds
\<C-