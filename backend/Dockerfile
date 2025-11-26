<<<<<<< HEAD
FROM dart:stable AS build

WORKDIR /app

# Copia os arquivos de dependências
COPY pubspec.* ./
RUN dart pub get

# Copia todo o código
COPY . .

# Compila o servidor
RUN dart compile exe bin/server.dart -o server

# Imagem final
FROM debian:bullseye-slim

WORKDIR /app

# Copia o binário compilado
COPY --from=build /app/server /app/server

# Cria o diretório de dados
RUN mkdir -p /app/data

# Expõe a porta (Railway vai usar a variável PORT)
EXPOSE 8080

# Executa o servidor
=======
# Use a imagem oficial do Dart
FROM dart:stable AS build

# Diretório de trabalho
WORKDIR /app

# Copie os arquivos do projeto
COPY pubspec.* ./
RUN dart pub get

COPY . .

# Compile o projeto
RUN dart compile exe bin/server.dart -o server

# Imagem final menor
FROM scratch
COPY --from=build /runtime/ /
COPY --from=build /app/server /app/

# Exponha a porta (ajuste se necessário)
EXPOSE 8080

# Execute o servidor
>>>>>>> e95bd29 (Add Dockerfile for Railway deployment)
CMD ["/app/server"]