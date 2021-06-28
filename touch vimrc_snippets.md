



command to open current buffer in vsplit
``` bash

command -nargs=1 Vsb call VsbFunction(<f-args>)

function VsbFunction (arg1)
  execute 'vert sb' a:arg1
endfunction

# to call 
# :Vsb somefile
```




