# 🔎 Crawle Telefone

Projeto desenvolvido em **Python** para estudo de **Web Crawling, Web Scraping, Expressões Regulares e automação de coleta de dados na web**.

O projeto reúne diferentes implementações de crawlers capazes de percorrer páginas, encontrar links e extrair informações específicas, como **endereços de e-mail e números de telefone**.

## 📌 Sobre o projeto

O projeto foi desenvolvido como parte dos meus estudos em **Engenharia de Software**, com o objetivo de entender na prática como um crawler funciona e como páginas da web podem ser analisadas e processadas automaticamente.

O repositório possui três implementações principais:

* `web_crawler.py` — crawler básico para percorrer páginas e coletar links;
* `crawler.py` — crawler voltado para encontrar e armazenar números de telefone;
* `email_finder.py` — crawler capaz de percorrer páginas e identificar endereços de e-mail.

---

## 🛠️ Tecnologias utilizadas

* **Python 3**
* **Requests** — realização de requisições HTTP;
* **BeautifulSoup** — análise e processamento do HTML;
* **Regex (`re`)** — identificação de padrões, como telefones e e-mails;
* **Threading** — execução de múltiplas tarefas simultaneamente.

## O projeto utiliza `requests` e `BeautifulSoup` nos três crawlers para realizar requisições e interpretar o conteúdo HTML.

# 📂 Estrutura

```text
Crawle-telefone/
│
├── crawler.py
├── email_finder.py
├── web_crawler.py
└── README.md
```

### `web_crawler.py`

É a implementação mais simples do projeto.

O crawler recebe uma URL pelo terminal, acessa a página, identifica os links absolutos encontrados nas tags `<a>` e adiciona novas URLs à fila de crawling.

Também possui uma opção `-g`, utilizada para registrar as URLs visitadas em um arquivo `links.txt`.

### `email_finder.py`

É uma evolução do crawler, adicionando a capacidade de procurar **endereços de e-mail** no conteúdo HTML.

Os e-mails são encontrados utilizando uma expressão regular e armazenados na lista `EMAILS`, evitando adicionar o mesmo endereço mais de uma vez.

### `crawler.py`

É a implementação voltada para a busca de **números de telefone**.

O programa acessa uma página de anúncios de automóveis, encontra os links dos anúncios e posteriormente acessa cada página para procurar números de telefone utilizando uma expressão regular.
Os números encontrados são armazenados em `telefones.csv`.

Além disso, essa implementação utiliza **10 threads** para realizar a descoberta dos telefones de forma concorrente.

---

# ⚙️ Funcionamento

De maneira geral, o fluxo dos crawlers é:

```text
             URL inicial
                  │
                  ▼
          Requisição HTTP
                  │
                  ▼
             HTML da página
                  │
                  ▼
          BeautifulSoup
                  │
                  ▼
          Encontrar links
                  │
                  ▼
          Novas páginas
                  │
                  ▼
        Extrair informações
             /         \
            /           \
       E-mails       Telefones
```

## O crawler mantém uma lista de URLs que ainda precisam ser processadas e um conjunto de URLs que já foram visitadas. Isso permite evitar o processamento repetido das mesmas páginas.

# 🚀 Como executar

## 1. Clone o repositório

```bash
git clone https://github.com/Bruno-dev1/Crawle-telefone.git
```

```bash
cd Crawle-telefone
```

## 2. Instale as dependências

```bash
pip install requests beautifulsoup4
```

---

## 🔗 Web Crawler

Para executar o crawler básico:

```bash
python web_crawler.py <URL>
```

Exemplo:

```bash
python web_crawler.py https://example.com
```

Para utilizar a opção de geração do arquivo `links.txt`:

```bash
python web_crawler.py <URL> -g
```

## O parâmetro é verificado pelo programa e, quando utilizado, as URLs processadas são adicionadas ao arquivo `links.txt`.

## 📧 Email Finder

Execute:

```bash
python email_finder.py <URL>
```

Exemplo:

```bash
python email_finder.py https://example.com
```

O programa percorre as páginas encontradas e imprime os e-mails identificados no conteúdo.

---

## 📞 Crawler de telefones

O `crawler.py` possui uma URL de destino configurada diretamente no código:

```python
DOMINIO = "https://django-anuncios.solyd.com.br"
URL_AUTOMOVEIS = "https://django-anuncios.solyd.com.br/automoveis/"
```

Ao executar:

```bash
python crawler.py
```

o programa acessa a página de automóveis, encontra os anúncios, acessa cada anúncio e procura números de telefone.
Os telefones encontrados são registrados no arquivo:

```text
telefones.csv
```

---

# 🧠 Conceitos estudados

Este projeto permite praticar vários conceitos importantes de programação e desenvolvimento:

### HTTP

Utilização da biblioteca `requests` para realizar requisições HTTP e obter o conteúdo das páginas.

### HTML Parsing

Utilização do **BeautifulSoup** para transformar o HTML recebido em uma estrutura que pode ser pesquisada pelo programa.

### Web Crawling

O programa começa com uma URL e encontra outras páginas através dos links presentes no HTML.

### Expressões Regulares

O `email_finder.py` utiliza regex para identificar e-mails, enquanto o `crawler.py` utiliza regex para encontrar números de telefone.

### Estruturas de dados

O projeto utiliza estruturas como:

```python
list
set
```

para controlar URLs pendentes, URLs já visitadas e informações encontradas.

### Concorrência

O crawler de telefones utiliza `threading` e cria **10 threads** para processar os anúncios.

---

# ⚠️ Uso responsável

Este projeto foi desenvolvido para **fins educacionais** e para estudar conceitos de crawling e scraping.

Ao utilizar crawlers em sites reais, é importante respeitar:

* Termos de uso do site;
* `robots.txt`, quando aplicável;
* Limites de requisições;
* Privacidade dos usuários;
* Legislação aplicável;
* Direitos dos proprietários dos dados.

Evite utilizar a ferramenta para coleta abusiva ou utilização indevida de dados pessoais.


Algumas melhorias que podem ser implementadas futuramente:

* [ ] Melhorar o tratamento de exceções;
* [ ] Adicionar controle de profundidade do crawler;
* [ ] Implementar limite de páginas visitadas;
* [ ] Adicionar suporte para URLs relativas;
* [ ] Melhorar a identificação de e-mails;
* [ ] Melhorar a identificação de diferentes formatos de telefone;
* [ ] Adicionar testes automatizados;
* [ ] Adicionar argumentos de linha de comando com `argparse`;
* [ ] Melhorar o controle de concorrência;
* [ ] Adicionar logs;
* [ ] Criar uma interface de terminal mais completa.

---

# 👨‍💻 Autor

**Bruno Santiago**

Estudante de **Engenharia de Software na UEPA**.


---

⭐ **Se o projeto foi útil para seus estudos, deixe uma estrela no repositório!**
