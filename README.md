# Mi Ruta Vocacional

Test vocacional CHASIDE adaptado al Perú, en una sola página web. Los estudiantes responden 98 preguntas de sí o no. Al final ven sus áreas más fuertes y carreras universitarias y técnicas del país, con enlaces a fuentes oficiales.

- Funciona en celulares y computadoras. Abre en modo claro y tiene un botón de sol y luna en la cabecera para cambiar a modo oscuro; la elección queda guardada en el dispositivo.
- No necesita servidor, base de datos ni registro.
- Todo está en un solo archivo, `index.html` (unos 170 KB, con las dos tipografías incluidas).

## Qué incluye

- **Datos obligatorios:** antes de empezar, el estudiante registra apellidos, nombres, grado, sección y fecha de aplicación. Si falta o está mal un dato, la página lo señala y no deja empezar. La fecha viene con el día actual y no acepta fechas futuras.
- **Test:** una pregunta por pantalla, con botones Sí y No del mismo aspecto para no inclinar las respuestas. Se puede volver atrás, y el avance se muestra en 7 etapas con un mensaje de ánimo entre cada una.
- **Guardado local:** el avance se guarda en el navegador, así que si el estudiante cierra la página puede continuar después.
- **Resultado:**
  - las dos áreas principales;
  - el puntaje en las 7 áreas, separando intereses y aptitudes;
  - avisos cuando los intereses y las aptitudes no coinciden, o cuando las respuestas no orientan (casi todo sí, casi todo no o un perfil plano);
  - carreras por área, filtradas en profesionales y técnicas;
  - carreras que combinan las dos áreas más altas;
  - siguientes pasos con enlaces oficiales.
- **Salida:** una ficha con los datos del estudiante para imprimir o guardar en PDF, y un resumen para copiar o compartir.
- **Insignias:** al cerrar cada una de las 7 etapas, el estudiante gana una figura de color; al terminar, las siete forman su tejido completo.
- **Accesibilidad:** navegación con teclado (S = sí, N = no, flecha izquierda = volver), lectores de pantalla y movimiento reducido.

## Publicarlo en GitHub Pages

1. Crea un repositorio y sube `index.html` y `README.md` a la raíz. En el plan gratuito de GitHub, Pages requiere que el repositorio sea público.
2. Entra a **Settings → Pages** y, en **Build and deployment**, elige **Deploy from a branch**.
3. Selecciona la rama `main` y la carpeta `/ (root)`, y guarda.
4. En unos minutos la página estará en `https://TU-USUARIO.github.io/NOMBRE-DEL-REPOSITORIO/`.

## Cómo editar el contenido

Todo el contenido editable está al inicio del `<script>` de `index.html`, en secciones numeradas:

| Sección | Qué contiene |
|---|---|
| 1. `CONFIG` | Título, autor, institución y fecha de actualización. El autor y la institución aparecen en el pie de página si los completas. |
| 2. `GRADOS` y `AREAS` | Grados de secundaria y, para cada área, su nombre, descripción, fortalezas y figura (tocapu). |
| 3. `CLAVE` | Clave de corrección CHASIDE. No la cambies sin revisar las preguntas. |
| 4. `PREGUNTAS` | Las 98 preguntas, en orden. |
| 5. `ENLACES` y `TIPOS` | Enlaces oficiales y tipos de formación (universidad, instituto, escuela de oficiales, etc.). |
| 6. `CARRERAS` | Carreras por área. |
| 7. `PUENTES` | Carreras que combinan dos áreas. |
| 8. `MENSAJES_ETAPA` | Mensajes entre etapas. |

Al cargar, la página verifica que la clave cubra las 98 preguntas sin repetir. Si algo falla, lo avisa en la consola del navegador (F12).

## Metodología

**Estructura.** Se mantiene la del CHASIDE: 98 preguntas y 7 áreas, cada una con 10 preguntas de intereses y 4 de aptitudes.

| Área | Intereses | Aptitudes |
|---|---|---|
| C: Administración y Negocios | 1, 12, 20, 53, 64, 71, 78, 85, 91, 98 | 2, 15, 46, 51 |
| H: Humanidades, Ciencias Sociales y Derecho | 9, 25, 34, 41, 56, 67, 74, 80, 89, 95 | 30, 63, 72, 86 |
| A: Arte, Diseño y Arquitectura | 3, 11, 21, 28, 36, 45, 50, 57, 81, 96 | 22, 39, 76, 82 |
| S: Ciencias de la Salud | 8, 16, 23, 33, 44, 52, 62, 70, 87, 92 | 4, 29, 40, 69 |
| I: Ingeniería y Tecnología | 6, 19, 27, 38, 47, 54, 60, 75, 83, 97 | 10, 26, 59, 90 |
| D: Defensa y Seguridad | 5, 14, 24, 31, 37, 48, 58, 65, 73, 84 | 13, 18, 43, 66 |
| E: Ciencias Naturales y Exactas | 17, 32, 35, 42, 49, 61, 68, 77, 88, 93 | 7, 55, 79, 94 |

**Adaptación.** El lenguaje se pasó al español del Perú y se corrigieron errores de redacción. Se reescribieron 14 preguntas que medían otra cosa:

- **Opiniones con las que casi todos están de acuerdo:** 30, 58, 63, 67 y 69.
- **Posturas políticas:** 31, 66 y 73.
- **Timidez o preferencia por el trabajo individual:** 79 y 94.
- **Conocimientos en vez de intereses:** 88 y 98.
- **Pregunta doble:** 59.
- **Situación ajena a escolares (despedida de soltero):** 2.

Cada una sigue sumando a su misma área.

**Cálculo del resultado.**

1. Cada «sí» suma un punto en su área. El total por área va de 0 a 14 y se muestra en porcentaje.
2. Las áreas se ordenan por total. Si hay empate, gana la que tiene más puntos de intereses.
3. Se compara el área con más intereses con el área con más aptitudes y se informa si coinciden.
4. Se muestran avisos en estos casos:
   - 80 o más respuestas «sí»;
   - 15 o menos;
   - menos de 6, en cuyo caso no se señalan áreas principales;
   - diferencia de 2 puntos o menos entre el área más alta y la más baja.

**Límites.** No hay baremos peruanos, y las «aptitudes» son autopercepción, no una medición de capacidades. Por eso conviene:

- presentarlo como orientación y no como diagnóstico;
- probarlo con un aula antes de usarlo a gran escala;
- revisar los resultados con el psicólogo o tutor del colegio.

## Privacidad

- La página no envía datos ni respuestas a ningún servidor. Los datos del estudiante (apellidos, nombres, grado, sección y fecha) y sus respuestas quedan en el `localStorage` del navegador del dispositivo.
- El estudiante puede borrarlos con los botones «Borrar y empezar de nuevo» o «Borrar mis datos de este dispositivo». En computadoras compartidas, conviene borrarlos al terminar.
- La tipografía va incrustada en el archivo, así que la página no se conecta a Google Fonts ni a otros servicios externos.
- GitHub Pages, como cualquier servidor web, puede registrar datos técnicos de las visitas (por ejemplo, la dirección IP) según la política de privacidad de GitHub.
- Si más adelante se agrega un panel para docentes que almacene resultados de estudiantes, habrá que cumplir la Ley N.° 29733 y su reglamento (D.S. N.° 016-2024-JUS). Eso incluye el consentimiento que corresponda para datos de menores de edad.

## Mantenimiento

- Revisa una vez al año los enlaces y la lista de carreras. Las convocatorias de las escuelas militares y policiales cambian cada año.
- Algunas escuelas no tienen enlace porque no se pudo verificar una dirección oficial estable. Para ellas, la página indica que se consulte la convocatoria en los canales oficiales:
  - Escuela de Oficiales y Escuela de Suboficiales de la FAP;
  - Escuela Técnica del Ejército;
  - Centro de Instrucción Técnica y Entrenamiento Naval.

## Fuentes

- Mi Carrera (MTPE): https://micarrera.trabajo.gob.pe/
- Ponte en Carrera (Minedu, MTPE e IPAE): https://ponteencarrera.minedu.gob.pe/
- Sunedu, universidades licenciadas: https://www.gob.pe/institucion/sunedu/pages/11262-consultar-si-una-universidad-esta-licenciada-por-la-sunedu
- Sunedu, carreras en universidades licenciadas: https://www.gob.pe/14408-consultar-listado-de-carreras-en-universidades-licenciadas-por-sunedu
- Minedu, Catálogo Nacional de la Oferta Formativa: https://www.gob.pe/57095-consultar-programas-de-estudios-del-catalogo-nacional-de-la-oferta-formativa-cnof
- Minedu, escuelas pedagógicas licenciadas: https://www.minedu.gob.pe/superiorpedagogica/escuelas-licenciadas/
- Pronabec, Beca 18: https://www.pronabec.gob.pe/beca-18/
- PNP, Dirección de Educación y Doctrina: https://direddoc.pnp.edu.pe/
- Escuela Naval del Perú: https://www.escuelanaval.edu.pe/
- Escuela Militar de Chorrillos: https://www.escuelamilitar.edu.pe/
- Adaptación del CHASIDE en Ecuador: https://dialnet.unirioja.es/descarga/articulo/8297957.pdf
- Propiedades psicométricas del CHASIDE en Honduras: https://www.mlsjournals.com/Psychology-Research-Journal/article/view/4247

## Licencia y créditos

- **Código:** elige una licencia antes de publicar (por ejemplo, MIT).
- **Tipografías:** Lexend (texto) y Outfit (títulos), bajo la SIL Open Font License 1.1. El aviso de licencia va dentro de cada archivo de fuente incrustado.
- **Colores:** violeta #5B3DF5 como color principal, con turquesa y naranja de acento, y siete colores de área. Se editan en el bloque `:root` del `<style>`, en la sección «Rediseño (v3)».
- **CHASIDE:** es un cuestionario de amplia difusión en Iberoamérica. Esta versión es una adaptación para uso educativo.
