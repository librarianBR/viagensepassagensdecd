# viagensepassagensdecd

## Vigens e passagens de Cargos de Direção no portal da Trânsparência do Governo Federal Brasileiro.

O seguinte notebook tem como objetivo identificar as viagens realizadas em um intervalo de tempo em anos dos ocupantes de cargos de direção (CD) de um determinado orgão que estão em exercicio, identificando a FUNCAO, ATIVIDADE, UORG_EXERCICIO, ORG_EXERCICIO, utilizando dados aberto do portal de transparência do governo brasileiro: 
https://portaldatransparencia.gov.br/.

Somente viagens realizadas. O filtro é de servidores que estão em exercicio no orgão que será filtrado.

Somente um órgão por vez.



O resultado esperado é um arquivo csv com os filtros selecionados.

## Sobre as bibliotecas  
Este notebook utiliza as bibliotecas:
- pandas, csv, os, zipfile, pickle, shutil, sys, requests, tempfile, date, time delta.
o arquivo *requirements.txt* tem a lista de todas a bibliotecas instaladas para a execução do notebook.

## Sobre os dados abertos
O portas da transparência oferta os dados abertos de muitos períodos, mas nem sempre estão atualizados para a data mais recente. 
No momento da produção deste notebook, dados do SIAPE (fonte das informações de ATIVIDADE, FUNCAO, UORG_EXERCICIO) estavam com 3 meses de diferença. Portanto fique atento a esta restrição. Os arquivos de viagem tinham 1 semana de diferença.   
Os arquivos são realmente grandes e o notebook trabalha com eles aos poucos tentando não afetar muito o espaço da maquina que a executa.

## Sobre o notebook  
O notebook (arquivo viagensFuncao.ipynb ) pode ser utilizado em computador com python e as bibliotecas citadas. Caso não possa executar localmente, utilize o google colab (https://colab.research.google.com/) com uma conta google.


## Identifique o ORG_EXERCICIO primeiro  
Para isso, acesse https://portaldatransparencia.gov.br/despesas/orgao?ordenarPor=orgaoSuperior&direcao=asc e pesquise pelo nome do Orgão.  

Copie esse dado tal qual é apresentado (ex.: Instituto Federal de São Paulo) **Precisa ser exatamente como está lá**

No notebook, célula 2, informe a instituição, entre aspas para a variavel ***instituição***.

Informe também o periodo que será consultado para a variável ***anos_para_baixar***. Perceba que os anos precisam estar dentro das colchetes, entre aspas, e separadas por virgula caso mais de um ano seja selecionado. Verifique a célula 2 para ter uma ideia de como é.

## Resultado

Um arquivo cvs será gerado e pode ser trabalhado em um editor de planilhas eletrônicos de sua preferencias.
Fique atento à codificação. Os dados abertos estão com a codificação iso-8859-1. caso não funcione teste utf-8

# TravelsCD / ViagensCD

<details open>
<summary><strong>🇺🇸 English</strong></summary>

## Travels and Tickets of Leadership Positions on the Transparency Portal  

This notebook (viagensFuncao.ipynb file) identifies travels conducted within a specified timeframe by occupants of leadership positions (CD) *in office* at a selected government agency. It extracts **FUNCAO**, **ATIVIDADE**, **UORG_EXERCICIO**, and **ORG_EXERCICIO** from the Brazilian government's Transparency Portal:  
https://portaldatransparencia.gov.br/.  

### Filters  
- Only travels by employees *currently in office*  
- One agency per execution  

### Output  
A CSV file with filtered data (encoding: ISO-8859-1 or UTF-8).  

---

## Libraries  
- `pandas`, `csv`, `os`, `zipfile`, `pickle`, `shutil`, `sys`, `requests`, `tempfile`, `date`, `timedelta`  
- Full list in `requirements.txt`  

---

## Data Notes  
- SIAPE data: **3-month delay**  
- Travel records: **1-week delay**  
- Processed incrementally due to large dataset size  

---

## Usage  
1. **Identify ORG_EXERCICIO**:  
   - Visit https://portaldatransparencia.gov.br/despesas/orgao?ordenarPor=orgaoSuperior&direcao=asc  
   - Copy agency name **exactly** (e.g., `Instituto Federal de São Paulo`)  

2. **Configure Variables**:  
   ```python
   institution = "AGENCY_NAME_HERE"  # Case-sensitive
   years_to_download = ["2023", "2024"]  # Years in quotes
