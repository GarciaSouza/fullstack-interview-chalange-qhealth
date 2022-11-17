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

NodeJs・![Golang](https://img.shields.io/badge/go-%2300ADD8.svg?style=for-the-badge&logo=go&logoColor=white)・Python・![Dart](https://img.shields.io/badge/dart-%230175C2.svg?style=for-the-badge&logo=dart&logoColor=white)・![Flutter](https://img.shields.io/badge/Flutter-%2302569B.svg?style=for-the-badge&logo=Flutter&logoColor=white)・![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)・VanillaJs・CSS・SASS・LESS・HTML5・MongoDB・SQLite・MemCache・Redis・Material UI・Bootstrap・Foundation

## Persona

- Consultorio
  - Nome: QHealth
  - Atendimento: Seg-Sab dás 08h00min ás 19h00min
  
- Paciente
  - Nome: Elon Musk
  - WhatsApp: +447975777666
  - Email: elon.musk@spacex.com
  
- Profissional
  - Nome: Dr. Albert Einstein
  - Especialidade: Endocrinologista
  - Tempo de atendimento: 1h
  - Atendimento: Seg-Sex dás 09h00min ás 18h00min


## História do usuário
```cucumber
#language: pt-BR

Funcionalidade: Agendamento de consulta
 "Eu, como paciente do consultório QHealth, quero agendar uma consulta com o profissional da minha escolha, 
 para evitar que eu ligue ou vá ao consultorio para esse agendamento. 
 Assim, fazendo com que evite filas ou fique muito tempo no telefone."
 
 Cenario: Agendamento realizado com sucesso
 Cenario: Falha ao agendar um horário não disponivel
 
Funcionalidade: Cancelamento de consulta
  "Eu, como paciente do consultório QHealth, quero cancelar uma consulta com o profissional da minha escolha, 
 para evitar que eu ligue ou vá ao consultorio para esse agendamento. 
 Assim, fazendo com que evite filas ou fique muito tempo no telefone."
 
 Cenario: Cancelamento realizado com sucesso
 Cenario: Falha ao cancelar devido ao prazo permitido expirado

Funcionalidade: Reagendamento de consulta
  "Eu, como paciente do consultório QHealth, quero reagendar uma consulta com o profissional da minha escolha, 
 para evitar que eu ligue ou vá ao consultorio para esse agendamento. 
 Assim, fazendo com que evite filas ou fique muito tempo no telefone."
 
 Cenario: Reagendamento realizado com sucesso
 Cenario: Falha ao reagendar um horário não disponivel
 Cenario: Falha ao reagendar devido ao prazo permitido expirado
 
Funcionalidade: Listagem de consultas agendadas
  "Eu, como paciente do consultório QHealth, quero ver todas as consultas que eu tenha agendada, 
 para evitar que eu ligue ou vá ao consultorio para verificar a minha agenda. 
 Assim, fazendo com que evite filas ou fique muito tempo no telefone."
 
 Cenario: Listagem realizada com sucesso
 Cenario: Sem agendas para serem listadas
```


