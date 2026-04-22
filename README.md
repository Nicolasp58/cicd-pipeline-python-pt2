# cicd-pipeline-python-pt2
## Staging ALB URL: http://calculadora-staging-alb-943589044.us-east-1.elb.amazonaws.com/

## Production ALB URL: http://calculadora-production-alb-2127964815.us-east-1.elb.amazonaws.com/
---

## 1. Flujo de trabajo con Terraform

El flujo empieza con un commit que activa el CI, donde se construye la imagen Docker y se sube a Docker Hub. Luego Terraform crea o actualiza la infraestructura en Staging, se despliega la imagen y se hacen pruebas. Si todo pasa, se hace lo mismo en producción y se ejecutan pruebas rápidas para verificar que el servicio funciona.

---

## 2. Terraform vs despliegue manual

Las ventajas son que todo queda automatizado y se puede repetir fácilmente y que queda versionado en código. Una desventaja es que al inicio es más complejo y cualquier error en el código puede afectar toda la infraestructura. Definirlo al principio fue un poco confuso, pero luego se entiende todo más fácil.

---

## 3. Uso de Staging

Staging ayuda a probar antes de ir a producción, reduciendo errores y riesgos. La desventaja es que agrega más pasos y puede hacer el proceso un poco más lento. Básicamente mejora la seguridad, pero reduce un poco la velocidad.

---

## 4. Test Staging vs Smoke Test Producción

En Staging se hacen pruebas más completas para validar que todo funcione bien. En Producción solo se hace un smoke test para confirmar que la app está funcionando. Esto es porque en producción no se quiere afectar a los usuarios.

---

## 5. Qué le falta al pipeline

De las partes que vimos en el ciclo le puede faltar monitoreo como logs y métricas para saber si algo falla después del despliegue o ver cual es el desempeño real. También se podrían agregar pruebas de seguridad, como escaneo de vulnerabilidades en la imagen Docker. Esto ayudaría a tener un sistema más confiable.

---

## 6. Experiencia implementando

Fue un poco difícil al inicio, pero útil porque automatiza todo el proceso. CI/CD ayuda mucho porque evita hacer despliegues manuales y reduce errores. Lo más difícil fue la complejidad inicial y entender todas las herramientas.