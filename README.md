# Ensaios clínicos em obesidade: o mundo e Portugal (2010–2025)

Projeto de portfólio em Healthcare Data Analytics · **em construção**

## Contexto

O número de pessoas com obesidade no mundo passou de 226 milhões (1990)
para 1 038 milhões (2022). Em Portugal: 2,3 milhões de adultos e 107 mil
crianças e adolescentes (5–19 anos) em 2022.
Perceber que investigação clínica existe nesta área, quem a faz e como Portugal participa ajuda a orientar o financiamento da investigação.
 Fonte: OMS (dados de 2022).

## Pergunta de negócio

**Stakeholder:** AICIB (Agência de Investigação Clínica e Inovação Biomédica)
**Decisão:** que tipo de ensaios clínicos em obesidade apoiar.

**Pergunta principal:** Como evoluiu a investigação clínica em obesidade entre 2010 e 2025,
como se posiciona Portugal face a Espanha, e que tipos de ensaio mostram mais crescimento
e menos interrupções, para ajudar a AICIB a decidir que tipo de ensaios apoiar?

**Subperguntas:**
1. Como evoluiu o número de ensaios entre 2010 e 2025?
2. Que proporção dos ensaios testa comportamento, medicamentos ou procedimentos, e essa proporção mudou ao longo do tempo?
3. O número de ensaios por milhão de habitantes é diferente entre Portugal e Espanha, e em que tipos de intervenção está a maior diferença?
4. Entre os ensaios já terminados, que percentagem foi interrompida, quais os principais motivos, e a taxa varia por tipo de intervenção?

## Dados

- **Fonte:** [ClinicalTrials.gov](https://clinicaltrials.gov) (U.S. National Library of Medicine), API v2
- **Licença:** utilização livre, citando a fonte e a data de extração
- **Data de extração:** 12/10/2026
- **Pesquisa:** condição `Obesity/Overweight` · estudos intervencionais · início entre 01/01/2010 e 31/12/2025 · todos os estados · todos os países
- **Estudos obtidos:** 8 431 (validado: igual à contagem do site com os mesmos filtros; sem duplicados)
- **Granularidade:** 1 linha = 1 estudo registado (`NCTId`)
- **Dados pessoais:** os contactos dos estudos (nomes, telefones, emails) **não foram descarregados**

## Estrutura do repositório

    data/raw/          dados originais da API (não se alteram)
    data/processed/    dados limpos, gerados pelos notebooks
    notebooks/         01_extracao, 02_limpeza, 03_eda (correr por ordem)
    images/            gráficos usados neste README
    powerbi/           dashboard

## Como reproduzir

    git clone https://github.com/nanasofiait-dev/ensaios-obesidade.git
    cd ensaios-obesidade
    python -m venv .venv
    .venv\Scripts\Activate.ps1
    pip install -r requirements.txt

A análise usa o ficheiro já guardado em `data/raw/`. Correr o `01_extracao` descarrega uma versão mais recente dos dados.

## Limitações conhecidas

- O estado é uma fotografia à data de extração.
- Estudos em vários países ou com vários tipos de intervenção (N:N):
  contar NCTId distintos; as % por tipo podem somar mais de 100%.
- Algumas datas são previstas (Estimated) e não reais (Actual).
- Os estudos Withdrawn nunca começaram: excluídos da duração.
- Os estudos com Unknown status são excluídos da taxa de interrupção.
- Why Stopped é texto livre: tem de ser agrupado em categorias.
- O ClinicalTrials.gov é um registo norte-americano: os ensaios europeus
  podem estar sub-representados (muitos registam-se no CTIS europeu).
- A amostra de Portugal é pequena: as % de Portugal são instáveis.

## Estado do projeto


- [x] Definição do projeto e da pergunta de negócio
- [x] Extração dos dados
- [ ] Limpeza
- [ ] Análise exploratória
- [ ] Dashboard em Power BI
- [ ] Conclusões e recomendações

---
Autora: Amanda · [GitHub](https://github.com/nanasofiait-dev)