<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Distrito Sanitário Eldorado - Exames Oftalmológicos</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background-color: #f8f9fa;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .header {
            text-align: center;
            margin-bottom: 30px;
            background: linear-gradient(135deg, #2c5282, #3182ce);
            color: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            position: relative;
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        .header p {
            font-size: 1.2em;
            opacity: 0.9;
        }

        .alert {
            background-color: #fff3cd;
            border: 2px solid #ffc107;
            color: #856404;
            padding: 20px;
            margin-bottom: 30px;
            border-radius: 8px;
            font-weight: bold;
            text-align: center;
            font-size: 1.1em;
        }

        .search-container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            margin-bottom: 30px;
        }

        .search-box {
            position: relative;
            max-width: 500px;
            margin: 0 auto;
        }

        .search-input {
            width: 100%;
            padding: 15px 50px 15px 20px;
            font-size: 16px;
            border: 2px solid #e2e8f0;
            border-radius: 25px;
            outline: none;
            transition: all 0.3s ease;
        }

        .search-input:focus {
            border-color: #3182ce;
            box-shadow: 0 0 0 3px rgba(49, 130, 206, 0.1);
        }

        .search-clear {
            position: absolute;
            right: 15px;
            top: 50%;
            transform: translateY(-50%);
            background: #e53e3e;
            color: white;
            border: none;
            border-radius: 50%;
            width: 25px;
            height: 25px;
            cursor: pointer;
            font-size: 14px;
            display: none;
        }

        .search-clear:hover {
            background: #c53030;
        }

        .categories {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }

        .category {
            background: white;
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .category:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 12px rgba(0, 0, 0, 0.15);
        }

        .category h2 {
            font-size: 1.5em;
            margin-bottom: 20px;
            padding: 15px;
            border-radius: 8px;
            text-align: center;
            color: white;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
        }

        .eldorado {
            border-left: 5px solid #38a169;
        }

        .eldorado h2 {
            background: linear-gradient(135deg, #38a169, #48bb78);
        }

        .bh {
            border-left: 5px solid #3182ce;
        }

        .bh h2 {
            background: linear-gradient(135deg, #3182ce, #4299e1);
        }

        .sem-prestador {
            border-left: 5px solid #e53e3e;
        }

        .sem-prestador h2 {
            background: linear-gradient(135deg, #e53e3e, #f56565);
        }

        .exam-list {
            list-style: none;
        }

        .exam-item {
            padding: 12px 15px;
            margin-bottom: 8px;
            background-color: #f7fafc;
            border-radius: 6px;
            border-left: 3px solid #e2e8f0;
            transition: all 0.3s ease;
            font-size: 0.95em;
        }

        .exam-item:hover {
            background-color: #edf2f7;
            border-left-color: #3182ce;
            transform: translateX(5px);
        }

        .exam-item.highlight {
            background-color: #fef08a;
            border-left-color: #f59e0b;
            font-weight: bold;
        }

        .exam-count {
            display: inline-block;
            background: #4a5568;
            color: white;
            padding: 4px 12px;
            border-radius: 15px;
            font-size: 0.8em;
            margin-left: 10px;
        }

        .footer {
            text-align: center;
            margin-top: 40px;
            padding: 20px;
            color: #666;
            border-top: 1px solid #e2e8f0;
        }

        .home-button {
            background-color: #000;
            color: #fff;
            font-weight: bold;
            padding: 0.5rem 1rem;
            border-radius: 0.5rem;
            text-decoration: none;
            transition: all 0.3s ease;
            position: absolute;
            top: 1rem;
            left: 1rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            z-index: 10;
        }

        .home-button:hover {
            background-color: #333;
            transform: translateY(-2px);
        }

        @media (max-width: 768px) {
            .container {
                padding: 15px;
            }

            .header h1 {
                font-size: 2em;
            }

            .categories {
                grid-template-columns: 1fr;
                gap: 20px;
            }

            .category {
                padding: 20px;
            }

            .home-button {
                top: 0.5rem;
                right: 0.5rem;
                padding: 0.4rem 0.8rem;
                font-size: 0.9rem;
            }
        }

        .no-results {
            text-align: center;
            color: #666;
            font-style: italic;
            padding: 20px;
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <a href="index.html" class="home-button">
                <i class="fas fa-home"></i>
                Tela Inicial
            </a>
            <h1>📋 Distrito Sanitário Eldorado</h1>
            <p>Relação dos Exames Oftalmologicos</p>
            <p>Pagina criada por Ana P. A. Silva/Suporte Vivver/ Distrito Eldorado</p>
        </div>

        <div class="alert">
            ⚠️ <strong>Atenção Unidades de Saúde!</strong><br>
            Segue uma lista com todos os exames de oftalmologia que são marcados pelo Distrito Eldorado, assim como os que estão SEM PRESTADOR e os que são marcados em Belo Horizonte.<br>
            <strong>Atenção na hora de enviá-los para a diretoria de regulação!</strong>
        </div>

        <div class="search-container">
            <div class="search-box">
                <input type="text" class="search-input" id="searchInput" placeholder="🔍 Digite o nome do exame para buscar...">
                <button class="search-clear" id="clearSearch">✕</button>
            </div>
        </div>

        <div class="categories">
            <div class="category eldorado">
                <h2>✅ Marcados pelo Distrito Eldorado <span class="exam-count" id="eldorado-count">26</span></h2>
                <ul class="exam-list" id="eldorado-list">
                    <li class="exam-item">Angiografia Fluorescente</li>
                    <li class="exam-item">Avaliação de Catarata</li>
                    <li class="exam-item">Avaliação de Prótese</li>
                    <li class="exam-item">Avaliação de Pterígio</li>
                    <li class="exam-item">Blefaroplastia</li>
                    <li class="exam-item">Campo Visual Computadorizado</li>
                    <li class="exam-item">Capsulotomia a Yag Laser</li>
                    <li class="exam-item">CDPO - Curva Diária de Pressão Ocular</li>
                    <li class="exam-item">Check-up de Estrabismo</li>
                    <li class="exam-item">Check-up de Glaucoma</li>
                    <li class="exam-item">Check-up de Plástica Ocular</li>
                    <li class="exam-item">Check-up de Pálpebra</li>
                    <li class="exam-item">Correção Cirurgia de Ptose</li>
                    <li class="exam-item">Correção de Blefarocalaze/Dermatocálaze</li>
                    <li class="exam-item">Correção de Entrópio e Ectrópio</li>
                    <li class="exam-item">Exerese de Pterígio</li>
                    <li class="exam-item">Exerese de Tumor de Pálpebra</li>
                    <li class="exam-item">Facoemulsificação com implante de LIO</li>
                    <li class="exam-item">Facotrabeculectomia</li>
                    <li class="exam-item">Fotocoagulação a Laser</li>
                    <li class="exam-item">Iridotomia a Laser</li>
                    <li class="exam-item">Mapeamento de Retina</li>
                    <li class="exam-item">Paquimetria</li>
                    <li class="exam-item">Trabeculectomia</li>
                    <li class="exam-item">Trec</li>
                    <li class="exam-item">Triquiase</li>
                </ul>
            </div>

            <div class="category bh">
                <h2>🏥 Marcados em Belo Horizonte <span class="exam-count" id="bh-count">25</span></h2>
                <ul class="exam-list" id="bh-list">
                    <li class="exam-item">Campo Visual Manual</li>
                    <li class="exam-item">Check-up Córnea</li>
                    <li class="exam-item">Correção Cirúrgica de Estrabismo</li>
                    <li class="exam-item">Dacriocistografia</li>
                    <li class="exam-item">Dacriocistorrinostomia</li>
                    <li class="exam-item">Ecografia B</li>
                    <li class="exam-item">Epilação à Laser</li>
                    <li class="exam-item">Exames sob sedação</li>
                    <li class="exam-item">Facectomia com implante de LIO</li>
                    <li class="exam-item">FDT</li>
                    <li class="exam-item">Gonioscopia</li>
                    <li class="exam-item">Implante secundário de LIO</li>
                    <li class="exam-item">Injeção Retrobulbar</li>
                    <li class="exam-item">Microscopia Especular</li>
                    <li class="exam-item">Neurooftalmologia</li>
                    <li class="exam-item">Reconstrução de Cavidade</li>
                    <li class="exam-item">Retinografia Colorida</li>
                    <li class="exam-item">Sondagem das Vias Lacrimais</li>
                    <li class="exam-item">Sondagem das Vias Lacrimais c/ sedação</li>
                    <li class="exam-item">Teste de sensibilidade ao contraste</li>
                    <li class="exam-item">Teste de Visão de Cores</li>
                    <li class="exam-item">Teste Lente de Contato</li>
                    <li class="exam-item">Topografia Corneana</li>
                    <li class="exam-item">Uveíte</li>
                    <li class="exam-item">Visão sub-Norma</li>
                    <li class="exam-item">Vitrectomia</li>
                </ul>
            </div>

            <div class="category sem-prestador">
                <h2>❌ Sem Prestador <span class="exam-count" id="sem-prestador-count">6</span></h2>
                <ul class="exam-list" id="sem-prestador-list">
                    <li class="exam-item">EOG - Eletrooculograma</li>
                    <li class="exam-item">ERG - Eletrorretinografia</li>
                    <li class="exam-item">Exerese Calázio</li>
                    <li class="exam-item">Potencial de Acuidade</li>
                    <li class="exam-item">Potencial Visual Evocado ou PVE</li>
                    <li class="exam-item">OCT</li>
                </ul>
            </div>
        </div>

        <div class="no-results" id="noResults">
            <p>🔍 Nenhum exame encontrado com o termo buscado.</p>
        </div>

        <div class="footer">
            <p>📋 Sistema de Consulta de Exames Oftalmológicos - Distrito Eldorado</p>
            <p>📅 Atualizado em: <span id="currentDate"></span></p>
        </div>
    </div>

    <script>
        // Elementos
        const searchInput = document.getElementById('searchInput');
        const clearButton = document.getElementById('clearSearch');
        const noResults = document.getElementById('noResults');
        const examLists = document.querySelectorAll('.exam-list');
        const categories = document.querySelectorAll('.category');

        // Contadores
        const eldoradoCount = document.getElementById('eldorado-count');
        const bhCount = document.getElementById('bh-count');
        const semPrestadorCount = document.getElementById('sem-prestador-count');

        // Data atual
        document.getElementById('currentDate').textContent = new Date().toLocaleDateString('pt-BR');

        // Função de busca
        function performSearch() {
            const searchTerm = searchInput.value.toLowerCase().trim();
            let hasResults = false;
            let visibleCounts = { eldorado: 0, bh: 0, semPrestador: 0 };

            if (searchTerm === '') {
                // Mostrar todos os exames
                document.querySelectorAll('.exam-item').forEach(item => {
                    item.style.display = 'block';
                    item.classList.remove('highlight');
                });
                categories.forEach(cat => cat.style.display = 'block');
                noResults.style.display = 'none';
                clearButton.style.display = 'none';
                
                // Restaurar contadores originais
                eldoradoCount.textContent = '26';
                bhCount.textContent = '25';
                semPrestadorCount.textContent = '6';
                return;
            }

            clearButton.style.display = 'block';

            // Buscar em todos os itens
            document.querySelectorAll('.exam-item').forEach(item => {
                const examName = item.textContent.toLowerCase();
                const category = item.closest('.category');
                
                if (examName.includes(searchTerm)) {
                    item.style.display = 'block';
                    item.classList.add('highlight');
                    hasResults = true;
                    
                    // Contar por categoria
                    if (category.classList.contains('eldorado')) {
                        visibleCounts.eldorado++;
                    } else if (category.classList.contains('bh')) {
                        visibleCounts.bh++;
                    } else if (category.classList.contains('sem-prestador')) {
                        visibleCounts.semPrestador++;
                    }
                } else {
                    item.style.display = 'none';
                    item.classList.remove('highlight');
                }
            });

            // Atualizar contadores
            eldoradoCount.textContent = visibleCounts.eldorado;
            bhCount.textContent = visibleCounts.bh;
            semPrestadorCount.textContent = visibleCounts.semPrestador;

            // Mostrar/ocultar categorias vazias
            categories.forEach(category => {
                const visibleItems = category.querySelectorAll('.exam-item[style*="block"]');
                if (visibleItems.length === 0) {
                    category.style.display = 'none';
                } else {
                    category.style.display = 'block';
                }
            });

            // Mostrar mensagem se não houver resultados
            noResults.style.display = hasResults ? 'none' : 'block';
        }

        // Função para limpar busca
        function clearSearch() {
            searchInput.value = '';
            performSearch(); // Re-executa a busca para resetar os filtros
        }

        // Event Listeners
        searchInput.addEventListener('input', performSearch);
        clearButton.addEventListener('click', clearSearch);

        // Inicializar contadores e exibir todos os exames ao carregar a página
        window.addEventListener('load', () => {
            performSearch();
        });
    </script>
</body>
</html>
