# Menggunakan image dasar Node.js versi 18 dengan varian "slim" (versi ringan)
FROM node:18-slim  

# Menetapkan direktori kerja di dalam container ke "/usr/src/app"
WORKDIR /usr/src/app  

# Menyalin file package.json dan yarn.lock ke dalam container
COPY package.json yarn.lock ./  

# Menginstal dependencies dalam mode produksi (tanpa devDependencies)
RUN yarn install --production  

# Menyalin seluruh isi proyek ke dalam container
COPY . .  

# Membuka port 5000 untuk menerima request dari luar container
EXPOSE 5000  

# Menjalankan aplikasi dengan menjalankan "index.js" menggunakan Node.js
CMD [ "node", "index.js" ]
