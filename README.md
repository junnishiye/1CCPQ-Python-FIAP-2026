# Roteiro detalhado do vídeo — Sprint 4

Duração planejada: aproximadamente **6 minutos e 10 segundos**. A faixa permitida é de 5 a 8 minutos.

## Como interpretar este roteiro

- O texto depois de `>` é falado pelo integrante.
- As indicações entre colchetes **não são lidas**.
- `[ENQUANTO FALA — ação]` significa executar a ação ao mesmo tempo que a frase seguinte é narrada.
- `[PAUSA 3s — ação]` aparece somente quando é preciso trocar de janela, aguardar um carregamento ou deixar um resultado novo visível.
- Após um clique que muda dados, aguarde o resultado aparecer antes de continuar.
- Os tempos são referências. Uma diferença de alguns segundos é aceitável, desde que o vídeo permaneça entre 5 e 8 minutos.

## Identificação usada no vídeo

- Disciplina: Estruturas de Dados e Algoritmos
- Turma: 1CCPQ
- Projeto: ChargeGrid Intelligence
- Andre Balan Felix dos Santos — RM 571691
- Henrique De Souza Aragão — RM 570529
- Gabriel Da Silva Silveira — RM 568910
- Davi Sinhorini Pacheco — RM 569487
- João Vitor Jun Nishiye De Sousa — RM 572079

Os nomes e RMs aparecem apenas na capa. Não é necessário ler a lista em voz alta. Confiram a grafia, a disciplina e a turma antes da gravação.

## Distribuição real do tempo

| Período | Integrante | Fala aproximada | Demonstração/pausas | Total |
|---|---|---:|---:|---:|
| 0:00–0:40 | Andre | 34 s | 3 s | ~40 s |
| 0:40–1:45 | Henrique | 49 s | 15 s | ~65 s |
| 1:45–2:40 | Gabriel | 45 s | 7 s | ~55 s |
| 2:40–3:35 | Davi | 45 s | 10 s | ~55 s |
| 3:35–4:55 | João | 67 s | 14 s | ~80 s |
| 4:55–5:30 | Andre | 26 s | 8 s | ~35 s |
| 5:30–6:05 | João/Grupo | 30 s | 3 s | ~35 s |

Henrique e João têm blocos maiores porque executam mais ações. Sempre que possível, essas ações acontecem junto com a narração.

## Preparação antes de gravar

1. Executar `python3 -m unittest discover -s tests -v` e confirmar que todos os testes passam.
2. Abrir o sistema com `python3 app.py`.
3. Deixar `backend.py` aberto no editor nos seguintes pontos:
   - `class SessaoRecarga`;
   - `def calcular_tarifa`;
   - `def busca_sequencial`;
   - `def _merge_sort_recursivo`;
   - `def _intercalar`.
4. Aumentar a fonte do editor para o código ficar legível no vídeo.
5. Fechar notificações e ocultar arquivos ou abas pessoais.
6. Gravar em 1080p e fazer um teste de áudio antes da gravação definitiva.
7. Limpar a base do sistema antes de começar, para que o cadastro manual seja `CG-0001`.

---

## 0:00–0:40 — Andre: identificação, problema e evolução

**Objetivo:** apresentar o projeto e contextualizar a evolução técnica.

**Capa e apresentação**

`[ENQUANTO FALA — manter a capa visível e apontar disciplina, turma, projeto, nomes e RMs]`

> Olá, somos da turma 1CCPQ, da disciplina de Estruturas de Dados e Algoritmos. Este é o ChargeGrid Intelligence, nosso sistema de gerenciamento de recargas de veículos elétricos. Os nomes e RMs dos integrantes estão apresentados na tela.

`[PAUSA 3s — trocar da capa para a tela inicial do sistema]`

**Problema e evolução**

`[ENQUANTO FALA — mostrar a tela inicial e apontar “Operação e sessões”]`

> O projeto controla várias recargas ao mesmo tempo, distribui a potência disponível e calcula energia, tarifa e custo. Na Sprint 4 separamos a interface do backend Python, adicionamos persistência e substituímos o Bubble Sort pelo Merge Sort manual, que é mais eficiente.

---

## 0:40–1:45 — Henrique Aragão: integração e demonstração funcional

**Objetivo:** provar que a interface está integrada ao backend Python e mostrar o fluxo operacional completo.

**Tecnologia e arquitetura**

`[ENQUANTO FALA — percorrer o formulário à esquerda e a tabela à direita]`

> A interface foi implementada em Tkinter.

`[ENQUANTO FALA — mover o mouse sobre “Interface”, “Backend Python”, “Processamento” e “Resultado” no cabeçalho]`

> As regras ficam no backend Python. O cabeçalho mostra o fluxo entre interface, processamento e resultado.

**Cadastro manual**

`[ENQUANTO FALA — posicionar o mouse sobre o botão “INICIAR SESSÃO”]`

> Ao iniciar uma sessão, o formulário envia os dados ao `ChargeGridBackend`.

`[ENQUANTO FALA — percorrer veículo, conector, perfil, potência, duração e horário]`

> São enviados veículo, conector, perfil, potência, duração e horário.

> Vamos cadastrar uma sessão.

`[PAUSA 3s — clicar em “INICIAR SESSÃO”, esperar a tabela atualizar e apontar o registro criado]`

**Retorno do backend**

`[ENQUANTO FALA — apontar o ID na tabela e depois a mensagem inferior]`

> O backend valida os dados, cria um objeto `SessaoRecarga` e o adiciona à lista. A tabela e a mensagem inferior exibem o ID e a tarifa devolvidos pelo Python.

**Múltiplas sessões e simulação**

> Agora carregamos o cenário com cinco registros.

`[PAUSA 5s — clicar em “Carregar cenário do vídeo”, confirmar e aguardar as cinco linhas aparecerem]`

`[ENQUANTO FALA — percorrer as cinco linhas com o mouse]`

> A lista comprova o armazenamento de múltiplas sessões.

> Ao avançar quinze minutos, o backend redistribui o limite de 60 quilowatts e atualiza energia e custo.

`[PAUSA 4s — clicar em “Avançar todas +15 min” e apontar as colunas Tempo, Energia e Custo]`

> Também encerramos uma sessão sem apagar seu histórico.

`[PAUSA 3s — selecionar uma sessão ativa, clicar em “Finalizar selecionada” e mostrar o status “Finalizada”]`

**Observação de gravação:** Henrique fala enquanto aponta os elementos. As pausas permanecem somente nos quatro momentos em que o sistema precisa exibir um resultado novo: cadastro, carregamento do cenário, avanço do tempo e finalização.

---

## 1:45–2:40 — Gabriel: estrutura de dados e tarifação

**Objetivo:** mostrar como uma sessão é representada, onde múltiplas sessões são armazenadas e como a tarifa é processada.

**Dataclass**

`[PAUSA 3s — trocar para o editor e centralizar “@dataclass” e “class SessaoRecarga”]`

> Cada recarga é representada pela dataclass `SessaoRecarga`.

`[ENQUANTO FALA — destacar id_sessao, veiculo, conector e tipo_carregador]`

> Ela guarda o ID, o veículo, o conector e o carregador.

`[ENQUANTO FALA — descer e destacar potência, tempo, tarifa, energia, custo e status]`

> Também guarda potência, tempo, tarifa, energia, custo e status. A dataclass organiza o modelo e facilita a conversão para JSON.

**Lista e persistência**

`[PAUSA 2s — localizar no editor “self.sessoes: list[SessaoRecarga] = []”]`

`[ENQUANTO FALA — manter a declaração de self.sessoes destacada]`

> O backend mantém os objetos em `self.sessoes`, uma lista usada pela busca, ordenação, estatísticas e interface.

> No salvamento, os objetos viram dicionários em JSON e podem ser recuperados depois.

**Tarifação**

`[PAUSA 2s — ir para “def calcular_tarifa” e deixar os blocos if visíveis]`

`[ENQUANTO FALA — apontar, na ordem, os quatro blocos de regras]`

> A tarifa parte de oitenta centavos e meio por quilowatt-hora e considera horário, demanda, perfil e potência.

> Como ela sempre aplica uma quantidade fixa de regras, sua complexidade é O de um, independentemente do número de sessões.

---

## 2:40–3:35 — Davi: busca sequencial e complexidade

**Objetivo:** executar a busca, mostrar seu código e relacionar as comparações à complexidade `O(n)`.

**Execução na interface**

`[PAUSA 3s — voltar à interface e clicar em “Mostrar todas”]`

`[ENQUANTO FALA — selecionar o campo de busca e confirmar “CG-0005”]`

> A chave da busca é o ID da sessão. Vamos procurar `CG-0005`.

> O pedido é enviado à busca sequencial do backend.

`[PAUSA 4s — clicar em “Buscar ID” e aguardar a única linha aparecer]`

`[ENQUANTO FALA — apontar a mensagem inferior, a contagem e “O(n)”]`

> A mensagem confirma a sessão e as cinco comparações realizadas.

**Código da busca**

`[PAUSA 3s — trocar para o editor e centralizar “def busca_sequencial”]`

`[ENQUANTO FALA — acompanhar o laço for, o contador e o if]`

> O algoritmo começa no primeiro elemento, aumenta o contador e compara um ID por vez.

> O `break` encerra a busca quando encontra o ID. Se ele não existir, toda a lista é percorrida.

**Big-O**

`[ENQUANTO FALA — manter visíveis o laço e a documentação “Complexidade: O(n)”]`

> No pior caso, `n` sessões exigem `n` comparações; portanto, a complexidade é O de n. Se a lista dobrar, o máximo de verificações também dobra. O melhor caso é O de um quando o ID está na primeira posição.

---

## 3:35–4:55 — João: Merge Sort manual e complexidade

**Objetivo:** ordenar registros diferentes, mostrar que o algoritmo é próprio e justificar `O(n log n)`.

**Execução da ordenação**

`[PAUSA 2s — voltar à interface e clicar em “Mostrar todas”]`

> Para ordenar as sessões, implementamos manualmente o Merge Sort, sem utilizar `sort` nem `sorted`.

`[ENQUANTO FALA — abrir o critério e escolher “Energia”]`

> A interface permite ordenar por ID, veículo, energia, custo, tempo ou tarifa.

`[ENQUANTO FALA — escolher o sentido “Decrescente”]`

> Neste exemplo, vamos ordenar a energia do maior para o menor valor.

`[PAUSA 4s — clicar em “Aplicar Merge Sort”, esperar a tabela mudar e percorrer a coluna Energia de cima para baixo]`

`[ENQUANTO FALA — apontar comparações, movimentações e O(n log n) na mensagem]`

> A mensagem inferior mostra as comparações, as movimentações e a complexidade medidas nesta execução.

**Divisão e intercalação no código**

`[PAUSA 3s — trocar para o editor e centralizar “def _merge_sort_recursivo”]`

`[ENQUANTO FALA — apontar “meio”, “itens[:meio]” e “itens[meio:]”]`

> O Merge Sort divide recursivamente a lista ao meio até obter partes com um único elemento.

> Depois, a função `intercalar` compara os elementos das duas metades.

`[PAUSA 2s — ir para “def _intercalar”]`

`[ENQUANTO FALA — acompanhar os dois índices, a comparação e os append]`

> A cada comparação, o elemento correto é inserido no resultado. No final, a lista reorganizada volta para a interface.

**Big-O e melhoria sobre a Sprint 3**

`[ENQUANTO FALA — manter visível a divisão recursiva]`

> Existem aproximadamente log de n níveis de divisão e até n elementos por nível. Por isso, a complexidade é O de n log n.

> Isso melhora o Bubble Sort O de n ao quadrado usado na Sprint 3. Com mil registros, o comportamento quadrático chega à ordem de um milhão de operações, enquanto n log n cresce mais lentamente.

`[PAUSA 3s — voltar à interface e mostrar novamente a tabela ordenada]`

---

## 4:55–5:30 — Andre: estatísticas e relatório final

**Objetivo:** demonstrar os indicadores calculados e o resumo final do sistema.

**Estatísticas**

`[PAUSA 3s — clicar na aba “Estatísticas” e aguardar os cartões aparecerem]`

`[ENQUANTO FALA — percorrer os cartões Sessões, Energia, Faturamento e Maior/Menor]`

> Em uma passagem, o backend soma energia e faturamento, conta sessões ativas e finalizadas e identifica o maior e o menor consumo.

`[ENQUANTO FALA — apontar a explicação O(n) na parte inferior]`

> Como os `n` registros são visitados uma vez, a complexidade é O de n.

**Relatório**

`[PAUSA 2s — clicar na aba “Relatório final”]`

`[ENQUANTO FALA — rolar pelo resumo, por duas sessões e pela seção de algoritmos]`

> O relatório reúne os indicadores, as sessões, os algoritmos e os eventos recentes.

> Ele também pode ser exportado em texto, completando o resumo da Sprint.

`[PAUSA 3s — clicar em “Exportar .txt”, mostrar a janela de salvamento e cancelar]`

---

## 5:30–6:05 — João ou grupo: defesa técnica e evoluções futuras

**Objetivo:** consolidar o fluxo demonstrado e apresentar pelo menos duas evoluções futuras.

`[PAUSA 3s — clicar na aba “Defesa técnica”]`

`[ENQUANTO FALA — percorrer o fluxo no topo e as métricas reais]`

> Esta tela resume o fluxo: o formulário envia os dados ao `ChargeGridBackend`, que processa a lista de sessões e devolve o resultado à interface.

`[ENQUANTO FALA — manter a aba de defesa técnica inteira visível]`

> Como evoluções futuras, podemos substituir o JSON por um banco de dados com autenticação e criar uma API para integrar o backend a um aplicativo mobile e a carregadores reais com OCPP.

> Demonstramos o backend Python, múltiplas sessões, tarifação, busca, Merge Sort, complexidade, estatísticas e relatório. Obrigado.

---

## Plano de contingência durante a gravação

- Se um clique demorar, continuar a gravação e esperar a tela responder; não preencher o silêncio com explicações improvisadas incorretas.
- Se o programa já tiver dados antigos, usar **Limpar base** antes de recomeçar.
- Se o cadastro informar conector ocupado, trocar o conector ou limpar a base.
- Se a janela de confirmação aparecer ao carregar o cenário, clicar em **Sim**; isso é esperado.
- Na exportação do relatório, basta mostrar a janela e cancelar. Não é necessário procurar o arquivo durante o vídeo.
- Se o vídeo ultrapassar 8 minutos, cortar apenas pausas excessivas. Não remover demonstrações ou explicações obrigatórias.

## Checklist obrigatório antes de publicar

- [ ] Duração entre 5 e 8 minutos.
- [ ] Disciplina, turma, nomes completos, RMs e projeto aparecem no início.
- [ ] Todos os cinco integrantes têm participação técnica audível.
- [ ] O programa é executado de verdade, não apenas mostrado em slides.
- [ ] Cadastro/início, múltiplas sessões e listagem aparecem.
- [ ] Busca funcionando e código da busca aparecem.
- [ ] Ordenação funcionando com vários registros e código do Merge Sort aparecem.
- [ ] Big-O é explicado a partir dos laços e divisões do código.
- [ ] Tarifação, estatísticas e relatório aparecem.
- [ ] Integração Interface → Backend Python → Resultado é explicada.
- [ ] Pelo menos duas evoluções futuras são apresentadas.
- [ ] Vídeo publicado no YouTube como **Público** ou **Não listado**.
- [ ] Link testado em janela anônima, sem solicitar acesso.
- [ ] Somente o link correto do YouTube é enviado no portal.
