# Homework Template for mgf3301

To compile:

```sh
latexmk -lualatex -file-line-error -shell-escape hw_template.tex
```

I use [vimtex](https://github.com/lervag/vimtex/) to compile with above options
automagically. My vim config is as follows:

```vim
let g:vimtex_compiler_latexmk_engines = {
  '_'                    : '-lualatex',
  'pdflatex'             : '-pdf',
  'dvipdfex'             : '-pdfdvi',
  'lualatex'             : '-lualatex',
  'xelatex'              : '-xelatex',
  'context (pdftex)'     : '-pdf -pdflatex=texexec',
  'context (luatex)'     : '-pdf -pdflatex=context',
  'context (xetex)'      : "-pdf -pdflatex='texexec --xtx'",
}

let g:vimtex_compiler_latexmk = {
  'executable': 'latexmk',
  'options': [
    '-shell-escape',
    '-verbose',
    '-file-line-error',
    '-synctex=1',
    '-interaction=nonstopmode',
  ],
  'build_dir': 'dist',
}
let g:tex_flavor = 'latex'
let g:vimtex_view_general_viewer = 'zathura'
let g:vimtex_viewer_general = 'zathura'
let g:vimtex_view_method = 'zathura'
let g:tex_conceal = 'abdmg'
" let g:vimtex_quickfix_mode = 0
```

I use lualatex flag because of the emoji package, which requires lualatex. You
can just remove emoji package and all `\emoji` reference and compiile with
standard pdflatex if you want (with just `latexmk hw_template.tex`.

I installed texlive on arch linux (via `pacman -S texlive-core texlive-bin
texlive-bibtexextr`), but on OS X you should just be able to install MacTex to
get access to `latexmk`.

Cheers~
