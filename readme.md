# 📋 Módulo de RRHH - Documentación de Casos de Uso

Este módulo forma parte del sistema de gestión interna y está orientado a la administración de recursos humanos. Permite gestionar empleados, novedades salariales, licencias y reportes del personal, integrándose con el Sistema de Planilla.

## 👥 Actores

- **Empleado**: Usuario con permisos para actualizar sus propios datos y gestionar licencias.
- **Jefe RRHH**: Usuario encargado de administrar toda la información del personal.
- **Sistema de Planilla**: Sistema externo encargado del cálculo y emisión de sueldos.

## ✅ Casos de Uso

### 1. Registrar nuevo empleado
**Actor:** Jefe RRHH  
**Descripción:** Permite ingresar los datos de un nuevo empleado al sistema.  
**Objetivo:** Incorporar nuevos registros al sistema de RRHH.

---

### 2. Actualizar datos personales  
**Actor:** Empleado  
**Descripción:** El empleado puede modificar sus datos personales, como dirección, teléfono, etc.

---

### 3. Gestionar licencias y ausencias  
**Actores:** Empleado, Jefe RRHH  
**Descripción:** Permite la solicitud, aprobación y seguimiento de licencias, permisos y ausencias.

---

### 4. Procesar novedades de sueldo  
**Actor:** Jefe RRHH  
**Descripción:** Registra ajustes salariales, bonificaciones o deducciones.  
**Integración:** Envía datos al **Sistema de Planilla** para el cálculo de sueldos.

---

### 5. Generar reportes de personal  
**Actor:** Jefe RRHH  
**Descripción:** Permite obtener reportes consolidados del personal y su situación laboral.

---

## 🔄 Flujo de Comunicación

- El **Jefe RRHH** interactúa con los casos de uso administrativos y de control.
- El **Empleado** puede actualizar su información y gestionar permisos.
- El **Sistema de Planilla** recibe datos directamente desde el caso de uso *Procesar novedades de sueldo*.

---

## 🧩 Diagrama de Casos de Uso

> El siguiente diagrama muestra las relaciones entre los actores y los casos de uso:

```plantuml
@startuml
left to right direction
skinparam packageStyle rectangle

actor "Empleado" as Empleado
actor "Jefe RRHH" as RRHH
actor "Sistema de Planilla" as Planilla

package "Módulo de RRHH" {
    
    usecase "Registrar nuevo empleado" as UC1
    usecase "Actualizar datos personales" as UC2
    usecase "Gestionar licencias y ausencias" as UC3
    usecase "Procesar novedades de sueldo" as UC4
    usecase "Generar reportes de personal" as UC5
}

RRHH --> UC1
RRHH --> UC3
RRHH --> UC4
RRHH --> UC5

Empleado --> UC2
Empleado --> UC3

UC4 --> Planilla : <<envía datos>>
@enduml
