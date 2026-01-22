<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard Comercial V4 - JAN 26</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            /* Paleta de Cores Principal */
            --brand-red: #D40000;
            --brand-white: #FCFCFC;

            /* Cores do Tema Neumórfico Escuro */
            --bg-dark: #1E1E1E;
            --text-dark: var(--brand-white);
            --text-muted-dark: #9ca3af;
            --shadow-dark: #121212;
            --shadow-light: #2a2a2a;
        }
        body { 
            font-family: 'Inter', sans-serif; 
            background-color: var(--bg-dark);
            color: var(--text-dark);
        }
        .kpi-card { 
            background-color: var(--bg-dark);
            border-radius: 20px;
            box-shadow: 8px 8px 16px var(--shadow-dark), -8px -8px 16px var(--shadow-light);
            transition: box-shadow 0.2s ease-in-out;
        }
        .kpi-card:hover { 
            box-shadow: inset 6px 6px 12px var(--shadow-dark), inset -6px -6px 12px var(--shadow-light);
        }
        .loading-spinner { 
            border-top-color: var(--brand-red); 
            animation: spin 1s linear infinite; 
        }
        @keyframes spin { to { transform: rotate(360deg); } }
        .text-muted { color: var(--text-muted-dark); }
        .text-accent { color: var(--brand-red); }
        .bg-accent { background-color: var(--brand-red); }
        .text-negative { color: var(--brand-red); }
        .text-positive { color: #22c55e; }
        
        .progress-track {
            background: var(--bg-dark);
            border-radius: 9999px;
            box-shadow: inset 4px 4px 8px var(--shadow-dark), inset -4px -4px 8px var(--shadow-light);
        }
    </style>
</head>
<body class="text-white">

    <div class="container mx-auto p-4 sm:p-6 lg:p-8">
        
        <header class="mb-8">
            <div>
                <h1 class="text-3xl font-bold text-white">Dashboard Comercial V4</h1>
                <p class="text-muted">Janeiro 2026 - Performance em Tempo Real</p>
            </div>
        </header>

        <!-- Loading State -->
        <div id="loading-state" class="text-center py-10">
            <div class="loading-spinner h-12 w-12 rounded-full border-4 border-gray-700 mx-auto"></div>
            <p class="mt-4 text-muted">Acessando os dados de Janeiro 26...</p>
        </div>

        <!-- Conteúdo Principal -->
        <main id="main-content" class="hidden">
            <!-- KPIs Principais -->
            <section id="kpis" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-8 gap-8 mb-8">
                <div class="kpi-card p-6 lg:col-span-2">
                    <div class="flex items-center space-x-4">
                        <div class="p-3 text-accent">
                            <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" /></svg>
                        </div>
                        <div class="flex-1 min-w-0">
                            <h3 class="text-sm font-medium text-muted">Meta do Mês</h3>
                            <p id="kpi-meta-mes" class="text-xl xl:text-2xl font-semibold text-white break-words">R$ 0</p>
                        </div>
                    </div>
                </div>
                <div class="kpi-card p-6 lg:col-span-2">
                     <div class="flex items-center space-x-4">
                        <div class="p-3 text-accent">
                            <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v.01" /></svg>
                        </div>
                        <div class="flex-1 min-w-0">
                            <h3 class="text-sm font-medium text-muted">Vendas</h3>
                            <p id="kpi-vendas-realizadas" class="text-xl xl:text-2xl font-semibold text-white break-words">R$ 0</p>
                        </div>
                    </div>
                </div>
                <div class="kpi-card p-6 lg:col-span-2">
                    <div class="flex items-center space-x-4">
                        <div class="p-3 text-accent">
                           <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 18h.01M8 21h8a2 2 0 002-2V5a2 2 0 00-2-2H8a2 2 0 00-2 2v14a2 2 0 002 2z" /></svg>
                        </div>
                        <div class="flex-1 min-w-0">
                            <h3 class="text-sm font-medium text-muted">Na Rua</h3>
                            <p id="kpi-na-rua" class="text-xl xl:text-2xl font-semibold text-white break-words">R$ 0</p>
                        </div>
                    </div>
                </div>
                <div class="kpi-card p-6 lg:col-span-2">
                     <div class="flex items-center space-x-4">
                        <div class="p-3 text-accent">
                           <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 7h.01M7 3h5c.512 0 1.024.195 1.414.586l7 7a2 2 0 010 2.828l-7 7a2 2 0 01-2.828 0l-7-7A2 2 0 013 12V7a4 4 0 014-4z" /></svg>
                        </div>
                        <div class="flex-1 min-w-0">
                            <h3 class="text-sm font-medium text-muted">Nº Vendas</h3>
                            <p id="kpi-total-vendas" class="text-xl xl:text-2xl font-semibold text-white break-words">0</p>
                        </div>
                    </div>
                </div>

                <!-- Ticket e CAC -->
                <div class="kpi-card p-6 lg:col-span-4">
                    <div class="flex items-center space-x-4">
                        <div class="p-3 text-accent">
                            <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 14l6-6m-5.5.5h.01m4.99 5h.01M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16l3.5-2 3.5 2 3.5-2 3.5 2z" /></svg>
                        </div>
                        <div class="flex-1 min-w-0">
                            <h3 class="text-sm font-medium text-muted">Ticket Médio</h3>
                            <p id="kpi-ticket-medio" class="text-xl xl:text-2xl font-semibold text-white break-words">R$ 0</p>
                        </div>
                    </div>
                </div>
                <div class="kpi-card p-6 lg:col-span-4">
                    <div class="flex items-center space-x-4">
                        <div class="p-3 text-accent">
                            <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z" /></svg>
                        </div>
                        <div class="flex-1 min-w-0">
                            <h3 class="text-sm font-medium text-muted">Custo de Aquisição (CAC)</h3>
                            <p id="kpi-cac" class="text-xl xl:text-2xl font-semibold text-white break-words">R$ 0</p>
                        </div>
                    </div>
                </div>

                <!-- Progresso Meta -->
                <div class="lg:col-span-8 kpi-card p-6">
                    <h3 class="text-lg font-medium text-white mb-2">Progresso para Meta</h3>
                    <div class="grid grid-cols-2 gap-4 mb-2 text-sm">
                        <div class="text-left">
                            <div class="font-medium text-accent">Realizado</div>
                            <div id="progress-percent" class="font-semibold text-base">0,00%</div>
                        </div>
                        <div class="text-right">
                            <div class="font-medium text-muted">Ritmo Ideal Hoje</div>
                             <div class="flex items-center justify-end space-x-1">
                                <span id="progress-ideal-percent" class="font-semibold text-base">0,00%</span>
                                <span class="text-muted">(<span id="progress-ideal-value">R$ 0,00</span>)</span>
                            </div>
                        </div>
                    </div>
                    <div class="w-full h-4 progress-track relative overflow-hidden">
                        <div id="progress-bar" class="bg-accent rounded-full h-4" style="width: 0%; transition: width 0.5s ease-in-out;"></div>
                        <div id="progress-ideal-marker" class="absolute top-0 h-full w-1 bg-white/60" style="left: 0%; transition: left 0.5s ease-in-out; box-shadow: 0 0 5px white;"></div>
                    </div>
                    <div class="text-right text-sm mt-2 text-muted">
                        <span id="progress-meta-label">Meta: R$ 0,00</span>
                    </div>
                </div>
            </section>

            <!-- Detalhes de Ritmo -->
            <section id="ritmo" class="grid grid-cols-1 md:grid-cols-3 gap-8 mb-8">
                <div class="kpi-card p-6">
                    <h3 class="font-semibold text-lg mb-4 text-white">Acompanhamento Diário</h3>
                    <div class="space-y-4">
                        <div class="flex justify-between"><span class="text-muted">Dias Úteis Mês:</span><span id="ritmo-dias-uteis-mes" class="font-medium">0</span></div>
                        <div class="flex justify-between"><span class="text-muted">Dias Úteis Hoje:</span><span id="ritmo-dias-uteis-hoje" class="font-medium">0</span></div>
                        <hr class="border-gray-700">
                        <div class="flex justify-between"><span class="text-muted">Meta por Dia Útil:</span><span id="ritmo-meta-dia" class="font-medium">R$ 0</span></div>
                    </div>
                </div>
                <div class="kpi-card p-6">
                    <h3 class="font-semibold text-lg mb-4 text-white">Situação Atual</h3>
                    <div class="space-y-4">
                        <div class="flex justify-between"><span class="text-muted">Ideal Acumulado:</span><span id="sit-ideal" class="font-medium">R$ 0</span></div>
                        <div class="flex justify-between"><span class="text-muted">Realizado:</span><span id="sit-real" class="font-medium">R$ 0</span></div>
                        <hr class="border-gray-700">
                        <div class="flex justify-between items-center">
                            <span class="text-muted">GAP:</span>
                            <div class="flex items-center space-x-2">
                                <span id="gap-icon"></span>
                                <span id="sit-gap" class="font-bold text-lg lg:text-xl">R$ 0</span>
                            </div>
                        </div>
                         <div id="gap-text" class="text-right text-xs pt-1 uppercase tracking-wider"></div>
                    </div>
                </div>
                <div class="kpi-card p-6">
                    <h3 class="font-semibold text-lg mb-4 text-white">Projeção</h3>
                    <div class="space-y-4">
                        <div class="flex justify-between"><span class="text-muted">Ritmo Atual:</span><span id="proj-ritmo" class="font-medium">R$ 0 / dia</span></div>
                        <div class="flex justify-between items-baseline"><span class="text-muted">Fechamento:</span><span id="proj-fechamento" class="font-bold text-lg lg:text-xl text-accent">R$ 0</span></div>
                         <hr class="border-gray-700">
                        <p class="text-xs text-muted text-center italic">Baseado no desempenho até agora.</p>
                    </div>
                </div>
            </section>
        </main>
    </div>

    <script>
        // --- CONFIGURAÇÃO ---
        const API_KEY = 'AIzaSyDTN7IBjVdS6hUOUup34NPKs_Xv8nzMiGY';
        const SHEET_ID = '1gvcSqx24Bid5m5aRzImTMM6JQdvGcTPQi7JSp55KwBs';
        const SHEET_NAME = 'JAN 26';
        // --- FIM DA CONFIGURAÇÃO ---

        document.addEventListener('DOMContentLoaded', loadDashboardData);

        const parseCurrency = (value = 'R$ 0,00') => {
            if (typeof value !== 'string') return Number(value) || 0;
            return Number(value.replace(/[^0-9,.-]+/g, "").replace(/\./g, "").replace(',', '.')) || 0;
        };

        const parseInteger = (value = '0') => parseInt(String(value).trim(), 10) || 0;

        const formatCurrency = (value = 0) => {
            return new Intl.NumberFormat('pt-BR', { style: 'currency', currency: 'BRL' }).format(value);
        };
        
        function findValue(sheetData, config) {
            let foundRow = -1, foundCol = -1;
            const searchTerm = config.label.toUpperCase();
            for (let r = 0; r < sheetData.length; r++) {
                if (!sheetData[r]) continue;
                for (let c = 0; c < sheetData[r].length; c++) {
                    if (sheetData[r][c] && sheetData[r][c].toString().trim().toUpperCase() === searchTerm) {
                       foundRow = r; foundCol = c; break;
                    }
                }
                if (foundRow !== -1) break;
            }
            if (foundRow === -1) {
                console.warn(`Métrica "${config.label}" não encontrada.`); return '0';
            }
            if (config.valuePosition) {
                const valueR = foundRow + config.valuePosition.rowOffset;
                const valueC = foundCol + config.valuePosition.colOffset;
                return sheetData[valueR] && sheetData[valueR][valueC] ? sheetData[valueR][valueC] : '0';
            }
            return '0';
        }

        function calculateSalesFromLeads(sheetData) {
            let leadsHeaderRow = -1;
            let statusCol = -1;
            let valorCol = -1;
            let vendasRealizadas = 0;
            let totalVendas = 0;

            for (let r = 0; r < sheetData.length; r++) {
                if (sheetData[r] && sheetData[r].some(cell => cell && cell.toString().trim().toUpperCase() === 'LEADS')) {
                    leadsHeaderRow = r;
                    statusCol = sheetData[r].findIndex(cell => cell && cell.toString().trim().toUpperCase() === 'STATUS');
                    valorCol = sheetData[r].findIndex(cell => cell && cell.toString().trim().toUpperCase() === 'VALOR');
                    break;
                }
            }

            if (leadsHeaderRow === -1 || statusCol === -1 || valorCol === -1) {
                return { vendasRealizadas: 0, totalVendas: 0 };
            }

            for (let r = leadsHeaderRow + 1; r < sheetData.length; r++) {
                if (sheetData[r] && sheetData[r][statusCol] && sheetData[r][statusCol].toString().trim().toUpperCase() === 'FECHADO') {
                    const valorVenda = parseCurrency(sheetData[r][valorCol] || '0');
                    vendasRealizadas += valorVenda;
                    totalVendas++;
                }
            }
            return { vendasRealizadas, totalVendas };
        }

        async function loadDashboardData() {
            // Tratamento para nomes de abas com espaços na URL da API
            const url = `https://sheets.googleapis.com/v4/spreadsheets/${SHEET_ID}/values/'${SHEET_NAME}'!A1:Z100?valueRenderOption=FORMATTED_VALUE&key=${API_KEY}`;
            
            try {
                const response = await fetch(url);
                if (!response.ok) {
                    const errorData = await response.json(); 
                    throw new Error(`Erro ${response.status}: ${errorData.error.message}`);
                }
                const data = await response.json();
                const sheetData = data.values || [];
                if (sheetData.length === 0) { throw new Error("Planilha vazia."); }
                
                const salesData = calculateSalesFromLeads(sheetData);

                const values = {
                    metaMes: findValue(sheetData, { label: 'META DO MÊS', valuePosition: { rowOffset: 0, colOffset: 1 } }),
                    naRua: findValue(sheetData, { label: 'Na Rua', valuePosition: { rowOffset: 0, colOffset: 1 } }),
                    totalVendas: salesData.totalVendas,
                    vendasRealizadas: salesData.vendasRealizadas,
                    diasUteisMes: findValue(sheetData, { label: 'Dias úteis mês', valuePosition: { rowOffset: 0, colOffset: 1 } }),
                    diasUteisHoje: findValue(sheetData, { label: 'Dias úteis hoje', valuePosition: { rowOffset: 0, colOffset: 1 } }),
                    cacValor: findValue(sheetData, { label: 'CAC', valuePosition: { rowOffset: 0, colOffset: 1 } }),
                };

                populateDashboard(values);
                document.getElementById('loading-state').style.display = 'none';
                document.getElementById('main-content').classList.remove('hidden');

            } catch (error) {
                console.error('Erro:', error);
                document.getElementById('loading-state').innerHTML = `<p class="text-red-500 font-bold p-4 bg-red-900/50 rounded-lg">Erro ao carregar JAN 26: ${error.message}</p>`;
            }
        }

        function populateDashboard(values) {
            const metaMes = parseCurrency(values.metaMes);
            const naRua = parseCurrency(values.naRua);
            const diasUteisMes = parseInteger(values.diasUteisMes);
            const diasUteisHoje = parseInteger(values.diasUteisHoje);
            const totalVendas = parseInteger(values.totalVendas);
            const vendasRealizadas = values.vendasRealizadas;
            const cac = parseCurrency(values.cacValor);

            const ticketMedio = totalVendas > 0 ? vendasRealizadas / totalVendas : 0;
            const metaPorDiaUtil = diasUteisMes > 0 ? metaMes / diasUteisMes : 0;
            const idealAcumulado = metaPorDiaUtil * diasUteisHoje;
            const progressoPercent = metaMes > 0 ? (vendasRealizadas / metaMes) * 100 : 0;
            const idealProgressoPercent = metaMes > 0 ? (idealAcumulado / metaMes) * 100 : 0;
            const gap = vendasRealizadas - idealAcumulado;
            const ritmoVendaAtual = diasUteisHoje > 0 ? vendasRealizadas / diasUteisHoje : 0;
            const projecaoFechamento = ritmoVendaAtual * diasUteisMes;

            document.getElementById('kpi-meta-mes').textContent = formatCurrency(metaMes);
            document.getElementById('kpi-vendas-realizadas').textContent = formatCurrency(vendasRealizadas);
            document.getElementById('kpi-total-vendas').textContent = totalVendas;
            document.getElementById('kpi-na-rua').textContent = formatCurrency(naRua);
            document.getElementById('kpi-ticket-medio').textContent = formatCurrency(ticketMedio);
            document.getElementById('kpi-cac').textContent = formatCurrency(cac);

            document.getElementById('progress-percent').textContent = `${progressoPercent.toFixed(2).replace('.', ',')}%`;
            document.getElementById('progress-ideal-percent').textContent = `${idealProgressoPercent.toFixed(2).replace('.', ',')}%`;
            document.getElementById('progress-ideal-value').textContent = formatCurrency(idealAcumulado);
            document.getElementById('progress-meta-label').textContent = `Meta Total: ${formatCurrency(metaMes)}`;
            document.getElementById('progress-bar').style.width = `${Math.min(progressoPercent, 100)}%`;
            document.getElementById('progress-ideal-marker').style.left = `${Math.min(idealProgressoPercent, 100)}%`;

            document.getElementById('ritmo-dias-uteis-mes').textContent = diasUteisMes;
            document.getElementById('ritmo-dias-uteis-hoje').textContent = diasUteisHoje;
            document.getElementById('ritmo-meta-dia').textContent = formatCurrency(metaPorDiaUtil);

            document.getElementById('sit-ideal').textContent = formatCurrency(idealAcumulado);
            document.getElementById('sit-real').textContent = formatCurrency(vendasRealizadas);
            
            const gapElement = document.getElementById('sit-gap');
            const gapIconElement = document.getElementById('gap-icon');
            const gapTextElement = document.getElementById('gap-text');

            gapElement.textContent = (gap >= 0 ? '+ ' : '') + formatCurrency(gap);
            if (gap >= 0) {
                gapElement.className = 'font-bold text-lg lg:text-xl text-positive';
                gapIconElement.innerHTML = `<svg class="h-5 w-5 text-positive" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 10l7-7m0 0l7 7m-7-7v18"></path></svg>`;
                gapTextElement.textContent = 'Acima do esperado';
                gapTextElement.className = 'text-right text-xs text-positive pt-1 uppercase tracking-wider';
            } else {
                gapElement.className = 'font-bold text-lg lg:text-xl text-negative';
                gapIconElement.innerHTML = `<svg class="h-5 w-5 text-negative" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path></svg>`;
                gapTextElement.textContent = 'Abaixo do esperado';
                gapTextElement.className = 'text-right text-xs text-negative pt-1 uppercase tracking-wider';
            }

            document.getElementById('proj-ritmo').textContent = `${formatCurrency(ritmoVendaAtual)} / dia`;
            document.getElementById('proj-fechamento').textContent = formatCurrency(projecaoFechamento);
        }
    </script>
</body>
</html>
