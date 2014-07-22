Vimrc
=====

  ```vim
set autoindent
set cindent
autocmd StdinReadPre * let s:std_in=1
autocmd VimEnter * if argc() == 0 && !exists("s:std_in") | NERDTree /applications/mamp/htdocs | endif
execute pathogen#infect()
map <silent> <C-x> :NERDTreeToggle<CR>
set t_Co=256
set background=dark
colorscheme mustang
highlight Normal ctermbg=NONE
highlight nonText ctermbg=NONE
syntax on

 inoremap ( ()<Esc>i
 inoremap [ []<Esc>i
 inoremap { {<CR>}<Esc>O
 autocmd Syntax html,vim inoremap < <lt>><Esc>i| inoremap > <c-r>=ClosePair('>')<CR>
 inoremap ) <c-r>=ClosePair(')')<CR>
 inoremap ] <c-r>=ClosePair(']')<CR>
 inoremap } <c-r>=CloseBracket()<CR>
 inoremap " <c-r>=QuoteDelim('"')<CR>
 inoremap ' <c-r>=QuoteDelim("'")<CR>
 
" function ClosePair(char)
"  if getline('.')[col('.') - 1] == a:char
"  return "\<Right>"
"  else
"  return a:char
"  endif
" endf
" 
" function CloseBracket()
"  if match(getline(line('.') + 1), '\s*}') < 0
"  return "\<CR>}"
"  else
"  return "\<Esc>j0f}a"
"  endif
" endf
" 
" function QuoteDelim(char)
"  let line = getline('.')
"  let col = col('.')
"  if line[col - 2] == "\\"
"  "Inserting a quoted quotation mark into the string
"  return a:char
"  elseif line[col - 1] == a:char
"  "Escaping out of the string
"  return "\<Right>"
"  else
"  "Starting a string
"  return a:char.a:char."\<Esc>i"
"  endif
" endf
