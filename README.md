Primeira coisa a se fazer é abir na pasta config/database.yml e mudar o data base para o correto que voce deseja usar seja no docker ou no computador o que eu vou usar esta no docker assim como os comentarios que vem com o rails nos diz precisamos do usuario , da password e porta eu como estou usando o banco de dados local usando docker basta rodar no terminal ``` docker ps
Found existing alias for "docker ps". You should use: "dps"
CONTAINER ID   IMAGE      COMMAND                  CREATED        STATUS       PORTS                                       NAMES
3f1834f3eaf4   postgres   "docker-entrypoint.s…"   5 months ago   Up 4 hours   0.0.0.0:5432->5432/tcp, :::5432->5432/tcp   postgres``` 
Aqui entao posso usar a imagem ja criada no meu docker e conectar no rails

Atencao 

Esse arquivo vai direto para o seu github por isso nunca use suas senhas de banco de dados ao inves disso use ou o aplication.yml ou o .env mas qual dos 2 usar no seu projeto ?

 Claro, irmão! Aqui vai o texto reformulado de forma **simples, direta** e com cara de artigo de README.md:

---

## ✅ Diferença entre `.env` e `application.yml` no Rails

No Ruby on Rails, usamos arquivos como `.env` ou `application.yml` para guardar **variáveis de ambiente** (senhas, tokens, chaves secretas). Ambos têm o mesmo propósito, mas funcionam de formas diferentes.

---

### 🔹 `.env` (usado com `dotenv-rails`)

* Formato simples: `NOME_VARIAVEL=valor`

* Exemplo:

  ```
  DATABASE_PASSWORD=123456
  SECRET_KEY_BASE=meu_segredo
  ```

* Carregado automaticamente com a gem [`dotenv-rails`](https://github.com/bkeepers/dotenv).

* Muito usado em projetos modernos e com deploys no Heroku ou Docker.

* ✅ Rápido, prático e direto ao ponto.

---

### 🔸 `application.yml` (usado com `figaro`)

* Formato YAML: `NOME_VARIAVEL: valor`

* Exemplo:

  ```yaml
  DATABASE_PASSWORD: 123456
  SECRET_KEY_BASE: meu_segredo
  ```

* Utiliza a gem [`figaro`](https://github.com/laserlemon/figaro).

* Também injeta as variáveis no `ENV`, mas é um pouco mais verboso.

* Era mais usado antigamente, antes do `dotenv` virar padrão.

---

### 📌 Qual usar?

Hoje em dia, o `.env` com `dotenv-rails` é a escolha mais comum e recomendada para a maioria dos projetos.

---

### ⚠️ Importante

Sempre adicione esses arquivos ao `.gitignore` para **não expor informações sensíveis** no GitHub:

```bash
# .gitignore
.env
config/application.yml
```

---

Nos vamos usar no nosso projeto o .env . como usar o .env basta na pasta raiz adicionar um novo arquivo .env nele deve conter as informacoes do .env.example
