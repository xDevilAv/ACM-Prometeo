---
title: Mission Functions
permalink: /en/Mission_Functions
published: true
---

{% include git-wiki/components/toc/toc-include.html %}

# Configuración del Addon de Evacuación

El addon de evacuación permite convertir las bajas de jugadores en unidades IA. Después, los jugadores podrán reaparecer en una ubicación predefinida y la baja podrá ser evacuada posteriormente.
<br><br>
Este punto de refuerzo debe definirse para establecer dónde serán teletransportados los jugadores después de la conversión. Debe situarse en una posición amiga previamente establecida, preferiblemente cerca de un medio de transporte que los jugadores utilizarán para regresar.

Los objetos de evacuación deben definirse para permitir evacuar a la baja y devolver el ticket de baja utilizado. Esto debería estar en una posición amiga previamente establecida, potencialmente dentro de un edificio médico.
<br><br>
Además, si se desea usar tickets de respawn (recomendado), se debe habilitar la resta de tickets de respawn en los atributos de la misión.

### Definir puntos de evacuación y refuerzo
{:.no_toc}

#### Punto de Refuerzo
El punto de refuerzo define dónde serán teletransportados los jugadores convertidos.

- Solo un punto de refuerzo por facción estará activo a la vez. Si hay varios, se utilizará el último que se inicialice.

<br><br>
<big>**Atributos del módulo**</big><br>
**Bando del jugador** - Define para qué facción está destinado el punto de refuerzo.

{% include video.html v="/wiki/image/mission_modules/reinforce_point.webm" type="video/webm" gif="true" s="50" f="center" t="Módulo Punto de Refuerzo" %}

#### Punto de Evacuación
El punto de evacuación controla qué objetos pueden utilizarse para evacuar bajas convertidas.

- El objeto objetivo no debe ser un objeto simple.
- Los objetos objetivo deberían hacerse indestructibles para evitar problemas.

<br><br>
<big>**Atributos del módulo**</big><br>
**Bando del jugador** - Define para qué facción está destinado el punto de evacuación.<br>
**Distancia de interacción** - Por defecto: `5`<br>
**Posición de interacción** - Por defecto: `[0,0,0]`

{% include video.html v="/wiki/image/mission_modules/evacuation_point.webm" type="video/webm" gif="true" s="50" f="center" t="Módulo Punto de Evacuación" %}

### Activar la resta de tickets de respawn en el archivo de misión
{:.no_toc}

Activa la resta de tickets cuando una unidad muere. Esto hará que las muertes de jugadores y bajas convertidas de la facción del jugador consuman tickets de respawn.

<img src="{{ '/wiki/image/mission_subtract_tickets.png' | relative_url }}" height="150">

# Instalación de Curación Total

La instalación de curación total permite definir fácilmente objetos que pueden curar completamente a unidades específicas o a todas las unidades dentro de ella.

- El objeto objetivo no debe ser un objeto simple.
- Los objetos objetivo deberían hacerse indestructibles para evitar problemas.

<br><br>
<big>**Atributos del módulo**</big><br>
**Distancia de interacción** - Por defecto: `5`<br>
**Posición de interacción** - Por defecto: `[0,0,0]`

{% include video.html v="/wiki/image/mission_modules/full_heal_facility.webm" type="video/webm" gif="true" s="50" f="center" t="Módulo Instalación de Curación Total" %}

<img src="{{ '/wiki/image/mission_healtent_use.png' | relative_url }}" height="500">

# Lista Personalizada de Tipos de Sangre

La lista personalizada de tipos de sangre permite sobrescribir los tipos de sangre basados en SteamID y establecer tipos de sangre específicos para cada jugador, por ejemplo según el tipo de sangre real del jugador.
<br><br>
Debe introducirse una función en el campo **init** de la misión que definirá los tipos de sangre asignados a determinados SteamID.

### Activar lista personalizada de tipos de sangre en los ajustes de circulación
{:.no_toc}

<img src="{{ '/wiki/image/mission_custom_bloodlist_enable.png' | relative_url }}" height="50">

### Definir tipos de sangre
{:.no_toc}

- Introduce este código en el campo **init** en los atributos de la misión:<br>
  - `[[["<STEAMID>",<ID>]]] call ACM_mission_fnc_createCustomBloodTypeList;`
- Esto vinculará el tipo de sangre deseado al SteamID especificado.

<table style = "width:8%;">
    <tr>
        <th>Tipo de sangre</th>
        <th>ID</th>
    </tr>
    <tr>
        <td>O+</td>
        <td>0</td>
    </tr>
    <tr>
        <td>O-</td>
        <td>1</td>
    </tr>
    <tr>
        <td>A+</td>
        <td>2</td>
    </tr>
    <tr>
        <td>A-</td>
        <td>3</td>
    </tr>
    <tr>
        <td>B+</td>
        <td>4</td>
    </tr>
    <tr>
        <td>B-</td>
        <td>5</td>
    </tr>
    <tr>
        <td>AB+</td>
        <td>6</td>
    </tr>
    <tr>
        <td>AB-</td>
        <td>7</td>
    </tr>
</table>

#### Ejemplo
{:.no_toc}

`[[["76561197960287930",1],["76561195961284930",4]]] call ACM_mission_fnc_createCustomBloodTypeList;`<br>

- **76561197960287930** tendrá tipo de sangre **O-**  
- **76561195961284930** tendrá tipo de sangre **B+**

<img src="{{ '/wiki/image/mission_custombloodlist.png' | relative_url }}" height="400">

# Generador de Bajas

El generador de bajas permite añadir fácilmente un sistema para generar bajas con diferentes niveles de gravedad para entrenamiento.
<br><br>
Debe crearse un objeto de referencia para definir dónde aparecerán las bajas.

También debe crearse un objeto de **ordenador de entrenamiento** para permitir al jugador generar bajas con el nivel de gravedad deseado.

### Objeto de referencia
{:.no_toc}

- Crea un nuevo objeto y establece su nombre de variable como algo único (por ejemplo `ACM_mission_TrainingSpot1`).
  - Esta variable se usará en el objeto del ordenador de entrenamiento para referenciar este objeto.
- Este objeto se utilizará como referencia para el punto donde aparecerán las bajas. Puede ocultarse si es necesario.

<img src="{{ '/wiki/image/mission_training_computer_ref.png' | relative_url }}" height="750">

### Ordenador de entrenamiento
{:.no_toc}

- Crea un nuevo objeto e introduce este código en su campo **init**:<br>

`[this, variable] call ACM_mission_fnc_initTrainingComputer`

  - Donde `this` es el objeto de interacción y `variable` es el nombre de la variable del objeto de referencia (por ejemplo `ACM_mission_TrainingSpot1`).

- Este objeto tendrá todas las interacciones ACE para generar, curar y eliminar bajas.

<img src="{{ '/wiki/image/mission_trainingcomputer.png' | relative_url }}" height="750">
