# Otimização Massiva de Contacto no Canal Outbound Voz
## 1- Descrição
### 1.1 - Background
O canal comercial de voz outbound contata Clientes de forma proativa, e é um dos canais privilegiados de contacto de uma agência de Viagens com os seus Clientes e representa um volume muito significativo da atividade comercial. A estratégia de definição de contactos a fazer deste canal é implementada por dialers de diferentes sistemas de parceiros destes serviços que podem beneficiar de estratégias de otimização analítica. 
A estratégia atual do dialer é genericamente implementada numa máquina que percorre sequencialmente os registos carregados - cada registo num lote corresponde a um par id_cliente e tlf de contacto. O dialer aplica algumas regras higiénicas tal como aplicação de "quarentenas" de 4 horas para cada par. Tipicamente o contacto fica "fechado" uma vez esgotado o nº de tentativas que são configuradas como valor máximo.

### 1.2 Objetivos
Disponibilizando informação transacional sobre uma destas atividades comerciais, pretende-se otimizar esta operação de outbound de forma a melhorar os seguintes aspetos:
*	contatarmos os Clientes mais cedo com menos tentativas;
*	falarmos com mais Clientes;
*	fazer os pontos anteriores garantindo que continuamos a ter uma distribuição de volume de chamadas que não gera desocupação dos agentes de outbound;

## 2- Tarefas
### 2.1 Previsão Atendimento de Chamada
Prever o evento de chamada atendida para segmento do Dataset obtido pela filtragem do campo Base = 'Teste'.
Disponibilizar em ficheiro para este conjunto de informação (e para cada registo) a probabilidade de atendimento e a classificação final dada pelo modelo.

### 2.2 Apresentação de Resultados
Preparar da melhor forma possível uma apresentação com a duração de 1hr de forma a explicar a abordagem seguida para atingir os objetivos declarados, estruturar os resultados obtidos, discutir em que medida a implementação da estratégia de contatação no dialer deve ser alterada para garantir a otimização e identificar oportunidades de melhoria. 
Disponibilizar o código, preferencialmente em R, para uma discussão técnica de implementação de 30mins.

## 3- Informação

### 3.1 - Sumário do conteúdo do dataset

|Mês Lote                             |      Base|Nr Clientes       |Nr Tentativas |
|:--------------------------------|:--------------|:----------------|:-----:|
|201706 | Teste|35.214 |349.526     |
|201706 | Treino|105.643 |1.049.338     |
|201601 a 201705|Historico |47.376 | 627.397        |

### 3.2 - Dicionário de Dados*
*Tanto quanto sabemos.

|Campo                             |      Descrição|
|:--------------------------------|:--------------:|
|Base | Identificação do segmento do dataset - Teste, Treino e informação histórica|
|Data_do_Lote | Dia da produção do Lote de Contacto|
|dt_hr_tentativa | Timestamp da tentativa de Contacto|
|id_cliente_A | ID único de um Cliente anonimizado|
|tlf_destino_A | Telefone de contacto anonimizado|
|indc_destino_A | 2 primeiros digitos do tlf de destino|
|tlf_origem_A | Telefone de origem anonimizado|
|indc_tlf_ori_A | 2 primeiros digitos do tlf de origem|
|duracao | duração da chamada|
|outcome | Resultado do contacto, pode assumir, tanto quanto sabemos valores em [1] |
|tipificacao | Última tipificação inserida em sistema pelo operador|

[1] Valores de Outcome
*	Handled - Cliente atende e chamada é atribuída a agente
*	Invalid number - Número inválido
*	Machine - Cliente não atende após máximo de toques e tem voicemail configurado
*	No answer - Cliente não atende após máximo de toques e não tem voicemail configurado
*	Nuisance - Cliente atende mas chamada não é atribuida a nenhum agente e cliente acaba por desligar
*	Rejected - Chamada rejeitada: Cliente - Duração >10seg, Rede/Centra/equipamento desligado (sem Voicemail) - duração = 0 seg"



