# Desafio para entrevista de fullstack

Esse desafio visa avaliar o pensamento lógico, resolução de problemas, conhecimento em estrutura de dados, qualidade de código e utilização de testes. O mesmo deve ser realizado seguindo a lista de tecnologias permitidas. Não necessáriamente deve-se usar todas. 

Ele deve ser entregue em até 7 dias corridos, contato a partir da entrevista.

## Como realizar o projeto?
Deve ser feito uma fork desse projeto e deve ser criando uma branch com o nome do seu id no github. Após o desenvolvimento, deve se disponibilizar um Dockerfile para cada projeto, back e front, e um arquivo docker-compose.yml disponibilizando a stack para que possamos subir em um dos nossos ambientes para testá-lo.

os projetos devem ficar em suas respectivas pastas: front e back, seguindo o modelo monorepo.

### O que vamos avaliar
Avaliaremos com espero as seguintes caracteristicas do desenvolvimento: 
 - Aderência a história do usuário
 - Qualidade de código: Good Smell, testes, scream arch, yagni, dry entre outras boas práticas
 - Aplicabilidade de conhecimentos em estrutura de dados: Árvore, Listas, Pilhas entre outros
 - Aplicabilidade de conhecimentos relacionados a sorts, map, reduce. *Se realizado na mão, será considerado diferencial*
 - Utilização de padrões como MVVM, entre outros para desenvolvimento do front.


---

# O Projeto

O projeto trata-se de um microapp de agendamento a onde o paciente vai selecionar um profissional da clinica e realizar um agendamento de uma consulta. O app deve ser dividido em uma API fornecida por um backend e um frontend.

### Stack
você pode usar quaisquer dessas tecnologias para realizar os projetos:

![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white) ![Golang](https://img.shields.io/badge/go-%2300ADD8.svg?style=for-the-badge&logo=go&logoColor=white) ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Dart](https://img.shields.io/badge/dart-%230175C2.svg?style=for-the-badge&logo=dart&logoColor=white) ![Flutter](https://img.shields.io/badge/Flutter-%2302569B.svg?style=for-the-badge&logo=Flutter&logoColor=white) ![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)・![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white) 
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)
![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white)・SASS・LESS・MongoDB・SQLite・MemCache・![Redis](https://img.shields.io/badge/redis-%23DD0031.svg?style=for-the-badge&logo=redis&logoColor=white) 
![MUI](https://img.shields.io/badge/MUI-%230081CB.svg?style=for-the-badge&logo=mui&logoColor=white)・Bootstrap・Foundation

## Persona

```yml

Consultorio:
  Nome: QHealth
  Atendimento: Seg-Sab dás 08h00min ás 19h00min
  Especialidades: 
    - Endocrinologista
    - Clínico Geral
    - Nutricionista
---
Paciente:
  Nome: Elon Musk
  WhatsApp: +447975777666
  Email: elon.musk@spacex.com
---  
Profissional:
  Nome: Dr. Albert Einstein
  Especialidade: Endocrinologista
  Tempo de atendimento: 1h
  Limite para cancelamento: 1h antes da consulta
  Atendimento: 
    - Seg. das 09h00min ás 18h00min
    - Qua. das 11h00min ás 13h00min
    - Sex. das 10h00min ás 19h00min
    - Sab. das 08h00min ás 10h00min
  
---
```

## História do usuário
```gherkin
# language: pt-BR

Funcionalidade: Agendamento de consulta
  Eu, como paciente do consultório QHealth, quero agendar uma consulta com o profissional da minha escolha, 
  para evitar que eu ligue ou vá ao consultorio para esse agendamento. 
  Assim, fazendo com que evite filas ou fique muito tempo no telefone.

  Cenário: Agendamento realizado com sucesso
    DADO que eu seja um paciente
    E que eu escolha a especialidade do profissional
    E escolha o profissional
    E que eu tenha acesso a agenda do profissional
    E que eu escolha uma data e horario para a consulta
    E que essa data e horário esteja disponível
    E que esteja dentro do horário de atendimento do profissional
    QUANDO agendado a consulta
    ENTÃO inclua o meu agendamento na agenda do profissional
    E inclua o meu nome ao agendamento
    E include meu número de Whatapp ao agendamento
    E inclua o meu email ao agendamento


  Cenário: Falha ao agendar um horário não disponivel
    DADO que eu seja um paciente
    E que eu escolha a especialidade do profissional
    E escolha o profissional
    E que eu tenha acesso a agenda do profissional
    E que eu escolha uma data e horario para a consulta
    E que esteja dentro do horário de atendimento do profissional
    E que esta data esteja indisponível
    QUANDO agendado a consulta
    ENTÃO não inclua o meu agendamento na agenda do profissional
    E informe-me que essa data está indisponível

  Cenário: Falha ao agendar um horário não disponivel
    DADO que eu seja um paciente
    E que eu escolha a especialidade do profissional
    E escolha o profissional
    E que eu tenha acesso a agenda do profissional
    E que eu escolha uma data e horario para a consulta
    E que esteja fora do horário de atendimento do profissional
    QUANDO agendado a consulta
    ENTÃO não inclua o meu agendamento na agenda do profissional
    E informe que o profissional não atende nesse horário

Funcionalidade: Cancelamento de consulta
  Eu, como paciente do consultório QHealth, quero cancelar uma consulta com o profissional da minha escolha, 
  para evitar que eu ligue ou vá ao consultorio para esse agendamento. 
  Assim, fazendo com que evite filas ou fique muito tempo no telefone.

  Cenário: Cancelamento realizado com sucesso
    DADO que eu seja um paciente
    E que eu tenha uma consulta agendada
    E que esteja no periodo de cancelamento aceito pelo médico
    QUANDO solicitado o cancelamento
    ENTÃO então remova a consulta da agenda do médico
    E remova os meus dados
    E informe-me que o cancelamento foi realizado


Cenario: Falha ao cancelar devido ao prazo permitido expirado
    Cenário: Cancelamento realizado com sucesso
    DADO que eu seja um paciente
    E que eu tenha uma consulta agendada
    E que esteja forma no periodo de cancelamento aceito pelo médico
    QUANDO solicitado o cancelamento
    ENTÃO não remova o agendamento
    E inclua uma observação de solicitação de cancelamento recusado
    E informe-me que não foi possivel cancelar a consulta devido ao limite permitido
    E informe o limite

Funcionalidade: Reagendamento de consulta
  Eu, como paciente do consultório QHealth, quero reagendar uma consulta com o profissional da minha escolha, 
  para evitar que eu ligue ou vá ao consultorio para esse agendamento. 
  Assim, fazendo com que evite filas ou fique muito tempo no telefone.

  Cenario: Reagendamento realizado com sucesso
    DADO que eu seja um paciente
    E que eu tenha uma consulta agendada
    E que esteja no periodo permitido de reagendamento aceito pelo médico
    E que o horário que eu escolha esteja disponível
    QUANDO solicitado o reagendamento
    ENTÃO então remova a consulta anterior da agenda do médico
    E remova os meus dados da consulta anterior
    E inclua o meu agendamento na agenda do profissional
    E inclua o meu nome ao agendamento
    E includa meu número de Whatapp ao agendamento
    E inclua o meu email ao agendamento
    E inclua uma observação de consulta reagendada
    E informe-me que o reagendamento foi realizado
    


  Cenario: Falha ao reagendar um horário não disponivel
    DADO que eu seja um paciente
    E que eu tenha uma consulta agendada
    E que esteja no periodo permitido de reagendamento aceito pelo médico
    E que o horário que eu escolhi não esteja disponivel
    QUANDO solicitado o reagendamento
    ENTÃO informe que o horário não está disponível e informe para selecionar outra data
    E não realize o agendamento

  Cenario: Falha ao reagendar devido ao prazo permitido expirado
    DADO que eu seja um paciente
    E que eu tenha uma consulta agendada
    E que esteja não periodo permitido de reagendamento aceito pelo médico
    E que o horário que eu escolha esteja disponível
    QUANDO solicitado o reagendamento
    ENTÃO informe que não há mais como reagendar devido ao limite para reagendamento
    E não realize o reagendamento
    
    
Funcionalidade: Listagem de consultas agendadas
  Eu, como profissional do consultório QHealth, quero ver todas as consultas que eu tenha agendada, para que eu me organize antes de cada consulta.

  Cenario: Listagem realizada com sucesso
    DADO que eu seja profissional de saúde
    E que eu tenha consultas em minha agenda
    QUANDO solicitar para ver a minha agenda
    ENTÃO mostrar a agenda da semana com todas as consultas agendadas

  Cenario: Sem agendas para serem listadas
    DADO que eu seja profissional de saúde
    E que eu não tenha consultas em minha agenda
    QUANDO solicitar para ver a minha agenda
    ENTÃO infome que eu não possuo agendamentos
```


