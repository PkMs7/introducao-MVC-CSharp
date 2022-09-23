# Passo a passo para criação de um projeto MVC com C#

## Preparando ambiente de trabalho

- **Passo 1:** Inicie o projeto no seu terminal (CLI) com o comando `dotnet new mvc`
- **Passo 2:** Para visualizar o projeto em seu navegador, use o seguinte comando `dotnet watch run`
- **Passo 3:** Inicie o Entity Framework no seu projeto com o comando `dotnet add package Microsoft.EntityFrameworkCore.{seuservidor}`
- **Obs.:** No **Passo 3** um ponto a ser observado: Se você não tem instalado o Entity Framework, instale na sua máquina com o comando `` (mais sobre como configurar clique aqui)
- **Passo 4:** Inicie também o pacote Design do Entity Framework `dotnet add package Microsoft.EntityFrameworkCore.Design`


## Preparando o banco de dados

- **Passo 1:** Crie suas models na pasta model de acordo com os dados que você usará no DataBase(DB).
- **Passo 2:** Crie sua pasta Context, onde ficarão seus códigos construtores do DB
- **Passo 3:** No arquivo _appsettings.Development.json_ configure o comando para iniciar suas migrations: 
    ```
    "ConnectionStrings": {
        "ConexaoPadrao": "Server=localhost\\sqlexpress; Initial Catalog={seucontext}Mvc; Integrated Security=True"
    }        
    ```
- **Passo 4:** No arquivo _Program.cs_ abaixo do comentário _Add services to the container._ configure o seguinte comando:
    ```
    builder.Services.AddDbContext<{seucontext}>(options => 
        options.UseSqlServer(builder.Configuration.GetConnectionString("ConexaoPadrao")));
    ```
- **Passo 5:** Crie agora suas migrations de acordo com a model que você criou. Use o comando `dotnet ef migrations add {nomeDaMigration}`
- **Passo 6:** Com a pasta migration criada agora crie os dados no seu DB com o seguinte comando `dotnet ef database update`

## Começando a programar

- **Passo 1:**