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
- **🟢 verificado** (con su artículo), verificado el 31-oct-2026 contra el texto vigente:
  - Entero de ISR y DeclaraNOT: 15 días **hábiles** siguientes a la firma (LISR arts. 126 y 132; CFF art. 12).
  - Aviso LFPIORPI: a más tardar el día 17 del mes siguiente (LFPIORPI art. 23).
  - Aviso a catastro: 15 días hábiles (Ley de Catastro de Nayarit, arts. 34-II y 36).
  - Avisos preventivos: el primero vence a los 30 días naturales; el definitivo se presenta después de la firma, dentro de esa vigencia, y dura 90 días naturales para inscribir (Ley del RPP de Nayarit, art. 91). La app avisa si la firma cae fuera de la vigencia del primer aviso.
  - Extranjeros (Ley de Inversión Extranjera): en zona restringida (100 km de fronteras, 50 km de playas; art. 2-VI) no pueden adquirir el dominio, así que la compraventa se formaliza con fideicomiso: permiso SRE a la fiduciaria (arts. 11 y 14) e inscripción en el RNIE dentro de 40 días hábiles (art. 32-III). Fuera de esa zona, convenio y permiso de la SRE (art. 10-A).
- **🟡 plazo por verificar:** ISABI (ley municipal) y CFDI de retenciones. La fecha es una propuesta editable.
- **práctica interna:** plazo de organización de la notaría, no un término legal.

Los días inhábiles se calculan según el art. 12 del CFF: fines de semana y días festivos oficiales.

## Requisitos
Se basan en la lista oficial de la notaría, «Requisitos escrituras_Not 41» (actos traslativos de dominio), con su misma redacción. Los requisitos que no están en esa lista y que la app agrega según las variables (cónyuge en sociedad conyugal, crédito, condominio, extranjero, ejidal, beneficiario controlador) aparecen marcados como **propuesta**, pendientes de validar.

Las reglas están en `index.html`, en los objetos `REQUISITOS` y `TAREAS`. Cada regla tiene una condición `aplicaSi` y un plazo relativo a la fecha de alta o de firma, así que para agregar o corregir un requisito basta con editar una línea.

## Próximos pasos
- Verificar los plazos 🟡 restantes (ISABI municipal, RMF) y el Reglamento de la LIE.
- Agregar otros actos: donación, adjudicación por herencia, poderes, etc.
- Base de datos compartida para todo el equipo y recordatorios en el calendario.
- Un asistente con Claude que revise el expediente y sugiera faltantes.
