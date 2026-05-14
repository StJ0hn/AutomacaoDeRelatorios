# Automação e Processamento de Relatórios de Vendas (Pipeline ETL)

Aplicação desenvolvida em Python para automação do fluxo de extração, processamento de métricas e distribuição de relatórios de desempenho de vendas.

## Objetivo
O projeto visa eliminar o processamento manual de dados corporativos operando como um pipeline de ETL. O script consolida bases de dados heterogêneas, processa Indicadores-Chave de Desempenho (KPIs) em memória e orquestra a distribuição hierárquica das informações, enviando dados granulares aos gerentes e análises consolidadas (rankings) à diretoria.

## Stack Tecnológico
* Linguagem: Python 3
* Processamento e Análise de Dados: Pandas
* Manipulação de Arquivos: openpyxl
* Integração de Rede: smtplib e email.message (Protocolo SMTP)

## Arquitetura e Fluxo de Processamento
O sistema foi estruturado para garantir a integridade dos cálculos antes da geração dos artefatos finais:
* Extração e Merge: Leitura de dados transacionais (`Vendas.xlsx`), cadastrais (`Lojas.csv`) e de contato (`Emails.xlsx`), consolidando-os em um único DataFrame através do relacionamento de chaves (`ID Loja`).
* Transformação e Cálculo de KPIs: Agregação de dados para o cálculo de Faturamento Total Anual, Quantidade de Vendas e Ticket Médio por unidade de negócio.
* Geração de Artefatos: Criação e exportação automatizada de planilhas de ranking hierárquico voltadas para a análise da diretoria.
* Distribuição Dinâmica: Iteração sobre a base processada para o disparo individualizado de e-mails via servidor SMTP, com injeção de dados específicos no corpo HTML das mensagens.

## Como Executar Localmente

1. Clone o repositório:
git clone https://github.com/SeuUser/nome-do-repo.git

2. Provisione um ambiente virtual e instale as dependências:
python -m venv venv
source venv/bin/activate (Linux/macOS) ou venv\Scripts\activate (Windows)
pip install pandas openpyxl

3. Estruturação do Diretório:
Certifique-se de que a pasta raiz contenha o diretório `/Base de dados/` com os arquivos `Vendas.xlsx`, `Lojas.csv` e `Emails.xlsx` formatados corretamente.

4. Configuração de Credenciais:
Edite o arquivo `automacao.py` inserindo as credenciais SMTP nas variáveis de ambiente adequadas (evite expor senhas diretamente no código fonte).

5. Execute o pipeline:
python automacao.py
