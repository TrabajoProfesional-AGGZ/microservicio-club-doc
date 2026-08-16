---
layout: default
title: Endpoints
nav_order: 2
---

# 🔌 Endpoints

En esta sección se listan todos los endpoints disponibles en el microservicio core del club (`microservicio-club`). 

Esta página sirve como referencia estática para garantizar el acceso a los contratos de la API de forma rápida y clara, organizada por dominios de negocio.

## 👥 Socios

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/socios/health</code> - Health Check
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>health_check_api_v1_socios_health_get</code></p>
    <p>Endpoint para verificar que el microservicio está funcionando correctamente.</p>
    <h3>Respuestas</h3>
    <p><strong>Código:</strong> <code>200 OK</code></p>
    <div class="language-json highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="p">{}</span>
</code></pre></div></div>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/socios</code> - Obtener Todos Los Socios
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_todos_los_socios_api_v1_socios_get</code></p>
    <p>Devuelve la lista paginada de socios registrados de forma síncrona con la base de datos.</p>
    <h3>Parámetros de consulta (Query Params)</h3>
    <ul>
      <li><code>pagina</code> (Integer, Opcional, Default: 1, Min: 1): Número de página.</li>
      <li><code>limite</code> (Integer, Opcional, Default: 50, Min: 1, Max: 100): Cantidad de registros por página.</li>
    </ul>
    <h3>Respuestas</h3>
    <p><strong>Código:</strong> <code>200 OK</code></p>
    <div class="language-json highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="p">{</span><span class="w">
  </span><span class="nl">"socios"</span><span class="p">:</span><span class="w"> </span><span class="p">[],</span><span class="w">
  </span><span class="nl">"total"</span><span class="p">:</span><span class="w"> </span><span class="integer">0</span><span class="w">
</span><span class="p">}</span>
</code></pre></div></div>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/socios</code> - Crear Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>crear_socio_api_v1_socios_post</code></p>
    <p>Registra un nuevo socio en el sistema, asegurando la unicidad de email y documento, y asignando automáticamente su número de socio y categoría.</p>
    <h3>Cuerpo de la Petición (Request Body)</h3>
    <div class="language-json highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="p">{</span><span class="w">
  </span><span class="nl">"nombre"</span><span class="p">:</span><span class="w"> </span><span class="s2">"string"</span><span class="p">,</span><span class="w">
  </span><span class="nl">"apellido"</span><span class="p">:</span><span class="w"> </span><span class="s2">"string"</span><span class="p">,</span><span class="w">
  </span><span class="nl">"fecha_nacimiento"</span><span class="p">:</span><span class="w"> </span><span class="s2">"YYYY-MM-DD"</span><span class="p">,</span><span class="w">
  </span><span class="nl">"tipo_doc"</span><span class="p">:</span><span class="w"> </span><span class="s2">"DNI"</span><span class="p">,</span><span class="w">
  </span><span class="nl">"nro_documento"</span><span class="p">:</span><span class="w"> </span><span class="s2">"string"</span><span class="p">,</span><span class="w">
  </span><span class="nl">"genero"</span><span class="p">:</span><span class="w"> </span><span class="s2">"M"</span><span class="p">,</span><span class="w">
  </span><span class="nl">"email"</span><span class="p">:</span><span class="w"> </span><span class="s2">"user@example.com"</span><span class="p">,</span><span class="w">
  </span><span class="nl">"telefono"</span><span class="p">:</span><span class="w"> </span><span class="s2">"string"</span><span class="p">,</span><span class="w">
  </span><span class="nl">"direccion"</span><span class="p">:</span><span class="w"> </span><span class="s2">"string"</span><span class="w">
</span><span class="p">}</span>
</code></pre></div></div>
    <h3>Respuestas</h3>
    <p><strong>Código:</strong> <code>201 Created</code></p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/socios/por-disciplina/{id_disciplina}</code> - Obtener Socios Por Disciplina
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_socios_por_disciplina_api_v1_socios_por_disciplina__id_disciplina__get</code></p>
    <p>Lista los socios inscriptos a una disciplina específica.</p>
    <h3>Parámetros</h3>
    <ul>
      <li><code>id_disciplina</code> (Path, UUID, Requerido)</li>
    </ul>
    <h3>Respuestas</h3>
    <p><strong>Código:</strong> <code>200 OK</code> (Retorna array de <code>SocioConSuscripcionResponse</code>)</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/socios/por-nro-socio/{nro_socio}</code> - Obtener Socio Por Nro Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_socio_por_nro_socio_api_v1_socios_por_nro_socio__nro_socio__get</code></p>
    <p>Busca un socio utilizando su número de socio institucional.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/socios/{id_socio}</code> - Obtener Socio Por Id
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_socio_por_id_api_v1_socios__id_socio__get</code></p>
    <p>Busca un socio por su identificador único universal (UUID). Devuelve error 404 si no existe.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/socios/por-email/{email}</code> - Obtener Socio Por Email
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_socio_por_email_api_v1_socios_por_email__email__get</code></p>
    <p>Busca un socio por su dirección de correo electrónico. Devuelve error 404 si no existe.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/socios/validar</code> - Validar Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>validar_socio_api_v1_socios_validar_post</code></p>
    <p>Valida la existencia de un socio mediante su número de socio y DNI.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/socios/{id_socio}/foto</code> - Subir Foto Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>subir_foto_socio_api_v1_socios__id_socio__foto_post</code></p>
    <p>Sube la foto de perfil del socio a Cloudinary (reemplaza el asset anterior si ya existía).</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #fd7e14; margin-bottom: 5px;">
    <strong style="color: #fd7e14;">PATCH</strong> <code>/api/v1/socios/{socio_id}</code> - Modificar Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>modificar_socio_api_v1_socios__socio_id__patch</code></p>
    <p>Permite actualizar parcialmente los datos de un socio por UUID.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #dc3545; margin-bottom: 5px;">
    <strong style="color: #dc3545;">DELETE</strong> <code>/api/v1/socios/{socio_id}</code> - Borrar Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>borrar_socio_api_v1_socios__socio_id__delete</code></p>
    <p>Realiza un borrado lógico del socio, alterando su estado a 'Inactivo'.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #fd7e14; margin-bottom: 5px;">
    <strong style="color: #fd7e14;">PATCH</strong> <code>/api/v1/socios/por-dni/{dni}</code> - Modificar Socio por DNI
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>modificar_socio_api_v1_socios_por_dni__dni__patch</code></p>
    <p>Permite actualizar parcialmente los datos de un socio utilizando su DNI.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/socios/por-dni/{dni}/reclamar</code> - Reclamar Cuenta Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>reclamar_cuenta_socio_api_v1_socios_por_dni__dni__reclamar_post</code></p>
    <p>Marca al socio como con cuenta reclamada tras finalizar el flujo de registro de la app de socio. Devuelve 409 si ya fue reclamada.</p>
  </div>
</details>

## 👨‍💼 Usuarios Administrativos

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/usuarios</code> - Listar Usuarios
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_usuarios_api_v1_usuarios_get</code></p>
    <p>Devuelve la lista paginada de usuarios administrativos.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/usuarios</code> - Crear Usuario
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>crear_usuario_api_v1_usuarios_post</code></p>
    <p>Registra un nuevo usuario administrativo en el sistema.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/usuarios/{id_usuario}</code> - Obtener Usuario
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_usuario_api_v1_usuarios__id_usuario__get</code></p>
    <p>Obtiene los detalles de un usuario administrativo por su UUID.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #fd7e14; margin-bottom: 5px;">
    <strong style="color: #fd7e14;">PATCH</strong> <code>/api/v1/usuarios/{id_usuario}</code> - Actualizar Usuario
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>actualizar_usuario_api_v1_usuarios__id_usuario__patch</code></p>
    <p>Actualiza parcialmente los datos de un usuario administrativo.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #dc3545; margin-bottom: 5px;">
    <strong style="color: #dc3545;">DELETE</strong> <code>/api/v1/usuarios/{id_usuario}</code> - Borrar Usuario
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>borrar_usuario_api_v1_usuarios__id_usuario__delete</code></p>
    <p>Elimina o desactiva un usuario administrativo.</p>
  </div>
</details>

## ⚽ Disciplinas

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/disciplinas</code> - Listar Disciplinas
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_disciplinas_api_v1_disciplinas_get</code></p>
    <p>Lista las disciplinas del club. Permite filtrar opcionalmente con el parámetro <code>solo_activas</code> (boolean).</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/disciplinas</code> - Crear Disciplina
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>crear_disciplina_api_v1_disciplinas_post</code></p>
    <p>Crea una nueva disciplina en el sistema.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/disciplinas/por-socio/{id_socio}</code> - Listar Disciplinas Por Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_disciplinas_por_socio_api_v1_disciplinas_por_socio__id_socio__get</code></p>
    <p>Lista las disciplinas asociadas a un socio específico.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/disciplinas/{id_disciplina}</code> - Obtener Disciplina Por Id
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_disciplina_por_id_api_v1_disciplinas__id_disciplina__get</code></p>
    <p>Obtiene el detalle de una disciplina por su UUID.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #dc3545; margin-bottom: 5px;">
    <strong style="color: #dc3545;">DELETE</strong> <code>/api/v1/disciplinas/{id_disciplina}</code> - Borrar Disciplina
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>borrar_disciplina_api_v1_disciplinas__id_disciplina__delete</code></p>
    <p>Elimina o da de baja una disciplina.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/disciplinas/{id_disciplina}/socios/{id_socio}</code> - Inscribir Socio A Disciplina
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>inscribir_socio_a_disciplina_api_v1_disciplinas__id_disciplina__socios__id_socio__post</code></p>
    <p>Inscribe a un socio en una disciplina específica.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/disciplinas/{id_disciplina}/socios/{id_socio}/lista-espera</code> - Anotar Socio En Lista Espera
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>anotar_socio_en_lista_espera_api_v1_disciplinas__id_disciplina__socios__id_socio__lista_espera_post</code></p>
    <p>Anota a un socio en la lista de espera cuando la disciplina se encuentra sin cupos.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #fd7e14; margin-bottom: 5px;">
    <strong style="color: #fd7e14;">PATCH</strong> <code>/api/v1/disciplinas/{id_disciplina}/socios/{id_socio}/lista-espera</code> - Resolver Lista Espera
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>resolver_lista_espera_api_v1_disciplinas__id_disciplina__socios__id_socio__lista_espera_patch</code></p>
    <p>Permite activar o eliminar a un socio de la lista de espera.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #fd7e14; margin-bottom: 5px;">
    <strong style="color: #fd7e14;">PATCH</strong> <code>/api/v1/disciplinas/{id_disciplina}/socios/{id_socio}/extender</code> - Extender Suscripcion Disciplina
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>extender_suscripcion_disciplina_api_v1_disciplinas__id_disciplina__socios__id_socio__extender_patch</code></p>
    <p>Extiende la vigencia de la suscripción de un socio a una disciplina.</p>
  </div>
</details>

## 🏗️ Instalaciones

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/instalaciones</code> - Listar Instalaciones
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_instalaciones_api_v1_instalaciones_get</code></p>
    <p>Devuelve la lista de instalaciones del club.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/instalaciones</code> - Crear Instalacion
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>crear_instalacion_api_v1_instalaciones_post</code></p>
    <p>Crea una nueva instalación deportiva o espacio en el club.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/instalaciones/{id_instalacion}</code> - Obtener Instalacion Por Id
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_instalacion_por_id_api_v1_instalaciones__id_instalacion__get</code></p>
    <p>Obtiene el detalle de una instalación por su UUID.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #fd7e14; margin-bottom: 5px;">
    <strong style="color: #fd7e14;">PATCH</strong> <code>/api/v1/instalaciones/{id_instalacion}</code> - Actualizar Instalacion
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>actualizar_instalacion_api_v1_instalaciones__id_instalacion__patch</code></p>
    <p>Actualiza parcialmente los datos de una instalación.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #dc3545; margin-bottom: 5px;">
    <strong style="color: #dc3545;">DELETE</strong> <code>/api/v1/instalaciones/{id_instalacion}</code> - Desactivar Instalacion
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>desactivar_instalacion_api_v1_instalaciones__id_instalacion__delete</code></p>
    <p>Desactiva una instalación.</p>
  </div>
</details>

## 📅 Reservas

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/reservas</code> - Listar Reservas
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_reservas_api_v1_reservas_get</code></p>
    <p>Lista todas las reservas activas.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/reservas</code> - Crear Reserva
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>crear_reserva_api_v1_reservas_post</code></p>
    <p>Crea una nueva reserva de instalación.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/reservas/por-socio/{nro_socio}</code> - Listar Reservas Por Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_reservas_por_socio_api_v1_reservas_por_socio__nro_socio__get</code></p>
    <p>Lista las reservas asociadas a un socio por su número de socio.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/reservas/por-instalacion/{id_instalacion}</code> - Listar Reservas Por Instalacion
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_reservas_por_instalacion_api_v1_reservas_por_instalacion__id_instalacion__get</code></p>
    <p>Lista las reservas asociadas a una instalación específica.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/reservas/turnos-disponibles/{id_instalacion}</code> - Listar Turnos Disponibles
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_turnos_disponibles_api_v1_reservas_turnos_disponibles__id_instalacion__get</code></p>
    <p>Lista los turnos disponibles para una instalación en una fecha determinada (Query param: <code>fecha</code>).</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/reservas/historicas</code> - Listar Reservas Historicas
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_reservas_historicas_api_v1_reservas_historicas_get</code></p>
    <p>Lista el historial de reservas pasadas.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/reservas/historicas/por-instalacion/{id_instalacion}</code> - Listar Reservas Historicas Por Instalacion
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_reservas_historicas_por_instalacion_api_v1_reservas_historicas_por_instalacion__id_instalacion__get</code></p>
    <p>Lista el historial de reservas de una instalación específica.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/reservas/historicas/por-socio/{nro_socio}</code> - Listar Reservas Historicas Por Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_reservas_historicas_por_socio_api_v1_reservas_historicas_por_socio__nro_socio__get</code></p>
    <p>Lista el historial de reservas de un socio específico por número de socio.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/reservas/{id_reserva}</code> - Obtener Reserva Por Id
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_reserva_por_id_api_v1_reservas__id_reserva__get</code></p>
    <p>Obtiene el detalle de una reserva por su ID.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #dc3545; margin-bottom: 5px;">
    <strong style="color: #dc3545;">DELETE</strong> <code>/api/v1/reservas/{id_reserva}</code> - Cancelar Reserva
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>cancelar_reserva_api_v1_reservas__id_reserva__delete</code></p>
    <p>Cancela una reserva existente.</p>
  </div>
</details>

## 📰 Noticias

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/noticias</code> - Listar Noticias
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_noticias_api_v1_noticias_get</code></p>
    <p>Lista todas las noticias del club.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/noticias</code> - Crear Noticia
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>crear_noticia_api_v1_noticias_post</code></p>
    <p>Crea una nueva noticia.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/noticias/vigentes</code> - Listar Vigentes
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_vigentes_api_v1_noticias_vigentes_get</code></p>
    <p>Lista únicamente las noticias que se encuentran vigentes.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/noticias/{id}</code> - Obtener Noticia
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_noticia_api_v1_noticias__id__get</code></p>
    <p>Obtiene el detalle de una noticia por su UUID.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #fd7e14; margin-bottom: 5px;">
    <strong style="color: #fd7e14;">PATCH</strong> <code>/api/v1/noticias/{id}</code> - Editar Noticia
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>editar_noticia_api_v1_noticias__id__patch</code></p>
    <p>Edita los datos de una noticia existente.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #dc3545; margin-bottom: 5px;">
    <strong style="color: #dc3545;">DELETE</strong> <code>/api/v1/noticias/{id}</code> - Eliminar Noticia
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>eliminar_noticia_api_v1_noticias__id__delete</code></p>
    <p>Elimina una noticia del sistema.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/noticias/imagen</code> - Subir Imagen Noticia
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>subir_imagen_noticia_api_v1_noticias_imagen_post</code></p>
    <p>Sube una imagen asociada a una noticia.</p>
  </div>
</details>

## 🚨 Alertas

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/alertas</code> - Listar Alertas
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_alertas_api_v1_alertas_get</code></p>
    <p>Lista todas las alertas creadas.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/alertas</code> - Crear Alerta
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>crear_alerta_api_v1_alertas_post</code></p>
    <p>Crea una nueva alerta orientada a grupos de socios.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/alertas/por-socio/{id_socio}</code> - Listar Alertas Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_alertas_socio_api_v1_alertas_por_socio__id_socio__get</code></p>
    <p>Lista las alertas que corresponden a un socio según su categoría y estado actuales.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #dc3545; margin-bottom: 5px;">
    <strong style="color: #dc3545;">DELETE</strong> <code>/api/v1/alertas/{id}</code> - Eliminar Alerta
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>eliminar_alerta_api_v1_alertas__id__delete</code></p>
    <p>Elimina una alerta del sistema.</p>
  </div>
</details>

## 💰 Finanzas

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/finanzas/{id_socio}</code> - Obtener Estado Financiero
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_estado_financiero_api_v1_finanzas__id_socio__get</code></p>
    <p>Obtiene el estado financiero detallado y cuotas de un socio por su UUID.</p>
  </div>
</details>

## ⚙️ Endpoints Internos

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/internos/cuotas/{id_cuota}/marcar-pagada</code> - Marcar Cuota Pagada Endpoint
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>marcar_cuota_pagada_endpoint_api_v1_internos_cuotas__id_cuota__marcar_pagada_post</code></p>
    <p>Marca una cuota como pagada internamente.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/internos/reservas/{id_reserva}/marcar-pagada</code> - Marcar Reserva Pagada
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>marcar_reserva_pagada_api_v1_internos_reservas__id_reserva__marcar_pagada_post</code></p>
    <p>Endpoint interno llamado por el microservicio de pagos o por WebApp a través del gateway.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/internos/entradas/{id_entrada}/marcar-pagada</code> - Marcar Entrada Pagada
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>marcar_entrada_pagada_api_v1_internos_entradas__id_entrada__marcar_pagada_post</code></p>
    <p>Endpoint interno llamado por el microservicio de pagos o por WebApp a través del gateway.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/internos/compras/{id_compra}/marcar-pagada</code> - Marcar Compra Pagada
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>marcar_compra_pagada_api_v1_internos_compras__id_compra__marcar_pagada_post</code></p>
    <p>Endpoint interno llamado por el microservicio de pagos o por WebApp a través del gateway.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/internos/comportamiento-pagos</code> - Obtener Comportamiento Pagos
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_comportamiento_pagos_api_v1_internos_comportamiento_pagos_get</code></p>
    <p>Obtiene métricas internas del comportamiento de pagos de los socios.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/internos/tendencias-pagos</code> - Obtener Tendencias Pagos
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_tendencias_pagos_api_v1_internos_tendencias_pagos_get</code></p>
    <p>Obtiene las tendencias mensuales de pagos del club.</p>
  </div>
</details>

## 📋 Trámites

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/tramites/tipos</code> - Listar Tipos Tramite
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_tipos_tramite_api_v1_tramites_tipos_get</code></p>
    <p>Lista los tipos de trámite disponibles (apto médico, declaración jurada, etc.).</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/tramites/por-socio/{id_socio}</code> - Listar Tramites Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_tramites_socio_api_v1_tramites_por_socio__id_socio__get</code></p>
    <p>Lista todos los trámites de un socio ordenados por fecha de carga.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/tramites/pendientes/{id_socio}</code> - Obtener Pendientes
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_pendientes_api_v1_tramites_pendientes__id_socio__get</code></p>
    <p>Devuelve trámites vencidos y por vencer (próximos 30 días) de un socio.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/tramites/{id_socio}</code> - Crear Tramite
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>crear_tramite_api_v1_tramites__id_socio__post</code></p>
    <p>Sube un formulario/trámite en base64 a Cloudinary con estado inicial 'en_revision'.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/tramites/{tramite_id}</code> - Obtener Tramite
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_tramite_api_v1_tramites__tramite_id__get</code></p>
    <p>Obtiene el detalle de un trámite por su ID.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #fd7e14; margin-bottom: 5px;">
    <strong style="color: #fd7e14;">PATCH</strong> <code>/api/v1/tramites/{tramite_id}/revisar</code> - Revisar Tramite
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>revisar_tramite_api_v1_tramites__tramite_id__revisar_patch</code></p>
    <p>Permite a un administrador aprobar o rechazar un trámite.</p>
  </div>
</details>

## 🔔 Notificaciones

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/notificaciones/token</code> - Registrar Device Token
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>registrar_device_token_api_v1_notificaciones_token_post</code></p>
    <p>Registra el token de dispositivo para envío de notificaciones push.</p>
  </div>
</details>

## 🎉 Eventos

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/eventos</code> - Listar Eventos
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_eventos_api_v1_eventos_get</code></p>
    <p>Lista los eventos programados.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/eventos</code> - Crear Evento
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>crear_evento_api_v1_eventos_post</code></p>
    <p>Crea un nuevo evento.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/eventos/historicos</code> - Listar Eventos Historicos
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_eventos_historicos_api_v1_eventos_historicos_get</code></p>
    <p>Lista el historial de eventos pasados.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/eventos/{id_evento}</code> - Obtener Evento
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_evento_api_v1_eventos__id_evento__get</code></p>
    <p>Obtiene el detalle de un evento por su UUID.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/eventos/imagen</code> - Subir Imagen Evento
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>subir_imagen_evento_api_v1_eventos_imagen_post</code></p>
    <p>Sube la imagen representativa de un evento.</p>
  </div>
</details>

## 🎟️ Entradas

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/entradas</code> - Comprar Entrada
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>comprar_entrada_api_v1_entradas_post</code></p>
    <p>Realiza la compra de una entrada para un evento.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/entradas/por-socio/{id_socio}</code> - Listar Entradas Activas Por Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_entradas_activas_por_socio_api_v1_entradas_por_socio__id_socio__get</code></p>
    <p>Lista las entradas activas de un socio.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/entradas/historicas/por-socio/{id_socio}</code> - Listar Entradas Historicas Por Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_entradas_historicas_por_socio_api_v1_entradas_historicas_por_socio__id_socio__get</code></p>
    <p>Lista el historial de entradas pasadas de un socio.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/entradas/pendientes/por-socio/{id_socio}</code> - Listar Entradas Pendientes Por Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_entradas_pendientes_por_socio_api_v1_entradas_pendientes_por_socio__id_socio__get</code></p>
    <p>Lista las entradas que se encuentran pendientes de pago para un socio.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/entradas/validar</code> - Validar Entrada Evento
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>validar_entrada_evento_api_v1_entradas_validar_get</code></p>
    <p>Valida una entrada para el acceso a un evento mediante Query parameters (<code>socio_id</code> e <code>id_evento</code>).</p>
  </div>
</details>

## 🛍️ Tienda y Productos

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/productos/disponibles</code> - Listar Disponibles
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_disponibles_api_v1_productos_disponibles_get</code></p>
    <p>Lista los productos activos que cuentan con stock disponible (orientado a socios).</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/productos</code> - Listar Todos
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_todos_api_v1_productos_get</code></p>
    <p>Lista todos los productos del inventario (orientado a administradores).</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/productos</code> - Crear Producto
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>crear_producto_api_v1_productos_post</code></p>
    <p>Crea un nuevo producto en la tienda.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/productos/imagen</code> - Subir Imagen Producto
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>subir_imagen_producto_api_v1_productos_imagen_post</code></p>
    <p>Sube una imagen de producto a Cloudinary y devuelve la URL.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/productos/{producto_id}</code> - Obtener Producto
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_producto_api_v1_productos__producto_id__get</code></p>
    <p>Obtiene el detalle de un producto (descripción, stock y precio) por su UUID.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #fd7e14; margin-bottom: 5px;">
    <strong style="color: #fd7e14;">PATCH</strong> <code>/api/v1/productos/{producto_id}</code> - Actualizar Producto
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>actualizar_producto_api_v1_productos__producto_id__patch</code></p>
    <p>Actualiza la información de un producto existente.</p>
  </div>
</details>

## 🛒 Compras

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/compras</code> - Comprar Producto
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>comprar_producto_api_v1_compras_post</code></p>
    <p>Registra la compra de un producto por parte de un socio.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/compras/socio/{id_socio}</code> - Listar Compras Pagadas Por Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_compras_pagadas_por_socio_api_v1_compras_socio__id_socio__get</code></p>
    <p>Lista las compras pagadas realizadas por un socio.</p>
  </div>
</details>

## 🧑‍💻 Empleados

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/empleados/por-legajo/{legajo}</code> - Obtener Empleado Por Legajo
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_empleado_por_legajo_api_v1_empleados_por_legajo__legajo__get</code></p>
    <p>Busca un empleado por su legajo. Devuelve error 404 si no existe.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #fd7e14; margin-bottom: 5px;">
    <strong style="color: #fd7e14;">PATCH</strong> <code>/api/v1/empleados/por-legajo/{legajo}</code> - Modificar Empleado
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>modificar_empleado_api_v1_empleados_por_legajo__legajo__patch</code></p>
    <p>Actualiza parcialmente los datos de un empleado por legajo.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/empleados/por-email/{mail}</code> - Obtener Empleado Por Email
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_empleado_por_email_api_v1_empleados_por_email__mail__get</code></p>
    <p>Busca un empleado por su dirección de correo electrónico.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/empleados/mail-por-legajo/{legajo}</code> - Obtener Mail Por Legajo
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>obtener_mail_por_legajo_api_v1_empleados_mail_por_legajo__legajo__get</code></p>
    <p>Devuelve únicamente el mail asociado a un legajo para resolver el login en la app de control de acceso antes de que exista sesión de Firebase.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/empleados</code> - Crear Empleado
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>crear_empleado_api_v1_empleados_post</code></p>
    <p>Registra un nuevo empleado en el sistema (alta administrativa).</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/empleados/validar</code> - Validar Empleado
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>validar_empleado_api_v1_empleados_validar_post</code></p>
    <p>Valida la existencia de un empleado mediante legajo, mail y DNI. Devuelve error 409 si ya reclamó su cuenta.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/empleados/por-legajo/{legajo}/reclamar</code> - Reclamar Cuenta Empleado
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>reclamar_cuenta_empleado_api_v1_empleados_por_legajo__legajo__reclamar_post</code></p>
    <p>Marca al empleado como con cuenta reclamada al finalizar el registro en la app de control de acceso.</p>
  </div>
</details>

## 🔒 Seguridad y Accesos, Sedes y Catálogos

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/estados-socio</code> - Listar Estados de Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_estados_api_v1_estados_socio_get</code></p>
    <p>Lista los posibles estados de un socio.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/categorias-socio</code> - Listar Categorias de Socio
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_categoria_api_v1_categorias_socio_get</code></p>
    <p>Lista las categorías disponibles para los socios.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/sedes</code> - Listar Sedes
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_sedes_api_v1_sedes_get</code></p>
    <p>Lista las sedes operativas del club.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/roles</code> - Listar Roles
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_roles_api_v1_roles_get</code></p>
    <p>Lista los roles y sus permisos asociados.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #28a745; margin-bottom: 5px;">
    <strong style="color: #28a745;">POST</strong> <code>/api/v1/roles</code> - Crear Rol
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>crear_rol_api_v1_roles_post</code></p>
    <p>Crea un nuevo rol en el sistema.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #fd7e14; margin-bottom: 5px;">
    <strong style="color: #fd7e14;">PATCH</strong> <code>/api/v1/roles/{id_rol}</code> - Actualizar Rol
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>actualizar_rol_api_v1_roles__id_rol__patch</code></p>
    <p>Actualiza un rol existente.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #dc3545; margin-bottom: 5px;">
    <strong style="color: #dc3545;">DELETE</strong> <code>/api/v1/roles/{id_rol}</code> - Eliminar Rol
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>eliminar_rol_api_v1_roles__id_rol__delete</code></p>
    <p>Elimina un rol del sistema.</p>
  </div>
</details>

<details>
  <summary style="font-size: 1.1em; cursor: pointer; padding: 10px; background-color: #f8f9fa; border-radius: 4px; border-left: 4px solid #007bff; margin-bottom: 5px;">
    <strong style="color: #007bff;">GET</strong> <code>/api/v1/permisos</code> - Listar Permisos
  </summary>
  <div style="padding: 15px; border: 1px solid #f8f9fa; border-top: none; margin-bottom: 20px;">
    <p><strong>ID de la Operación:</strong> <code>listar_permisos_api_v1_permisos_get</code></p>
    <p>Lista todos los permisos disponibles.</p>
  </div>
</details>
