[![Build Status](https://travis-ci.org/soutomario/reactive-github.svg?branch=develop)](https://travis-ci.org/soutomario/reactive-github)

# Conceitos do React
- ajax?
- utilizando outras libs para manipular o dom?
- Statefull vs Stateless?
> Statefull: Manipula estado | Stateless: Renderiza Informação

- smart vs dumb?
> Statefull vs Stateless  

- container vs presentational?
> Statefull vs Stateless  

# Base
- App que consome a API do GitHub: https://api.github.com/
- Documentação da API: http://developer.github.com/v3

# 01 - Fazer toda a marcação do app
- Sempre começar em um componente stateless, fazendo toda a marcação da necessária para ai então fazer as ações e separar em componentes

# 02 - Separar os componentes
- Separar os componentes e marcar as `propTypes`

> *propTypes* definem os tipos que as propriedades que os componentes recebem devem ter Ex: Um componente de botão que recebe uma propriedade handleClick que é atribuida ao evento onClick, necessariamente precisa ser uma função.

- Só transformar em Statefull, componentes que precisem de ações (ou quando começar a definição dos estados da aplicação)

# 03 - Criar o estado da aplicação
- O componente `App`, é definido como o principal da aplicação, ele é responsável por controlar o estado e passar o estado para os componentes
- Por ser o componente principal e ser statefull ele é definido com uma `class` do ES6
```js
import React, { Component } from 'react'
class App extends Component {
  render () {
    return <div>My app</div>
  }
}
```
- O Fluxo de Informação fica o seguinte:

* App - Statefull define os estados de todos os componentes passando como props para o AppContainer
* AppContainer - Define os propTypes das props que ele recebe e repassa as mesmas para os componentes mais internos. E assim segue o fluxo.
* Cada componente tem atribuida de maneira estática as props que serão recebidas dinamicamente pela api.

# 04 - Fazer o request dos dados do usuário
- Adicionada a biblioteca Ajax do @fdaciuk
- Criação do evento de consultar a API do github a partir do componente `search.js`

# 05 - Populando corretamente os dados do usuário
- Trazer a função de consulta da API pra o componente `App` e passar como prop em um handleSearch para o componente de busca
- Popular dados dos repositórios

# 06 - Eventos para complementar a UX
- Habilitar e desabilitar o campo de busca
- Como o foco do React não é manipulação de DOM, ele gerencia eventos passando um `null` para o objeto de evento. Isso ocorre pelo fato dele reautilizar o mesmo, por isso é necessário criar uma variavel que receba o target do evento, ou utilizar e.persist() (para o react persistir com os dados do evento) 

# 07 - Atribuição de loader
-  Como cada componente é individual, criamos um estado que informa se está acontecendo uma transição de dados ou não e ai criamos um loader por exemplo.

# 08 - Organizando as propTypes
