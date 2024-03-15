# Postech_Hackathon

## Ricardo Morello Santos - RM 349844

A entrega do hackathon seguiu o diagrama de classes apresentado abaixo:

![Diagrama_classes_hackathon](https://github.com/RMorelloS/Postech_Hackathon/assets/32580031/66475f44-5303-46c5-9047-4f0d807b90a4)


Para tanto, considerou-se as seguintes cardinalidades:

1. Uma pessoa pode realizar uma ou mais reservas (1:N)
2. Uma localidade possui um ou mais prédios (1:N)
3. Um prédio possui um ou mais quartos (1:N)
4. Uma reserva possui um ou mais quartos (1:N)
5. Uma reserva possui um ou mais serviços opcionais (1:N)


Para esta entrega, foram desenvolvidos 4 microsserviços principais:

## 1. Gestão de pessoas

Link para o repositório específico do serviço de gestão de pessoas: <https://github.com/RMorelloS/Hackathon_gestaopessoas>

Cadastro, visualização, atualização e exclusão de pessoas

## 2. Gestão de itens e serviços opcionais:

Link para o repositório específico do serviço de gestão de itens/serviços opcionais: <https://github.com/RMorelloS/Hackathon_gestaoitensservicos>

Cadastro, visualização, atualização e exclusão de itens/serviços opcionais

## 3. Gestão de localidades/prédios/quartos

Link para o repositório específico do serviço de gestão de localidades/prédios/quartos: <https://github.com/RMorelloS/Hackathon_gestaolocalidades>

Cadastro, visualização, atualização e exclusão de localidades, prédios e quartos

## 4. Gestão de reservas

Link para o repositório específico do serviço de gestão de reservas: <https://github.com/RMorelloS/Hackathon_gestaoreservas>

Validação das reservas (intersecção com outras reservas, validação dos itens/quartos solicitados)

Cadastro, visualização, atualização e exclusão de reservas

Envio de e-mail com confirmação da reserva. O e-mail gerado é semelhante ao print abaixo:

![image](https://github.com/RMorelloS/Postech_Hackathon/assets/32580031/17707f7d-d289-4502-9196-cd521a992f36)



# Tecnologias utilizadas
Foram utilizadas as seguintes ferramentas:

1. Spring boot
2. PostgreSQL
3. Validação com Hybernate
4. Docker

Todos os microsserviços acompanham um arquivo Dockerfile. Para gerar a imagem, basta aplicar os comandos:

```bash
docker build -t gestaoreservas:latest .
docker build -t gestaoitensservicos:latest .
docker build -t gestaopessoas:latest .
docker build -t gestaolocalidades:latest .
```

Em seguida, o arquivo docker-compose abaixo permite executar todas as imagens e a base de dados postgresql:

```bash
services:
  api1:
    image: 'gestaoreservas:latest'
    container_name: gestaoreservas
    ports:
      - "8084:8084"
    depends_on:
      - db

  api2:
    image: 'gestaolocalidades:latest'
    container_name: gestaolocalidades
    ports:
      - "8083:8083"
    depends_on:
      - db

  api3:
    image: 'gestaoitensservicos:latest'
    container_name: gestaoitensservicos
    ports:
      - "8082:8082"
    depends_on:
      - db

  api4:
    image: 'gestaopessoas:latest'
    container_name: gestaopesssoas
    ports:
      - "8081:8081"
    depends_on:
      - db

  db:
    image: 'postgres:13.1-alpine'
    container_name: dbhackathon
    environment:
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=hack2024
```
