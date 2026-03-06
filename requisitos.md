# InfoBairro – Documento de Requisitos do Sistema

---

# 1. Contexto do Sistema

O **InfoBairro** é uma aplicação web que permite aos usuários visualizar, avaliar e comentar sobre bairros por meio de um **mapa interativo integrado à API do Google Maps**.

O sistema permite:

- Cadastro e autenticação de usuários  
- Cadastro, edição e exclusão de bairros  
- Visualização de bairros no mapa com pings geográficos  
- Avaliação de bairros por categorias  
- Comentários na aba específica de cada bairro  
- Filtro e pesquisa de bairros por nome ou critérios de avaliação  

O sistema será utilizado por:

- **Administradores**
- **Administradores Master**
- **Usuários**

---

# 2. Perfis de Usuário

O sistema possui três perfis de acesso:

- **ADMIN MASTER**
- **ADMIN**
- **USER**

## Permissões

| Operação | ADMIN MASTER | ADMIN | USER |
|--------|--------|--------|--------|
| Registrar usuário | ✔ | ✔ | ✔ |
| Visualizar informações dos bairros | ✔ | ✔ | ✔ |
| Navegar pelo mapa | ✔ | ✔ | ✔ |
| Comentar | ✔ | ✔ | ✔ |
| Curtir comentário | ✔ | ✔ | ✔ |
| Avaliar bairro | ✔ | ✔ | ✔ |
| Criar bairros | ✔ | ✔ | ✖ |
| Editar bairros | ✔ | ✔ | ✖ |
| Excluir bairro | ✔ | ✖ | ✖ |
| Moderar comentários | ✔ | ✔ | ✖ |
| Gerenciar usuários (bloquear/excluir) | ✔ | ✔ | ✖ |
| Gerenciar administradores | ✔ | ✖ | ✖ |
| Filtrar bairros por critério | ✔ | ✔ | ✔ |

---

# 3. Requisitos Funcionais (RF)

## Módulo 1 – Bairro

**RF01** – O sistema deve permitir que o **ADMIN** cadastre novos bairros.  

**RF02** – O sistema deve permitir que o **ADMIN** edite as informações de um bairro.  

**RF03** – O sistema deve permitir que usuários visualizem os bairros cadastrados no mapa.  

**RF04** – O sistema deve permitir que o **ADMIN MASTER** exclua bairros.

---

## Módulo 2 – Avaliação

**RF05** – O sistema deve permitir que o usuário avalie bairros nos seguintes critérios:

- Segurança  
- Transporte  
- Infraestrutura  
- Educação  
- Saúde  
- Comércio  
- Lazer  
- Serviços de Entrega  

**RF06** – O sistema deve calcular e exibir a **média das avaliações de cada bairro**.

**RF07** – O sistema deve permitir que o usuário visualize as avaliações já realizadas.

---

## Módulo 3 – Comentário

**RF08** – O sistema deve permitir que o usuário publique comentários na aba de comentários de cada bairro.

**RF09** – O sistema deve permitir que usuários visualizem os comentários publicados.

**RF10** – O sistema deve permitir que usuários curtam comentários.

**RF11** – O sistema deve identificar automaticamente se o usuário é **morador ou visitante do bairro** e exibir o selo correspondente no comentário.

**RF12** – O sistema deve submeter automaticamente todos os comentários a uma **verificação baseada na Política de Comunidade**.

---

## Módulo 4 – Usuário

**RF13** – O sistema deve permitir que o usuário realize cadastro utilizando **e-mail e senha válidos**.

**RF14** – O sistema deve permitir que o usuário realize **login utilizando e-mail e senha cadastrados**.

**RF15** – O sistema deve permitir que administradores **gerenciem contas de usuários (bloquear ou excluir)**.

---

## Módulo 5 – Endereço

**RF16** – O sistema deve permitir que o usuário cadastre seu **endereço para validação de morador ou visitante**.

**RF17** – O sistema deve utilizar o endereço cadastrado para determinar o **selo exibido nos comentários**.

---

# 4. Regras de Negócio (RN)

## Autenticação

**RN01** – O e-mail do usuário deve ser **único no sistema**.

**RN02** – A senha deve possuir **no mínimo 8 caracteres** e conter pelo menos:

- 1 letra maiúscula  
- 1 letra minúscula  
- 1 número  

**RN03** – O acesso a funcionalidades administrativas deve ser restrito a usuários com perfil **ADMIN** ou **ADMIN MASTER**.

---

## Bairros

**RN04** – O nome do bairro **não pode ser duplicado** no sistema.

**RN05** – Todas as informações obrigatórias do bairro devem ser preenchidas no momento do cadastro.

**RN06** – A coordenada geográfica (**latitude e longitude**) deve ser definida no momento da criação do bairro.

**RN07** – Dois bairros **não podem possuir a mesma coordenada geográfica**.

**RN08** – Apenas **ADMIN MASTER** pode excluir bairros.

---

## Avaliações

**RN09** – Um usuário pode realizar **apenas uma avaliação por critério em cada bairro**.

**RN10** – A **média das avaliações** deve ser recalculada automaticamente após cada nova avaliação ou edição.

---

## Comentários

**RN11** – Comentários que violem a **Política de Comunidade** devem ser encaminhados automaticamente para **moderação**.

**RN12** – Comentários devem respeitar o **limite máximo de 800 caracteres**.

**RN13** – Não são permitidos comentários contendo:

- Divulgação de serviços  
- Links externos  
- Endereços de e-mail  
- Redes sociais  

**RN14** – Comentários são exibidos de forma **anônima para outros usuários**, mantendo a identidade visível apenas para administradores.

---

# 5. Endpoints da API

## Autenticação
