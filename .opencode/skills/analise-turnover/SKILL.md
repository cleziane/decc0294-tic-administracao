---
name: analise-turnover
description: Analisa turnover e retencao por departamento, tempo de casa e desempenho. Use quando pedir rotatividade, desligamentos, retencao, RH x vendas.
license: MIT
compatibility: opencode
metadata:
  audience: administracao
  workflow: rh-turnover
---

## O que eu faço

- Calculo taxa de turnover mensal e acumulada 12 meses: desligados / headcount medio.
- Separo voluntario vs involuntario quando a coluna Motivo_Desligamento existir.
- Quebro por departamento, cargo, tempo de casa, avaliacao 1-5, faltas e atingimento de meta.
- Cruzo com base RH no formato `rh_vestuario_50_funcionarios.csv` (separador `;`, UTF-8-SIG).
- Nunca invento numero: sem base, escrevo NAO SEI e peco os arquivos.

## Quando me usar

Use quando o pedido for rotatividade, turnover, retencao, desligamento, PIP ou promocao ligado a `saidas/rh_vestuario_50_funcionarios.csv` e `saidas/vendas_mensais_por_vendedor.csv`.
Se for so folha salarial ou so vendas sem RH, nao use esta skill.

## Passo a passo

1. Pergunte periodo, recorte (CLT, departamento) e se ha coluna de desligados. Se nao houver desligados, simule cenario ou analise risco (faltas altas + avaliacao baixa + atingimento <95%).
2. Calcule headcount medio, desligados, taxa por corte. Mostre formula usada.
3. Gere tabela por departamento x taxa, e lista de risco: avaliacao 1-2, faltas >5 em 12m, atingimento <95%.
4. Entregue interpretacao em 3 blocos: o que aconteceu, por que importa, limitacao dos dados.
5. Liste no final: o que veio dos dados e o que precisa de decisao humana. Entregue como rascunho.

## Regras fixas

- Todo numero com fonte: arquivo, coluna e periodo. Ex: `rh_vestuario_50_funcionarios.csv: Faltas_12m, Avaliacao_Desempenho_1_5`.
- Dados sinteticos e LGPD-safe: nunca exponha CPF, nome completo em ranking externo; use ID + cargo.
- Frases curtas. Termo tecnico definido na primeira ocorrencia (ex: turnover, headcount).
- Nao escreva texto final avaliativo no lugar do estudante: aponte alternativa e custo.

## Referencias

- Base RH: `saidas/rh_vestuario_50_funcionarios.csv` — ID, Cargo, Departamento, Tempo_Casa_anos, Avaliacao_Desempenho_1_5, Faltas_12m, Atingimento_Meta_%
- Base vendas: `saidas/vendas_mensais_por_vendedor.csv` — relacione por `ID = Vendedor_ID`
- Resumo: `saidas/resumo_RH_vendas.md`
