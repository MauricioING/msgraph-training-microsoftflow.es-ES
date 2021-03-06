<!-- markdownlint-disable MD002 MD041 -->

En este ejercicio, creará un nuevo conector personalizado que se puede usar en flujo o en aplicaciones lógicas de Azure. El archivo de definición de la API abierta se crea previamente con la ruta de acceso `$batch` correcta para el punto de conexión de Microsoft Graph y la configuración adicional para habilitar la importación simple.

Con un editor de texto, cree un nuevo archivo vacío `MSGraph-Delegate-Batch.swagger.json` denominado y agregue el siguiente código.

[!code-json[](../LabFiles/MSGraph-Delegate-Batch.swagger.json)]

Abra un explorador y vaya a [Microsoft Flow](https://flow.microsoft.com). Inicie sesión con su cuenta de administrador de inquilinos de Office 365. En el menú de la izquierda, expanda **datos** y elija **conectores personalizados**.

![Captura de pantalla del elemento de menú conectores personalizados en Microsoft Flow](./images/flow-conn1.png)

En la página **conectores personalizados** , elija el vínculo **nuevo conector personalizado** en la parte superior derecha y, a continuación, seleccione el elemento **importar un archivo de OpenAPI** en el menú desplegable. Escriba `MS Graph Batch Connector` en el cuadro de texto **nombre del conector** . Elija el botón **importar** para cargar el archivo de la API abierta. Busque el `MSGraph-Delegate-Batch.swagger.json` archivo que ha creado. Elija **continuar** para cargar el archivo OpenAPI.

 ![Captura de pantalla del cuadro de diálogo crear conector personalizado](./images/flow-conn3.png)

En la página Configuración del conector, elija el vínculo **seguridad** en el menú de navegación. Rellene los campos como se indica a continuación.

- **Elija qué autenticación implementa la API**:`OAuth 2.0`
- **Proveedor de identidad**:`Azure Active Directory`
- **Identificador de cliente**: identificador de la aplicación que creó en el ejercicio anterior.
- **Secreto de cliente**: la clave que creó en el ejercicio anterior
- **Dirección URL de inicio de sesión**:`https://login.windows.net`
- **Identificador de inquilino**:`common`
- **Dirección URL**del `https://graph.microsoft.com` recurso: (sin finalización/)
- **Ámbito**: dejar en blanco

Elija **crear conector** en la parte superior derecha

![Captura de pantalla de la pestaña seguridad en la configuración del conector](./images/flow-conn4.png)

Una vez creado el conector, copie la **dirección URL de redireccionamiento**generada.

![Captura de pantalla de la dirección URL de redireccionamiento generada](./images/flow-conn5.png)

Vuelva a la aplicación registrada en el [portal de Azure](https://aad.portal.azure.com) que creó en el ejercicio anterior. Seleccione **información general** en la hoja **aplicación para lotes de MS Graph** y, a continuación, seleccione **Agregar un URI de redireccionamiento**. Agregue la **URL de redireccionamiento** que ha copiado en el campo **URI de redireccionamiento** y elija **Guardar**.

![Captura de pantalla de la hoja direcciones URL de respuesta en Azure portal](./images/flow-conn-preview6.png)
