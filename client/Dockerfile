# Menggunakan image dasar Node.js versi 14 dengan varian "slim" (versi ringan)
FROM node:14-slim  

# Menetapkan direktori kerja di dalam container ke "/usr/src/app"
WORKDIR /usr/src/app  

# Menyalin file package.json dan yarn.lock ke dalam container
COPY package.json yarn.lock ./  

# Menjalankan instalasi dependencies menggunakan Yarn
RUN yarn install  

# Menyalin seluruh isi proyek ke dalam container
COPY . .  

# Membangun aplikasi React (menghasilkan folder "build")
RUN yarn build  

# Menginstal "serve" secara global untuk menyajikan aplikasi React yang sudah dibangun
RUN yarn global add serve  

# Menjalankan perintah "serve" untuk menyajikan folder "build" pada port 3000
CMD ["serve", "-s", "build", "-l", "3000"]
