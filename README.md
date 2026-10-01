# New Agenda 2.0

Sistema web de agenda desenvolvido em **PHP**, com **MySQL** para armazenamento dos dados. O projeto possui cadastro e autenticação de usuários, gerenciamento de contatos e geração de relatórios em PDF.

## Tecnologias utilizadas

* PHP 8.1 ou superior
* MySQL 8.0 ou superior
* PDO para conexão com o banco de dados
* HTML, CSS e JavaScript
* Bootstrap 4 / AdminLTE
* Dompdf para geração de documentos PDF

## Estrutura principal

```text
agendaPhp/
├── config/
│   └── conexao.php          # Configuração da conexão com o banco
├── paginas/
│   ├── home.php             # Área principal após o login
│   └── conteudo/            # Funcionalidades da agenda
├── includes/                # Cabeçalho, rodapé e logout
├── plugins/                 # Bibliotecas JavaScript/CSS utilizadas pelo sistema
├── dist/                    # Arquivos do AdminLTE
├── img/                     # Imagens e avatares
├── index.php                # Tela de login
├── cad_user.php             # Cadastro de usuário
└── new_agenda.sql            # Estrutura e dados iniciais do banco
```

## Requisitos

Antes de executar o projeto, tenha instalado um ambiente de servidor local, como:

* **XAMPP** (Apache + PHP + MySQL/MariaDB), ou
* **LAMP** (Linux + Apache + PHP + MySQL).

Também é necessário habilitar o **PDO MySQL** no PHP.

## Como instalar e executar

### 1. Copie o projeto para o servidor

No XAMPP, coloque a pasta `agendaPhp` dentro de:

```text
C:\xampp\htdocs\
```

No Linux com Apache, normalmente:

```text
/var/www/html/
```

### 2. Crie o banco de dados

Abra o **phpMyAdmin** ou o cliente MySQL e crie um banco chamado:

```text
new_agenda
```

### 3. Importe o banco de dados

No phpMyAdmin:

1. Acesse o banco `new_agenda`.
2. Clique em **Importar**.
3. Selecione o arquivo `new_agenda.sql`, localizado na raiz do projeto.
4. Execute a importação.

O arquivo SQL já contém a estrutura das tabelas e dados iniciais necessários para testar o sistema.

Também é possível importar pelo terminal:

```bash
mysql -u SEU_USUARIO -p new_agenda < new_agenda.sql
```

### 4. Configure a conexão com o banco

Abra:

```text
config/conexao.php
```

A configuração utilizada pelo projeto é:

```php
define('DB_CONFIG', [
    'host'   => 'localhost',
    'dbname' => 'new_agenda',
    'user'   => 'admin',
    'pass'   => 'bdjmf'
]);
```

Caso seu MySQL utilize outro usuário ou senha, altere os valores de `user` e `pass` para as credenciais do seu ambiente.

> **Importante:** em um ambiente de produção, não mantenha credenciais reais diretamente no código-fonte. Utilize variáveis de ambiente ou outra forma segura de configuração.

### 5. Inicie o servidor

No XAMPP, inicie:

* Apache
* MySQL

Depois, abra no navegador:

```text
http://localhost/agendaPhp/
```

Se a pasta estiver com outro nome dentro do servidor, substitua `agendaPhp` pelo nome correspondente.

## Acesso ao sistema

Após importar o banco, a tabela `tb_user` já possui usuários de teste cadastrados no arquivo `new_agenda.sql`.

Para testar o login, utilize um dos e-mails presentes na tabela `tb_user` e a senha correspondente ao cadastro. As senhas armazenadas no banco estão protegidas por **hash**, portanto não devem ser substituídas diretamente por texto puro.

Também é possível criar um novo usuário pela opção **"Se ainda não tem cadastro clique aqui!"** disponível na tela de login.

## Funcionalidades

* Login e logout de usuários
* Cadastro de usuários
* Cadastro de contatos
* Edição de contatos
* Exclusão de contatos
* Perfil do usuário
* Relatório de contatos
* Geração de relatório em PDF
* Interface baseada em AdminLTE e Bootstrap

## Banco de dados

O banco utilizado pelo projeto é:

```text
new_agenda
```

Principais tabelas:

* `tb_user` — armazena os usuários do sistema.
* `tb_contatos` — armazena os contatos cadastrados e relacionados aos usuários.

O relacionamento entre usuários e contatos é definido pelo campo `id_user`.

## Solução de problemas

### Erro de conexão com o banco

Verifique se:

1. O MySQL está em execução.
2. O banco `new_agenda` foi criado.
3. O arquivo `new_agenda.sql` foi importado corretamente.
4. Usuário e senha em `config/conexao.php` estão corretos.
5. O PHP possui suporte a PDO MySQL habilitado.

### Página PHP não abre corretamente

Confirme se o projeto está dentro do diretório do servidor web e se o Apache está em execução. O projeto deve ser acessado pelo endereço `http://localhost/...`, e não abrindo o arquivo `.php` diretamente pelo gerenciador de arquivos.

## Observação

O projeto já possui diversas bibliotecas front-end e dependências PHP incluídas no próprio repositório. Caso seja necessário reinstalar as dependências do Dompdf, o diretório `paginas/conteudo/pdf/` possui o arquivo `composer.json` correspondente.

## Licença

Este projeto é destinado a fins acadêmicos e de estudo.
