<img width="1837" height="717" alt="Captura de tela 2025-08-07 110910" src="https://github.com/user-attachments/assets/f5642ddc-bcb8-407b-a259-9b534a6cfd50" />
<img width="1824" height="508" alt="Captura de tela 2025-08-07 110934" src="https://github.com/user-attachments/assets/16ea83f9-8b08-4b32-9e33-03eb0c0468b0" />
<img width="1839" height="718" alt="Captura de tela 2025-08-07 110950" src="https://github.com/user-attachments/assets/8abc6803-2bf2-4d5c-9a9c-55d4be153bea" />
<img width="1840" height="531" alt="Captura de tela 2025-08-07 111007" src="https://github.com/user-attachments/assets/4afb2566-5e93-4319-877a-3f3e17e93c7d" />
<img width="1834" height="605" alt="Captura de tela 2025-08-07 111022" src="https://github.com/user-attachments/assets/0bdcaaf1-d402-483a-ad72-474f22ef9ed3" />
<img width="1812" height="664" alt="Captura de tela 2025-08-07 111045" src="https://github.com/user-attachments/assets/0048770a-9f44-40de-8c66-b98a44715351" />
<img width="1789" height="513" alt="Captura de tela 2025-08-07 111058" src="https://github.com/user-attachments/assets/08146a0c-0e95-4198-8d59-d13b30952c1b" />
<img width="1804" height="663" alt="Captura de tela 2025-08-07 111111" src="https://github.com/user-attachments/assets/687bb9c2-554d-463a-98c4-cf3f522c52b2" />
<img width="1802" height="721" alt="Captura de tela 2025-08-07 111125" src="https://github.com/user-attachments/assets/54a6f9ec-6d5a-4594-bb3b-1e6b5c595e8c" />
<img width="1827" height="684" alt="Captura de tela 2025-08-07 111136" src="https://github.com/user-attachments/assets/5ce56f05-cfbf-4a52-9c77-2fbc5e8224d4" />
<img width="1820" height="477" alt="Captura de tela 2025-08-07 111148" src="https://github.com/user-attachments/assets/2433efc5-6d25-4f57-8be5-65afdcf44b05" />
<img width="1789" height="724" alt="Captura de tela 2025-08-07 111202" src="https://github.com/user-attachments/assets/c44a03da-2fe5-4b2e-8432-7721d3b6d2f3" />
<img width="1835" height="702" alt="Captura de tela 2025-08-07 111213" src="https://github.com/user-attachments/assets/681582f3-6b59-41cc-96d3-65a28cf75d0e" />

import pandas as pd # pd é um apelido para pandas, mais curto.

df = pd.read_csv("https://raw.githubusercontent.com/guilhermeonrails/data-jobs/refs/heads/main/salaries.csv") # read é uma funsão, serve para ler o link com os dados.

df.head(10) # head é uma funsão, serve para ler ou dar uma olhadinha em algumas linhas do dados.

df.info() #info é uma funsão , serve para pegar informação, dar infotmação.

df.describe() # describe é uma funsão, serve para ter uma descrição mais aprofundada, entender melhor quais são as informações que temos na nossa base de dados.

df.shape # shape é um atributo,ele traz a dimensão desse arquivo. ou seja sao 133349 linhas e 11 colunas

linhas, colunas = df.shape[0], df.shape [1] # server para fazer um relatório.
print("Numeros de linhas:", linhas)
print("Numeros de colunas:", colunas)

df.columns

df.rename(columns={
    'work_year': 'ano_trabalho',
    'experience_level': 'nivel_experiencia',
    'employment_type': 'tipo_emprego',
    'job_title': 'cargo',
    'salary': 'salario',
    'salary_currency': 'moeda_salario',
    'salary_in_usd': 'salario_em_usd',
    'employee_residence': 'residencia_empregado',
    'remote_ratio': 'taxa_remoto',
    'company_location': 'localizacao_empresa',
    'company_size': 'tamanho_empresa'
}, inplace=True)

df["senioridade"].value_counts() # SE = senior. MI = pleno. EN = junior. EX = outros

senioridade = {
    'SE': 'Senior',
    'MI': 'Pleno',
    'EN': 'Junior',
    'EX': 'Executivo'
}
df['senioridade'] = df['senioridade'].replace(senioridade)
df["senioridade"].value_counts()

df["contrato"].value_counts() # FT = quem trabalha em horário integral. CT = contrato temporario. PT = trabalho de meio periodo. FL = fleelancer.

contrato = {
    'FT': 'Tempo Integral',
    'CT': 'Contrato Temporário',
    'PT': 'Meio Período',
    'FL': 'Freelancer'
}
df['contrato'] = df['contrato'].replace(contrato)
df["contrato"].value_counts()

df["remoto"].value_counts() # numero 0 são os trabalho presencial. numero 100 é trabalho remoto. numero 50 vagas hibridas

remoto = {
    0: 'Presencial',
    100: 'Remoto',
    50: 'Híbrido'
}
df['remoto'] = df['remoto'].replace(remoto)
df["remoto"].value_counts()

df["tamanho_empresa"].value_counts() # M = empresa tamanho medio. L = empresa tamanho grande. S = empresa tamanho pequena.

tamanho_empresa = {
    'M': 'Médio',
    'L': 'Grande',
    'S': 'Pequeno'
}
df['tamanho_empresa'] = df['tamanho_empresa'].replace(tamanho_empresa)
df["tamanho_empresa"].value_counts()

df["cargo"].value_counts() 

cargo = {
    'Data Scientist': 'Cientista de Dados',
    'Data Analyst': 'Analista de Dados',
    'Data Engineer': 'Engenheiro de Dados',
    'Machine Learning Scientist': 'Cientista de Dados',
    'Research Scientist': 'Cientista de Dados',
    'Research Scientist': 'Cientista de Dados',
    'Data Architect': 'Engenheiro de Dados',

}
df['cargo'] = df['cargo'].replace(cargo)
df["cargo"].value_counts()

df.head()

df.describe(include="object") # include é uma informação, UNIQUE, significa que temos 4 valores unicos de senioridade (senior, pleno, junior e executivo). 4 tipos de contrato ... 386 cargos... etc... 
# TOP, qual tipo de senioridade mais comum? Senior. Qual tipo de contrato mais comum? Tempo Integral. Qual tipo de moeda mais comum? UDS etc...
# FREQ vê quantas vezes esse valor ta se repetindo , tipo , o senior apareceu 77241 vezes.


 #traduza para português as categorias da coluna "" do dataframe d


https://colab.research.google.com/drive/1USwCdItDm3_cObqVpo9SEuA0lKMJV4an?usp=sharing # Dados-com-Pandas
