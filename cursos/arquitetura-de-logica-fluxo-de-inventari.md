# Guia de Lógica: Estruturação e Persistência de Dados

Este guia descreve como planejar o fluxo de um sistema que gerencia dados em memória e garante que as informações não sejam perdidas ao fechar o programa.

---

## 1. Estrutura do Projeto no Repositório

Em um repositório real, a organização deve separar a documentação, os termos de uso e os módulos de lógica:

* **LEIAME.md**: Documento de apresentação do projeto. Deve conter o objetivo do sistema, as regras de negócio suportadas e as instruções para execução.
* **LICENSE**: Ficheiro com os termos legais de utilização e distribuição do código.
* **Módulo de Dados**: Responsável por definir como a informação de cada produto (código, nome, quantidade e preço) será representada e agrupada.
* **Módulo de Persistência**: Responsável exclusivamente pela leitura e escrita no disco rígido.
* **Módulo Principal**: Responsável por gerir a interação com o utilizador e o menu de opções.

---

## 2. Passo a Passo do Fluxo Lógico

### Etapa A: Inicialização do Sistema
1. **Verificação de Ficheiro Existente**: Antes de mostrar o menu ao utilizador, o sistema deve tentar abrir o ficheiro de dados do disco.
2. **Carga Inicial**: Se o ficheiro existir, o sistema lê os registros um por um e preenche a lista em memória. Se não existir, o sistema inicia com a lista vazia.
3. **Controlo do Limite**: Durante a leitura do ficheiro, o programa deve garantir que não ultrapassa a capacidade máxima de registros suportada pela memória.

---

### Etapa B: O Ciclo Principal (Menu)
O programa deve manter-se em execução contínua através de um laço de repetição. A cada ciclo, o sistema realiza os seguintes passos:

1. **Exibição de Opções**: Apresenta as ações disponíveis (Registar, Listar, Salvar e Sair).
2. **Captação da Decisão**: Aguarda a entrada do utilizador para decidir qual caminho tomar.
3. **Desvio Condicional**:
   * **Se escolher Registar**: Verifica se ainda há espaço na memória. Se houver, solicita cada dado do produto sequencialmente e incrementa o contador total de itens.
   * **Se escolher Listar**: Percorre a lista em memória do início até o número total de itens cadastrados, exibindo as informações formatadas no ecrã.
   * **Se escolher Salvar**: Aciona o módulo de escrita para transferir todos os dados da memória para o ficheiro de texto no disco.
   * **Se escolher Sair**: Encerra o laço de repetição e finaliza a aplicação com segurança.

---

## 3. Boas Práticas de Pensamento Algorítmico

* **Separação de Responsabilidades**: A lógica que desenha o menu não deve ser a mesma que escreve no ficheiro. Mantenha as tarefas isoladas.
* **Validação de Entrada**: Sempre valide se os dados inseridos pelo utilizador correspondem ao esperado antes de salvar na memória.
* **Tratamento de Falhas**: Se o ficheiro estiver corrompido ou o disco estiver cheio, o algoritmo deve informar o problema ao utilizador sem interromper o programa bruscamente.