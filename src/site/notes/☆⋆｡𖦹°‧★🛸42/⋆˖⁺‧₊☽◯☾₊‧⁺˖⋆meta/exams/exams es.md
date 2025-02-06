---
{"dg-publish":true,"permalink":"/☆⋆｡𖦹°‧★🛸42/⋆˖⁺‧₊☽◯☾₊‧⁺˖⋆meta/exams/exams es/","tags":["42madrid"]}
---

❗❗❗No puedes hacer nada hasta que no sean en punto y tienes que conseguir llegar a la *examshell* antes de las 16:10❗❗❗
Y ten en cuenta que cualquier cosa que te cuente yo aquí podría variar o que yo no lo recuerde correctamente


# cómo empezar el examen y que no te echen
0. No hacer nada en el ordenador hasta que sea en punto
1. hacer login con las credenciales
	- usuario: exam
	- contraseña: exam
2. Antes de nada quítale el sonido a tu ordenador. mediante teclado o en el icono de sonido arriba a la derecha. Podrían echarte si hace algún ruido
3. Arriba a la derecha le das a Ajustes/Settings y cambia tu teclado para asegurarte de que está en español. Si no, cuando tengas que poner la contraseña de tu usuario puede que tengas problemas.
	1. Abres settings
	2. En la barra lateral de la izquierda busca "Teclado" o "Keyboard" y haz click
	3. Arriba del todo te aparecerá un apartado "Input Sources" donde seguramente solo aparece "English (US)" o algo parecido.
	4. Dale al "+" y añade "Spanish", si hay varias versiones yo suelo elegir "Spanish (Windows)" ni idea de por qué xd
	5. ya puedes cerrar y continuar
4. abre una terminal. Mejor si sabes hacerlo con teclado. En "Spanish (Windows)" suele ser "Ctrl + ⌥ + T". Intenta averiguar si esto te funciona o alternativas antes del examen
5. empieza a navegar en la terminal para ver que carpetas contienen las instrucciones que tienen que seguir

⚠ ❗❗❗ No sabemos si esto va a cambiar de un examen a otro, pero yo cuento lo que me tocó a mí, presta atención a posibles cambios que pueden haber ⚠ ❗❗❗

- 📁`~/docs/` — instrucciones del examen. hay 2 tipos de archivos, cada uno con varias versiones para diferentes idiomas (ES, ENG, PR, KR...)
	- 📄`README.md` resumen de las instrucciones (versión corta)
	- 📄 (no me acuerdo de cómo se llama) con instrucciones súper detalladas de cómo llegar a la "**examshell**" y hacer el examen
- 📁`~/rendu/` — la carpeta/directorio que se autogenera al entrar a la *examshell* y es un repo donde vas a ir subiendo tus ejercicios usando git
- 📁`~/subjects/` — la carpeta/directorio a la que el programa de la *examshell* va autogenerando los enunciados de los ejercicios que tienes que hacer

De acuerdo a las instrucciones, tienes que abrir una terminal y ejecutar:
```bash
$ anuro
```
Este comando inicia un programa por terminal que será el examen.
Te va a pedir un login y tienes que poner tu usuario y contraseña de la intra. Por eso es muy importante que pongas tu teclado a "Spanish" o lo que prefieras para no liarla con la contraseña.

Acuérdate de seguir las instrucciones y conseguir una terminal que muestre la examshell ❗❗ANTES DE LOS PRIMEROS 10 MIN DEL EXAMEN❗❗ (era algo de este aspecto:)

```
>>examshell>
```
 
👀 no confíes en lo que te cuento aquí, intenta leerte los documentos dentro de  `~/docs` o una carpeta parecida si la deciden llamar de otra manera, para entender el proceso de examen y cómo funciona  `anuro`.
Incluso te dice qué hacer si algo parece fallar, cuándo contactar al staff, preguntas frecuentes...etc.

# puntaje y ejercicios

El examen tiene 10 niveles(1 ej/nivel) y la puntuación será entre 0 y 100.
- Cada nivel son X puntos (para mi los 4 niveles que hice fueron 10pts cada uno) 
- No tienes acceso a todos los ejercicios a la vez, cada vez que pasas de nivel se autogenera un nuevo ejercicio, en `~/subjects`
	- no sé si soy la única persona que lo notó o si lo soñé, pero juro que después de un tiempo, los archivos de enunciado en `~/subjects` desaparecían de la carpeta. Yo recomiendo abrirte una terminal aparte donde vas haciendo `cat` de cada enunciado y no cerrarla
- No todos tendremos los mismos ejercicios. Para un mismo nivel habrá variaciones para que no te toque lo mismo que a quien se siente a tu lado
- Recuerda ir haciendo commits y push frecuentemente, a algunos les pasó que cuando nos cambiaron de clúster, perdieron el progreso por no haber hecho commit y push
- En las instrucciones lo cuenta con más detalle, pero no pasa nada si no pasas un nivel. Te toca repetir el ejercicio hasta que lo pases. Sin embargo, al igual los proyectos, cada vez tienes que esperar más a hacer el reintento
- Léete bien las instrucciones. En el examen 00 teníamos que compilar con `clang` en vez de `cc`



