# Demo de Componentes Vue

Este proyecto es una demostración de varios componentes de interfaz de usuario utilizando Vue.js, Tailwind CSS y shadcn-vue. Muestra un componente de contador interactivo con múltiples características y opciones de estilo.

## Descripción General del Proyecto

El componente principal `ComponentDemo.vue` demuestra el uso de varios componentes de interfaz de usuario de la biblioteca shadcn-vue, integrados con la API de Composición de Vue 3 y Tailwind CSS para el estilo.

### Características

- Contador interactivo con botones de incremento y decremento
- Entrada numérica para manipulación directa del contador
- Interruptor para resaltar números pares
- Botón de aleatorización para establecer un conteo aleatorio
- Alertas dinámicas basadas en hitos del contador
- Diseño responsivo utilizando Tailwind CSS

## Componentes Utilizados

1. **Card**: Componente contenedor para toda la demostración
    - CardHeader
    - CardTitle
    - CardDescription
    - CardContent
    - CardFooter

2. **Button**: Utilizado para acciones de incremento, decremento y aleatorización

3. **Input**: Entrada numérica para el contador

4. **Switch**: Interruptor para resaltar números pares

5. **Alert**: Muestra mensajes de hitos
    - AlertTitle
    - AlertDescription

6. **Label**: Utilizado para etiquetar la entrada del contador y el interruptor

## Estructura del Proyecto

```
.
├── src/
│   ├── components/
│   │   ├── ui/
│   │   │   ├── button.vue
│   │   │   ├── input.vue
│   │   │   ├── switch.vue
│   │   │   ├── alert.vue
│   │   │   ├── card.vue
│   │   │   └── label.vue
│   │   └── ComponentDemo.vue
│   ├── assets/
│   │   └── index.css
│   ├── App.vue
│   └── main.ts
├── public/
├── Dockerfile
├── compose.yaml
├── package.json
├── tailwind.config.js
├── tsconfig.json
├── vite.config.ts
└── README.md
```

## Configuración e Instalación

1. Clonar el repositorio:
   ```shell
   git clone <url-del-repositorio>
   cd demo-componentes-vue
   ```

2. Instalar dependencias:
   ```shell
   npm install
   ```

3. Ejecutar el servidor de desarrollo:
   ```shell
   npm run dev
   ```

4. Compilar para producción:
   ```shell
   npm run build
   ```

## Soporte Docker

Este proyecto incluye soporte para Docker para facilitar el despliegue y desarrollo.

Para construir y ejecutar el contenedor Docker:

1. Construir la imagen Docker:
   ```shell
   docker build -t demo-componentes-vue .
   ```

2. Ejecutar el contenedor:
   ```shell
   docker run -p 8080:8080 demo-componentes-vue
   ```

Alternativamente, puedes usar Docker Compose:

```shell
docker-compose up
```


## Personalización

- Tailwind CSS: El proyecto utiliza una configuración personalizada de Tailwind. Puedes modificar el tema en `tailwind.config.js`.
- Componentes: Los componentes de shadcn-vue se encuentran en `src/components/ui/`. Puedes personalizar estos componentes o agregar nuevos según sea necesario.

## Dependencias

- Vue.js 3
- Vite
- TypeScript
- Tailwind CSS
- Componentes shadcn-vue
- lucide-vue-next (para iconos)
