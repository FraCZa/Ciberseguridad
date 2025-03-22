- Que hacer cuando logramos entrar a la maquina victima?


==TRATAMIENTO DE LA TTY

- Vamos a usar l siguiente comando:
```
script /dev/null -c bash
```
- al ejecutar este comando conseguimos un pront:
![[Pasted image 20241219130509.png]]
- Luego apretamos `ctrl + z`
- Ponemos a continuación:
```
stty raw -echo; fg
```
- Y luego ponemos:
```
reset xterm
```
- Luego exportamos 2 variables dentro de la maquina:
```
export TERM=xterm
export SHELL=bash
```
- Esto es para estar mejor estabilizado dentro de la maquina victima.






==PARA TRYHACKME==

```
python -c "import pty;pty.spawn('/bin/bash')"
```
