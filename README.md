# Control de Expedientes — Compraventa de inmueble

Aplicación interna de la **Notaría Pública 41 (Nayarit)** para dar seguimiento a los expedientes de compraventa, de modo que no se pase ningún plazo ni término.

Hecha en un curso/hackatón de Claude para abogados, con Claude Code.

## Qué hace
1. **Alta del expediente con sus variables:** vendedor y comprador (persona física o moral), estado civil, comprador extranjero, pago de contado o con crédito hipotecario (banco, INFONAVIT o FOVISSSTE), condominio, zona restringida, origen ejidal, hipoteca previa, apoderado y exención de ISR.
2. **Checklist de requisitos al cliente** generado según esas variables, con las casillas *pedido / recibido / cotejado*. Un botón copia la lista de pendientes, lista para enviar por WhatsApp o correo.
3. **Cronograma antes, durante y después de la firma.** Las fechas límite se calculan a partir de la fecha de alta y de la fecha de firma, y cada tarea tiene un responsable. Si cambia la fecha de firma, todo se recalcula.
4. **Semáforo:** 🔴 vencida · 🟠 vence en 3 días o menos · 🟢 al día.
5. **Agenda global:** lo que vence de todos los expedientes, ordenado por fecha.
6. **Respaldo:** exportar e importar en JSON.

## Cómo usarla
Abrir `index.html` en el navegador. No necesita instalación, servidor ni internet. Para ver un ejemplo, use **Cargar 3 expedientes de ejemplo**.

## Privacidad
Los datos se guardan **solo en el navegador** de quien la usa (localStorage); nada se envía a internet. Use un número interno y un alias o iniciales en lugar de los nombres de los otorgantes, y exporte respaldos con regularidad.

## Sobre los plazos
- **🟡 plazo por verificar:** término legal (ISR, DeclaraNOT, ISABI, LFPIORPI, RPP, SRE/RNIE) que **aún no se ha verificado en fuente oficial**. La fecha es una propuesta editable en cada expediente.
- **práctica interna:** plazo de organización de la notaría, no un término legal.

Las reglas están en `index.html`, en los objetos `REQUISITOS` y `TAREAS`. Cada regla tiene una condición `aplicaSi` y un plazo relativo a la fecha de alta o de firma, así que para agregar o corregir un requisito basta con editar una línea.

## Próximos pasos
- Verificar los plazos 🟡 contra la ley vigente y marcarlos como verificados.
- Agregar otros actos: donación, adjudicación por herencia, poderes, etc.
- Base de datos compartida para todo el equipo y recordatorios en el calendario.
- Un asistente con Claude que revise el expediente y sugiera faltantes.
