
# Projeto Django com Variáveis de Ambiente

## Passo a Passo para Configurar o Arquivo `.env`

### 1. Instalar Dependências

Para carregar as variáveis de ambiente a partir de um arquivo `.env`, vamos usar a biblioteca `python-dotenv`. Primeiro, instale-a com o comando:

```bash
pip install python-dotenv
```

### 2. Criar o Arquivo `.env`

Na raiz do projeto, crie um arquivo chamado `.env`. Esse arquivo armazenará todas as informações sensíveis, como o nome do banco de dados, usuário, senha, entre outros.

```env
DB_NAME=nome_do_banco
DB_USER=usuario_do_banco
DB_PASSWORD=senha_do_banco
DB_HOST=localhost
DB_PORT=porta_do_bd

# Chave Secreta do Django
SECRET_KEY=sua_chave_secreta

# Debug (True para desenvolvimento, False para produção)
DEBUG=True
```

### 3. Configurar o `.gitignore`

Para garantir que o arquivo `.env` não seja enviado para o repositório Git, adicione-o ao arquivo `.gitignore`.

```plaintext
.env
```

Isso evitará que o arquivo `.env` seja incluído nos commits.

### 4. Carregar o `.env` no `settings.py`

No arquivo `settings.py` do seu projeto Django, importe e carregue as variáveis de ambiente. Adicione o seguinte código no início do arquivo:

```python
import os
from dotenv import load_dotenv

# Carrega as variáveis do arquivo .env
load_dotenv()
```

Agora, substitua as configurações sensíveis pelo uso das variáveis de ambiente. Por exemplo:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',  # Altere para o banco de dados que você usa
        'NAME': os.getenv('DB_NAME'),
        'USER': os.getenv('DB_USER'),
        'PASSWORD': os.getenv('DB_PASSWORD'),
        'HOST': os.getenv('DB_HOST'),
        'PORT': os.getenv('DB_PORT'),
    }
}

# Outras configurações sensíveis
SECRET_KEY = os.getenv('SECRET_KEY')
DEBUG = os.getenv('DEBUG') == 'True'
```

### 5. Testar a Configuração

Depois de configurar o `.env`, execute o servidor Django para confirmar que tudo está funcionando corretamente:

```bash
python manage.py runserver
```

Se tudo estiver configurado corretamente, o Django deve conseguir acessar o banco de dados e outras configurações sem problemas.

## Caso de erro desative o anti virus do seu pc, apos isso pode ativa-lo novamente
