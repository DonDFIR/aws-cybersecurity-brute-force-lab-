<div align="center">

# AWS Cybersecurity | Brute Force Lab

**Kali Linux · Medusa · Metasploitable 2 · DVWA**

![Kali Linux](https://img.shields.io/badge/Kali_Linux-557C94?style=for-the-badge&logo=kalilinux&logoColor=white)
![Medusa](https://img.shields.io/badge/Medusa-Password_Auditing-7B2D8E?style=for-the-badge)
![DIO](https://img.shields.io/badge/Bootcamp-AWS_Cybersecurity-orange?style=for-the-badge)

</div>

## Objetivo
Simular Brute Force e Password Spraying em ambiente isolado, praticando enumeração e autenticação em FTP, SMB e DVWA.

## Ambiente
- **Kali Linux:** estação de testes.
- **Metasploitable 2:** alvo para FTP e SMB.
- **DVWA:** aplicação Web vulnerável.
- **VirtualBox:** rede Host-only.

## Técnicas
| Técnica | Funcionamento |
|---|---|
| Brute Force | Testa várias combinações de credenciais. |
| Password Spraying | Testa poucas senhas contra vários usuários. |
| Enumeração SMB | Identifica usuários e compartilhamentos. |
| Wordlists | Arquivos com candidatos a usuários e senhas. |

## Comandos

**Listar compartilhamentos SMB**
```bash
smbclient -L //IP_DO_ALVO -U USUARIO
```

**Acessar compartilhamento**
```bash
smbclient //IP_DO_ALVO/COMPARTILHAMENTO -U USUARIO
```

**Criar listas de teste**
```bash
echo -e 'user1\nuser2\nadmin' > users.txt
echo -e 'senha1\nsenha2\nsenha3' > pass.txt
```
`>` cria ou sobrescreve o arquivo; `>>` acrescenta conteúdo. No `smbclient`, `ls` lista arquivos, `get` baixa e `put` envia arquivos.

## Evidências

| Etapa | Capturas |
|---|---|
| Ambiente e enumeração | [VM](Images/Alcan%C3%A7ando%20a%20maquina%20Vulneravel.png) · [enum4linux](Images/comando_enum4linux.png) · [usuários](Images/Users_encontrados.png) · [lista](Images/Lista_enum_User_Pass.png) |
| FTP | [Brute Force FTP](Images/BruteForce_FTP.png) |
| DVWA | [DVWA](Images/DVWA.png) · [falha](Images/Falha_Login.png) · [sucesso](Images/Login_sucesso.png) · [combinação](Images/Combinacao_acesso.png) |
| SMB | [Brute Force](Images/BruteForce_SMB.png) · [acesso](Images/acesso_SMB.png) · [usuários e senhas](Images/Users_Passwords.png) |

## Mitigações
- **FTP:** desabilitar se desnecessário; preferir SFTP/FTPS.
- **Web:** MFA, rate limiting e monitoramento de falhas.
- **SMB:** restringir origens, revisar permissões e desabilitar SMBv1 quando possível.
- **Identidades:** senhas únicas e monitoramento de tentativas repetidas.

## Conclusão
O laboratório demonstrou como tentativas automatizadas atingem diferentes serviços e como enumeração e respostas de autenticação podem apoiar a detecção. O exercício reforçou a importância de controles de acesso e monitoramento.

## Referências
[Kali Linux](https://www.kali.org/) · [Medusa](http://www.foofus.net/jmk/medusa/medusa.html) · [Nmap](https://nmap.org/book/) · [DVWA](https://github.com/digininja/DVWA) · [Samba](https://www.samba.org/)
