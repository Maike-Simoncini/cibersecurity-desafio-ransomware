# Ransomware em Python 🔒

Este projeto foi desenvolvido como parte do desafio **"Entendendo um Ransomware na Prática com Python"**, proposto pela **[Digital Innovation One (DIO)](https://digitalinnovation.one/)**. O objetivo é compreender, de forma educacional, como funciona um ransomware simples utilizando criptografia simétrica.

> ⚠️ **Este código é exclusivamente para fins educacionais e de estudo.**  
> **Nunca utilize este tipo de ferramenta em sistemas reais.**

---

## 🎯 Objetivos

- Implementar um script capaz de **criptografar** um arquivo usando o algoritmo AES no modo CTR.
- Criar um script capaz de **descriptografar** o mesmo arquivo, desde que a chave correta seja fornecida.
- Entender os riscos e mecanismos por trás de ataques de ransomware.
- Praticar versionamento de código com **Git** e **GitHub**.
- Documentar o raciocínio técnico de forma clara e profissional.

---

## 📁 Estrutura do Projeto

```
.
├── encrypter.py        # Script para criptografar o arquivo
├── decrypter.py        # Script para descriptografar o arquivo
├── teste.txt           # Arquivo de exemplo (criado manualmente)
├── README.md           # Este arquivo
└── /images/            # (Opcional) Capturas de tela
```

---

## 🛠️ Pré-requisitos

- Python 3.x instalado
- Biblioteca `pyaes` instalada

### Instalação da dependência

```bash
pip install pyaes
```

---

## ▶️ Como Executar

### 1. Crie o arquivo de teste

Crie um arquivo chamado `teste.txt` com o conteúdo:

```
alo brasil
```

Você pode fazer isso via terminal:

**Linux / macOS / WSL:**
```bash
echo "alo brasil" > teste.txt
```

**Windows (CMD):**
```cmd
echo alo brasil > teste.txt
```

### 2. Criptografar o arquivo

Execute o script de criptografia:

```bash
python encrypter.py
```

Após a execução:
- O arquivo `teste.txt` será **apagado**.
- Um novo arquivo `teste.txt.ransomwaretroll` será criado com o conteúdo criptografado.

### 3. Descriptografar o arquivo

Execute o script de descriptografia:

```bash
python decrypter.py
```

Após a execução:
- O arquivo `teste.txt.ransomwaretroll` será **apagado**.
- O arquivo original `teste.txt` será **restaurado** com o conteúdo `"alo brasil"`.

---

## 🔐 Sobre a Chave de Criptografia

- A chave usada é: `b"testeransomwares"` (16 bytes).
- O modo de operação é **AES-CTR** via a biblioteca `pyaes`.
- **AES-CTR não requer padding**, o que o torna ideal para este exemplo simples.
- Em um cenário real, a chave seria mantida em segredo pelo atacante — aqui, ela está hardcoded para fins didáticos.

---

## 📚 Recursos Utilizados

- Repositório base do instrutor: [github.com/cassiano-dio/cibersecurity-desafio-ransomware](https://github.com/cassiano-dio/cibersecurity-desafio-ransomware)
- Apresentação do curso: *Criando um Ransomware em Python.pptx*
- Documentação da biblioteca `pyaes`: [https://pypi.org/project/pyaes/](https://pypi.org/project/pyaes/)
