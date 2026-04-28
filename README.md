# 📊 PlanFinanciero

**Herramienta integral de planificación financiera personal desarrollada para asesores financieros independientes.**

[![Tecnología](https://img.shields.io/badge/React-HTML5-blue.svg)](https://reactjs.org/)
[![Licencia](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Estado](https://img.shields.io/badge/Estado-Producción-brightgreen.svg)]()

---

## 🚀 Descripción

PlanFinanciero es una aplicación web standalone que permite a los asesores financieros crear planes financieros personalizados para sus clientes. La herramienta cubre análisis de gastos/ingresos, planificación de objetivos, simulación de jubilación, análisis hipotecario, balance patrimonial y gestión de riesgos.

**Características principales:**
- ✅ **Sistema de acceso seguro** con tokens únicos + PIN de 4 dígitos por cliente
- ✅ **8 módulos de análisis financiero** completos
- ✅ **Envío automático de informes** vía email al asesor
- ✅ **Simulación de hipotecas** con 3 sistemas de amortización (Francés, Alemán, Americano)
- ✅ **Análisis de seguros** y riesgos de invalidez
- ✅ **Planificación de jubilación** con proyecciones actuariales
- ✅ **Balance patrimonial detallado** con análisis de liquidez

---

## 🎯 Casos de Uso

### Para Asesores Financieros
- Creación de planes financieros personalizados
- Análisis integral de la situación patrimonial del cliente  
- Simulaciones de escenarios (jubilación, invalidez, shocks)
- Informes profesionales automatizados
- Gestión de múltiples clientes simultáneos

### Para Clientes
- Autoevaluación financiera guiada
- Establecimiento de objetivos financieros
- Simulación de estrategias de ahorro e inversión
- Análisis de necesidades de seguros
- Envío seguro de información al asesor

---

## 🛠️ Tecnología

- **Frontend**: React 18.2 (standalone, sin build)
- **Estilos**: CSS nativo con variables personalizadas
- **Matemáticas**: Implementación nativa de funciones financieras (PMT, PV, FV, etc.)
- **Persistencia**: localStorage (datos locales por cliente)
- **Email**: Integración con Formsubmit.co (sin servidor)
- **Deploy**: HTML estático (GitHub Pages, Netlify, etc.)

---

## 📖 Módulos Incluidos

| Módulo | Descripción | Funcionalidades clave |
|--------|-------------|------------------------|
| **📊 Gastos e Ingresos** | Análisis del cash flow mensual | Categorización, tasa de ahorro, fondo de emergencia |
| **🎯 Objetivos** | Planificación de metas financieras | Cálculo de PMT, VF con inflación, priorización |
| **🏖️ Jubilación** | Simulación actuarial de pensión | Déficit de cobertura, SWR, rentabilidades diferenciadas |
| **🏠 Hipotecas** | Análisis de financiación inmobiliaria | 3 sistemas de amortización, LTV, DSR, prepagos |
| **📈 Panel Financiero** | Dashboard consolidado | KPIs principales, alertas, ratios de salud financiera |
| **🏛️ Balance Patrimonial** | Inventario de activos y pasivos | Análisis de liquidez, diversificación, apalancamiento |
| **🛡️ Seguros** | Análisis de coberturas | Déficits de vida/invalidez, optimización de primas |
| **⚠️ Riesgo Invalidez** | Simulación de incapacidad laboral | VP de pérdida económica, recomendaciones de cobertura |

---

## 🔧 Instalación y Configuración

### Opción 1: GitHub Pages (Recomendado)
1. **Crear repositorio público** en GitHub
2. **Subir** `PlanFinanciero.html` al repositorio
3. **Activar GitHub Pages** en Settings → Pages → Deploy from branch: `main`
4. **URL disponible** en: `https://tu-usuario.github.io/tu-repositorio/PlanFinanciero.html`

### Opción 2: Netlify Drop
1. Ir a [app.netlify.com/drop](https://app.netlify.com/drop)
2. Arrastrar `PlanFinanciero.html` al navegador
3. URL instantánea disponible

### Opción 3: Servidor local
```bash
# Servidor Python simple
python -m http.server 8000

# O con Node.js
npx serve .
```

---

## 📧 Configuración de Email

La aplicación usa **Formsubmit.co** para envío directo de informes:

1. **Primera vez**: Un cliente envía el informe → recibes email de confirmación de Formsubmit
2. **Confirmar**: Pulsa "Confirm email" en ese primer email
3. **Listo**: Todos los envíos posteriores llegan automáticamente a tu bandeja

**Sin configuración previa** — Sin API keys — Sin cuentas que mantener

---

## 🔒 Seguridad y Privacidad

### Modelo de Seguridad
- **Tokens UUID v4**: 2^122 combinaciones posibles (~imposible de adivinar)
- **PIN de 4 dígitos**: Enviado por canal separado (WhatsApp, llamada)
- **Rate limiting**: Máximo 5 intentos de PIN cada 5 minutos
- **Datos locales**: Información almacenada solo en el navegador del cliente
- **Sin servidor central**: No hay base de datos que comprometer

### Cumplimiento Regulatorio
- **RGPD**: Compatible con modelo de "Excel digital"
- **MiFID II**: Herramienta del asesor para uso 1-a-1
- **LSSI**: Requiere aviso legal si se publica públicamente
- **Encargado del tratamiento**: Contrato con proveedor de email (Gmail/Formsubmit)

---

## 🎛️ Guía de Uso

### Para el Asesor
1. **Abrir** la aplicación sin parámetros → Panel del asesor
2. **Crear cliente** → Se genera link único + PIN automáticamente
3. **Enviar link** por un canal (email) y **PIN por otro** (WhatsApp)
4. **Recibir informe** cuando el cliente pulse "Enviar a mi asesor"

### Para el Cliente
1. **Abrir link** recibido del asesor
2. **Introducir PIN** de 4 dígitos
3. **Completar** las 8 hojas del plan financiero
4. **Enviar** resumen al asesor en un clic

### Formato del Informe
El asesor recibe un **informe visual tipo "captura de pantalla"** de las 8 hojas con:
- KPIs destacados en cajas formatadas
- Tablas con bordes ASCII profesionales  
- JSON completo para reimportación de datos
- Recomendaciones específicas por módulo

---

## 📊 Funciones Matemáticas

Implementación nativa de matemáticas financieras:

```javascript
// Ejemplos de funciones disponibles
F.pmt(rate, nper, pv)           // Pago periódico
F.pv(rate, nper, pmt)           // Valor presente
F.fv(rate, nper, pmt, pv)       // Valor futuro
F.pmtFV(rate, nper, fv, pv)     // PMT para alcanzar VF objetivo
F.pvAnnuity(rate, years, pmt)   // VP de anualidad
F.amortScheduleByType(tipo, capital, rate, years) // Cuadros de amortización
```

Sistemas de amortización soportados:
- **Francés**: Cuota constante (estándar en España)
- **Alemán**: Capital constante, cuota decreciente
- **Americano**: Solo intereses + bullet final

---

## 🤝 Contribuciones

Este proyecto está optimizado para asesores financieros. Las contribuciones son bienvenidas:

1. **Fork** del repositorio
2. **Crear branch** de feature (`git checkout -b feature/nueva-funcionalidad`)
3. **Commit** cambios (`git commit -am 'Añadir nueva funcionalidad'`)
4. **Push** al branch (`git push origin feature/nueva-funcionalidad`)
5. **Crear Pull Request**

---

## 📄 Licencia

MIT License - Ver archivo [LICENSE](LICENSE) para más detalles.

---

## 👨‍💼 Autor

**Iker Lainach**  
Asesor Financiero Independiente | CFA Level III Candidate | EFA

*Desarrollado para optimizar la relación asesor-cliente en planificación financiera personal.*

---

## 🆘 Soporte

Para soporte técnico o consultas sobre la herramienta:
- **Issues**: [GitHub Issues](../../issues)
- **Email**: ikerlainach@gmail.com

---

**⚡ ¿Listo para digitalizar tu asesoramiento financiero?** Despliega PlanFinanciero en menos de 5 minutos y ofrece a tus clientes una experiencia de planificación financiera de nivel institucional.