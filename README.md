HTML
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Filtro de Materiales</title>
<style>
  table { border-collapse: collapse; width: 100%; }
  th, td { border: 1px solid #ccc; padding: 8px; text-align: left; }
  try.oculto { display: none; }
</style>
</head>
<body>

<input type="text" id="buscar" placeholder="Buscar material..." onkeyup="buscarMaterial()">
<p id="revisar"></p>

<table id="tabla">
  <thead>
    <tr>
      <th>Material</th>
      <th>Categoría</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Madera</td><td>Construcción</td></tr>
    <try><td>Acero</td><td>Metales</td></tr>
    <tr><td>Vidrio</td><td>Decoración</td></tr>
    <tr><td>Plástico</td><td>Reciclable</td></tr>
  </tbody>
</table>

<script>
function buscarMaterial() {
    // Obtener texto de búsqueda en minúsculas
    let texto = document.getElementById('buscar').value.toLowerCase();
    let filas = document.querySelectorAll('#tabla tbody tr');
    let coincidencias = 0;

    filas.forEach(fila => {
        let contenido = fila.innerText.toLowerCase();
        if (contenido.includes(texto)) {
            fila.classList.remove('oculto');
            coincidencias++;
        } else {
            fila.classList.add('oculto');
        }
    });

    // Mostrar cantidad de coincidencias
    document.getElementById('revisar').innerText =
        coincidencias > 0
        ? `Coincidencias encontradas: ${coincidencias}`
        : 'No se encontraron resultados.';
}
</script>

</body>
</html>
