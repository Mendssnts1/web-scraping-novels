
---

# Web Scraping para Sites de Novels Chinesas

Este projeto é um script de **web scraping** desenvolvido para facilitar o acesso e leitura de **novels chinesas**. O objetivo é coletar os capítulos das novels diretamente de sites de leitura, organizá-los e salvá-los em um arquivo `.txt`, permitindo que o usuário leia offline de forma prática e organizada.

## Funcionalidades

- **Exibe uma lista de novels altamente recomendadas** para leitura.
- **Permite ao usuário escolher uma novel da lista** com base em uma tabela.
- **Seleciona o número de capítulos a serem lidos** e o capítulo inicial.
- **Salva os capítulos selecionados em um arquivo `.txt`**, com título e conteúdo formatados para fácil leitura.
- **Organiza o conteúdo de forma que o usuário possa ler offline** sem depender de uma conexão com a internet.

## Estrutura do Projeto

O script é dividido em diversos módulos que realizam tarefas específicas de web scraping e processamento de dados. As principais funções são:

### 1. **GET TOTAL PAGES**
   Este módulo determina o número total de páginas disponíveis para uma novel no site, essencial para mapear todos os capítulos.

   ```python
   def get_total_pages(novel_url, header):
       # Função para pegar o número total de páginas
   ```

### 2. **ALL CHAPTERS ON PAGES**
   Coleta todos os links de capítulos de uma novel, página por página.

   ```python
   def get_all_chapter_links(novel_url, header):
       # Função para pegar todos os links de capítulos
   ```

### 3. **SCRAPING OF CHAPTER CONTENT**
   Obtém o título e conteúdo de um capítulo específico.

   ```python
   def scrape_chapter_content(chapter_url, header):
       # Função para extrair título e conteúdo de um capítulo
   ```

### 4. **SAVES THE CHAPTER IN FILE TXT**
   Salva os capítulos extraídos em um arquivo `.txt`, com títulos e conteúdos bem formatados.

   ```python
   def saved_chapter(novel_url, start_chapter, num_chapters, output_file, header):
       # Função para salvar os capítulos em um arquivo
   ```

### 5. **SYNOPSIS FROM EVERY NOVEL**
   Coleta a sinopse de cada novel, permitindo que o usuário leia um resumo antes de decidir qual livro escolher.

   ```python
   def scrape_sinopse(chapter_url, header):
       # Função para coletar sinopse de cada novel
   ```

### 6. **RATINGS AND TOTAL WATCHED**
   Obtém a classificação (rating) média e o número total de visualizações de cada novel, ajudando o usuário a escolher novels populares e bem avaliadas.

   ```python
   def scrape_rating(chapter_url, header):
       # Função para pegar rating e número de visualizações
   ```

### 7. **DATA FRAME PREVIEW**
   Exibe uma tabela com todas as novels disponíveis, suas sinopses, ratings e links, estruturados em um DataFrame do `pandas`.

   ```python
   data = pd.DataFrame(list(a.items()), columns=["titulo", "Url"])
   data["Sinopse"] = data["Url"].apply(lambda url: scrape_sinopse(url, header))
   data["Rating"] = data["Url"].apply(lambda url: scrape_rating(url, header))
   ```

### 8. **INTERACTIVE USER INPUT FOR CHAPTER SELECTION**
   Permite ao usuário interagir com o script, escolhendo a novel, o número de capítulos e o capítulo inicial para começar a leitura.

   ```python
   choise_novel = int(input("De acordo com a tabela de novels, escolha a novel baseado no numero: "))
   num_chapters = int(input("Quantos capitulos vc quer ler?  "))
   start_chapter = int(input("Qual capitulo vc quer iniciar? "))
   ```

## Como Usar

1. **Clone o repositório**:
   ```bash
   git clone https://github.com/seu-usuario/web-scraping-novels.git
   cd web-scraping-novels
   ```

2. **Instale as dependências**:
   Crie um ambiente virtual (opcional) e instale as dependências necessárias:
   ```bash
   pip install -r requirements.txt
   ```

3. **Execute o script**:
   O script interativo permite que você escolha qual novel e quais capítulos deseja ler. Para rodá-lo, basta executar:
   ```bash
   python scraper.py
   ```

4. **Personalize o arquivo de saída**:
   O conteúdo dos capítulos selecionados será salvo em um arquivo `.txt` com o nome personalizado.

## Exemplo de Arquivo `.txt`

Após selecionar os capítulos desejados, o conteúdo será salvo em um arquivo como este:

```
[Capítulo 1] O Começo do Herói
Conteúdo do Capítulo 1...

[Capítulo 2] O Confronto
Conteúdo do Capítulo 2...
```

## Conclusão

Esse projeto visa proporcionar uma maneira fácil e eficiente de acessar novels chinesas e armazenar seu conteúdo de forma organizada para leitura offline. O código pode ser facilmente adaptado para outros tipos de scraping e projetos semelhantes.

## Tecnologias Utilizadas

- **requests**: Para realizar as requisições HTTP.
- **BeautifulSoup**: Para parseamento de HTML e extração de dados.
- **pandas**: Para organização e exibição dos dados coletados.
- **googletrans**: Para tradução de conteúdo, se necessário.

---

Essa descrição é clara, explicativa e oferece as informações necessárias para qualquer pessoa entender o funcionamento do seu projeto, além de fornecer instruções claras de uso. Adicione o arquivo `.txt` com os capítulos da novel para que os usuários vejam um exemplo real de como o conteúdo é estruturado.
