# Sistema de Gerenciamento de Produtos

Este é um sistema desktop desenvolvido em **C# com Windows Forms** e **MySQL**, voltado para o gerenciamento completo de produtos. O sistema conta com funcionalidades de **autenticação, login, cadastro de usuários, recuperação de senha** e operações **CRUD** para produtos.

---

## Funcionalidades

### Login

* Permite autenticar com **nome de usuário** e **senha** ou **e-mail** e **senha**.

### Autenticação

* Senha criptografada com SHA256.
* Exibição do nome do usuário logado na tela principal após login ou cadastro.

### Cadastro de Usuário

* Cadastro de novos usuários com:

  * Nome completo
  * Nome de usuário
  * E-mail
  * CPF
  * Senha
* Validação de CPF e e-mail.
* Verificação se e-mail ou CPF já existem no banco.
* Redirecionamento automático para a tela de gerenciamento após cadastro.

### Recuperação de Senha

* Redefinição de senha por e-mail.
* Valida se o e-mail informado existe no banco antes de atualizar a senha.

### Gerenciamento de Produtos (CRUD)

* Exibe o nome do usuário logado.
* Cadastro de produtos com:

  * Nome do produto
  * Preço
  * Quantidade em estoque
  * Categoria (puxada da tabela `categorias` no banco de dados)
* Listagem de todos os produtos.
* Edição de produtos existentes.
* Exclusão de produtos.
* Busca por nome ou categoria em uma única barra de pesquisa.

---

## Estrutura do Projeto

* **FormCadastro**: Form principal que contém dois *UserControls* integrados:

  * **UC\_Login**: Tela de login.
  * **UC\_RecuperarSenha**: Tela de recuperação de senha.
* **FormGerenciamentoProdutos**: Form para as operações de CRUD de produtos.
* **Classes de domínio**:

  * `Produtos`: Responsável pelas operações de inserção, atualização, exclusão, listagem e busca de produtos.
  * `Usuarios`: Responsável pelas operações de cadastro, autenticação, recuperação de senha, criptografia de senha, e validações de CPF e e-mail.
* **ConexaoBD**: Classe responsável pela conexão com o MySQL.

---

## Estrutura de Classes

### Classe `Produtos`

Gerencia todas as operações relacionadas a produtos:

* `InserirProduto(string nome, decimal preco, int quantidade, int idCategoria)`
* `AtualizarProduto(int id, string nome, decimal preco, int quantidade, int idCategoria)`
* `ExcluirProduto(int id)`
* `ListarTodosProdutos()`
* `BuscarProdutoPorNomeOuCategoria(string termo)`

Esta classe representa cada produto com os atributos `Id`, `Nome`, `Preco`, `Quantidade` e `IdCategoria`, e centraliza toda a lógica de manipulação dos produtos no banco de dados.

### Classe `Usuarios`

Gerencia todas as operações relacionadas a usuários:

* `CadastrarUsuario(string nome, string nomeUsuario, string email, string cpf, string senha)`
* `LoginExiste(string login)`
* `ValidarLogin(string login, string senha)`
* `BuscarUsuarioAutenticado(string login)`
* `ValidarCPF(string cpf)`
* `VerificarEmail(string email)`
* `RedefinirSenha(string email, string novaSenha)`
* `CriptografarSenha(string senha)`

Esta classe é responsável pela gestão completa dos usuários do sistema, incluindo o cadastro com validações, login por nome de usuário ou e-mail, busca do usuário logado, criptografia da senha com SHA256, verificação da existência de login, CPF ou e-mail, e redefinição de senha com segurança.

---

## Tecnologias Utilizadas

* **C# (Windows Forms)**
* **MySQL**
* **MySql.Data Connector**
* **Criptografia SHA256**
* **Programação Orientada a Objetos**
* **UserControls para dinamismo da interface**

---

## Como Executar

1. Clone este repositório.
2. Abra o projeto no Visual Studio 2022.
3. Configure a string de conexão com o seu banco MySQL em `ConexaoBD.cs`.
4. Execute o script SQL para criar as tabelas:

   * `usuarios` (id\_usuario, nome, email, cpf, nome\_usuario, senha)
   * `categorias` (id\_categoria, nome\_categoria)
   * `produtos` (id\_produto, nome, preco, quantidade, id\_categoria)
5. Compile e execute o projeto.

---

## Autor

**Eloiza15** — Desenvolvedor do sistema

---

## Licença

MIT © 2025
