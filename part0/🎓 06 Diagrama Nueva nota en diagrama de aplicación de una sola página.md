# 🎓 Curso de Desarrollador University of Helsinki

**University of Helsinki:** [🔗 University of Helsinki Helsinki](https://www.helsinki.fi/en)
---

## 📄 TAREA: * 0.6: Diagrama de Creación de una Nueva Nota en una SPA*

**Autor:** William O Lozano G.  
**Repositorio oficial:** [🔗 GitHub - Curso Universidad Helsinki](https://github.com/wolg67/CursoUniversidadHelsinki.git)  
**Fecha de actualización:** 2025-09-14  

---

## 📒  0.6: Diagrama de Creación de una Nueva Nota en una SPA.

Este diagrama ilustra el flujo de interacción entre el **navegador del cliente** y el **servidor remoto** cuando un usuario crea una nueva nota en la aplicación web de una sola página (SPA) https://studies.cs.helsinki.fi/exampleapp/new_note de la Universidad de Helsinki. 

> 💡 **Contexto**: Tras cargar la interfaz inicial, el usuario ingresa un mensaje en el campo de texto y hace clic en el botón *“Save”*. Esto desencadena una nueva secuencia de solicitudes HTTP que culmina en la actualización del contenido visual sin recargar la página.

### 📚 DIAGRAMA DE SECUENCIA

```mermaid
sequenceDiagram
participant browser as Navegador
participant server as Servidor (Helsinki CS)
browser ->>+ server: GET https://studies.cs.helsinki.fi/exampleapp/new_note
Note over browser: Dirección del recurso que <br/>el navegador está solicitando. <br/>Code: 200 OK indica que la <br/>solicitud fue exitosa <br/>y el servidor devolvió <br/>el recurso solicitado
server -->>- browser: Documento HTML 
browser ->>+ server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
server -->>- browser: El Archivo CSS
browser ->>+ server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
server -->>- browser: El Archivo JavaScript
Note over browser: El navegador comienza a ejecutar <br/>el código JavaScript que obtiene <br/>el JSON del servidor despues <br/>de escribir el mensaje y presionarnar <br/> el Boton "save". <br/>Code: 200 OK indica que la <br/>solicitud fue exitosa <br/>y el servidor devolvió <br/>el recurso solicitado
browser ->>+ server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
server -->>- browser: [{ content: "Excelente Curso Universidad Helinski WOLG", date: "2025-09-14T17:43:59.898Z", ... }]
Note over browser: El navegador ejecuta la función <br/>de devolución de  llamada <br/>que muestra las notas, <br/>agregando en el data.js <br/>el mensaje enviado. <br/>Code: 200 OK indica que la <br/>solicitud fue exitosa <br/>y el servidor devolvió <br/>el recurso solicitado
```
