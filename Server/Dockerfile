FROM node:18

WORKDIR /app

COPY package*.json ./

# Clean install without copying node_modules
RUN npm install

COPY . .

# Rebuild bcrypt to match the Linux environment
RUN npm rebuild bcrypt --build-from-source

EXPOSE 3001
CMD ["node", "app.js"]
