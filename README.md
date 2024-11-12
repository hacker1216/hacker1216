<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Teoría de Conjuntos</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        input, button {
            margin: 5px;
        }
    </style>
</head>
<body>
    <h1>Operaciones en Teoría de Conjuntos</h1>

    <h2>Conjunto A</h2>
    <input type="text" id="setA" placeholder="Ej: 1,2,3" />
    
    <h2>Conjunto B</h2>
    <input type="text" id="setB" placeholder="Ej: 2,3,4" />
    
    <button onclick="performOperations()">Realizar Operaciones</button>

    <h2>Resultados</h2>
    <p id="union"></p>
    <p id="interseccion"></p>
    <p id="diferenciaAB"></p>
    <p id="diferenciaBA"></p>

    <script>
        function parseSet(input) {
            return input.split(',').map(Number).filter(n => !isNaN(n));
        }

        function union(setA, setB) {
            return [...new Set([...setA, ...setB])];
        }

        function interseccion(setA, setB) {
            return setA.filter(value => setB.includes(value));
        }

        function diferencia(setA, setB) {
            return setA.filter(value => !setB.includes(value));
        }

        function performOperations() {
            const setA = parseSet(document.getElementById('setA').value);
            const setB = parseSet(document.getElementById('setB').value);

            const resultUnion = union(setA, setB);
            const resultInterseccion = interseccion(setA, setB);
            const resultDiferenciaAB = diferencia(setA, setB);
            const resultDiferenciaBA = diferencia(setB, setA);

            document.getElementById('union').innerText = `Unión (A ∪ B): ${resultUnion.join(', ')}`;
            document.getElementById('interseccion').innerText = `Intersección (A ∩ B): ${resultInterseccion.join(', ')}`;
            document.getElementById('diferenciaAB').innerText = `Diferencia (A - B): ${resultDiferenciaAB.join(', ')}`;
            document.getElementById('diferenciaBA').innerText = `Diferencia (B - A): ${resultDiferenciaBA.join(', ')}`;
        }
    </script>
</body>
</html>
