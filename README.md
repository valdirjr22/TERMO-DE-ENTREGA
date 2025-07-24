<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cadastro de Entrega de Equipamento no Ano de 2025</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts - Inter -->
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
            .termo-container button, .filtro-container, .form-container, .cursos-cadastrados, h1 {
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

    <h1 class="text-3xl md:text-4xl font-extrabold text-center mb-8 text-blue-700">Cadastro de Entrega de Equipamento no Ano de 2025</h1>

    <div id="formSection" class="form-container w-full max-w-2xl bg-white p-8 rounded-lg shadow-xl mb-8">
        <form id="formCadastro" onsubmit="gerarTermo(event)">
            <label for="nome" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Nome Completa:</label>
            <input type="text" id="nome" name="nome" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">

            <label for="cpf" class="block text-sm font-medium text-gray-700 mb-1 mt-4">CPF:</label>
            <input type="text" id="cpf" name="cpf" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">

            <label for="matricula" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Número de Matrícula:</label>
            <input type="text" id="matricula" name="matricula" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">

            <label for="serie" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Série:</label>
            <input type="text" id="serie" name="serie" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">

            <label for="turma" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Turma:</label>
            <input type="text" id="turma" name="turma" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">

            <label for="turno" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Turno:</label>
            <input type="text" id="turno" name="turno" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">

            <label for="curso" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Curso:</label>
            <select id="curso" name="curso" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">
                <option value="">Selecione o curso</option>
                <option value="MédioTec">MédioTec</option>
            </select>

            <label for="equipamento" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Equipamento (Chromebook):</label>
            <input type="text" id="equipamento" name="equipamento" placeholder="Ex: Chromebook Samsung KT4BR" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">

            <label for="numeroSerie" class="block text-sm font-medium text-gray-700 mb-1 mt-4">Número de Série:</label>
            <input type="text" id="numeroSerie" name="numeroSerie" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">

            <button type="submit" id="submitButton" class="w-full py-2 px-4 border border-transparent rounded-md shadow-sm text-lg font-semibold text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500 mt-6">Gerar Termo de Entrega</button>
        </form>
        <!-- Button to view registered students -->
        <button onclick="showStudentsList()" class="w-full py-2 px-4 border border-transparent rounded-md shadow-sm text-lg font-semibold text-white bg-purple-600 hover:bg-purple-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-purple-500 mt-4">Ver Alunos Cadastrados</button>
    </div>

    <div class="termo-container w-full max-w-3xl bg-white p-8 rounded-lg shadow-xl mb-8 hidden print:block" id="termoContainer">
        <h2 class="text-2xl font-semibold text-center mb-4 text-blue-600">Termo de Entrega de Equipamento Eletrônico</h2>
        <pre id="termoTexto" class="whitespace-pre-wrap break-words text-left mx-auto w-4/5 p-4 bg-gray-50 rounded-md border border-gray-200 text-sm"></pre>
        <button onclick="imprimirTermo()" class="py-2 px-6 border border-transparent rounded-md shadow-sm text-base font-medium text-white bg-green-600 hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500 mt-6 print:hidden">Imprimir Termo</button>
    </div>

    <div id="studentsListSection" class="cursos-cadastrados w-full max-w-4xl bg-white p-8 rounded-lg shadow-xl mb-8 hidden">
        <h2 class="text-2xl font-semibold text-center mb-4 text-blue-600">Alunos Cadastrados</h2>
        
        <div class="filtro-container w-full flex flex-wrap items-end gap-4 mb-8 p-6 bg-white rounded-lg shadow-md">
            <button onclick="listarAlunos()" class="py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">Lista</button>

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
                <label for="filtroNumeroSerie" class="block text-sm font-medium text-gray-700">Pesquisar por Nº de Série:</label>
                <input type="text" id="filtroNumeroSerie" onkeyup="filtrarLista()" placeholder="Digite o Nº de Série" class="px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">
            </div>
            
            <button onclick="filtrarLista()" class="py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">Pesquisar</button>
            <button onclick="imprimirRelatorio()" class="py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-green-600 hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500">Imprimir Relatório</button>
        </div>

        <div class="overflow-x-auto">
            <table id="tabelaAlunos" class="min-w-full divide-y divide-gray-200 rounded-lg overflow-hidden">
                <thead class="bg-gray-50">
                    <tr>
                        <th scope="col" class="px-2 py-1 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nome</th>
                        <th scope="col" class="px-2 py-1 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Curso</th>
                        <th scope="col" class="px-2 py-1 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Matrícula</th>
                        <th scope="col" class="px-2 py-1 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Turma</th>
                        <th scope="col" class="px-2 py-1 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Turno</th>
                        <th scope="col" class="px-2 py-1 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Ações</th>
                    </tr>
                </thead>
                <tbody class="bg-white divide-y divide-gray-200">
                    <!-- Alunos cadastrados aparecerão aqui -->
                </tbody>
            </table>
        </div>
        <!-- Button to go back to the form -->
        <button onclick="showForm()" class="w-full py-2 px-4 border border-transparent rounded-md shadow-sm text-lg font-semibold text-white bg-gray-600 hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-500 mt-6">Voltar ao Cadastro</button>
    </div>

    <script>
        let alunoEditandoIndex = null;

        // Function to show the form section and hide others
        function showForm() {
            document.getElementById('formSection').classList.remove('hidden');
            document.getElementById('termoContainer').classList.add('hidden');
            document.getElementById('studentsListSection').classList.add('hidden');
        }

        // Function to show the students list section and hide others
        function showStudentsList() {
            document.getElementById('formSection').classList.add('hidden');
            document.getElementById('termoContainer').classList.add('hidden');
            document.getElementById('studentsListSection').classList.remove('hidden');
            listarAlunos(); // Ensure the list is updated when shown
        }

        function gerarTermo(event) {
            event.preventDefault();

            const nome = document.getElementById("nome").value;
            const cpf = document.getElementById("cpf").value;
            const matricula = document.getElementById("matricula").value;
            const serie = document.getElementById("serie").value;
            const turma = document.getElementById("turma").value;
            const turno = document.getElementById("turno").value;
            const curso = document.getElementById("curso").value;
            const equipamento = document.getElementById("equipamento").value;
            const numeroSerie = document.getElementById("numeroSerie").value;

            const aluno = {
                nome,
                cpf,
                matricula,
                serie,
                turma,
                turno,
                curso,
                equipamento,
                numeroSerie
            };

            let alunos = JSON.parse(localStorage.getItem('alunos')) || [];

            if (alunoEditandoIndex !== null) {
                alunos[alunoEditandoIndex] = aluno;
                alunoEditandoIndex = null;
                document.getElementById("submitButton").textContent = "Gerar Termo de Entrega";
            } else {
                alunos.push(aluno);
            }

            localStorage.setItem('alunos', JSON.stringify(alunos));
            listarAlunos();
            showStudentsList(); // Show the list after generating a term

            const termo = `


Eu, ${nome} portador do CPF ${cpf},Aluno do curso ${curso}, de Matrícula ${matricula} na Instituição Senac Paulista, da Turma/Turno ${turma}/${turno}, no ano letivo de 2025. Declaro ter Recebi o equipamento da Instituição nas condições descritas abaixo,em plenas condições de funcionamento.

• Equipamento: ${equipamento} com seu Carregador
• Marca/Modelo: Samsung / KT4BR
• Número de Série: ${numeroSerie}

Além disso, confirmo que o equipamento está acompanhado do seu carregador.E em caso de danos ou extravios, comprometo-me em arcar com os custos de reparo ou reposição do equipamento, conforme estabelecido em contrato no ato do início do ano letivo.Assim, o presente recebimento é feito com a anuência do Senac Paulista.

             ASSINATURA DO ALUNO/OU RESPONSAVEL
___________________________________________________

REPRESENTANTE DA INSTITUIÇÃO
Valdir Rodrigues da Silva Junior
Monitor de TI

Paulista, ______ de ____________________ de 2025.
            `;

            document.getElementById("termoTexto").textContent = termo;
            document.getElementById("termoContainer").style.display = 'block';
        }

        function listarAlunos() {
            const alunos = JSON.parse(localStorage.getItem('alunos')) || [];
            const tabelaAlunos = document.getElementById("tabelaAlunos").getElementsByTagName("tbody")[0];
            tabelaAlunos.innerHTML = "";

            alunos.forEach((aluno, index) => {
                const row = tabelaAlunos.insertRow();
                row.innerHTML = `
                    <td class="px-2 py-1 whitespace-nowrap">${aluno.nome}</td>
                    <td class="px-2 py-1 whitespace-nowrap">${aluno.curso}</td>
                    <td class="px-2 py-1 whitespace-nowrap">${aluno.matricula}</td>
                    <td class="px-2 py-1 whitespace-nowrap">${aluno.turma}</td>
                    <td class="px-2 py-1 whitespace-nowrap">${aluno.turno}</td>
                    <td class="px-2 py-1 whitespace-nowrap text-right text-xs font-medium">
                        <button class="btn-editar px-1 py-0.5 text-xs font-medium text-white bg-green-500 rounded-md hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500" onclick="editarAluno(${index})">Editar</button>
                        <button class="btn-excluir ml-0.5 px-1 py-0.5 text-xs font-medium text-white bg-red-500 rounded-md hover:bg-red-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500" onclick="excluirAluno(${index})">Excluir</button>
                    </td>
                `;
            });

            preencherFiltros(alunos);
        }

        function preencherFiltros(alunos) {
            const filtroTurma = document.getElementById("filtroTurma");
            const filtroTurno = document.getElementById("filtroTurno");

            filtroTurma.innerHTML = "<option value=''>Todas as turmas</option>";
            filtroTurno.innerHTML = "<option value=''>Todos os turnos</option>";

            const turmas = [...new Set(alunos.map(a => a.turma))];
            const turnos = [...new Set(alunos.map(a => a.turno))];

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
        }

        function filtrarLista() {
            const filtroTurma = document.getElementById("filtroTurma").value;
            const filtroTurno = document.getElementById("filtroTurno").value;
            const filtroNumeroSerie = document.getElementById("filtroNumeroSerie").value.toLowerCase(); // Get serial number filter value
            const alunos = JSON.parse(localStorage.getItem('alunos')) || [];

            const alunosFiltrados = alunos.filter(aluno => {
                const turmaMatch = filtroTurma ? aluno.turma === filtroTurma : true;
                const turnoMatch = filtroTurno ? aluno.turno === filtroTurno : true;
                // New filter for serial number
                const numeroSerieMatch = filtroNumeroSerie ? aluno.numeroSerie.toLowerCase().includes(filtroNumeroSerie) : true;
                return turmaMatch && turnoMatch && numeroSerieMatch; // Combine all filters
            });

            const tabelaAlunos = document.getElementById("tabelaAlunos").getElementsByTagName("tbody")[0];
            tabelaAlunos.innerHTML = ""; // Clear existing rows

            if (alunosFiltrados.length === 0 && filtroNumeroSerie !== '') {
                // If no matching students found and a serial number was searched, display message
                const row = tabelaAlunos.insertRow();
                row.innerHTML = `<td colspan="6" class="px-2 py-1 whitespace-nowrap text-center text-red-500 font-medium">Equipamento não localizado.</td>`;
            } else {
                // Otherwise, populate the table with filtered students
                alunosFiltrados.forEach((aluno, index) => {
                    const row = tabelaAlunos.insertRow();
                    row.innerHTML = `
                        <td class="px-2 py-1 whitespace-nowrap">${aluno.nome}</td>
                        <td class="px-2 py-1 whitespace-nowrap">${aluno.curso}</td>
                        <td class="px-2 py-1 whitespace-nowrap">${aluno.matricula}</td>
                        <td class="px-2 py-1 whitespace-nowrap">${aluno.turma}</td>
                        <td class="px-2 py-1 whitespace-nowrap">${aluno.turno}</td>
                        <td class="px-2 py-1 whitespace-nowrap text-right text-xs font-medium">
                            <button class="btn-editar px-1 py-0.5 text-xs font-medium text-white bg-green-500 rounded-md hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500" onclick="editarAluno(${index})">Editar</button>
                            <button class="btn-excluir ml-0.5 px-1 py-0.5 text-xs font-medium text-white bg-red-500 rounded-md hover:bg-red-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500" onclick="excluirAluno(${index})">Excluir</button>
                        </td>
                    `;
                });
            }
        }

        function editarAluno(index) {
            const alunos = JSON.parse(localStorage.getItem('alunos')) || [];
            const aluno = alunos[index];
            document.getElementById("nome").value = aluno.nome;
            document.getElementById("cpf").value = aluno.cpf;
            document.getElementById("matricula").value = aluno.matricula;
            document.getElementById("serie").value = aluno.serie;
            document.getElementById("turma").value = aluno.turma;
            document.getElementById("turno").value = aluno.turno;
            document.getElementById("curso").value = aluno.curso;
            document.getElementById("equipamento").value = aluno.equipamento;
            document.getElementById("numeroSerie").value = aluno.numeroSerie;

            alunoEditandoIndex = index;
            document.getElementById("submitButton").textContent = "Editar Entrega";
            showForm(); // Show the form for editing
        }

        function excluirAluno(index) {
            let alunos = JSON.parse(localStorage.getItem('alunos')) || [];
            alunos.splice(index, 1);
            localStorage.setItem('alunos', JSON.stringify(alunos));
            listarAlunos();
        }

        function imprimirTermo() {
            window.print();
        }

        // New function to print the report
        function imprimirRelatorio() {
            const alunos = JSON.parse(localStorage.getItem('alunos')) || [];
            let relatorioContent = `
                <html>
                <head>
                    <title>Relatório de Entregas de Equipamentos</title>
                    <style>
                        body { font-family: 'Inter', sans-serif; margin: 20px; }
                        h1 { text-align: center; color: #1e40af; } /* Tailwind blue-700 equivalent */
                        table { width: 100%; border-collapse: collapse; margin-top: 20px; border-radius: 0.375rem; overflow: hidden; } /* rounded-lg */
                        th, td { border: 1px solid #e5e7eb; padding: 8px; text-align: left; } /* border-gray-200 */
                        th { background-color: #f9fafb; color: #6b7280; font-weight: 500; text-transform: uppercase; font-size: 0.75rem; } /* bg-gray-50, text-gray-500, uppercase, tracking-wider */
                        td { color: #1f2937; font-size: 0.875rem; } /* text-gray-900, text-sm */
                        @media print {
                            .no-print { display: none; }
                        }
                    </style>
                </head>
                <body class="print-report-only">
                    <h1>Relatório de Entregas de Equipamentos - 2025</h1>
                    <table>
                        <thead>
                            <tr>
                                <th>Nome do Aluno</th>
                                <th>Série</th>
                                <th>Número de Série da Máquina</th>
                            </tr>
                        </thead>
                        <tbody>
            `;

            alunos.forEach(aluno => {
                relatorioContent += `
                            <tr>
                                <td>${aluno.nome}</td>
                                <td>${aluno.serie}</td>
                                <td>${aluno.numeroSerie}</td>
                            </tr>
                `;
            });

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
        window.onload = showForm;
    </script>

</body>
</html>
