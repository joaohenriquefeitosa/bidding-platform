# Dockerfile para Vue.js
FROM node:18

# Criar diretório de trabalho
WORKDIR /app

# Copiar dependências
COPY package*.json ./

# Instalar dependências
RUN npm install

# Copiar o código-fonte
COPY . .

# Expor a porta 8080
EXPOSE 8080

# Executar o servidor de desenvolvimento
CMD ["npm", "run", "dev"]
