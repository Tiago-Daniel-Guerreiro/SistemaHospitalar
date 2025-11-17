# Sistema de Gestão Hospitalar

![Language](https://img.shields.io/badge/Python-3.13%2B-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Status](https://img.shields.io/badge/Status-Projeto%20Escolar-brightgreen)

Um sistema de gestão hospitalar desenvolvido em Python, focado na aplicação de princípios de Programação Orientada a Objetos (POO). O projeto modela entidades e processos complexos de um hospital, como o registo de pacientes, a gestão de diferentes tipos de funcionários, a alocação de salas e um sistema avançado de gestão de horários e calculo de pagamentos. A interação é feita através de uma interface de linha de comando (CLI).

Este projeto foi realizado no âmbito da disciplina de Programação e Sistemas de Informação do Curso Técnico De Gestão e Programação De Sistemas Informáticos.

## 🚀 Tecnologias Utilizadas
O projeto foi construído utilizando exclusivamente Python e as suas bibliotecas nativas, com foco na lógica e na arquitetura do software.

## 🎯 Objetivo Principal
O objetivo central foi projetar e implementar um sistema funcional que demonstrasse o domínio e a aplicação prática dos seguintes conceitos de Programação Orientada a Objetos:~
- **Classes Abstratas:** Para criar "contratos" e modelos base (`Pessoa`, `Sala`).
- **Herança Simples e Múltipla:** Para criar especializações (`Medico` herda de `Funcionario`) e combinar papéis (`EnfermeiroChefe` herda de `Enfermeiro` e `Administrativo`).
- **Polimorfismo:** Para permitir que o sistema trate objetos de diferentes classes de forma homogénea (ex: calcular pagamentos ou exibir detalhes de diferentes funcionários com a mesma chamada de método).
- **Encapsulamento:** Para proteger os dados internos e garantir a sua integridade através de _properties_ e _setters_ com regras de validação.
- **Modularização:** Para organizar o código em módulos com responsabilidades distintas, promovendo a coesão e o baixo acoplamento.

## ❓ O Problema
A gestão de um ambiente hospitalar é uma tarefa de alta complexidade que envolve a coordenação de múltiplos elementos: o fluxo de pacientes, a alocação de recursos físicos como salas, a gestão de uma equipa diversificada de profissionais e o cálculo de remunerações que variam conforme o cargo, o turno e o desempenho. A criação de um sistema digital para gerir estas operações exige uma modelação de dados que reflita estas complexidades e interações.

## ✔️ A Solução
Foi desenvolvido um sistema modular em Python, executado via linha de comando, que modela as operações hospitalares através de uma arquitetura coesa e dividida em três camadas principais:
1.  **`Program.py` - O Núcleo do Sistema (Modelo):**
    - Contém a representação de todas as entidades: `Pessoa`, `Paciente`, `Funcionario`, `Sala` e as suas especializações (`Medico`, `Enfermeiro`, `SalaAtendimento`, `SalaCirurgia`).
    - Implementa um sistema de pagamento flexível através do padrão **Strategy**, onde diferentes `RegraDePagamento` (bónus, pagamento por hora, etc.) podem ser dinamicamente adicionadas a um funcionário.
    - Utiliza a classe `SistemaHospital` como um orquestrador central que gere todos os dados em memória.

2.  **`Horario.py` - Gestão Avançada de Tempo:**
    - Um módulo altamente especializado e isolado, responsável por toda a lógica temporal.
    - Modela conceitos como `HoraMinuto`, `IntervaloTempo` e `Pausas`, com validações robustas.
    - Calcula automaticamente o tempo de trabalho diurno e noturno, mesmo em turnos que atravessam a meia-noite.
    - A classe `FuncionarioHorario` atua como uma fachada, simplificando a interação entre um `Funcionario` e a complexa lógica de horários.

3.  **`Console.py` - A Interface do Utilizador (Controlador/Visão):**
    - Responsável por toda a interação com o utilizador através de menus de texto.
    - Traduz as ações do utilizador (ex: "chamar próximo paciente") em chamadas aos métodos dos objetos do modelo.
    - Mantém a lógica de negócio separada da apresentação, permitindo que a interface possa ser substituída no futuro (ex: por uma interface gráfica ou web) com menor impacto.

## 👤 Meu Papel
Este projeto foi desenvolvido em colaboração. Embora tenha tido um papel ativo em todas as fases do projeto, as minhas principais responsabilidades centraram-se na arquitetura e na implementação da lógica de negócio. Fui responsável por:

- Arquitetura e Modelo de Dados: Estruturar o modelo de classes de raiz, definindo a hierarquia de herança, as classes abstratas e a aplicação de polimorfismo, que são o pilar de todo o sistema.

- Desenvolvimento de Componentes Core: Implementar os mecanismos mais complexos, como o motor de cálculo de horários (Horario.py) e o sistema de pagamentos flexível com o padrão Strategy.

- Refatoração e Qualidade de Código: Após uma fase inicial, liderei uma refatoração significativa do código para aumentar a modularidade e garantir o baixo acoplamento entre os módulos (Program, Horario, Console), melhorando a manutenibilidade geral da aplicação.

## ⚙️ Principais Desafios
Durante o desenvolvimento, os desafios mais significativos foram:

- **Gestão da Complexidade Temporal:** Implementar a lógica no `Horario.py` para calcular corretamente as durações e interseções de tempo, especialmente ao lidar com turnos noturnos e pausas, exigiu uma modelação cuidadosa e abstrações bem definidas.
- **Herança Múltipla e Composição:** A criação da classe `EnfermeiroChefe`, que combina as responsabilidades de `Enfermeiro` e `Administrativo`, apresentou um desafio na gestão da inicialização e na combinação de diferentes regras de pagamento, resolvido com uma chamada controlada aos construtores das classes-mãe, e verificação de regras de pagamentos repetidas.
- **Acoplamento vs. Prazo:** Equilibrar a ambição de criar um sistema completo com o tempo disponível resultou em algumas decisões que aumentaram o acoplamento entre certos componentes.

## ✅ Resultados
O projeto resultou num protótipo de sistema de informação hospitalar funcional e modular, que cumpre todos os objetivos académicos propostos.
- **Aplicação Prática de POO:** O sistema é uma demonstração clara e funcional do uso de herança, polimorfismo, encapsulamento e modularização para resolver um problema complexo.
- **Sistema Extensível:** A arquitetura, especialmente o sistema de regras de pagamento, foi projetada para ser facilmente extensível sem necessidade de alterar o código existente.
- **Código Legível e Organizado:** A separação de responsabilidades em três módulos distintos (`Program.py`, `Horario.py`, `Console.py`) torna o código mais fácil de entender, manter e evoluir.

## 🛠️ Como Utilizar
Para executar o sistema, siga os passos abaixo:

1.  Certifique-se de que tem o **Python 3.13** instalado.
2.  Clone este repositório:
    ```bash
    git clone https://github.com/Tiago-Daniel-Guerreiro/Sistema_Hospitalar.git
    ```
3.  Na pasta do projeto execute o ficheiro principal:
    ```bash
    python Console.py
    ```
	
5.  O programa irá perguntar se deseja inicializar o sistema com dados padrão para demonstração. Escolha 's' (sim) para uma experiência mais completa.

## 🔮Próximos Passos
Embora o projeto tenha cumprido os seus objetivos, existem várias melhorias possíveis para o futuro:
- **Persistência de Dados:** Implementar uma forma de guardar e carregar o estado do sistema (ex: usando ficheiros JSON, CSV ou uma base de dados como SQLite) para que os dados não se percam ao fechar a aplicação.
- **Interface Gráfica (GUI):** Substituir a interface de linha de comando por uma interface gráfica mais amigável, utilizando bibliotecas como Tkinter, PyQt, ou até mesmo uma versão web com Flask/Django.
- **Testes Automatizados:** Desenvolver um conjunto de testes unitários e de integração (com `pytest` ou `unittest`) para garantir a estabilidade e a correção do código à medida que evolui.
- **Refatoração:** Analisar e refatorar pontos de maior acoplamento para aumentar ainda mais a modularidade e a testabilidade do sistema.
