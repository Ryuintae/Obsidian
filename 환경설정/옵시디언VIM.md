let mapleader=" " "스페이스바로 leader키를 사용할수있게한다.    
set ignorecase    
set smartcase    
set visualbell    
set number relativenumber    
" set noerrorbells    
set expandtab    
set autoindent    
set hlsearch    
set incsearch    
set ideajoin    
set mouse=a    
set idearefactormode=keep    
set mousefocus    
set scollfocus    
set scrolloff=3    
set highlightedyank    
set clipboard=unnamed

noremap j h    
noremap i k    
noremap k j    
noremap h i    
noremap J ^    
noremap L $    
noremap H I    
" 맨위 이동 맨 아래 이동  nmap I gg    
nmap K G    
vmap I gg    
vmap K G

nnoremap <BS> <C-S-6>

" nnoremap k kzz "커서가 중간에 위치하게한다.    
" nnoremap j jzz "위와 동일