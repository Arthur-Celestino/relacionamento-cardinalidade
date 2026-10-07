# 📊 Modelo Lógico - Banco de Dados

### Professora Ellen Martins Lopes da Silva - 02/10/2026

Este projeto apresenta um modelo de banco de dados relacionado a **jogadores, jogos e partidas**.

O objetivo da atividade é compreender entidades, atributos, cardinalidades e relacionamentos, além de transformar um relacionamento muitos para muitos em uma tabela intermediária.

## 📚 Entidades

As principais entidades utilizadas no modelo são:

- **JOGADOR**
- **JOGO**
- **PARTIDA**
- **PARTICIPACAO**

### 🎮 JOGADOR

Representa os jogadores cadastrados no sistema.

Alguns de seus atributos são:

- ID_Jogador
- Nome
- E-mail
- Nickname

### 🕹️ JOGO

Representa os jogos cadastrados no sistema.

### 🏆 PARTIDA

Representa as partidas realizadas dentro de um jogo.

### 👥 PARTICIPACAO

Representa a participação de um jogador em uma determinada partida.

Também permite armazenar a pontuação obtida pelo jogador naquela partida.

---

## ❓ Perguntas e Respostas

### 1. Qual a diferença entre entidade e atributo?

**Entidade** é algo que possui existência própria no sistema e sobre o qual queremos guardar informações.

Exemplos:

- JOGADOR
- JOGO
- PARTIDA

**Atributo** é uma característica de uma entidade.

Por exemplo, na entidade **JOGADOR**, podemos ter:

- ID_Jogador
- Nome
- E-mail
- Nickname

---

### 2. Como você definiu os mínimos e máximos?

Os mínimos e máximos foram definidos de acordo com as regras do sistema:

- Um **JOGADOR** pode participar de **0 até N** partidas.
- Uma **PARTIDA** pode ter **1 até N** jogadores.
- Um **JOGO** pode possuir **0 até N** partidas.
- Cada **PARTIDA** pertence a **1 JOGO**.

O **0** representa que a participação é opcional.

O **1** indica que a ocorrência é obrigatória.

O **N** indica que podem existir várias ocorrências.

---

### 3. Por que PARTICIPACAO precisa existir no modelo lógico?

A entidade **PARTICIPACAO** precisa existir porque:

- Um jogador pode participar de várias partidas.
- Uma partida pode ter vários jogadores.

Isso caracteriza um relacionamento **N:N (muitos para muitos)**.

No modelo lógico, esse relacionamento precisa ser transformado em uma tabela intermediária chamada:

**PARTICIPACAO**

Ela pode possuir os seguintes atributos:

- ID_Jogador (FK)
- ID_Partida (FK)
- Pontuacao

Dessa forma, conseguimos registrar qual jogador participou de qual partida.

---

### 4. Onde a pontuação deve ser armazenada — e por quê?

A **Pontuacao** deve ser armazenada em **PARTICIPACAO**.

Isso acontece porque a pontuação pertence à participação específica de um jogador em uma determinada partida.

O mesmo jogador pode obter pontuações diferentes em partidas diferentes.

Se a pontuação fosse colocada em **JOGADOR**, não seria possível armazenar corretamente várias pontuações.

Se fosse colocada em **PARTIDA**, não seria possível diferenciar a pontuação de cada jogador.

Por isso, o local correto é:

**PARTICIPACAO → Pontuacao**

---

## 🔗 Relacionamentos

O modelo possui os seguintes relacionamentos:

```text
JOGADOR
   │
   │ 0:N
   │
   ▼
PARTICIPACAO
   │
   │ N:1
   │
   ▼
PARTIDA
   │
   │ N:1
   │
   ▼
JOGO
