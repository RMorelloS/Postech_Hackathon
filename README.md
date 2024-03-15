# Postech_Hackathon

A entrega do hackathon seguiu o diagrama de classes apresentado abaixo:

![Diagrama_classes_hackathon](https://github.com/RMorelloS/Postech_Hackathon/assets/32580031/66475f44-5303-46c5-9047-4f0d807b90a4)

Para esta entrega, foram desenvolvidos 4 microsserviços principais:

## 1. Gestão de pessoas
Cadastro, visualização, atualização e exclusão de pessoas

## 2. Gestão de itens e serviços opcionais:
Cadastro, visualização, atualização e exclusão de itens/serviços opcionais

## 3. Gestão de localidades/prédios/quartos
Cadastro, visualização, atualização e exclusão de localidades, prédios e quartos

## 4. Gestão de reservas
Validação das reservas (intersecção com outras reservas, validação dos itens/quartos solicitados)
Cadastro, visualização, atualização e exclusão de reservas
Envio de e-mail com confirmação da reserva

Para tanto, considerou-se as seguintes cardinalidades:

1. Uma pessoa pode realizar uma ou mais reservas (1:N)
2. Uma localidade possui um ou mais prédios (1:N)
3. Um prédio possui um ou mais quartos (1:N)
4. Uma reserva possui um ou mais quartos (1:N)
5. Uma reserva possui um ou mais serviços opcionais (1:N)



