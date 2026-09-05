# 📉 A empresa continua saudável. Então por que o lucro está desaparecendo?

### A matemática que a maioria dos empresários não vê vindo

![Python](https://img.shields.io/badge/python-3.10%2B-blue)
![Jupyter](https://img.shields.io/badge/jupyter-notebook-orange)
![License](https://img.shields.io/badge/license-MIT-green)

[![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ErikCassiocs/como-a-selic-influencia-sua-empresa/blob/main/selic_alta_destroi_empresas_endividadas.ipynb)

> ⬆️ Troque `SEU_USUARIO/SEU_REPO` pelo caminho real deste repositório assim que subir o `.ipynb`, para o botão abrir direto no Colab.

---

## 🎯 Sobre o projeto

Todo empresário já ouviu a frase: *"pode pegar dívida, o juro é dedutível do IR"*. É verdade — mas incompleta. A parte que falta é exatamente a que quebra empresas.

Este notebook simula uma empresa fictícia **operacionalmente saudável** (mesmo EBIT, mesma margem, mesmas vendas, em todos os cenários) e varia apenas a Selic, para mostrar — com dados reais do Banco Central, DRE simulado e gráficos — como a despesa financeira de uma dívida atrelada a CDI consome o lucro líquido muito mais rápido do que a intuição sugere, e por que o "desconto do IR" que parece proteger a empresa desaparece exatamente quando ela mais precisa dele.

**A tese central:**
> A Selic não precisa destruir a operação de uma empresa para destruir seu lucro. Basta que o custo da dívida consuma o resultado operacional.

## 📓 O que o notebook mostra

| # | Seção | Conteúdo |
|---|---|---|
| 1 | Dados reais da Selic | Série histórica da Meta Selic direto da API do Banco Central (SGS, série 432) |
| 2 | A "ilusão" do juro dedutível | Por que o tax shield só existe enquanto há lucro tributável |
| 3 | Empresa fictícia e premissas | Todos os parâmetros do modelo, declarados explicitamente |
| 4 | Tabela comparativa | DRE simulado em 3 cenários de Selic (10%, 15%, 20%) |
| 5 | Simulação contínua | Lucro líquido de Selic 5% a 25%, com o ponto de cobertura do custo da dívida sobre o EBIT |
| 6 | Perda por ponto percentual | Os dois regimes constantes (com e sem escudo fiscal) e o salto entre eles |
| 7 | Animação interativa | Gráfico Plotly com play/slider mostrando o lucro sumindo conforme a Selic sobe |
| 8 | Conclusão | Principais aprendizados e ferramentas de gestão de risco |

## ⚙️ Premissas do modelo (importante — leia antes de tirar conclusões)

Todas ajustáveis na seção 3 do notebook:

- **Receita líquida:** R$ 100 milhões/ano, com **EBIT de 20%** (R$ 20 milhões), constante em todos os cenários — a operação nunca muda, só a Selic.
- **Dívida:** R$ 80 milhões, 100% atrelada a **CDI + spread bancário de 2 p.p.**
- **CDI ≈ Selic − 0,10 p.p.** (aproximação usual de mercado) → **custo efetivo da dívida ≈ Selic + 1,9 p.p.** A despesa financeira **não** é `Dívida × Selic` pura.
- **Alíquota efetiva de IR/CSLL: 34%**, com aproveitamento integral do benefício fiscal **enquanto houver lucro tributável**.
- O ponto em que a despesa financeira passa a cobrir 100% do EBIT é específico **desta** combinação de dívida e spread — não é um limiar universal de Selic para qualquer empresa endividada.

## 🧪 Como rodar

### Opção 1 — Google Colab (recomendado)
Clique no botão "Abrir no Colab" no topo deste README, ou faça upload manual do arquivo `.ipynb` em [colab.research.google.com](https://colab.research.google.com). Todas as dependências são instaladas automaticamente na primeira célula.

### Opção 2 — Jupyter local
```bash
git clone https://github.com/SEU_USUARIO/SEU_REPO.git
cd SEU_REPO
pip install pandas numpy matplotlib plotly requests notebook
jupyter notebook selic_alta_destroi_empresas_endividadas.ipynb
```

## 🌐 Fonte de dados

Série **432 — Meta Selic definida pelo Copom (% a.a.)**, via [API de Dados Abertos do Banco Central](https://dadosabertos.bcb.gov.br/dataset/432-taxa-de-juros---selic) (SGS).

> Desde 26/03/2025 o BCB limita cada consulta a no máximo 10 anos de intervalo. O notebook já trata isso automaticamente, quebrando o período em janelas menores e concatenando os resultados, com novas tentativas em caso de timeout. Se a API estiver indisponível, o notebook usa uma pequena amostra offline para não travar.

## 📁 Estrutura

```
.
├── selic_alta_destroi_empresas_endividadas.ipynb   # o notebook
└── README.md
```

## ⚠️ Aviso

Este é um exercício **educacional**, com uma empresa e parâmetros fictícios. Não é recomendação de investimento nem substitui uma análise financeira real — que também consideraria capital de giro, outras receitas/despesas, covenants, hedge, etc.

## 📜 Licença

Distribuído sob licença MIT. Sinta-se livre para usar, adaptar e republicar com os créditos devidos.
