There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

Para resolver este nivel primero lo que hice fue hacer uso del nmap localhost, para saber que puertos estaban libres, en la segunda terminar del tmux, hice un echo de la contraseña anterior e hice que netcat escuchara un puerto libre para que la contraseña fuera enviada a ese puerto, después de eso hice que el archivo se conectara a ese puerto y si las contraseñas coincidían me mostraba la contraseña y así lo hizo


![](../../images/Pasted%20image%2020260405124055.png)

