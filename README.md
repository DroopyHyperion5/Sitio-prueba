# Sitio-prueba<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8" />
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.1/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-F3w7mX95PdgyTmZZMECAngseQB83DfGTowi0iMjiWaeVhAn4FJkqJByhZMI3AhiU" crossorigin="anonymous" />
</head>

<body>
    <div id="tablero"></div>
    <div id="mensajes"></div>
    <script>
        var turno = 0;
        for (var i = 0; i < 25; i++) {
            document.getElementById("tablero").innerHTML +=
                '<button id="b' + i + '" onclick="MarcaLaCasilla(event)" type="button" class="btn btn-success btn-lg">🐱‍👤</button>';

            if ((i + 1) % 5 === 0) {
                document.getElementById("tablero").innerHTML += '<br>';
            }
        }

        //HORIZONTAL
        function MarcaLaCasilla(e) {//FUNCION DE VICTORIA

            var nombre = e.target.id;
            if (turno === 0) {
                document.getElementById(nombre).innerHTML = "❌";
            }
            else {
                document.getElementById(nombre).innerHTML = "⭕";
            }
            document.getElementById(nombre).disabled = true;
            turno = (turno + 1) % 2;
            revisarGanador();
        }

        function revisarGanador() {
            for (var jugador = 0; jugador <= 1; jugador++) {
                var marca = "";
                if (jugador === 0) {
                    marca = "❌";
                }
                else { marca = "⭕" }
                for (var principio = 0; principio <= 20; principio += 5) {
                    var Linea = true;
                    for (var i = principio; i < 5 + principio; i = i += 1) {
                        var Ncasilla = "b" + i;
                        Linea &= document.getElementById(Ncasilla).innerHTML === marca;
                    }
                    if (Linea) {
                        document.getElementById("mensajes").innerHTML = "Ganador: " + marca;
                        terminarJuego();
                    }
                }
            }

            //VERTICAL

            for (var jugador = 0; jugador <= 1; jugador++) {
                var marca = "";
                if (jugador === 0) {
                    marca = "❌";
                }
                else { marca = "⭕"; }
                for (var principio = 0; principio <= 4; principio++) {
                    var Linea = true;
                    for (var i = principio; i <= 20 + principio; i = i + 5) {
                        var Ncasilla = "b" + i;
                        Linea &= document.getElementById(Ncasilla).innerHTML === marca;
                    }
                    if (Linea) {
                        document.getElementById("mensajes").innerHTML = "Ganador: " + marca;
                        terminarJuego();
                    }
                }
            }

            //DIAGONAL

            //❌
            if (document.getElementById("b0").innerHTML === "❌" &&
                document.getElementById("b6").innerHTML === "❌" &&
                document.getElementById("b12").innerHTML === "❌" &&
                document.getElementById("b18").innerHTML === "❌" &&
                document.getElementById("b24").innerHTML === "❌") {
                alert("Ganador: ❌ ");
            }

            if (document.getElementById("b4").innerHTML === "❌" &&
                document.getElementById("b8").innerHTML === "❌" &&
                document.getElementById("b12").innerHTML === "❌" &&
                document.getElementById("b16").innerHTML === "❌" &&
                document.getElementById("b20").innerHTML === "❌") {
                alert("Ganador: ❌ ");
            }

            //⭕
            if (document.getElementById("b0").innerHTML === "⭕" &&
                document.getElementById("b6").innerHTML === "⭕" &&
                document.getElementById("b12").innerHTML === "⭕" &&
                document.getElementById("b18").innerHTML === "⭕" &&
                document.getElementById("b24").innerHTML === "⭕") {
                alert("Ganador: ⭕ ");
            }

            if (document.getElementById("b4").innerHTML === "⭕" &&
                document.getElementById("b8").innerHTML === "⭕" &&
                document.getElementById("b12").innerHTML === "⭕" &&
                document.getElementById("b16").innerHTML === "⭕" &&
                document.getElementById("b20").innerHTML === "⭕") {
                alert("Ganador: ⭕ ");
            }

        }//FIN REVISION JUGADOR
    </script>
</body>

</html>
