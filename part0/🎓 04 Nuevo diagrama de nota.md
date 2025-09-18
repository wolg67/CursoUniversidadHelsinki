# 🎓 Curso de Desarrollador University of Helsinki

**University of Helsinki:** [🔗 University of Helsinki Helsinki](https://www.helsinki.fi/en)
---

## 📄 TAREA: *0.4: Nuevo diagrama de nota*

**Autor:** William O Lozano G.  
**Repositorio oficial:** [🔗 GitHub - Curso Universidad Helsinki](https://github.com/wolgprogramador-cell/CursoUniversidadHelsinki.git)  
**Fecha de actualización:** 2025-09-14  

---

## 📒   04 Nuevo diagrama de nota.

Este diagrama ilustra el flujo de interacción entre el **navegador del cliente** y el **servidor remoto** cuando un usuario crea una nueva nota en la aplicación web de una sola página (SPA) https://studies.cs.helsinki.fi/exampleapp/new_note de la Universidad de Helsinki. 

> 💡 **Contexto**: Tras cargar la interfaz inicial, el usuario ingresa un mensaje en el campo de texto y hace clic en el botón *“Save”*. Esto desencadena una nueva secuencia de solicitudes HTTP que culmina en la actualización del contenido visual sin recargar la página.

### 📚 DIAGRAMA DE SECUENCIA

```mermaid
sequenceDiagram
  participant browser as Navegador
  participant server as Servidor (Helsinki CS)
  Note over browser: El Formulario está en el navegador: <br>https://studies.cs.helsinki.fi/exampleapp/note.<br> Se escribe la nota "Este Curso de la Universidad <br/>de Helsinki es excelente:wolg" y se da clic <br>en “Save”. El navegador hace una solicitud POST a: <br>https://studies.cs.helsinki.fi/exampleapp/new_note
  browser ->>+ server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
  Note over browser: El servidor responde con 302 Found <br/>y sugiere Location: /exampleapp/notes
  server -->>- browser:  302 Found + https://studies.cs.helsinki.fi/exampleapp/note
  Note over browser: El navegador hace una nueva solicitud, <br/>esta vez con método GET, a la <br/>URL indicada en el encabezado Location: <br/>./exampleapp/note
  browser ->>+ server: GET https://studies.cs.helsinki.fi/exampleapp/notes
  Note over browser: El servidor genera el HTML de la lista <br/>de notas e incluye la que se acaba de crear, <br/>y responde con: 200 OK, lo cual indica <br/>que la operación se realizó con éxito
  server -->>+ browser: 200 OK + Documento HTML
  browser ->>+ server: 200 OK + GET https://studies.cs.helsinki.fi/exampleapp/main.css
  server -->>- browser: El Archivo CSS
  browser ->>+ server: 200 OK + GET https://studies.cs.helsinki.fi/exampleapp/main.js
  server -->>- browser: El Archivo JavaScript
  Note over browser: El navegador comienza a ejecutar <br/>el código JavaScript que obtiene <br/>el JSON del servidor despues <br/>de escribir el mensaje y presionar <br/> el Boton "save". <br/>Code: 200 OK indica que la <br/>solicitud fue exitosa <br/>y el servidor devolvió <br/>el recurso solicitado
  browser ->>+ server: 200 OK + GET https://studies.cs.helsinki.fi/exampleapp/data.json
  Note over browser: El navegador ejecuta la función <br/>de devolución de  llamada <br/>que muestra las notas, <br/>agregando en el data.js <br/>el mensaje enviado. <br/>Code: 200 OK indica que la <br/>solicitud fue exitosa <br/>y el servidor devolvió <br/>el recurso solicitado
  server -->>- browser: Nota añadida [{ content: "Este Curso de la Universidad de Helsinki es excelente:wolg", date: "2025-09-14T17:43:59.898Z", ... }]
```
