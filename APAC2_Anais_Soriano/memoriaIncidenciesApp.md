# Memoria Aplicacion Incidencias

### Sobre el codigo de las actividades:

Primero que todo vamos al fichero build.gradle para activar buildFeatures, simplemente lo ponemos en true, esto nos servira para poder utilizar el binding.

Desde el MainActivity:

- Creamos la variable binding : ActivityMainBinding que hace referencia al layout "activity_main.xml" y la variable incidenciaToRemove

- En el metodo onCreate a partir del binding asociamos el fichero "activity_main.xml" ,el id IncidenciesRecyclerView que hace referencia a la lista de incidencias que deberian aparecer en la pantalla y el layoutManager que gestionara los eventos click y click largo que pueden efectuarse sobre alguna incidencia.

- El el metodo itemClicked creamos un nuevo Intent para abrir la actividad de edición proporcionandole la incidencia sobre la qual se ha hecho click.

- En el metodo itemLongClick cuando se hace un click largo sobre alguna incidencia se abre un dialogo preguntando si queremos borrarla.

- En el metodo onCreateOptionsMenu inicializamos el menu para crear una nueva incidencia y en onOptionsItemSelected quando se pulsa en NEW nos abre la actividad editaIncidenciaActivity con todas las opciones en blanco y al pulsar en el boton guardar se crea una nueva incidencia con los parametros introducidos.

- En el metodo onResume redibujamos el RecyclerView cuando la vista vuelve a primer plano.

- En el metodo onPositiveClick(), si pulsamos aceptar en el quadro de dialogo eliminamos el item y actualizamos el adaptador del recyclerView.

Desde EditaIncidenciaActivity:

- En el metodo onCreate() a partir del binding asociamos el layout "activity_edita_incidencia.xml", añadimos la información del Intent indicendia si existe(imagen, descripción, titulo de la incidencia,servicio,etc...) y por ultimo capturamos el click sobre el boton guardar.

- En el metodo guardaIncidencia() creamos una nueva incidencia a partir de la información de las vistas , y una vez creada guardamos la incidencia actual por esta, si la incidencia actual es nula añadiremos una nueva incidencia a la lista de incidencias.

Desde IncidenciaViewHolder:

- Enlazamos los datos de la incidencia con la vista y con su gestor de eventos. Capturamos los eventos y invocamos a su callback correspondiente

Desde AdaptadorIncidencies:

- El adaptador obtiene en su constructor los gestores de eventos eventListenerClick y eventListenerLongClick

- En el metodo OnCreateViewHolder() se invoca al layoutInflater y inflamos la vista con este inflate pasandole el layout "incidencia_layout_materialcardview.xml", y este metodo devuelve "IncidenciaViewHolder(vista)"

- En el metodo onBindViewHolder() le proporcionamos el parc y los eventos de click y click largo que recibimos.

- El metodo getItemCount() devuelve el numero de elementos que hay en el Dataset

Desde MyDialogFragment:

- Definimos la interficie que han de implementar las actividades que utilizen el fragmento.

- En onCreateDialog() definimos el titulo y la descripcion del dialogo de texto 

- En onSaveInstanceState() guardamos el estado de la aplicacion quando se efectue alguna accion sobre esta.


#### DRAWABLE:
Incidencia.png- Es la imagen que usamos para cada incidencia
incidenciesPortada.png- Es la imagen que usamos para la portada del diseño de la actividad Login 
#### LAYOUT:
- Activity_login.xml: Este diseño muestra el diseño de la actividad Login
- Activity_main.xml: Este diseño es un recyclerView donde se mostraran la lista de tarjetas, su id es “IncidenciesRecyclerView” 
- Activity_edita_incidencia.xml: Este diseño consta de:
    - imageView3 – Esta es la imagen de la portada de la incidencia (en esta aplicación es siempre la misma imagen “incidencia.png”)
    - titol_incidencia – Muestra la variable “assumpte” de cada incidencia
    - descripcio_incidencia – Muestra la variable “descripcio” de cada incidencia
    - carrer – Muestra la variable “ubicacio” de cada incidencia
    - spinnerServei – Muestra tres opciones “Jardineria, Infraestructures, Obres” y la que elijas se guarda en la variable serveis de cada incidencia.
    - switchResolt – Muestra la variable “resolt” que es una variable booleana que se pone en true o false dependiendo de si la marcas, esta variable se refiere a si ha sido resuelta la incidencia.
    - buttonSave – Este botón sirve para que se guarden las incidencias con los datos que se hayan introducido o que se cree una nueva con esos datos.
- Incidencia_layout_materialcardview: Este diseño consta de un MaterialCardView y un contraintLayout :
	- Titol – Hace referencia a la variable “assumpte” de Incidencia
	- Descripcio  – Hace referencia a la variable “descripcio” de Incidencia
    - imageView – Hace referencia a la variable “img” de Incidencia, en este aplicación todas las incidencies tienen la misma imatge

#### MENU:
- Menú_principal.xml- Este xml esta formado por el componente “nova_in”, su función es que cuando el usuario lo pulse, se acceda a la actividad EditaIncidencia pero con todos los campos vacíos, y que cuando el usuario pulse el botón guardar se cree una nueva incidenia con los datos que ha puesto el usuario. El titulo de “nova_in” es NEW!, y he cambiado su showAction a ifRoom para que se muestre como un único botón a la barra donde se encuentra el nombre de la aplicación.

#### VALUES:
- Serveis.xml – Este xml muestra las posibles opciones del spinner de la actividad edita_incidencia.
