#Etapa 1: Construcción de los recursos
FROM node:20 AS build

# Establecemos el directorio de trabajo
WORKDIR /app

# Copiamos los archivos de dependencias
COPY package*.json ./

# Instalar las dependencias
RUN npm install

# Copiamos todo el proyecto
COPY . .

# /dist es la carpeta por defecto que sirve nginx
# /build es la carpeta por defecto que crea React
RUN npm run build


#/********************************************/
#Etapa 2: Construcción de la imagen final
FROM nginx:alpine

# Copiamos los archivos construidos en la etapa anterior a la carpeta por defecto de nginx
COPY --from=build /app/dist /usr/share/nginx/html

# Exponemos el puerto 80
EXPOSE 80

# Comando por defecto
CMD ["nginx", "-g", "daemon off;"]

#/********************************************/