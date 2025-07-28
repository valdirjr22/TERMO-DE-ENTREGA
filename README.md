<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cadastro e Devolução de Equipamento no Ano de 2025</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        /* Custom styles for print, overriding Tailwind where necessary */
        @media print {
            body {
                margin: 0;
                padding: 0;
                text-align: center;
                font-family: 'Inter', sans-serif; /* Ensure font is consistent in print */
            }
            .termo-container {
                display: block !important; /* Force display for print */
                margin-top: 80px;
                text-align: center;
                width: 100%;
            }
            .termo-container pre {
                font-size: 16px;
                line-height: 1.5;
                margin: 0 auto;
                width: 80%;
                text-align: left;
                display: block;
            }
            .termo-container button, .filtro-container, .form-container, .cursos-cadastrados, h1, .choice-buttons {
                display: none !important; /* Hide other elements when printing term */
            }
            /* Specific print styles for the report */
            .print-report-only {
                display: block !important;
            }
            .print-report-only h1 {
                display: block !important;
            }
            .print-report-only table {
                width: 100%;
                border-collapse: collapse;
                margin-top: 20px;
            }
            .print-report-only th, .print-report-only td {
                border: 1px solid #ddd;
                padding: 8px;
                text-align: left;
            }
            .print-report-only th {
                background-color: #f2f2f2;
            }
        }
    </style>
</head>
<body class="bg-gray-100 min-h-screen flex flex-col items-center p-4 font-inter text-gray-800">

    <h1 class="text-3xl md:text-4xl font-extrabold text-center mb-8 text-blue-700">Sistema de Gestão de Equipamentos - 2025</h1>

    <div id="initialChoice" class="choice-buttons w-full max-w-2xl bg-white p-8 rounded-lg shadow-xl mb-8 flex justify-center gap-4">
        <button onclick="showDeliveryForm()" class="py-3 px-6 border border-transparent rounded-md shadow-sm text-lg font-semibold text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
            Cadastro de Entrega
        </button>
        <button onclick="showReturnForm()" class="py-3 px-6 border border-transparent rounded-md shadow-sm text-lg font-semibold text-white bg-green-600 hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500">
            Cadastro de Devolução
        </button>
        <button onclick="showStudentsList()" class="py-3 px-6 border border-transparent rounded-md shadow-sm text-lg font-semibold text-white bg-purple-600 hover:bg-purple-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-purple-500">
            Ver Registros
        </button>
    </div>

    <div id="deliveryFormSection" class="form-container w-full max-w-2xl bg-white p-8 rounded-lg shadow-xl mb-8 hidden">
        <h2 class="text-2xl font-semibold text-center mb-6 text-blue-600">Cadastro de Entrega de Equipamento</h2>
        <form id="formDelivery" onsubmit="gerarTermoEntrega(event)">
            <label for="nomeEntrega" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Nome Completo:</label>
            <input type="text" id="nomeEntrega" name="nome" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">

            <label for="cpfEntrega" class="block text-sm font-medium text-gray-700 mb-1 mt-4">CPF:</label>
            <input type="text" id="cpfEntrega" name="cpf" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">

            <label for="matriculaEntrega" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Número de Matrícula:</label>
            <input type="text" id="matriculaEntrega" name="matricula" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">

            <label for="serieEntrega" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Série:</label>
            <input type="text" id="serieEntrega" name="serie" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">

            <label for="turmaEntrega" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Turma:</label>
            <input type="text" id="turmaEntrega" name="turma" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">

            <label for="turnoEntrega" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Turno:</label>
            <input type="text" id="turnoEntrega" name="turno" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">

            <label for="cursoEntrega" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Curso:</label>
            <select id="cursoEntrega" name="curso" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">
                <option value="">Selecione o curso</option>
                <option value="MédioTec">MédioTec</option>
                </select>

            <label for="anoEntrega" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Ano:</label>
            <input type="number" id="anoEntrega" name="ano" required min="2020" max="2099" value="2025" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">

            <label for="equipamentoEntrega" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Equipamento (Chromebook):</label>
            <input type="text" id="equipamentoEntrega" name="equipamento" placeholder="Ex: Chromebook Samsung KT4BR" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">

            <label for="numeroSerieEntrega" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Número de Série:</label>
            <input type="text" id="numeroSerieEntrega" name="numeroSerie" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">

            <button type="submit" id="submitDeliveryButton" class="w-full py-2 px-4 border border-transparent rounded-md shadow-sm text-lg font-semibold text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500 mt-6">Gerar Termo de Entrega</button>
            <button type="button" onclick="showInitialChoice()" class="w-full py-2 px-4 border border-transparent rounded-md shadow-sm text-lg font-semibold text-white bg-gray-600 hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-500 mt-4">Voltar</button>
        </form>
    </div>

    <div id="returnFormSection" class="form-container w-full max-w-2xl bg-white p-8 rounded-lg shadow-xl mb-8 hidden">
        <h2 class="text-2xl font-semibold text-center mb-6 text-green-600">Cadastro de Devolução de Equipamento</h2>
        <form id="formReturn" onsubmit="gerarTermoDevolucao(event)">
            <label for="nomeDevolucao" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Nome Completo:</label>
            <input type="text" id="nomeDevolucao" name="nome" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm">

            <label for="cpfDevolucao" class="block text-sm font-medium text-gray-700 mb-1 mt-4">CPF:</label>
            <input type="text" id="cpfDevolucao" name="cpf" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm">

            <label for="matriculaDevolucao" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Número de Matrícula:</label>
            <input type="text" id="matriculaDevolucao" name="matricula" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm">

            <label for="serieDevolucao" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Série:</label>
            <input type="text" id="serieDevolucao" name="serie" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm">

            <label for="turmaDevolucao" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Turma:</label>
            <input type="text" id="turmaDevolucao" name="turma" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm">

            <label for="turnoDevolucao" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Turno:</label>
            <input type="text" id="turnoDevolucao" name="turno" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm">

            <label for="cursoDevolucao" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Curso:</label>
            <select id="cursoDevolucao" name="curso" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm">
                <option value="">Selecione o curso</option>
                <option value="MédioTec">MédioTec</option>
                </select>

            <label for="anoDevolucao" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Ano:</label>
            <input type="number" id="anoDevolucao" name="ano" required min="2020" max="2099" value="2025" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm">

            <label for="equipamentoDevolucao" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Equipamento (Chromebook):</label>
            <input type="text" id="equipamentoDevolucao" name="equipamento" placeholder="Ex: Chromebook Samsung KT4BR" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm">

            <label for="numeroSerieDevolucao" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Número de Série:</label>
            <input type="text" id="numeroSerieDevolucao" name="numeroSerie" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm">

            <label for="dataDevolucao" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Data de Devolução:</label>
            <input type="date" id="dataDevolucao" name="dataDevolucao" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm">

            <label for="condicaoDevolucao" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Condição do Equipamento na Devolução:</label>
            <select id="condicaoDevolucao" name="condicaoDevolucao" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm">
                <option value="">Selecione a condição</option>
                <option value="Em perfeito estado">Em perfeito estado</option>
                <option value="Com avarias">Com avarias</option>
                <option value="Extraviado">Extraviado</option>
            </select>

            <label for="observacoesDevolucao" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Observações da Devolução (Opcional):</label>
            <textarea id="observacoesDevolucao" name="observacoesDevolucao" rows="3" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm"></textarea>

            <button type="submit" id="submitReturnButton" class="w-full py-2 px-4 border border-transparent rounded-md shadow-sm text-lg font-semibold text-white bg-green-600 hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500 mt-6">Gerar Termo de Devolução</button>
            <button type="button" onclick="showInitialChoice()" class="w-full py-2 px-4 border border-transparent rounded-md shadow-sm text-lg font-semibold text-white bg-gray-600 hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-500 mt-4">Voltar</button>
        </form>
    </div>

    <div class="termo-container w-full max-w-3xl bg-white p-8 rounded-lg shadow-xl mb-8 hidden print:block" id="termoContainer">
        <h2 class="text-2xl font-semibold text-center mb-4 text-blue-600" id="termoTitle"></h2>
        <pre id="termoTexto" class="whitespace-pre-wrap break-words text-left mx-auto w-4/5 p-4 bg-gray-50 rounded-md border border-gray-200 text-sm"></pre>
        <button onclick="imprimirTermo()" class="py-2 px-6 border border-transparent rounded-md shadow-sm text-base font-medium text-white bg-green-600 hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500 mt-6 print:hidden">Imprimir Termo</button>
        <button type="button" onclick="hideTermoAndShowChoice()" class="py-2 px-6 border border-transparent rounded-md shadow-sm text-base font-medium text-white bg-gray-600 hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-500 mt-4 print:hidden">Voltar</button>
    </div>

    <div id="studentsListSection" class="cursos-cadastrados w-full max-w-4xl bg-white p-8 rounded-lg shadow-xl mb-8 hidden">
        <h2 class="text-2xl font-semibold text-center mb-4 text-blue-600">Registros de Equipamentos</h2>

        <div class="filtro-container w-full flex flex-wrap items-end gap-4 mb-8 p-6 bg-white rounded-lg shadow-md">
            <button onclick="listarRegistros()" class="py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">Lista Completa</button>

            <div class="flex flex-col flex-grow">
                <label for="filtroTipo" class="block text-sm font-medium text-gray-700">Filtrar por Tipo:</label>
                <select id="filtroTipo" onchange="filtrarLista()" class="px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">
                    <option value="">Todos os Tipos</option>
                    <option value="entrega">Entrega</option>
                    <option value="devolucao">Devolução</option>
                </select>
            </div>

            <div class="flex flex-col flex-grow">
                <label for="filtroTurma" class="block text-sm font-medium text-gray-700">Filtrar por Turma:</label>
                <select id="filtroTurma" onchange="filtrarLista()" class="px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">
                    <option value="">Todas as turmas</option>
                </select>
            </div>

            <div class="flex flex-col flex-grow">
                <label for="filtroTurno" class="block text-sm font-medium text-gray-700">Filtrar por Turno:</label>
                <select id="filtroTurno" onchange="filtrarLista()" class="px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">
                    <option value="">Todos os turnos</option>
                </select>
            </div>

            <div class="flex flex-col flex-grow">
                <label for="filtroAno" class="block text-sm font-medium text-gray-700">Filtrar por Ano:</label>
                <select id="filtroAno" onchange="filtrarLista()" class="px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">
                    <option value="">Todos os Anos</option>
                </select>
            </div>

            <div class="flex flex-col flex-grow">
                <label for="filtroNumeroSerie" class="block text-sm font-medium text-gray-700">Pesquisar por Nº de Série:</label>
                <input type="text" id="filtroNumeroSerie" onkeyup="filtrarLista()" placeholder="Digite o Nº de Série" class="px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">
            </div>

            <button onclick="filtrarLista()" class="py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">Pesquisar</button>
            <button onclick="imprimirRelatorio()" class="py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-green-600 hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500">Imprimir Relatório</button>
        </div>

        <div class="overflow-x-auto">
            <table id="tabelaRegistros" class="min-w-full divide-y divide-gray-200 rounded-lg overflow-hidden">
                <thead class="bg-gray-50">
                    <tr>
                        <th scope="col" class="px-2 py-1 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Tipo</th>
                        <th scope="col" class="px-2 py-1 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nome</th>
                        <th scope="col" class="px-2 py-1 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Curso</th>
                        <th scope="col" class="px-2 py-1 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Ano</th>
                        <th scope="col" class="px-2 py-1 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Matrícula</th>
                        <th scope="col" class="px-2 py-1 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Turma</th>
                        <th scope="col" class="px-2 py-1 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Turno</th>
                        <th scope="col" class="px-2 py-1 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nº Série</th>
                        <th scope="col" class="px-2 py-1 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Data</th>
                        <th scope="col" class="px-2 py-1 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Ações</th>
                    </tr>
                </thead>
                <tbody class="bg-white divide-y divide-gray-200">
                    </tbody>
            </table>
        </div>
        <button onclick="showInitialChoice()" class="w-full py-2 px-4 border border-transparent rounded-md shadow-sm text-lg font-semibold text-white bg-gray-600 hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-500 mt-6">Voltar ao Início</button>
    </div>

    <script>
        let registroEditandoIndex = null;
        let tipoRegistroEditando = null; // To keep track if we are editing 'entrega' or 'devolucao'

        // Function to show/hide sections
        function showSection(sectionId) {
            document.getElementById('initialChoice').classList.add('hidden');
            document.getElementById('deliveryFormSection').classList.add('hidden');
            document.getElementById('returnFormSection').classList.add('hidden');
            document.getElementById('termoContainer').classList.add('hidden');
            document.getElementById('studentsListSection').classList.add('hidden');

            document.getElementById(sectionId).classList.remove('hidden');
        }

        function showInitialChoice() {
            showSection('initialChoice');
            // Reset forms when going back to initial choice
            document.getElementById('formDelivery').reset();
            document.getElementById('formReturn').reset();
            registroEditandoIndex = null;
            tipoRegistroEditando = null;
            document.getElementById("submitDeliveryButton").textContent = "Gerar Termo de Entrega";
            document.getElementById("submitReturnButton").textContent = "Gerar Termo de Devolução";
        }

        function showDeliveryForm() {
            showSection('deliveryFormSection');
            document.getElementById('formDelivery').reset(); // Clear form when showing
            // Set default year for delivery form
            document.getElementById("anoEntrega").value = new Date().getFullYear();
            registroEditandoIndex = null;
            tipoRegistroEditando = null;
            document.getElementById("submitDeliveryButton").textContent = "Gerar Termo de Entrega";
        }

        function showReturnForm() {
            showSection('returnFormSection');
            document.getElementById('formReturn').reset(); // Clear form when showing
            // Set default year for return form
            document.getElementById("anoDevolucao").value = new Date().getFullYear();
            registroEditandoIndex = null;
            tipoRegistroEditando = null;
            document.getElementById("submitReturnButton").textContent = "Gerar Termo de Devolução";
        }

        function showStudentsList() {
            showSection('studentsListSection');
            listarRegistros(); // Ensure the list is updated when shown
        }

        function hideTermoAndShowChoice() {
            document.getElementById('termoContainer').classList.add('hidden');
            showInitialChoice();
        }

        function gerarTermoEntrega(event) {
            event.preventDefault();

            const nome = document.getElementById("nomeEntrega").value;
            const cpf = document.getElementById("cpfEntrega").value;
            const matricula = document.getElementById("matriculaEntrega").value;
            const serie = document.getElementById("serieEntrega").value;
            const turma = document.getElementById("turmaEntrega").value;
            const turno = document.getElementById("turnoEntrega").value;
            const curso = document.getElementById("cursoEntrega").value;
            const ano = document.getElementById("anoEntrega").value; // Get Ano
            const equipamento = document.getElementById("equipamentoEntrega").value;
            const numeroSerie = document.getElementById("numeroSerieEntrega").value;
            const dataRegistro = new Date().toLocaleDateString('pt-BR');

            const registro = {
                type: 'entrega',
                nome,
                cpf,
                matricula,
                serie,
                turma,
                turno,
                curso,
                ano, // Store Ano
                equipamento,
                numeroSerie,
                dataRegistro
            };

            let registros = JSON.parse(localStorage.getItem('registros')) || [];

            if (registroEditandoIndex !== null && tipoRegistroEditando === 'entrega') {
                registros[registroEditandoIndex] = registro;
                registroEditandoIndex = null;
                tipoRegistroEditando = null;
                document.getElementById("submitDeliveryButton").textContent = "Gerar Termo de Entrega";
            } else {
                registros.push(registro);
            }

            localStorage.setItem('registros', JSON.stringify(registros));

            const termo = `


Eu, ${nome} portador do CPF ${cpf},Aluno do curso ${curso}, de Matrícula ${matricula} na Instituição Senac Paulista, da Turma/Turno ${turma}/${turno}, no ano letivo de ${ano}. Declaro ter Recebi o equipamento da Instituição nas condições descritas abaixo,em plenas condições de funcionamento.

• Equipamento: ${equipamento} com seu Carregador
• Marca/Modelo: Samsung / KT4BR
• Número de Série: ${numeroSerie}

Além disso, confirmo que o equipamento está acompanhado do seu carregador.E em caso de danos ou extravios, comprometo-me em arcar com os custos de reparo ou reposição do equipamento, conforme estabelecido em contrato no ato do início do ano letivo.Assim, o presente recebimento é feito com a anuência do Senac Paulista.

             ASSINATURA DO ALUNO/OU RESPONSAVEL
___________________________________________________

REPRESENTANTE DA INSTITUIÇÃO
Valdir Rodrigues da Silva Junior
Monitor de TI

Paulista, ______ de ____________________ de ${ano}.
            `;

            document.getElementById("termoTitle").textContent = "Termo de Entrega de Equipamento Eletrônico";
            document.getElementById("termoTexto").textContent = termo;
            showSection('termoContainer');
        }

        function gerarTermoDevolucao(event) {
            event.preventDefault();

            const nome = document.getElementById("nomeDevolucao").value;
            const cpf = document.getElementById("cpfDevolucao").value;
            const matricula = document.getElementById("matriculaDevolucao").value;
            const serie = document.getElementById("serieDevolucao").value;
            const turma = document.getElementById("turmaDevolucao").value;
            const turno = document.getElementById("turnoDevolucao").value;
            const curso = document.getElementById("cursoDevolucao").value;
            const ano = document.getElementById("anoDevolucao").value; // Get Ano
            const equipamento = document.getElementById("equipamentoDevolucao").value;
            const numeroSerie = document.getElementById("numeroSerieDevolucao").value;
            const dataDevolucao = document.getElementById("dataDevolucao").value; // YYYY-MM-DD
            const condicaoDevolucao = document.getElementById("condicaoDevolucao").value;
            const observacoesDevolucao = document.getElementById("observacoesDevolucao").value;
            const dataRegistro = new Date().toLocaleDateString('pt-BR');

            const registro = {
                type: 'devolucao',
                nome,
                cpf,
                matricula,
                serie,
                turma,
                turno,
                curso,
                ano, // Store Ano
                equipamento,
                numeroSerie,
                dataDevolucao,
                condicaoDevolucao,
                observacoesDevolucao,
                dataRegistro
            };

            let registros = JSON.parse(localStorage.getItem('registros')) || [];

            if (registroEditandoIndex !== null && tipoRegistroEditando === 'devolucao') {
                registros[registroEditandoIndex] = registro;
                registroEditandoIndex = null;
                tipoRegistroEditando = null;
                document.getElementById("submitReturnButton").textContent = "Gerar Termo de Devolução";
            } else {
                registros.push(registro);
            }

            localStorage.setItem('registros', JSON.stringify(registros));

            const termo = `


Eu, ${nome} portador do CPF ${cpf},Aluno do curso ${curso}, de Matrícula ${matricula} na Instituição Senac Paulista, da Turma/Turno ${turma}/${turno}, no ano letivo de ${ano}.
Declaro ter DEVOLVIDO o equipamento da Instituição nas condições descritas abaixo, na data de ${new Date(dataDevolucao).toLocaleDateString('pt-BR')}.

• Equipamento: ${equipamento}
• Marca/Modelo: Samsung / KT4BR
• Número de Série: ${numeroSerie}
• Condição na Devolução: ${condicaoDevolucao}
${observacoesDevolucao ? `• Observações: ${observacoesDevolucao}` : ''}

Confirmo que a devolução foi realizada de acordo com as políticas da Instituição.

             ASSINATURA DO ALUNO/OU RESPONSAVEL
___________________________________________________

REPRESENTANTE DA INSTITUIÇÃO
Valdir Rodrigues da Silva Junior
Monitor de TI

Paulista, ______ de ____________________ de ${ano}.
            `;
            document.getElementById("termoTitle").textContent = "Termo de Devolução de Equipamento Eletrônico";
            document.getElementById("termoTexto").textContent = termo;
            showSection('termoContainer');
        }

        function listarRegistros() {
            const registros = JSON.parse(localStorage.getItem('registros')) || [];
            const tabelaRegistrosBody = document.getElementById("tabelaRegistros").getElementsByTagName("tbody")[0];
            tabelaRegistrosBody.innerHTML = "";

            registros.forEach((registro, index) => {
                const row = tabelaRegistrosBody.insertRow();
                const dataDisplay = registro.type === 'entrega' ? registro.dataRegistro : registro.dataDevolucao ? new Date(registro.dataDevolucao).toLocaleDateString('pt-BR') : '';

                row.innerHTML = `
                    <td class="px-2 py-1 whitespace-nowrap">${registro.type === 'entrega' ? 'Entrega' : 'Devolução'}</td>
                    <td class="px-2 py-1 whitespace-nowrap">${registro.nome}</td>
                    <td class="px-2 py-1 whitespace-nowrap">${registro.curso}</td>
                    <td class="px-2 py-1 whitespace-nowrap">${registro.ano || '-'}</td>
                    <td class="px-2 py-1 whitespace-nowrap">${registro.matricula}</td>
                    <td class="px-2 py-1 whitespace-nowrap">${registro.turma}</td>
                    <td class="px-2 py-1 whitespace-nowrap">${registro.turno}</td>
                    <td class="px-2 py-1 whitespace-nowrap">${registro.numeroSerie}</td>
                    <td class="px-2 py-1 whitespace-nowrap">${dataDisplay}</td>
                    <td class="px-2 py-1 whitespace-nowrap text-right text-xs font-medium">
                        <button class="btn-editar px-1 py-0.5 text-xs font-medium text-white bg-green-500 rounded-md hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500" onclick="editarRegistro(${index})">Editar</button>
                        <button class="btn-excluir ml-0.5 px-1 py-0.5 text-xs font-medium text-white bg-red-500 rounded-md hover:bg-red-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500" onclick="excluirRegistro(${index})">Excluir</button>
                    </td>
                `;
            });

            preencherFiltros(registros);
        }

        function preencherFiltros(registros) {
            const filtroTurma = document.getElementById("filtroTurma");
            const filtroTurno = document.getElementById("filtroTurno");
            const filtroAno = document.getElementById("filtroAno");

            // Store current selected values to preserve them after repopulating
            const selectedTurma = filtroTurma.value;
            const selectedTurno = filtroTurno.value;
            const selectedAno = filtroAno.value;

            filtroTurma.innerHTML = "<option value=''>Todas as turmas</option>";
            filtroTurno.innerHTML = "<option value=''>Todos os turnos</option>";
            filtroAno.innerHTML = "<option value=''>Todos os Anos</option>";

            const turmas = [...new Set(registros.map(r => r.turma))].sort();
            const turnos = [...new Set(registros.map(r => r.turno))].sort();
            // Ensure year is treated as a string for Set and sort correctly as numbers
            const anos = [...new Set(registros.map(r => r.ano).filter(Boolean))].sort((a, b) => a - b);


            turmas.forEach(turma => {
                const option = document.createElement("option");
                option.value = turma;
                option.textContent = turma;
                filtroTurma.appendChild(option);
            });

            turnos.forEach(turno => {
                const option = document.createElement("option");
                option.value = turno;
                option.textContent = turno;
                filtroTurno.appendChild(option);
            });

            anos.forEach(ano => {
                const option = document.createElement("option");
                option.value = ano;
                option.textContent = ano;
                filtroAno.appendChild(option);
            });

            // Restore previously selected values
            filtroTurma.value = selectedTurma;
            filtroTurno.value = selectedTurno;
            filtroAno.value = selectedAno;
        }

        function filtrarLista() {
            const filtroTipo = document.getElementById("filtroTipo").value;
            const filtroTurma = document.getElementById("filtroTurma").value;
            const filtroTurno = document.getElementById("filtroTurno").value;
            const filtroAno = document.getElementById("filtroAno").value; // Get Ano filter value
            const filtroNumeroSerie = document.getElementById("filtroNumeroSerie").value.toLowerCase();
            const registros = JSON.parse(localStorage.getItem('registros')) || [];

            const registrosFiltrados = registros.filter(registro => {
                const tipoMatch = filtroTipo ? registro.type === filtroTipo : true;
                const turmaMatch = filtroTurma ? registro.turma === filtroTurma : true;
                const turnoMatch = filtroTurno ? registro.turno === filtroTurno : true;
                const anoMatch = filtroAno ? String(registro.ano) === filtroAno : true; // Match by Ano
                const numeroSerieMatch = filtroNumeroSerie ? registro.numeroSerie.toLowerCase().includes(filtroNumeroSerie) : true;
                return tipoMatch && turmaMatch && turnoMatch && anoMatch && numeroSerieMatch; // Include anoMatch
            });

            const tabelaRegistrosBody = document.getElementById("tabelaRegistros").getElementsByTagName("tbody")[0];
            tabelaRegistrosBody.innerHTML = "";

            if (registrosFiltrados.length === 0 && filtroNumeroSerie !== '') {
                const row = tabelaRegistrosBody.insertRow();
                row.innerHTML = `<td colspan="10" class="px-2 py-1 whitespace-nowrap text-center text-red-500 font-medium">Nenhum equipamento localizado com o número de série fornecido.</td>`;
            } else if (registrosFiltrados.length === 0) {
                const row = tabelaRegistrosBody.insertRow();
                row.innerHTML = `<td colspan="10" class="px-2 py-1 whitespace-nowrap text-center text-gray-500 font-medium">Nenhum registro encontrado com os filtros selecionados.</td>`;
            } else {
                registrosFiltrados.forEach((registro, index) => {
                    const row = tabelaRegistrosBody.insertRow();
                    const dataDisplay = registro.type === 'entrega' ? registro.dataRegistro : registro.dataDevolucao ? new Date(registro.dataDevolucao).toLocaleDateString('pt-BR') : '';

                    row.innerHTML = `
                        <td class="px-2 py-1 whitespace-nowrap">${registro.type === 'entrega' ? 'Entrega' : 'Devolução'}</td>
                        <td class="px-2 py-1 whitespace-nowrap">${registro.nome}</td>
                        <td class="px-2 py-1 whitespace-nowrap">${registro.curso}</td>
                        <td class="px-2 py-1 whitespace-nowrap">${registro.ano || '-'}</td>
                        <td class="px-2 py-1 whitespace-nowrap">${registro.matricula}</td>
                        <td class="px-2 py-1 whitespace-nowrap">${registro.turma}</td>
                        <td class="px-2 py-1 whitespace-nowrap">${registro.turno}</td>
                        <td class="px-2 py-1 whitespace-nowrap">${registro.numeroSerie}</td>
                        <td class="px-2 py-1 whitespace-nowrap">${dataDisplay}</td>
                        <td class="px-2 py-1 whitespace-nowrap text-right text-xs font-medium">
                            <button class="btn-editar px-1 py-0.5 text-xs font-medium text-white bg-green-500 rounded-md hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500" onclick="editarRegistro(${index})">Editar</button>
                            <button class="btn-excluir ml-0.5 px-1 py-0.5 text-xs font-medium text-white bg-red-500 rounded-md hover:bg-red-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500" onclick="excluirRegistro(${index})">Excluir</button>
                        </td>
                    `;
                });
            }
        }

        function editarRegistro(index) {
            const registros = JSON.parse(localStorage.getItem('registros')) || [];
            const registro = registros[index];

            registroEditandoIndex = index;
            tipoRegistroEditando = registro.type;

            if (registro.type === 'entrega') {
                document.getElementById("nomeEntrega").value = registro.nome;
                document.getElementById("cpfEntrega").value = registro.cpf;
                document.getElementById("matriculaEntrega").value = registro.matricula;
                document.getElementById("serieEntrega").value = registro.serie;
                document.getElementById("turmaEntrega").value = registro.turma;
                document.getElementById("turnoEntrega").value = registro.turno;
                document.getElementById("cursoEntrega").value = registro.curso;
                document.getElementById("anoEntrega").value = registro.ano; // Set Ano
                document.getElementById("equipamentoEntrega").value = registro.equipamento;
                document.getElementById("numeroSerieEntrega").value = registro.numeroSerie;
                document.getElementById("submitDeliveryButton").textContent = "Atualizar Entrega";
                showDeliveryForm();
            } else if (registro.type === 'devolucao') {
                document.getElementById("nomeDevolucao").value = registro.nome;
                document.getElementById("cpfDevolucao").value = registro.cpf;
                document.getElementById("matriculaDevolucao").value = registro.matricula;
                document.getElementById("serieDevolucao").value = registro.serie;
                document.getElementById("turmaDevolucao").value = registro.turma;
                document.getElementById("turnoDevolucao").value = registro.turno;
                document.getElementById("cursoDevolucao").value = registro.curso;
                document.getElementById("anoDevolucao").value = registro.ano; // Set Ano
                document.getElementById("equipamentoDevolucao").value = registro.equipamento;
                document.getElementById("numeroSerieDevolucao").value = registro.numeroSerie;
                document.getElementById("dataDevolucao").value = registro.dataDevolucao;
                document.getElementById("condicaoDevolucao").value = registro.condicaoDevolucao;
                document.getElementById("observacoesDevolucao").value = registro.observacoesDevolucao;
                document.getElementById("submitReturnButton").textContent = "Atualizar Devolução";
                showReturnForm();
            }
        }

        function excluirRegistro(index) {
            if (confirm("Tem certeza que deseja excluir este registro?")) {
                let registros = JSON.parse(localStorage.getItem('registros')) || [];
                registros.splice(index, 1);
                localStorage.setItem('registros', JSON.stringify(registros));
                listarRegistros();
            }
        }

        function imprimirTermo() {
            window.print();
        }

        function imprimirRelatorio() {
            const registros = JSON.parse(localStorage.getItem('registros')) || [];
            const filtroTipo = document.getElementById("filtroTipo").value;
            const filtroTurma = document.getElementById("filtroTurma").value;
            const filtroTurno = document.getElementById("filtroTurno").value;
            const filtroAno = document.getElementById("filtroAno").value; // Get Ano filter value
            const filtroNumeroSerie = document.getElementById("filtroNumeroSerie").value.toLowerCase();

            const registrosParaRelatorio = registros.filter(registro => {
                const tipoMatch = filtroTipo ? registro.type === filtroTipo : true;
                const turmaMatch = filtroTurma ? registro.turma === filtroTurma : true;
                const turnoMatch = filtroTurno ? registro.turno === filtroTurno : true;
                const anoMatch = filtroAno ? String(registro.ano) === filtroAno : true; // Match by Ano
                const numeroSerieMatch = filtroNumeroSerie ? registro.numeroSerie.toLowerCase().includes(filtroNumeroSerie) : true;
                return tipoMatch && turmaMatch && turnoMatch && anoMatch && numeroSerieMatch; // Include anoMatch
            });

            let relatorioContent = `
                <html>
                <head>
                    <title>Relatório de Registros de Equipamentos - 2025</title>
                    <style>
                        body { font-family: 'Inter', sans-serif; margin: 20px; }
                        h1 { text-align: center; color: #1e40af; margin-bottom: 20px; }
                        table { width: 100%; border-collapse: collapse; margin-top: 20px; border-radius: 0.375rem; overflow: hidden; }
                        th, td { border: 1px solid #e5e7eb; padding: 8px; text-align: left; }
                        th { background-color: #f9fafb; color: #6b7280; font-weight: 500; text-transform: uppercase; font-size: 0.75rem; }
                        td { color: #1f2937; font-size: 0.875rem; }
                        .filter-info { margin-bottom: 15px; font-size: 0.9rem; color: #4b5563; }
                        .filter-info strong { color: #1f2937; }
                        @media print {
                            .no-print { display: none; }
                        }
                    </style>
                </head>
                <body class="print-report-only">
                    <h1>Relatório de Registros de Equipamentos - 2025</h1>
                    <div class="filter-info">
                        <strong>Filtros Aplicados:</strong>
                        Tipo: ${filtroTipo ? (filtroTipo === 'entrega' ? 'Entrega' : 'Devolução') : 'Todos'} |
                        Turma: ${filtroTurma || 'Todas'} |
                        Turno: ${filtroTurno || 'Todos'} |
                        Ano: ${filtroAno || 'Todos'} |
                        Nº Série: ${filtroNumeroSerie || 'Todos'}
                    </div>
                    <table>
                        <thead>
                            <tr>
                                <th>Tipo</th>
                                <th>Nome do Aluno</th>
                                <th>Matrícula</th>
                                <th>Curso</th>
                                <th>Ano</th>
                                <th>Turma</th>
                                <th>Turno</th>
                                <th>Equipamento</th>
                                <th>Nº Série</th>
                                <th>Data</th>
                                ${filtroTipo === 'devolucao' || filtroTipo === '' ? '<th>Condição Devolução</th><th>Observações</th>' : ''}
                            </tr>
                        </thead>
                        <tbody>
            `;

            if (registrosParaRelatorio.length === 0) {
                relatorioContent += `
                    <tr>
                        <td colspan="${filtroTipo === 'devolucao' || filtroTipo === '' ? '12' : '10'}" style="text-align: center;">Nenhum registro encontrado para os filtros selecionados.</td>
                    </tr>
                `;
            } else {
                registrosParaRelatorio.forEach(registro => {
                    const dataDisplay = registro.type === 'entrega' ? registro.dataRegistro : registro.dataDevolucao ? new Date(registro.dataDevolucao).toLocaleDateString('pt-BR') : '';
                    relatorioContent += `
                                <tr>
                                    <td>${registro.type === 'entrega' ? 'Entrega' : 'Devolução'}</td>
                                    <td>${registro.nome}</td>
                                    <td>${registro.matricula}</td>
                                    <td>${registro.curso}</td>
                                    <td>${registro.ano || '-'}</td>
                                    <td>${registro.turma}</td>
                                    <td>${registro.turno}</td>
                                    <td>${registro.equipamento}</td>
                                    <td>${registro.numeroSerie}</td>
                                    <td>${dataDisplay}</td>
                                    ${registro.type === 'devolucao' || filtroTipo === '' ? `<td>${registro.condicaoDevolucao || '-'}</td><td>${registro.observacoesDevolucao || '-'}</td>` : ''}
                                </tr>
                    `;
                });
            }

            relatorioContent += `
                        </tbody>
                    </table>
                </body>
                </html>
            `;

            const printWindow = window.open('', '_blank');
            printWindow.document.write(relatorioContent);
            printWindow.document.close();
            printWindow.print();
        }

        // Initialize the view on page load
        window.onload = showInitialChoice;
    </script>

</body>
</html>
