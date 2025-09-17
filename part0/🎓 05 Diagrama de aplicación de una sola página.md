# 🎓 Curso de Desarrollador University of Helsinki

**University of Helsinki:** [🔗 University of Helsinki Helsinki](https://www.helsinki.fi/en)
---

## 📄 TAREA: *0.5: Diagrama de aplicación de una sola página*

**Autor:** William O Lozano G.  
**Repositorio oficial:** [🔗 GitHub - Curso Universidad Helsinki](https://github.com/wolgprogramador-cell/CursoUniversidadHelsinki.git)  
**Fecha de actualización:** 2025-09-14  

---

## 📒 0.5: Diagrama de Aplicación de Una Sola Página (SPA)

Este diagrama ilustra el flujo de comunicación entre el **navegador del cliente** y el **servidor remoto** en una aplicación web moderna de la página https://studies.cs.helsinki.fi/exampleapp/spa  donde todos los recursos se cargan dinámicamente mediante solicitudes asíncronas.

### 📚 DIAGRAMA DE SECUENCIA

```mermaid
sequenceDiagram
participant browser as Navegador
participant server as Servidor (Helsinki CS)
browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
Note over browser: Dirección del recurso solicitado.<br> Código de estado:200 OK <br> El servidor responde con el documento HTML principal.
server-->>browser: Documento HTML
browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
server-->>browser: Archivo CSS (estilos)
browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
Note over browser:  Solicitud HTTP `GET` al archivo `spa.js`.<br> Este script gestiona la lógica dinámica de la SPA.<br> Código: `200 OK` — Recurso entregado correctamente.
server-->>browser: Archivo JavaScript (`spa.js`)
Note over browser: El navegador inicia la ejecución del código JavaScript.<br> Se prepara para obtener datos dinámicos desde `/data.json`.
browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
Note over browser: Solicitud `GET` al endpoint de datos.<br> Código: `200 OK` — Respuesta JSON válida recibida.
server-->>browser: { content: "Excelente Curso Universidad Helsinki WOLG", date: "2025-09-14T17:43:59.898Z", ... }
```
