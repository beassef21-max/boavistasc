# BOAVISTA S.C SAF — Núcleo de Saúde & Performance

Dashboard profissional em Streamlit para monitoramento neuromuscular via ForceDecks, com identidade visual do BOAVISTA S.C SAF.

## Como iniciar

### Opção 1 — Windows
Dê duplo clique em `INICIAR_DASHBOARD.bat`.

### Opção 2 — VS Code
Abra esta pasta no VS Code e execute no terminal:

```powershell
pip install -r requirements.txt
python -m streamlit run dashboard.py
```

O Streamlit normalmente abrirá `http://localhost:8501`.

## Estrutura da pasta

- `dashboard.py` — aplicativo principal.
- `requirements.txt` — dependências.
- `INICIAR_DASHBOARD.bat` — inicialização rápida no Windows.
- `IMG_2812.png` — escudo original do BOAVISTA usado como referência/asset.
- `01_ENTRADA` — coloque aqui os exports CSV do ForceDecks.
- `02_BANCO/cadastro_atletas.csv` — cadastro de posição e grupo dos atletas.

## Fluxo diário

1. Coloque novos exports CSV do ForceDecks em `01_ENTRADA`.
2. Cadastre posição e grupo em `02_BANCO/cadastro_atletas.csv`.
3. Atualize/reinicie o Streamlit.
4. O histórico e os indicadores são recalculados automaticamente.

## Indicadores

- CMJ do dia
- Último CMJ
- Máximo histórico
- Baseline (média dos 5 melhores resultados acumulados)
- Δ% vs último
- Δ% vs máximo
- Δ% vs baseline
- Z-score por posição
- Status de atenção do CMJ
- RSI
- Classificação do RSI

## Critérios do RSI

- 🟢 `>= 0,50` — Adequado
- 🟡 `>= 0,45 e < 0,50` — Atenção
- 🔴 `< 0,45` — Crítico

O RSI é identificado automaticamente em colunas como `RSI`, `RSI-modified` ou `Reactive Strength Index`.

## Módulos

- **Dashboard** — visão geral do elenco (KPIs, alertas, RSI médio por posição).
- **Ciência** — distribuição do CMJ, dispersão CMJ x RSI e Z-score por posição.
- **Desempenho** — ranking do elenco (top 5, menor Δ% baseline, ranking completo).
- **Prevenção** — atletas em risco e evolução histórica de alertas.
- **Resultados** — análise agregada por posição.
- **Atletas** — perfil individual com evolução de CMJ/RSI e histórico de testes.
- **Avaliações** — registro completo de avaliações com filtros por atleta e período.
- **Relatórios** — central de impressão: escolha filtros (posição, grupo, atletas, período) e as seções a incluir (resumo, critérios de RSI, alertas, tabela de monitoramento, análise por posição, evolução, perfil de atleta) e clique em **Imprimir / Salvar PDF** para abrir a caixa de impressão do navegador.
- **Comparativos** — compara a evolução de CMJ e RSI entre atletas selecionados.
- **Configurações** — ajuste os limiares de classificação (RSI e Δ% baseline) e a identidade do clube; as alterações são salvas em `02_BANCO/config.json`.

## Gerando um relatório para impressão

1. Abra o módulo **Relatórios**.
2. Defina os filtros (posição, grupo, atletas específicos, período).
3. Marque as seções que deseja incluir no documento.
4. Clique em **🖨️ Imprimir / Salvar PDF** — o navegador abre a caixa de impressão nativa mostrando somente o relatório (sem menu lateral ou controles). Escolha uma impressora ou "Salvar como PDF".
