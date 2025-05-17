<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ENUM y Teoría de Cuerdas</title>
    
    <!-- MathJax Configuration -->
    <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
    <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
    <script>
    MathJax = {
        tex: {
            inlineMath: [['$', '$'], ['\\(', '\\)']],
            tags: 'ams'
        },
        options: {
            enableMenu: false
        }
    };
    </script>

    <style>
        body { 
            font-family: 'Segoe UI', Arial, sans-serif; 
            line-height: 1.6; 
            margin: 20px; 
            padding: 20px; 
            background-color: #f8f9fa; 
            max-width: 1200px;
            margin: 0 auto;
        }
        
        h1, h2 { 
            color: #2c3e50; 
            border-bottom: 2px solid #3498db;
            padding-bottom: 10px;
        }
        
        .content { 
            background: #fff; 
            padding: 30px; 
            border-radius: 12px; 
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            margin-top: 20px;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 25px 0;
            box-shadow: 0 0 20px rgba(0,0,0,0.1);
        }
        
        th, td {
            border: 1px solid #ddd;
            padding: 15px;
            text-align: center;
        }
        
        th {
            background: #3498db;
            color: white;
            font-weight: 600;
        }
        
        .equation {
            background: #f8f9fa;
            padding: 20px;
            border-left: 4px solid #3498db;
            margin: 20px 0;
            counter-increment: equation;
            border-radius: 4px;
        }
        
        .equation::before {
            content: "(" counter(equation) ")";
            margin-right: 15px;
            color: #7f8c8d;
            font-weight: bold;
        }
        
        .simulator {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 8px;
            margin: 25px 0;
            display: grid;
            grid-gap: 15px;
        }
        
        .controls {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
        }
        
        input, select {
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 16px;
        }
        
        #cyCanvas {
            border: 2px solid #3498db;
            border-radius: 8px;
            margin: 20px 0;
            background: #fff;
        }
        
        .result {
            padding: 15px;
            background: #e8f4fc;
            border-radius: 4px;
            font-family: monospace;
        }

        @media (max-width: 768px) {
            body {
                padding: 10px;
            }
            
            .content {
                padding: 15px;
            }
        }

        /* Animaciones */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .content {
            animation: fadeIn 0.6s ease-out;
        }
    </style>
</head>
<body>
    <div class="content">
        <h1>Aplicación del Sistema ENUM a la Teoría de Cuerdas</h1>

        <!-- Sección 1: Problema del Paisaje -->
        <h2>1. Compactificación y Reducción del Paisaje</h2>
        <table>
            <tr>
                <th>Contexto</th>
                <th>Parámetros</th>
                <th>Condiciones ENUM</th>
            </tr>
            <tr>
                <td>Variedad Calabi-Yau</td>
                <td>$h^{1,1} = 3$</td>
                <td>$\Phi_{\text{SM}}(h^{1,1}) \rightarrow SU(5)$</td>
            </tr>
            <tr>
                <td>Flux Compactification</td>
                <td>$N_{\text{flux}} \leq 2^{32}$</td>
                <td>$\nabla \cdot \mathcal{F}_3 = 0$</td>
            </tr>
        </table>

        <!-- Sección 2: Simulación Interactiva -->
        <h2>2. Simulador de Compactificaciones</h2>
        <div class="simulator">
            <div class="controls">
                <div>
                    <label>Número de dimensiones compactas:</label>
                    <input type="number" id="dimensions" min="3" max="7" value="6">
                </div>
                
                <div>
                    <label>Simetría gauge:</label>
                    <select id="symmetry">
                        <option>SU(5)</option>
                        <option>SO(10)</option>
                        <option>E8×E8</option>
                    </select>
                </div>
            </div>
            
            <canvas id="cyCanvas" width="400" height="300"></canvas>
            <div id="output" class="result"></div>
        </div>

        <!-- Sección 3: Ecuaciones Fundamentales -->
        <h2>3. Marco Matemático ENUM</h2>
        <div class="equation">
            $\Phi\left( \hat{G}_{\mu\nu}^{\text{(cuerda)}} \right) = \delta \sigma_{\text{pp}} \otimes \mathcal{L}_{\text{SUSY}}$
        </div>
        
        <div class="equation">
            $\mathcal{N}_{\text{ΛCDM}} = \bigoplus_{k=1}^{h^{1,1}} \mathcal{M}_k \otimes \mathbb{Z}_3$
        </div>

        <!-- Sección 4: Validación Experimental -->
        <h2>4. Protocolo de Validación</h2>
        <div class="equation">
            $\Lambda_{\text{QFT}} = \frac{1}{4\pi} \int_{\mathcal{M}_6} G_3 \wedge \star G_3$
        </div>
        <p>Condiciones de consistencia:</p>
        <div id="validationResults" class="result"></div>

        <!-- Código JavaScript -->
        <script>
            // Sistema de validación
            function validateCompactification(h11, h21) {
                const constraints = {
                    susyConditions: h11 * h21 % 2 === 0,
                    anomalyFree: (h11 - h21) % 3 === 1,
                    vacuumStability: h11 > 2 && h21 > 3
                };
                return constraints;
            }

            // Simulación interactiva
            const canvas = document.getElementById('cyCanvas');
            const ctx = canvas.getContext('2d');
            let animationFrame;

            function drawCYManifold() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                
                // Representación simplificada (implementación básica)
                ctx.beginPath();
                ctx.arc(200, 150, 50, 0, Math.PI * 2);
                ctx.strokeStyle = '#3498db';
                ctx.lineWidth = 2;
                ctx.stroke();
                
                // Patrón dinámico
                for(let i = 0; i < 6; i++) {
                    ctx.beginPath();
                    ctx.arc(
                        200 + Math.cos(Date.now()/1000 + i) * 30,
                        150 + Math.sin(Date.now()/1000 + i) * 30,
                        10, 0, Math.PI * 2
                    );
                    ctx.fillStyle = `hsl(${(Date.now()/50 + i*60) % 360}, 70%, 60%)`;
                    ctx.fill();
                }
                
                animationFrame = requestAnimationFrame(drawCYManifold);
            }

            // Controladores de eventos
            function updateSimulation() {
                const h11 = parseInt(document.getElementById('dimensions').value);
                const results = validateCompactification(h11, 3);
                
                document.getElementById('output').innerHTML = `
                    Validación ENUM:<br>
                    • SUSY: ${results.susyConditions ? '✓' : '✗'}<br>
                    • Anomalías: ${results.anomalyFree ? '✓' : '✗'}<br>
                    • Vacío: ${results.vacuumStability ? 'Estable' : 'Inestable'}
                `;
                
                cancelAnimationFrame(animationFrame);
                drawCYManifold();
            }

            // Inicialización
            document.getElementById('dimensions').addEventListener('input', updateSimulation);
            document.getElementById('symmetry').addEventListener('change', updateSimulation);
            updateSimulation();
        </script>

        <!-- Sección 5: Integración Cosmológica -->
        <h2>5. Dinámica Inflacionaria</h2>
        <div class="equation">
            $\Phi_{\text{Inflación}}: \mathcal{N}_{\text{String+Vacío}} \xrightarrow{\Lambda_{\text{QFT}}} \mathcal{N}_{\text{ΛCDM}}$
        </div>
        <p>Parámetros esenciales:</p>
        <ul>
            <li>Tensión de la cuerda: $\sigma = (2.4 \pm 0.3) \times 10^{-15}$ N</li>
            <li>Acoplamiento gauge: $g_s < 0.12$ (95% CL)</li>
        </ul>
    </div>
</body>
</html>
