# Threat Modeling Lab - STRIDE + DREAD

Exercício prático **sem nota** para aplicar, num sistema de verdade (fictício), o que vimos em aula sobre **modelagem de ameaças**.
Você recebe a especificação do **OrbitaPay Mobile** (app de pagamentos), identifica ameaças com **STRIDE** e prioriza as 3 mais críticas com **DREAD**.

> O sistema, os componentes e os dados são **fictícios**.

## Como abrir
1. Baixe a pasta e dê **duplo clique em `index.html`** (qualquer navegador atual). Não precisa de internet nem instalação.
2. Se quiser, digite seu nome/RM no topo (só aparece no relatório que você baixar).

## O que fazer (sugestão: 40-60 min)

| Etapa | Aba | O que você faz |
|---|---|---|
| 0 | **Especificação** | Leia o texto e o diagrama (DFD) com as fronteiras de confiança. |
| 1 | **STRIDE** | Para cada componente, cadastre ameaças por categoria (S, T, R, I, D, E) e uma mitigação. Use a matriz para ver o que falta. |
| 2 | **DREAD** | Marque ☆ nas 3 ameaças mais críticas e dê nota de 1 a 10 para cada critério. |
| 3 | **Comparar** | Compare com a análise de referência. Só depois de esgotar as suas ideias. |

Você precisa de pelo menos **5 ameaças** cadastradas para liberar a comparação. O botão **Relatório** baixa seu modelo em `.md`; o **Debrief** traz perguntas para a discussão.

## Cola STRIDE

| Letra | Ameaça | Propriedade violada | Pergunta-guia |
|---|---|---|---|
| **S** | Spoofing | Autenticação | Alguém pode se passar por outro usuário, serviço ou sistema? |
| **T** | Tampering | Integridade | Alguém pode alterar dados, código ou mensagens sem ser percebido? |
| **R** | Repudiation | Não repúdio | Alguém pode negar uma ação e não haver prova? |
| **I** | Information disclosure | Confidencialidade | Que dado sensível pode ser visto por quem não deveria? |
| **D** | Denial of service | Disponibilidade | Como deixar o componente indisponível? |
| **E** | Elevation of privilege | Autorização | Como ganhar permissões que não deveria ter? |

**STRIDE por elemento** (quais categorias se aplicam a cada tipo):
- Processo (serviço, app): **S T R I D E**
- Repositório de dados: **T R I D**
- Entidade externa: **S R**
- Fluxo de dados: **T I D**

## DREAD (nota de 1 a 10 em cada critério)

| Critério | Pergunta |
|---|---|
| **D**amage | Quão grave seria o estrago? |
| **R**eproducibility | Quão fácil é repetir o ataque? |
| **E**xploitability | Quanto esforço e habilidade o atacante precisa? |
| **A**ffected users | Quantos usuários seriam atingidos? |
| **D**iscoverability | Quão fácil é descobrir a falha? |

A média define o risco: **Baixo** (< 4), **Médio** (4 a 6,9) e **Alto** (≥ 7).
DREAD é **subjetivo**. Muitos times hoje usam alternativas como **CVSS** ou o **OWASP Risk Rating**. O valor do exercício está na discussão sobre priorização.

## Dicas (sem spoilers)
- **Leia a especificação como atacante.** Cada frase descreve uma decisão de design. Pergunte de cada uma: "e se isso for abusado?".
- **Fronteiras de confiança** são onde dados cruzam de um nível de confiança para outro. Comece por elas.
- **Nunca confie no cliente.** O que o app envia pode ter sido alterado, mesmo que você tenha escrito o app.
- **Pense em cada categoria para cada componente.** Uma célula vazia na matriz é um ponto cego a investigar, ou uma célula realmente sem risco (justifique).
- **Descreva quem faz o quê e qual o impacto.** "Falta segurança" não é uma ameaça. "Atacante com um token roubado transfere dinheiro de outro usuário" é.
- **Mitigação concreta:** prefira "validar a propriedade do recurso no servidor" a "melhorar a segurança".
- **No DREAD, justifique cada nota.** Por que Damage 9 e não 6? Se você não consegue explicar, a nota está chutada.
- **Não precisa achar todas.** Qualidade e raciocínio contam mais que quantidade.

## Combinados
- Ambiente de **treino**: errar faz parte.
- Discuta com a dupla, mas **registre o seu próprio modelo**.
- Não compartilhe a análise de referência com quem ainda não terminou.
