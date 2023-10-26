"" Source your .vimrc  
"source ~/.vimrc  
  
" english auto change  
let keep_input_source_in_normal=ABC  
set keep-english-in-normal  
" set keep-english-in-normal-and-restore-in-insert  
  
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
  
  
" 3 lines above/below cursor when scrolling  
set NERDTree  
" set surround  
set multiple-cursors  
" set easymotion  
" set quickscope  
  
  
" essential  
"아래의 코드를 보면 ijkl로 매핑을해 사용할수있다.  
noremap j h  
noremap i k  
noremap k j  
noremap h i  
noremap J ^  
noremap L $  
noremap H I  
" 맨위 이동 맨 아래 이동  
nmap I gg  
nmap K G  
vmap I gg  
vmap K G  
" toggle sidebar  
nmap <C-e> :NERDTreeFocus<cr>  
  
" These create newlines like o and O but stay in normal mode  
  
" zen mode  
noremap <leader>kz :action ToggleZenMode<CR>  
  
  
" Quit visual mode  
" nnoremap k kzz "커서가 중간에 위치하게한다.  
" nnoremap j jzz "위와 동일  
  
nnoremap <BS> <C-S-6>  
  
  
nnoremap <leader>y "+y "운영체제에 clipboard에 카피한다.  
nnoremap <leader>p "+p "운영체제에 clipboard를 paste한다.  
vnoremap <leader>y "+y  
nnoremap Y y$  
vnoremap v <Esc>  
nnoremap <Esc> :noh<cr>:w<cr><Esc>  
inoremap <Esc> <Esc>:w<CR>  
" nnoremap jk :noh<cr>:w<cr><esc>  
inoremap jk <esc>:w<CR>  
inoremap ㅓㅏ <esc>:w<CR>  
" njorejap jㅏ :joh<cr>:w<cr><esc>" Tab operation  
nnoremap <leader>l gt "열려 있는 파일을 이동한다.  
nnoremap <leader>j gT "열려 있는 파일을 이동한다.  
  
" mehotd up  
nmap [[ <Action>(MethodUp)  
nmap ]] <Action>(MethodDown)  
  
" goto Error and Declaration 이것들은 거의 필수와 마찬가지다 정의된 코드로 이동하는 명령어다."  
nmap gb <Action>(Back)  
nmap gD <Action>(GotoTypeDeclaration)  
nmap gf <Action>(Forward)  
nmap gl <Action>(QuickJavaDoc)  
nmap gL <Action>(QuickImplementations)  
nmap gy <Action>(ShowErrorDescription)  
nmap gn <Action>(GotoNextError)  
nmap gp <Action>(GotoPreviousError)  
nmap <TAB> <Action>(GotoNextError)  
nmap <S-TAB> <Action>(GotoPreviousError)  
  
"Editor indent"  
nmap > <S-v>:action EditorIndentSelection<cr>  
nmap < <S-v>:action EditorUnindentSelection<cr>  
vmap > <Action>(EditorIndentSelection)  
vmap < <Action>(EditorUnindentSelection)  
  
" moving row"  
nnoremap <C-k> :m +1<CR>  
nnoremap <C-i> :m -2<CR>  
inoremap <C-k> <Esc>:m +1<CR>gi  
inoremap <C-i> <Esc>:m -2<CR>gi  
vnoremap <C-k> :action MoveStatementDown<CR>  
vnoremap <C-i> :action MoveStatementUp<CR>  
  
  
" Refactorings  
map <leader>t <Action>(Refactorings.QuickListPopupAction)  
  
" Closing tabs  
nmap <leader>q :action CloseContent<cr>  
nmap <leader>Q :action CloseAllEditorsButActive<cr>  
  
" edit ideavim config  
nnoremap <leader>vv :e ~/.ideavimrc<CR>  
nnoremap <leader>vr :source ~/.ideavimrc<CR>  
  
" code Run & Debug  
nmap <leader>r :action Run<cr>  
nmap <leader>d :Debug<cr  
nmap <leader>f :action ReformatCode<cr>  
nmap <leader>h :action FindInPath<cr>  
  
" Navigation  
nmap ? :action/h/ FindInPath<cr>  
nmac 키를 누르면 저장과 하이라이트된 단어를 취소시킨다. ; <leader>; :action FileStructurePopup<cr>  
nmap <leader>e :action RecentFiles<cr>  
nmap <C-Enter> :action Generate<cr>  
imap <C-Enter> :action Generate<cr>  
  
  
" multi Cursor  
map <C-N>  <A-N>  
map <C-P>  <A-P>  
map <C-X>  <A-X>  
  
map g<C-N> <Action>(SelectAllOccurrences)