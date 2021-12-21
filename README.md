# fundamentos-de-programacao-bancos-de-dados

# 0. Introdução:

**Como organizar informação**

Quando você selecionar uma linha na transcrição, será direcionado à seção equivalente no vídeo
Imagine que você é dono de um restaurante e você queira fazer uma promoção. Você sabe qual que é o prato mais vendido? Você tem noção de quanto desconto que você pode dar para não perder dinheiro? E o seu estoque? Como é que você controla ele? Você sabe se vai ter comida suficiente para fazer todos os pratos? E as receitas, todas em um papel, né? 

Agora imagine você rastreando tudo isso em uma simples planilha de Excel. Sim, é possível, mas realmente não é aconselhável por algumas razões. Um dos grandes problemas de uma planilha é você, ou outras pessoas, inserir dados incorretos; é muito fácil, e todo o ser humano faz - e uma planilha aceita qualquer informação. 

E outra coisa: extrair informações de uma planilha quando se tem uma estrutura de dados um pouco mais complexa é bem tedioso e muitas vezes impraticável. O que você precisa é de uma ferramenta mais sofisticada, um banco de dados. 

Ele te permite trabalhar com grandes quantidades de dados, podendo atualizá-los com facilidade e consultá-los de uma maneira que você precisa. A suas informações precisam ser armazenadas de uma forma organizada, consistente e confiável. 

Além disso, um banco de dados te dá recursos de segurança para controlar o acesso às informações, evitar redundâncias de dados e validar ações a serem executadas. O que o banco de dados te dá são respostas. Quantos kilos de file mignon que tem que comprar para durar uma semana típica de Agosto, baseado na movimentação média nesse mesmo período em anos passados. 

Isso soa complexo, mas para um banco de dados não é; para uma planilha de Excel, talvez sim. Agora, existem alguns modelos de bancos de dados usados em diferentes aplicações. 

Temos o Modelo Plano (ou tabular); 
o Modeloem Rede; 
Modelo Hierárquico; Modelo Relacional; 
Orientado a objetos; e vários outros tipos. 

Não vou entrar em detalhes sobre eles, pois o modelo mais comum é o Modelo Relacional. Ele é usado em sistemas bancários, de supermercados, em aplicativos no seu smartphone, em lojas online e em muito mais lugares. 

Neste curso vou falar sobre:

como funcionam os bancos de dados; 
quais são as suas regras; 
que ferramentas você tem disponível para inserir, manter e principalmente buscar as informações que você precisa. 

Pode parecer um bicho de sete cabeças, mas eu vou te explicar passo a passo como construir o seu primeiro banco de dados. Vamos lá?

**O que você deveria saber**

Quando você selecionar uma linha na transcrição, será direcionado à seção equivalente no vídeo
Antes de mais nada, eu quero fazer uma distinção muito importante. Vou falar sobre bancos de dados em geral, sem entrar em nenhum **sistema de gerenciamento de banco de dados** ou **"SGDB"** específico, pois existem vários. Em inglês esses sistemas são chamados de **"DBMS". DBMS, "Database Management Systems"** Mas vou me referenciar a eles como um sistema para simplificar as coisas aqui. Alguns exemplos de sistemas são: 

**1.o "MySQL";
2.o "SQL Server";
3.ou o "Microsoft Acess".**


Eles são utilizados para interagir com bancos de dados, mas não se preocupe, para acompanhar esse curso você não precisa de nenhum software especial. Você também não precisa saber programar e nem conhecer os conceitos básicos de estruturação de dados. Você também não precisa nem ter acesso a um banco de dados em si para acompanhar esse curso. Vou falar sobre alguns conceitos básicos que fazem um banco de dados relacional funcionar, e demonstrar alguns exemplos práticos de como trabalhar com eles.

# 1. Dados que geram informações

**Problemas comuns**

Quando você selecionar uma linha na transcrição, será direcionado à seção equivalente no vídeo
Para começar, não vou mergulhar em nenhum software específico e construir um banco de dados. Primeiro eu vou explicar quais são os problemas que o banco de dados resolve. Quando você lida com dados, você sempre tem que ter em mente os seguintes problemas em potencial: 

**Considerações>**

- a quantidade de dados - sim, o volume ou o **tamanho do seu banco de dados**; 
- como que você gerencia as **atualizações dessas informações**; 
- como que você garante que as **informações são corretas ou precisas**; 
- como que você **mantém a segurança de seus dados**; 
- e como que você **implementa redundância, ou seja, duplicação dos seus dados**, para não perder informações no caso de uma falha de um dos banco de dados; 
- e finalmente o **valor dos seus dados, o quanto que eles são importantes para você**. 
 
 **1. Tamanho**
 
  Vamos falar primeiro sobre a **quantidade de dados, o tamanho do seu banco de dados**. Por que isso seria um problema? Você já tentou trabalhar com uma planilha com mais de mil linhas? É, fica muito lento. Os bancos de dados são utilizados para lidar com uma quantidade enorme de dados. 
 
 **2. Atualizações**
 
  E para fazer **a atualização das informações no seu banco de dados?** O que que acontece se dois usuários diferentes no seu banco de dados tentarem alterar o mesmo telefone da mesma pessoa ao mesmo tempo **(Alterar Registros)**?
  
  E se forem várias pessoas tentando acessar o mesmo arquivo ao mesmo tempo? Como é que você lida com isso **(Acesso múltiplos)**? 
  
  Se você trabalha com um sistema tradicional baseado em arquivos, isso simplesmente é muito problemático. Somente os dados da última pessoa que salvou o arquivo serão armazenados, sem saber quem mudou o que no arquivo **(Historio de versões)**. 
  
  **3. Precisão**
  
  Agora vamos dar uma olhada no problema de **precisão dos dados**. Você precisa de um mecanismo que não permita que um texto seja inserido no lugar de um valor numérico **(Tipos de dados)**. 
  
    Exemplo: **? xpto kg de tomete**  
  
  Não faria sentido eu dizer "xPTO" kgs de tomate. 
  
  Você também não quer que um valor numérico seja inserido em uma data, por exemplo **(informações consistente)**. Quando é que seu aniversário? É dez? Não faz sentido, correto? 
  
    Exemplo: **Aniversário: 10**
  
  Tudo isso para dizer que é necessário garantir que os dados sejam coerentes com o tipo de informação que você quer armazenar. 
  
  **4. Segurança**
  
  Muito importante é a **segurança** também, obviamente. Seus dados precisam estar seguros **(Sigilo das informações)**. Não seria muito bom se seu concorrente tivesse acesso ao nome, telefone, e-mail de todos os seus clientes, ou descobrisse quais são os itens do cardápio que você mais vende, o seu volume de vendas ou outros dados sigilosos. Mas por outro lado você deixar as informações sobre o cardápio acessíveis para todo mundo ver, mas somente o nome do item e o preço. Você não quer divulgar a receita completa **(Acesso parcial)**. 
  
  Um banco de dados oferece ferramentas para definir quem pode ver o que **(Control de permissões)**, quem pode alterar quais informações e quem foi que alterou um valor específico e quando **(Histórico de alterações)**, entre uma série de outras funcionalidades. 
  
  **5. Redundância**
  
  Outra preocupação que temos é **redundância ou a duplicação de seus dados**, não queremos ter várias cópias na mesma informação. Mas veja bem, ter sistemas redundantes por si só não é uma coisa ruim, como é o caso de backups ou cópias de segurança. Isso é uma coisa boa **(Cópias propositais, ok!)**, mas os dados em si não é tão bom, porque você pode gerar conflitos ou incertezas sobre qual que é o valor correto. 
  
  Por exemplo, na tabela de itens do cardápio aqui, 
  
    **id |        nome      |   preço**
    **1  |    Fíle Mignon   |   R$15,00**
      2  |    Batata Doce   |   R$5,53
    **3  |    Fíle Mignon   |   R$15,00**
      4  |      Batata      |   R$2,01
  
  
  por engano o filé mignon está listado duas vezes **(Informações conflitantes)**: uma vez com um **valor de 12 reais**, e outra com um **valor de 15 reais**. Qual que é o valor certo? É difícil dizer aqui sem saber quem foi que criou esse registro e quando. O mais importante é criar mecanismos que evitem ou pelo menos alertem o usuário que temos o potencial de informações duplicadas. 
  
  E finalmente qual a **importância dos seus dados**. 
  .Você está armazenando a cor preferida do usuário, ou o seu tipo sanguíneo, alergias e outras informações que podem salvar a sua vida **(Tipo de informação)**? 
  .E o que acontece com a sua empresa e com seus clientes se você perder essas informações **(Relevância)**? 
  .Os dados que você armazena são críticos (**Dependência)**? Na maioria dos casos você não pode perder nada, nem uma única mudança. 
  
  **Banco de dados:**
  
  E é para solucionar esses tipos de problemas que precisamos de bancos de dados. 
  
  Não precisamos deles somente como um lugar para colocar dados. Precisamos de uma novidade para que o volume de dados possa crescer e que esse crescimento seja gerenciável; que seja fácil de procurar pelas informações desejadas; que seja fácil atualizar os dados - até mesmo que seja por muitas pessoas ao mesmo tempo; que os dados sejam precisos internamente e consistentes, mantendo-os seguros; e finalmente que você possa controlar o acesso a eles, acompanhando exatamente quem fez o quê e quando.





