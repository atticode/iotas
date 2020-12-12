+++
title = "Setting"
date = 2020-12-12T13:40:58+08:00
isCJKLanguage = true
description = ""
tags = []
categories = []
weight = 10
+++

## vim 配置
### Vim 设置状态栏

```vim-script

"statusline 设置状态栏                                                                                                                                 
set statusline=  
set statusline+=%7*\[%n]                                  "buffernr
set statusline+=%1*\ %<%F\                                "文件路径
set statusline+=%2*\ %y\                                  "文件类型
set statusline+=%3*\ %{''.(&fenc!=''?&fenc:&enc).''}      "编码1
set statusline+=%3*\ %{(&bomb?\",BOM\":\"\")}\            "编码2
set statusline+=%4*\ %{&ff}\                              "文件系统(dos/unix..)
set statusline+=%5*\ %{&spelllang}\%{HighlightSearch()}\  "语言 & 是否高亮，H表示高亮?
set statusline+=%8*\ %=\ row:%l/%L\ (%03p%%)\             "光标所在行号/总行数 (百分比)
set statusline+=%9*\ col:%03c\                            "光标所在列
set statusline+=%0*\ \ %m%r%w\ %P\ \                      "Modified? Read only? Top/bottom
function! HighlightSearch()
      if &hls
          return 'H'
      else
          return ''
      endif
endfunction
hi User1 ctermfg=white  ctermbg=darkred
hi User2 ctermfg=blue  ctermbg=58
hi User3 ctermfg=white  ctermbg=100
hi User4 ctermfg=darkred  ctermbg=95
hi User5 ctermfg=darkred  ctermbg=77
hi User7 ctermfg=darkred  ctermbg=blue  cterm=bold
hi User8 ctermfg=231  ctermbg=blue
"hi User9 ctermfg=#ffffff  ctermbg=#810085
hi User0 ctermfg=yellow  ctermbg=138

```

## Vim 的 emmet 插件

### 安装
1. 将压缩包中的plugin/emmet.vim 文件拷贝到 vim 安装目录下的 plugin/ 文件夹
2. 将压缩包中的autoload/ 下的 emmet.vim文件和emmet/文件夹拷贝到 vim安装目录下的 autoload/ 文件夹