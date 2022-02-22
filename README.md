# Projeto TrybeWallet

Neste projeto foi desenvolvido uma carteira de controle de gastos, sendo possível:
  - Adicionar, remover e editar um gasto;
  - Visualizar uma tabelas com seus gastos;
  - Visualizar o total de gastos convertidos para uma moeda de escolha;<br>

  Este projeto é foi feito durante o curso de Desenvolvimento Web FullStack da [Trybe](https://www.betrybe.com/).

# Tecnologias utilizadas: <br/>
![Javascript](https://img.shields.io/badge/JavaScript-323330?style=for-the-badge&logo=javascript&logoColor=F7DF1E)
![ReactJs](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Redux](https://img.shields.io/badge/Redux-593D88?style=for-the-badge&logo=redux&logoColor=white)
# API de Cotações de Moedas

Para desenvolver esta aplicação foi utilizada a API  _awesomeapi API de Cotações_
- https://economia.awesomeapi.com.br/json/all

- [Documentação](https://docs.awesomeapi.com.br/api-de-moedas).
# Requisitos do projeto - Definidos pela [Trybe](https://www.betrybe.com/).
## Lista de requisitos
### Página de Login

Crie uma página para que a pessoa usuária se identifique, com email e senha. Esta página deve ser a página inicial de seu aplicativo.

  ![image](login.gif)

#### 1. Crie uma página inicial de login com os seguintes campos e características:

  * A rota para esta página deve ser ‘/’.

  * Você deve criar um local para que a pessoa usuária insira seu email e senha.

  * Crie um botão com o texto ‘Entrar’.
#### 2. Realize as seguintes verificações nos campos de email, senha e botão:

  * O email está no formato válido, como 'alguem@alguem.com'.

  * A senha possui 6 ou mais caracteres.

  * Salve o email no estado da aplicação, com a chave ***email***, assim que a pessoa usuária logar.

  * A rota deve ser mudada para '/carteira' após o clique no botão '**Entrar**'.
#### 3. Utilize o Redux para salvar no estado global as informações da pessoa logada

  * Salve o email no estado da aplicação, com a chave email, assim que o usuário logar.

  * A rota deve ser mudada para `/carteira` quando o login for efetuado com sucesso.

  O que será testado:
  ```
  - O estado global possui a chave `email` no formato esperado
  - A rota deve ser mudada para `/carteira` após o clique no botão
  ```
---
### Página da Carteira

Crie uma página para gerenciar a carteira de gastos em diversas moedas, e que traga a despesa total em uma moeda só. Esta página deve ser renderizada por um componente chamado ***Wallet***.

  ![image](carteira.gif)
---
### Configurando sua página

#### 4. Crie uma página para sua carteira com as seguintes características:

  * A rota para esta página deve ser `/carteira`

  * O componente deve se chamar Wallet e estar localizado na pasta `src/pages` no arquivo `Wallet.js`
### Header (cabeçalho)

#### 5. Crie um header para a página de carteira contendo as seguintes características:

  * Um elemento que exiba o email da pessoa usuária que fez login.

  ```
  Dica: você deve pegar o email do estado global da aplicação (no Redux)
  ```

  * Um campo com a despesa total gerada pela lista de gastos.

    * Inicialmente esse campo deve exibir o valor `0`

  * Um campo que mostre qual câmbio está sendo utilizado, que será neste caso será 'BRL'.
### Formulário de adição de Despesa
#### 6. Desenvolva um formulário para adicionar uma despesa contendo as seguintes características:

  * Um campo para adicionar valor da despesa.

    * O campo deverá ter a label `Valor`.

  * Um campo de texto para adicionar a descrição da despesa.

    * O campo deverá ter a label `Descrição`.

  * Um campo de select para adicionar em qual moeda será registrada a despesa.

    * O campo deverá ter a label `Moeda`.

    * O campo deverá ser um `<select>`.

    * As opções do select serão preenchidas através da consulta à API. Isso será feito em um requisito mais a frente. Nesse momento você pode deixar o `<select>` vazio.

  * Um campo para adicionar qual método de pagamento será utilizado.

    * O campo deverá ter a label `Método de pagamento`.

    * Este campo deve ser um `<select>`. A pessoa usuária deve poder escolher entre os campos: 'Dinheiro', 'Cartão de crédito' e 'Cartão de débito'.

  * Um campo para selecionar uma categoria (tag) para a despesa.

    * Este campo deve ser um `<select>`. A pessoa usuária deve poder escolher entre os campos: 'Alimentação', 'Lazer', 'Trabalho', 'Transporte' e 'Saúde'.

    * O campo deverá ter a label `Tag`.
---
#### 7. Implemente a lógica para preencher as opções do campo "Moedas", buscando as siglas das moedas da API:

  * Ao entrar na página `/carteira`, você deverá fazer uma requisição para a API das moedas e preencher as opções do `<select>` de "Moedas" com os valores retornados. Utilizando as siglas das moedas.

  * As opções devem conter os valores: 'USD', 'CAD', 'EUR', 'GBP', 'ARS', 'BTC', 'LTC', 'JPY', 'CHF', 'AUD', 'CNY', 'ILS', 'ETH' e 'XRP'.

    * Esses valores devem vir da API através do endpoint: https://economia.awesomeapi.com.br/json/all.

    * Remova das informações trazidas pela API a opção 'USDT' (Dólar Turismo).
----
#### 8. Desenvolva a opção de "Adicionar despesa" na sua tabela de gastos

  * Desenvolva a funcionalidade do botão "Adicionar despesa" de modo que ao clicar no botão, as seguintes ações sejam executadas:
    
    * Os valores dos campos devem ser salvos no estado da aplicação, na chave ***expenses***, dentro de um array contendo todos gastos que serão adicionados:

      * O `id` da despesa **deve** ser um número sequencial, começando em 0. Ou seja: a primeira despesa terá id 0, a segunda terá id 1, a terceira id 2, e assim por diante.

      * Você deverá salvar a cotação do câmbio feita no momento da adição para ter esse dado quando for efetuar uma edição do gasto. Caso você não tenha essa informação salva, o valor da cotação trazida poderá ser diferente do obtido anteriormente.

    * Após adicionar a despesa, atualize a soma total das despesas. Essa informação deve ficar no header dentro do elemento
### Tabela de Gastos

#### 9. Desenvolva uma tabela com os gastos contendo as seguintes características:

  * A tabela deve possuir um cabeçalho **exatamente** com os campos Descrição, Tag, Método de pagamento, Valor, Moeda, Câmbio utilizado, Valor convertido, Moeda de conversão e Editar/Excluir

  * Atente-se ao formato semântico da tabela. Utilize os elementos corretos para o cabeçalho, para as linhas e para as células.

  * A tabela deve ser alimentada pelo estado da aplicação, que estará disponível na chave ***expenses*** que vem do reducer `wallet`.

    * O campo de Moeda e Moeda de Conversão deverão conter o nome da moeda. Portanto, ao invés de 'USD' ou 'EUR', deve conter "Dólar Comercial" e "Euro", respectivamente

    * Por padrão, o campo 'Moeda de conversão' exibirá 'Real'

    * Atenção também às casas decimais dos campos. Como são valores contábeis, eles devem apresentar duas casas após a vírgula. Arredonde sua resposta somente na hora de renderizar o resultado, e para os cálculos utilize sempre os valores vindos da API (utilize o campo `ask` que vem da API).

    * Utilize sempre o formato `0.00` (número - ponto - duas casas decimais)
#### 10. Crie um botão para deletar uma despesa da tabela contendo as seguintes características:


   ![image](btnExcluir.gif)

  * O botão deve estar na linha da tabela.

  * Ao ser clicado, o botão deleta a linha da tabela, alterando o estado global.
#### 11. Crie um botão para editar uma despesa da tabela contendo as seguintes características:

   ![image](btnEditar.gif)

  * O botão deve estar dentro da linha da tabela

  * Ao ser clicado, o botão habilita um formulário para editar a linha da tabela. Ao clicar em "Editar despesa" ela é atualizada, alterando o estado global.

    * O botão para submeter a despesa para edição deverá conter **exatamente** o texto "Editar despesa"

    **Atenção**: o câmbio utilizado na edição deve ser o mesmo do cálculo feito na adição do gasto.
