# Prática de Git & GitHub

Repositório criado para aprender e praticar os principais comandos do **Git** e **GitHub** de forma colaborativa.

## O que é Git?

Git é um sistema de controle de versão distribuído que permite rastrear mudanças no código-fonte ao longo do tempo. Com ele, você pode trabalhar em equipe sem perder nenhuma alteração.

## O que é GitHub?

GitHub é uma plataforma online que hospeda repositórios Git. Além de armazenar seu código na nuvem, o GitHub facilita a colaboração entre desenvolvedores através de funcionalidades como Pull Requests, Issues e Code Review.


## Comandos essenciais

| Comando | Descrição |
|---------|-----------|
| `git clone <url>` | Clona um repositório remoto |
| `git status` | Mostra o estado atual das alterações |
| `git add .` | Adiciona todas as alterações para commit |
| `git commit -m "msg"` | Cria um commit com uma mensagem |
| `git push` | Envia os commits para o repositório remoto |
| `git pull` | Atualiza o repositório local com as mudanças remotas |
| `git branch` | Lista as branches existentes |
| `git checkout -b <nome>` | Cria e muda para uma nova branch |
| `git log` | Mostra o histórico de commits |
| `git blame <arquivo>` | Mostra quem alterou cada linha de um arquivo |
| `git revert <hash>` | Reverte um commit específico |


## O que é um Pull Request?

Um Pull Request (PR) é um pedido para que suas alterações sejam revisadas e incorporadas ao código principal. Em vez de enviar mudanças direto para a `main`, você trabalha em uma **branch separada** e abre um PR no GitHub. Assim, outros membros da equipe podem revisar, comentar e aprovar antes do código ser aceito.

## O que é Merge?

Merge é o processo de **juntar** duas branches. Quando seu Pull Request é aprovado, o instrutor (ou você) faz o merge, as suas alterações passam a fazer parte da branch `main`. Se duas pessoas editaram o mesmo trecho de código, o Git avisa que existe um **merge conflict**, e você precisa decidir manualmente qual versão manter (ou combinar as duas).





---



.
# Atividades Práticas

As atividades estão organizadas em níveis progressivos. Complete cada nível antes de avançar para o próximo.

---

## Nível 1 — Primeiros Passos

### Atividade 1.1: Clone e crie sua branch

1. Clone este repositório:
   ```bash
   git clone https://github.com/TrilhaUFPB/learning-git.git
   cd learning-git
   ```
2. Crie uma branch com seu nome:
   ```bash
   git checkout -b seu-nome-sobrenome
   ```

### Atividade 1.2: Crie seu perfil

1. Dentro da pasta `profiles/`, crie um arquivo com seu nome: `seu-nome.md`
2. Preencha com suas informações pessoais seguindo o modelo:

   ```markdown
   # Seu Nome

   - **Curso:** Ciência da Computação
   - **Período:** 1º
   - **GitHub:** @seu-usuario
   - **Um fato curioso sobre você:** Eu já assisti 300 episódios de anime em um mês
   - **Tecnologia favorita:** Python
   - **Objetivo na área de tech:** Trabalhar com inteligência artificial
   ```

3. Faça o commit e push:
   ```bash
   git add .
   git commit -m "adiciona perfil de Seu Nome"
   git push origin seu-nome-sobrenome
   ```

### Atividade 1.3: Abra um Pull Request

1. Vá até o repositório no GitHub
2. Clique em **"Compare & pull request"**
3. Escreva uma descrição breve e abra o PR
4. Aguarde a revisão!

---

## Nível 2 — Colaboração

### Atividade 2.1: Revise o PR de um colega

1. Vá até a aba **Pull Requests** no GitHub
2. Escolha o PR de um colega
3. Revise o código e deixe um comentário construtivo
4. Aprove ou sugira mudanças

### Atividade 2.2: Resolvendo Merge Conflicts (em grupo)

Nesta atividade, seu grupo vai **propositalmente** criar merge conflicts para aprender a resolvê-los.

**Decidam quem será a pessoa A, B, C (e D, caso sejam o grupo 3)**

**Passo a passo:**

1. Escolham o arquivo do grupo (com o numero da sua equipe no hackathon) dentro de `desafio-merge/` (ex: `grupo-1.md`, `grupo-2.md`, etc.)
2. **Todos** do grupo criem uma branch a partir da `main`:
   ```bash
   git checkout main
   git pull
   git checkout -b merge-seuNome
   ```
3. **Todos** editem o **mesmo trecho** do arquivo do grupo (onde diz `EDITE AQUI`), cada um colocando uma resposta diferente
4. **Pessoa A** faz commit e push primeiro:
   ```bash
   git add .
   git commit -m "resposta de Pessoa A"
   git push origin merge-seuNome
   ```
   Abre um Pull Request. O instrutor faz merge.
5. **Pessoa B** tenta fazer push e recebe um erro! Precisa resolver o conflito:
   ```bash
   git pull origin main
   ```
   O Git vai mostrar algo como:
   ```
   <<<<<<< HEAD
   Resposta da Pessoa B
   =======
   Resposta da Pessoa A
   >>>>>>> main
   ```
6. **Pessoa B** resolve o conflito mantendo **ambas** as respostas, faz commit e push. O instrutor faz merge.
7. **Pessoa C** repete o processo — agora precisa resolver o conflito com as respostas de A e B já presentes!
8. **Pessoa D** (se houver) repete novamente — resolvendo com A, B e C.

Cada pessoa faz commit da resolução e abre seu Pull Request:
```bash
git add .
git commit -m "resolve conflito - adiciona resposta de Seu Nome"
git push origin merge-seuNome
```

> **Dica:** Conflitos não são erros! Eles acontecem o tempo todo em equipes e são normais. O importante é saber resolvê-los com calma. Cada rodada o conflito fica um pouco maior, isso é proposital!

---

## Nível 3 — Desafios

### Desafio 4.1: Git Detetive

Um commit "misterioso" introduziu um erro neste repositório. Use os comandos abaixo para encontrar o culpado:

```bash
git log --oneline
git blame <arquivo-suspeito>
git show <hash-do-commit>
```

Descubra **qual commit** introduziu o erro e **quem** foi o autor.

### Desafio 4.2: Revertendo um erro

1. Identifique o commit problemático usando `git log`
2. Reverta o commit:
   ```bash
   git revert <hash-do-commit>
   ```
3. Faça push da correção

### Desafio 4.3: Cherry-pick

Duas branches foram criadas com funcionalidades diferentes. Sua missão:

1. Identifique um commit útil na branch `feature-a`
2. Aplique **apenas aquele commit** na branch `feature-b`:
   ```bash
   git checkout feature-b
   git cherry-pick <hash-do-commit>
   ```

### Desafio 4.4: Criando uma Release

Quando todos os perfis estiverem no `main`, vamos criar a primeira release juntos:

```bash
git tag -a v1.0.0 -m "primeira release - todos os perfis adicionados"
git push origin v1.0.0
```

---

## Bônus — Mural da Sabedoria

Adicione uma frase, dica de tech ou mensagem motivacional ao arquivo `WALL.md`. Pode ser qualquer coisa:

- Uma dica de programação que você gostaria de ter aprendido antes
- Seu recurso de estudo favorito
- Uma frase que te inspira

---

## Estrutura do Repositório

```
learning-git/
├── README.md
├── WALL.md
├── profiles/
│   ├── exemplo.md
│   └── seu-nome.md
└── desafio-merge/
    ├── grupo-1.md  (trio)
    ├── grupo-2.md  (trio)
    ├── grupo-3.md  (quarteto)
    └── grupo-4.md  (trio)
```

---

**Bora praticar!**
