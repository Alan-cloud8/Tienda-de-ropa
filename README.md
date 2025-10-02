<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Asistente Académico Integral</title>
    <style>
        :root {
            --primary: #3498db;
            --secondary: #2ecc71;
            --accent: #e74c3c;
            --dark: #2c3e50;
            --light: #ecf0f1;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
        }
        
        header {
            background: linear-gradient(135deg, var(--primary), var(--dark));
            color: white;
            padding: 1.5rem;
            text-align: center;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        h1 {
            font-size: 2.2rem;
            margin-bottom: 0.5rem;
        }
        
        .subtitle {
            font-size: 1.1rem;
            opacity: 0.9;
        }
        
        .container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 1.5rem;
        }
        
        .subject-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }
        
        .subject-card {
            background: white;
            border-radius: 10px;
            padding: 1.5rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s, box-shadow 0.3s;
            cursor: pointer;
        }
        
        .subject-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
        }
        
        .subject-card.math {
            border-top: 5px solid var(--primary);
        }
        
        .subject-card.science {
            border-top: 5px solid var(--secondary);
        }
        
        .subject-card.language {
            border-top: 5px solid var(--accent);
        }
        
        .subject-card.social {
            border-top: 5px solid #f39c12;
        }
        
        .subject-card h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: var(--dark);
        }
        
        .subject-card p {
            margin-bottom: 1rem;
            color: #555;
        }
        
        .tools {
            background: white;
            border-radius: 10px;
            padding: 1.5rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
            margin-bottom: 2rem;
        }
        
        .tools h2 {
            color: var(--dark);
            margin-bottom: 1rem;
            border-bottom: 2px solid var(--light);
            padding-bottom: 0.5rem;
        }
        
        .tool-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1rem;
        }
        
        .tool-item {
            background: var(--light);
            padding: 1rem;
            border-radius: 8px;
            text-align: center;
            cursor: pointer;
            transition: background 0.3s;
        }
        
        .tool-item:hover {
            background: #dfe6e9;
        }
        
        .calculator {
            background: white;
            border-radius: 10px;
            padding: 1.5rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
            margin-bottom: 2rem;
        }
        
        .calculator h2 {
            color: var(--dark);
            margin-bottom: 1rem;
            border-bottom: 2px solid var(--light);
            padding-bottom: 0.5rem;
        }
        
        .calc-display {
            width: 100%;
            height: 60px;
            font-size: 1.5rem;
            padding: 0.5rem 1rem;
            margin-bottom: 1rem;
            border: 1px solid #ddd;
            border-radius: 5px;
            text-align: right;
            background: #f9f9f9;
        }
        
        .calc-buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 0.5rem;
        }
        
        .calc-btn {
            padding: 1rem;
            font-size: 1.2rem;
            border: none;
            border-radius: 5px;
            background: var(--light);
            cursor: pointer;
            transition: background 0.3s;
        }
        
        .calc-btn:hover {
            background: #d1d8e0;
        }
        
        .calc-btn.operator {
            background: var(--primary);
            color: white;
        }
        
        .calc-btn.operator:hover {
            background: #2980b9;
        }
        
        .calc-btn.equals {
            background: var(--secondary);
            color: white;
        }
        
        .calc-btn.equals:hover {
            background: #27ae60;
        }
        
        .resources {
            background: white;
            border-radius: 10px;
            padding: 1.5rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
        }
        
        .resources h2 {
            color: var(--dark);
            margin-bottom: 1rem;
            border-bottom: 2px solid var(--light);
            padding-bottom: 0.5rem;
        }
        
        .resource-list {
            list-style-type: none;
        }
        
        .resource-list li {
            padding: 0.8rem 0;
            border-bottom: 1px solid #eee;
        }
        
        .resource-list li:last-child {
            border-bottom: none;
        }
        
        .resource-list a {
            color: var(--primary);
            text-decoration: none;
            transition: color 0.3s;
        }
        
        .resource-list a:hover {
            color: var(--dark);
            text-decoration: underline;
        }
        
        footer {
            background: var(--dark);
            color: white;
            text-align: center;
            padding: 1.5rem;
            margin-top: 2rem;
        }
        
        @media (max-width: 768px) {
            .subject-grid {
                grid-template-columns: 1fr;
            }
            
            .tool-grid {
                grid-template-columns: 1fr 1fr;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>Asistente Académico Integral</h1>
        <p class="subtitle">Enfocado en matemáticas pero con recursos para todas las materias básicas</p>
    </header>
    
    <div class="container">
        <div class="subject-grid">
            <div class="subject-card math">
                <h3>Matemáticas</h3>
                <p>Álgebra, geometría, cálculo, estadística y más. Encuentra explicaciones, ejercicios y herramientas para resolver problemas matemáticos.</p>
                <button class="tool-item" onclick="openMathTools()">Herramientas Matemáticas</button>
            </div>
            
            <div class="subject-card science">
                <h3>Ciencias</h3>
                <p>Física, química, biología y ciencias de la tierra. Aprende conceptos fundamentales y resuelve problemas científicos.</p>
                <button class="tool-item" onclick="openScienceTools()">Herramientas de Ciencias</button>
            </div>
            
            <div class="subject-card language">
                <h3>Lenguaje</h3>
                <p>Gramática, literatura, redacción y comprensión lectora. Mejora tus habilidades de comunicación escrita y oral.</p>
                <button class="tool-item" onclick="openLanguageTools()">Herramientas de Lenguaje</button>
            </div>
            
            <div class="subject-card social">
                <h3>Ciencias Sociales</h3>
                <p>Historia, geografía, economía y civismo. Comprende la sociedad y su desarrollo a través del tiempo.</p>
                <button class="tool-item" onclick="openSocialTools()">Herramientas Sociales</button>
            </div>
        </div>
        
        <div class="tools">
            <h2>Herramientas de Estudio</h2>
            <div class="tool-grid">
                <div class="tool-item" onclick="openCalculator()">Calculadora Científica</div>
                <div class="tool-item" onclick="openFormulaSheet()">Fórmulas Matemáticas</div>
                <div class="tool-item" onclick="openPeriodicTable()">Tabla Periódica</div>
                <div class="tool-item" onclick="openGrammarGuide()">Guía de Gramática</div>
                <div class="tool-item" onclick="openHistoryTimeline()">Línea de Tiempo Histórica</div>
                <div class="tool-item" onclick="openPracticeTests()">Exámenes de Práctica</div>
            </div>
        </div>
        
        <div class="calculator">
            <h2>Calculadora Básica</h2>
            <input type="text" class="calc-display" id="display" readonly>
            <div class="calc-buttons">
                <button class="calc-btn" onclick="clearDisplay()">C</button>
                <button class="calc-btn" onclick="deleteLast()">⌫</button>
                <button class="calc-btn operator" onclick="appendToDisplay('/')">/</button>
                <button class="calc-btn operator" onclick="appendToDisplay('*')">×</button>
                
                <button class="calc-btn" onclick="appendToDisplay('7')">7</button>
                <button class="calc-btn" onclick="appendToDisplay('8')">8</button>
                <button class="calc-btn" onclick="appendToDisplay('9')">9</button>
                <button class="calc-btn operator" onclick="appendToDisplay('-')">-</button>
                
                <button class="calc-btn" onclick="appendToDisplay('4')">4</button>
                <button class="calc-btn" onclick="appendToDisplay('5')">5</button>
                <button class="calc-btn" onclick="appendToDisplay('6')">6</button>
                <button class="calc-btn operator" onclick="appendToDisplay('+')">+</button>
                
                <button class="calc-btn" onclick="appendToDisplay('1')">1</button>
                <button class="calc-btn" onclick="appendToDisplay('2')">2</button>
                <button class="calc-btn" onclick="appendToDisplay('3')">3</button>
                <button class="calc-btn equals" onclick="calculate()" rowspan="2">=</button>
                
                <button class="calc-btn" onclick="appendToDisplay('0')" style="grid-column: span 2;">0</button>
                <button class="calc-btn" onclick="appendToDisplay('.')">.</button>
            </div>
        </div>
        
        <div class="resources">
            <h2>Recursos Adicionales</h2>
            <ul class="resource-list">
                <li><a href="#" onclick="openAlgebraGuide()">Guía Completa de Álgebra</a></li>
                <li><a href="#" onclick="openGeometryGuide()">Fórmulas de Geometría</a></li>
                <li><a href="#" onclick="openPhysicsFormulas()">Fórmulas de Física</a></li>
                <li><a href="#" onclick="openChemistryGuide()">Guía de Química</a></li>
                <li><a href="#" onclick="openLiteratureGuide()">Resúmenes de Literatura</a></li>
                <li><a href="#" onclick="openHistoryGuide()">Linea de Tiempo Histórica</a></li>
                <li><a href="#" onclick="openStudyTips()">Técnicas de Estudio Efectivas</a></li>
            </ul>
        </div>
    </div>
    
    <footer>
        <p>Asistente Académico Integral &copy; 2023 - Herramientas para el éxito estudiantil</p>
    </footer>

    <script>
        // Funciones para la calculadora
        let display = document.getElementById('display');
        
        function appendToDisplay(value) {
            display.value += value;
        }
        
        function clearDisplay() {
            display.value = '';
        }
        
        function deleteLast() {
            display.value = display.value.slice(0, -1);
        }
        
        function calculate() {
            try {
                display.value = eval(display.value);
            } catch (error) {
                display.value = 'Error';
            }
        }
        
        // Funciones para abrir diferentes herramientas (simuladas)
        function openMathTools() {
            alert('Abriendo herramientas matemáticas: Calculadora avanzada, graficador, solucionador de ecuaciones...');
        }
        
        function openScienceTools() {
            alert('Abriendo herramientas de ciencias: Simulaciones, laboratorio virtual, tabla periódica interactiva...');
        }
        
        function openLanguageTools() {
            alert('Abriendo herramientas de lenguaje: Corrector gramatical, diccionario, generador de ensayos...');
        }
        
        function openSocialTools() {
            alert('Abriendo herramientas de ciencias sociales: Mapas interactivos, línea de tiempo, análisis de documentos...');
        }
        
        function openCalculator() {
            alert('Calculadora científica abierta con funciones trigonométricas, logarítmicas y estadísticas.');
        }
        
        function openFormulaSheet() {
            alert('Mostrando hoja de fórmulas matemáticas: álgebra, geometría, cálculo, estadística...');
        }
        
        function openPeriodicTable() {
            alert('Mostrando tabla periódica interactiva con información detallada de cada elemento.');
        }
        
        function openGrammarGuide() {
            alert('Abriendo guía completa de gramática y ortografía con ejemplos y ejercicios.');
        }
        
        function openHistoryTimeline() {
            alert('Mostrando línea de tiempo histórica interactiva con eventos importantes.');
        }
        
        function openPracticeTests() {
            alert('Generando exámenes de práctica personalizados según tu nivel y materias.');
        }
        
        // Funciones para recursos adicionales
        function openAlgebraGuide() {
            alert('Descargando guía completa de álgebra con explicaciones y ejercicios resueltos.');
        }
        
        function openGeometryGuide() {
            alert('Mostrando fórmulas de geometría con diagramas interactivos.');
        }
        
        function openPhysicsFormulas() {
            alert('Abriendo compendio de fórmulas de física organizadas por temas.');
        }
        
        function openChemistryGuide() {
            alert('Accediendo a guía de química con conceptos, reacciones y laboratorio virtual.');
        }
        
        function openLiteratureGuide() {
            alert('Mostrando resúmenes y análisis de obras literarias importantes.');
        }
        
        function openHistoryGuide() {
            alert('Abriendo línea de tiempo histórica con eventos y figuras importantes.');
        }
        
        function openStudyTips() {
            alert('Mostrando técnicas de estudio efectivas y consejos para mejorar el rendimiento académico.');
        }
    </script>
</body>
</html>
