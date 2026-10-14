# ChargeGrid Intelligence — Sprint 4

Sistema gráfico de gerenciamento e simulação de sessões de recarga com interface Tkinter e backend integralmente desenvolvido em Python.

## O que melhorou em relação à Sprint 3

- separação explícita entre `app.py` (interface) e `backend.py` (processamento);
- Merge Sort manual `O(n log n)` no lugar do Bubble Sort `O(n²)`;
- contagem visível de comparações e movimentações dos algoritmos;
- persistência automática das sessões em JSON;
- balanceamento de potência entre sessões ativas;
- cenário pronto para uma demonstração reproduzível em vídeo;
- aba “Defesa técnica” com fluxo de dados, conceitos e métricas reais;
- testes automatizados para as regras e algoritmos do backend.

## Estrutura

```text
Sprint 4/
├── app.py                  # Interface gráfica Tkinter
├── backend.py              # Regras, dados, algoritmos e persistência
├── README.md               # Execução e arquitetura
├── ROTEIRO_VIDEO.md        # Roteiro de 5–8 minutos para cinco integrantes
├── dados/
│   └── sessoes.json        # Criado automaticamente ao executar
└── tests/
    └── test_backend.py     # Testes automatizados do backend
```

## Executar

Requisitos:

- Python 3.10 ou superior;
- Tkinter, normalmente incluído na instalação do Python.

Na pasta `Sprint 4`, execute:

```bash
python3 app.py
```

No Debian/Ubuntu, se o Tkinter não estiver instalado:

```bash
sudo apt install python3-tk
```

O projeto utiliza somente a biblioteca padrão do Python; não é necessário instalar pacotes com `pip`.

## Executar os testes

```bash
python3 -m unittest discover -s tests -v
```

Os testes cobrem:

- criação e armazenamento de múltiplas sessões;
- validação de conectores;
- tarifação dinâmica;
- avanço da recarga e cálculo de energia/custo;
- balanceamento do limite da estação;
- busca sequencial e contagem de comparações;
- Merge Sort crescente e decrescente;
- estatísticas;
- persistência JSON;
- cenário completo de demonstração.

## Arquitetura e fluxo dos dados

```text
Interface Tkinter
      ↓ entradas do formulário
ChargeGridBackend (Python)
      ↓ valida e processa
list[SessaoRecarga]
      ↓ busca / Merge Sort / tarifa / estatísticas
Objeto de resultado
      ↓
Interface atualiza tabela, indicadores e relatório
```

`SessaoRecarga` é uma `dataclass` que representa uma sessão. Ela armazena ID, veículo, conector, carregador, perfil, potências solicitada e liberada, tempos, tarifa, energia, custo, status e datas. O backend mantém múltiplos objetos em `self.sessoes`, uma lista Python.

## Algoritmos avaliados

### Busca sequencial — `O(n)`

A busca compara o ID procurado com cada sessão da lista e termina ao encontrar o registro ou chegar ao fim. No pior caso, visita as `n` sessões. Se a entrada dobrar, a quantidade máxima de comparações cresce aproximadamente na mesma proporção.

### Merge Sort manual — `O(n log n)`

O algoritmo divide recursivamente a lista em metades e intercala as partes de forma ordenada. O código não utiliza `sort()` nem `sorted()` para realizar a funcionalidade avaliada. Há cerca de `log n` níveis de divisão e até `n` elementos processados por nível.

### Outras complexidades

- tarifação: `O(1)`, pois há um número fixo de regras;
- estatísticas: `O(n)`, com uma passagem pela lista;
- inserção de uma sessão no final da lista: `O(1)` amortizado;
- persistência completa: `O(n)`, pois serializa todas as sessões.

## Tarifação

A base é `R$ 0,805/kWh`. Os fatores são multiplicativos:

- horário de pico, das 18h às 21h: `× 1,20`;
- demanda a partir de 80% do limite: `× 1,08`;
- demanda a partir de 100% do limite: `× 1,15` em lugar de `× 1,08`;
- Assinante: `× 0,90`;
- Frota: `× 0,95`;
- potência solicitada acima de 11 kW: `× 1,10`.

Energia e custo são acumulados quando o tempo da simulação avança:

```text
energia (kWh) = potência liberada (kW) × tempo (h)
custo (R$) = energia (kWh) × tarifa (R$/kWh)
```

## Sequência recomendada para testar antes de gravar

1. Abra o programa e clique em **Carregar cenário do vídeo**.
2. Mostre as cinco sessões e use **Avançar todas +15 min**.
3. Busque `CG-0005` e destaque a contagem de comparações.
4. Clique em **Mostrar todas**.
5. Ordene por **Energia**, em ordem **Decrescente**, com o Merge Sort.
6. Abra **Estatísticas**.
7. Abra **Relatório final** e exporte o `.txt`.
8. Abra **Defesa técnica** e mostre o fluxo e as métricas.
9. No editor, abra `backend.py` nos trechos `SessaoRecarga`, `busca_sequencial` e `ordenar_merge_sort`.

## Entrega no portal

De acordo com o enunciado da Sprint 4, o portal recebe **exclusivamente o link do vídeo publicado no YouTube**. O vídeo deve permanecer Público ou Não listado, nunca Privado. Antes de enviar, abra o link em uma janela anônima e confirme que ele funciona sem login ou autorização.

