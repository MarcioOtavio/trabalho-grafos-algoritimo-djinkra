<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Metodologia do Projeto de Ciência de Dados - Análise de AVC</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f8fafc; /* slate-50 */
        }
        .flowchart-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 1.25rem; /* 20px */
        }
        .flow-step, .sub-step, .model-step {
            background-color: white;
            border: 1px solid #e2e8f0; /* slate-200 */
            border-radius: 0.75rem; /* 12px */
            padding: 1.25rem;
            text-align: center;
            box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
            transition: all 0.3s ease;
            max-width: 90%;
        }
        .flow-step:hover, .sub-step:hover, .model-step:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -2px rgb(0 0 0 / 0.1);
        }
        .step-title {
            font-weight: 600;
            font-size: 1.125rem; /* text-lg */
            color: #1e3a8a; /* blue-900 */
            margin-bottom: 0.5rem;
        }
        .step-description {
            color: #475569; /* slate-600 */
            font-size: 0.875rem; /* text-sm */
        }
        .arrow {
            color: #94a3b8; /* slate-400 */
            font-size: 2.5rem;
            font-weight: 300;
            line-height: 1;
        }
        .step-group {
            border: 2px dashed #93c5fd; /* blue-300 */
            background-color: #eff6ff; /* blue-50 */
            padding: 1.5rem;
            border-radius: 1rem;
        }
        .model-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 1rem;
            align-items: center;
        }
    </style>
</head>
<body class="p-4 sm:p-6 md:p-10">

    <div class="max-w-7xl mx-auto">
        <h1 class="text-3xl sm:text-4xl font-bold text-center text-slate-800 mb-4">
            Fluxo Metodológico do Projeto
        </h1>
        <p class="text-lg text-center text-slate-600 mb-12">
            Análise de Fatores de Risco Associados a Acidente Vascular Cerebral (AVC) com Dados da PNS 2019.
        </p>

        <div class="flowchart-container">

            <!-- Etapa 1: Coleta de Dados -->
            <div class="flow-step w-full md:w-3/5 lg:w-2/5">
                <div class="step-title">1. Coleta e Entendimento dos Dados</div>
                <div class="step-description">
                    Aquisição da base de dados da <strong>Pesquisa Nacional de Saúde (PNS) de 2019</strong>, realizada pelo IBGE. Análise inicial da estrutura e dicionário de dados.
                </div>
            </div>

            <div class="arrow">&#129047;</div>

            <!-- Etapa 2: Pré-processamento -->
            <div class="flow-step w-full md:w-4/5 lg:w-3/5 step-group">
                <div class="step-title">2. Pré-processamento e Análise Exploratória (EDA)</div>
                <div class="step-description mb-6">Fase de preparação e investigação inicial dos dados para identificar padrões, anomalias e relações entre as variáveis.</div>
                <div class="flex flex-col md:flex-row gap-4 justify-center">
                    <div class="sub-step flex-1">
                        <h3 class="font-semibold text-blue-800">Limpeza dos Dados</h3>
                        <p class="text-xs text-slate-500">Tratamento de valores ausentes (NaNs), correção de inconsistências e remoção de outliers.</p>
                    </div>
                    <div class="sub-step flex-1">
                        <h3 class="font-semibold text-blue-800">Transformação</h3>
                        <p class="text-xs text-slate-500">Codificação de variáveis categóricas (ex: One-Hot Encoding) e normalização de features numéricas.</p>
                    </div>
                </div>
            </div>
            
            <div class="arrow">&#129047;</div>

            <!-- Etapa 3: Seleção e Engenharia de Atributos -->
            <div class="flow-step w-full md:w-4/5 lg:w-3/5 step-group">
                 <div class="step-title">3. Engenharia e Seleção de Atributos</div>
                 <div class="step-description mb-6">Seleção das variáveis mais relevantes e criação de novas features para melhorar o desempenho dos modelos.</div>
                <div class="flex flex-col gap-4">
                    <div class="sub-step">
                        <h3 class="font-semibold text-blue-800">Filtragem da Amostra</h3>
                        <p class="text-xs text-slate-500">Definição da população de estudo, aplicando filtros conforme os objetivos da pesquisa (ex: faixa etária).</p>
                    </div>
                    <div class="sub-step">
                        <h3 class="font-semibold text-blue-800">Seleção de Atributos (Feature Selection)</h3>
                        <p class="text-xs text-slate-500">Uso de testes estatísticos (Qui-quadrado) e análise de importância para selecionar as variáveis preditoras mais impactantes.</p>
                    </div>
                     <div class="sub-step">
                        <h3 class="font-semibold text-blue-800">Balanceamento da Base</h3>
                        <p class="text-xs text-slate-500">Criação de uma amostra balanceada por <strong>sexo, etnia e pelo atributo alvo (AVC)</strong> para garantir um modelo não enviesado.</p>
                    </div>
                </div>
            </div>

            <div class="arrow">&#129047;</div>

            <!-- Etapa 4: Modelagem Preditiva -->
            <div class="flow-step w-full md:w-4/5 lg:w-3/5 step-group">
                <div class="step-title">4. Modelagem Preditiva</div>
                <div class="step-description mb-4">Divisão da base em <strong> 70% para treino e 30% para teste</strong>. Treinamento do modelo de <strong>Regressão Logística</strong>.</div>
                <div class="model-container">
                    <div class="model-step">
                        <h3 class="font-semibold text-blue-800">Regressão Logística</h3>
                        <p class="text-xs text-slate-500">Modelo estatístico para classificação binária.</p>
                    </div>
                </div>
            </div>

            <div class="arrow">&#129047;</div>

            <!-- Etapa 5: Avaliação -->
            <div class="flow-step w-full md:w-3/5 lg:w-2/5">
                <div class="step-title">5. Avaliação do Modelo</div>
                <div class="step-description">
                    Análise de performance no conjunto de teste (30%) com a <strong>Acurácia (proporção de predições corretas)</strong> como métrica principal.
                </div>
            </div>

            <div class="arrow">&#129047;</div>

            <!-- Etapa 6: Interpretação -->
            <div class="flow-step w-full md:w-3/5 lg:w-2/5 bg-green-50 border-green-300">
                <div class="step-title text-green-900">6. Interpretação e Descoberta de Conhecimento</div>
                <div class="step-description text-green-700">
                    Análise dos resultados do modelo para extrair <strong>conhecimento não trivial</strong> sobre os principais fatores associados ao AVC na população estudada.
                </div>
            </div>

        </div>
    </div>
</body>
</html>
