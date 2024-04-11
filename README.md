#  Missão Prática | Nível 4 | Mundo 4
 
- Objetivos da prática

```
  - Demonstrar habilidade na criação e gerenciamento de recursos na 
  Nuvem Azure, adquirindo conhecimento sobre a estrutura básica da 
  plataforma Azure

  - Utilizar efetivamente o portal Azure para criar e configurar uma 
  Máquina Virtual (VM), demonstrando compreensão dos recursos e suas funções.

  - Configurar regras de rede e grupos de segurança, adquirindo conhecimento sobre a
estrutura das regras de rede na Nuvem Azure.
 
 - Importar um arquivo .bacpac para um banco de dados no Banco de Dados SQL do
Azure;

 - Criar e configurar um aplicativo web no Azure, demonstrando compreensão do
mecanismo de hospedagem e implantação de aplicativos web.
``` 

 - Especificação

https://sway.cloud.microsoft/s/Y32eUDswcOxAHalk/embed


# Microatividades  

## 1 - Criar uma Máquina Virtual (VM) no Azure

 Material necessário para a prática

   - Conta no Microsoft Azure.
   - Navegador Web (Google Chrome, Firefox, MS Edge, Safari ou Opera).

```
 obs: realizei a adesão ao plano estudantil oferecido a instituição   

```
### conta

<img src="images/inscricao.azure.png" alt="" style="width: 55%; display: block;"/>

<BR>

### maquina virtual

<img src="images/maquina.virtual.propriedades.png" alt="" style="width: 55%; display: block;"/>

<BR>

## 2 - Configurar Regras de Rede e Grupos de Segurança no Azure

 - Crie uma regra para permitir que qualquer pessoa na internet possa acessar um
servidor Web hospedado na máquina virtual criada anteriormente. Preencha os campos
necessários para a regra, incluindo:

   - Origem: O filtro de origem pode ser qualquer (any), um intervalo de endereços IP,
Meu endereço IP, um grupo de segurança de aplicativo ou uma marca padrão. Ele
especifica o tráfego de entrada de um intervalo de endereços IP de origem específico
que será permitido ou negado por essa regra.

   - Intervalos de porta de origem: Forneça uma única porta, como, 80; um intervalo de
portas, como, 1024 a 65535, ou uma lista separada por vírgulas de portas e/ou
intervalos de portas únicos, como 80,1024-65535. Isso especifica de quais portas a
entrada de tráfego será permitida ou negada por esta regra. Forneça um asterisco (*)
para permitir o tráfego por meio de qualquer porta.

   - Destino: O filtro de destino pode ser Qualquer um, um intervalo de endereços IP, um
grupo de segurança de aplicativos ou uma marca padrão. Ele especifica o tráfego de
saída de um intervalo de endereços IP de destino específico que será permitido ou
negado por essa regra.


   - Serviço: O serviço especifica o protocolo de destino e o intervalo de porta para essa
regra. Você pode escolher um serviço predefinido, como RDP ou SSH, ou fornecer um
intervalo de porta personalizado. Se selecionar um serviço específico o próximo item
(Intervalos de porta de destino) será preenchido com o valor padrão e não será
editável.

   - Intervalos de porta de destino: Somente editável se na opção anterior for marcado
“Custom”. Forneça uma única porta, como, 80; um intervalo de portas, como, 1024 a
65535, ou uma lista separada por vírgulas de portas e/ou intervalos de portas únicos,
como 80,1024-65535. Isso especifica de quais portas a entrada de tráfego será
permitida ou negada por esta regra. Forneça um asterisco (*) para permitir o tráfego
por meio de qualquer porta.

   - Protocolo: Escolha entre as opções disponíveis (Any, TCP, UDP ou ICMP)
Ação: selecione entre permitir ou negar
Prioridade: ordem de processamento da regra. As regras são processadas em ordem
de prioridade; quanto menor for o número, maior a prioridade. Recomendamos deixar
lacunas entre as regras - 100, 200, 300, etc. - para que seja mais fácil adicionar
novas regras sem ter que editar regras existentes.
Nome da regra: Especifique um nome para a regra.
   
   - Descrição: Preencha uma descrição da regra especificando a sua finalidade

<BR>
   
<img src="images/maquina.virtual.regra.acesso.png" alt="" style="width: 55%; display: block;"/>

<BR>


## 3 - Criar um banco de dados SQL do Azure

 - O resultado esperado desta microatividade é que seja criado com
sucesso um Banco de Dados SQL na Microsoft Azure. Demonstrar de que o banco de
dados tenha sido criado com as configurações desejadas e que ele apareça na lista de
recursos no painel do Azure.

   - criação do banco
 
<BR>
   
<img src="images/criar.banco.png" alt="" style="width: 55%; display: block;"/>

<BR>

   - conclusão do banco

<BR>
   
<img src="images/sql.server.pronto.png" alt="" style="width: 55%; display: block;"/>

<BR>

 - 
•	obs: devido a um erro de digitação, o nome do banco ficou como 'fullstak' porem 
   posteriormente corrigido para 'fullstack'


## 4 - Conecta-se ao seu banco de dados

- Verificação do comando az sql db list para listar todos os bancos de dados no
servidor lógico do SQL do Azure. Você verá um grande bloco de JSON como saída.

<BR>
   
<img src="images/verificarBancoPowerShellAzure.png" alt="" style="width: 55%; display: block;"/>

<BR>

- Agora a verificação do comando para visualizar apenas os nomes dos bancos de
dados. Desta vez, foi utilizada a ferramenta jq, um analisador JSON de linha de comando,
para extrair somente os campos de nome. Direcione a saída dos comandos az para o jq
usando o seguinte comando:

 

az sql db list | jq '[.[] | {name: .name}]'

 

- O resultado do comando apresentará atributos "name". Serão observados  dois atributos “name”. 
Um refere-se ao banco de dados criado nas atividades anteriores, denominado "fullstak", para este roteiro. 
No entanto, é importante observar que o banco de dados do sistema "master" também será listado, pois inclui os
metadados do servidor, como configurações de entrada e do sistema.


<BR>
   
<img src="images/listarBancoPowerShellAzure.png" alt="" style="width: 55%; display: block;"/>

<BR>

Verificação do comando az sql db show usado para obter detalhes específicos sobre o
banco de dados. Substitua [nome-do-banco] pelo nome que você obteve no comando
anterior.

az sql db show --name fullstak
 

O resultado será uma extensa saída JSON. Para extrair informações relevantes, utilize a
ferramenta jq novamente.


<BR>
   
<img src="images/detalhesBancoSqlServer.png" alt="" style="width: 55%; display: block;"/>

<BR>


 -  Desta vez, foi redirecionada a saída para o jq, filtrando
apenas o nome, tamanho máximo e status do banco de dados previamente criado. Isso
permitirá uma visualização específica, confirmando que o banco de dados está online e
revelando o volume máximo de armazenamento disponível.
 

az sql db show --name fullstak | jq '{name: .name, maxSizeBytes: .maxSizeBytes,
status: .status}'

<BR>
   
<img src="images/volumeMaximoSQLServer.png" alt="" style="width: 55%; display: block;"/>

<BR>

- Agora é o momento de estabelecer uma conexão utilizando a ferramenta sqlcmd. Execute o
comando abaixo para obter a cadeia de conexão do banco de dados que está sendo
utilizado em um formato adequado para o sqlcmd:

az sql db show-connection-string --client sqlcmd --name fullstak

<BR>
   
<img src="images/obtendoStringConexaoViaPowerShell.png" alt="" style="width: 55%; display: block;"/>

<BR>

IMPORTANTE: poderá aparecer uma mensagem de erro semelhante ao exemplo a
seguir:

 

Sqlcmd: Error: Microsoft ODBC Driver 17 for SQL Server:

Cannot open server 'contoso' requested by the login.

Client with IP address 'nnn.nnn.nnn.nnn' is not allowed to access the server.

To enable access, use the Windows Azure Management Portal or run
sp_set_firewall_rule

on the master database to create a firewall rule for this IP address or address range.

It may take up to five minutes for this change to take effect.

Se ocorrer esse erro, será necessário adicionar uma nova regra de firewall ao cliente.
Para fazer isso, siga as etapas abaixo:

 

Na página inicial do Azure, vá para "Serviços do Azure" e selecione "Todos os
recursos". Isso abrirá o painel de todos os recursos.
Localize o seu banco de dados e selecione-o. Isso abrirá o painel do banco de dados
SQL que você criou, neste roteiro, o banco chamado fullstack.
No menu superior, escolha "Definir o firewall do servidor". Isso abrirá o painel de
Rede.
Na seção "Regras de firewall", escolha "Adicionar uma regra de firewall". Isso abrirá
o painel para adicionar uma nova regra de firewall.
Insira um "Nome de regra" exclusivo e, em seguida, insira o endereço IP da
mensagem de erro nos campos "IP inicial" e "IP final".
Caso o acesso ao banco seja realizado através de endereços IP alocados para
qualquer serviço ou ativo do Azure, marcar o campo “Exceções: Permitir que serviços
e recursos do Azure acessem este servidor”
Clique em "OK".
Clique em "Salvar".
Execute novamente o comando.


<BR>
   
<img src="images/fireWallConfigurado.png" alt="" style="width: 55%; display: block;"/>

<BR>


## 5 - CRUD em um Banco de Dados

Neste ponto da prática, foi solicitada a criação, conexão e
manipulação de um banco de dados SQL no ambiente Azure. Utilizando instruções T-
SQL, abordaremos desde a criação de tabelas até operações CRUD (Create, Read,
Update, Delete).

 
A atividade inclui a criação de uma tabela denominada "Drivers" com atributos
específicos. Posteriormente, verificaremos a existência da tabela, inseriremos dados de
exemplo, realizaremos consultas para leitura, efetuaremos atualizações e exclusões,
concluindo com a verificação da tabela vazia.

obs: no meu caso, optei por usar o management sql server realizando uma coneção a
minha conta na azure

<BR>
   
<img src="images/conectandoManagementAzure.png" alt="" style="width: 55%; display: block;"/>

<BR>

- Operação de criação de tabela: Na sessão do management, executando a instrução
T-SQL para criar uma tabela chamada Drivers. A tabela é composta por quatro
colunas: um identificador exclusivo, sobrenome, nome do motorista e cidade de
origem do motorista.

CREATE TABLE Drivers (DriverID int, LastName varchar(255), FirstName varchar(255),
OriginCity varchar(255));

GO

<BR>
   
<img src="images/criarTBDrivers.atividade5.png" alt="" style="width: 55%; display: block;"/>

<BR>

- Verificação da Existência da Tabela Drivers: 2.    Execute as seguintes instruções T-
SQL para verificar se a tabela Drivers existe. Você deverá obter uma saída conforme a
imagem a seguir.

SELECT name FROM sys.tables;

GO

<BR>
   
<img src="images/verificacao.systable.png" alt="" style="width: 55%; display: block;"/>

<BR>

- Operação de inserção: Para testar a operação de criação de registros no banco de
dados, execute as instruções T-SQL a seguir para adicionar uma linha de exemplo à
tabela.

INSERT INTO Drivers (DriverID, LastName, FirstName, OriginCity) VALUES (754, 'Silva',
'João', 'Rio de Janeiro');

GO

# Missão Prática | Tirando proveito da nuvem para projetos de software


## Projeto de Banco de Dados: 

 - Considerando o seguinte contexto

Como líder de desenvolvimento de software, você propõe o desenvolvimento de um
protótipo que inclui a criação de um banco de dados no Azure SQL. Este banco de
dados será projetado para armazenar informações cruciais, incluindo:
 

  - Dados dos motoristas: informações pessoais, qualificações, histórico de viagens.

  - Informações dos clientes: detalhes de contato, histórico de pedidos, preferências.
  
  - Detalhes dos pedidos: informações do pedido, status, cronograma de entrega.

O protótipo servirá como base para o aplicativo de produção futuro. Portanto, as
escolhas tecnológicas feitas agora devem ser escaláveis e compatíveis com as
soluções finais.

### Scripts

 1) Banco de dados


```  
CREATE DATABASE [LogiMovTransport]  (EDITION = 'GeneralPurpose', 
SERVICE_OBJECTIVE = 'GP_Gen5_2', MAXSIZE = 32 GB) WITH CATALOG_COLLATION = SQL_Latin1_General_CP1_CI_AS, LEDGER = OFF;

GO

ALTER DATABASE [LogiMovTransport] SET ANSI_NULL_DEFAULT OFF 
GO

ALTER DATABASE [LogiMovTransport] SET ANSI_NULLS OFF 
GO

ALTER DATABASE [LogiMovTransport] SET ANSI_PADDING OFF 
GO

ALTER DATABASE [LogiMovTransport] SET ANSI_WARNINGS OFF 
GO

ALTER DATABASE [LogiMovTransport] SET ARITHABORT OFF 
GO

ALTER DATABASE [LogiMovTransport] SET AUTO_SHRINK OFF 
GO

ALTER DATABASE [LogiMovTransport] SET AUTO_UPDATE_STATISTICS ON 
GO

ALTER DATABASE [LogiMovTransport] SET CURSOR_CLOSE_ON_COMMIT OFF 
GO

ALTER DATABASE [LogiMovTransport] SET CONCAT_NULL_YIELDS_NULL OFF 
GO

ALTER DATABASE [LogiMovTransport] SET NUMERIC_ROUNDABORT OFF 
GO

ALTER DATABASE [LogiMovTransport] SET QUOTED_IDENTIFIER OFF 
GO

ALTER DATABASE [LogiMovTransport] SET RECURSIVE_TRIGGERS OFF 
GO

ALTER DATABASE [LogiMovTransport] SET AUTO_UPDATE_STATISTICS_ASYNC OFF 
GO

ALTER DATABASE [LogiMovTransport] SET ALLOW_SNAPSHOT_ISOLATION ON 
GO

ALTER DATABASE [LogiMovTransport] SET PARAMETERIZATION SIMPLE 
GO

ALTER DATABASE [LogiMovTransport] SET READ_COMMITTED_SNAPSHOT ON 
GO

ALTER DATABASE [LogiMovTransport] SET  MULTI_USER 
GO

ALTER DATABASE [LogiMovTransport] SET ENCRYPTION ON
GO

ALTER DATABASE [LogiMovTransport] SET QUERY_STORE = ON
GO

ALTER DATABASE [LogiMovTransport] SET QUERY_STORE (OPERATION_MODE = READ_WRITE, CLEANUP_POLICY = (STALE_QUERY_THRESHOLD_DAYS = 30), DATA_FLUSH_INTERVAL_SECONDS = 900, INTERVAL_LENGTH_MINUTES = 60, MAX_STORAGE_SIZE_MB = 100, QUERY_CAPTURE_MODE = AUTO, SIZE_BASED_CLEANUP_MODE = AUTO, MAX_PLANS_PER_QUERY = 200, WAIT_STATS_CAPTURE_MODE = ON)
GO

/*** 

The scripts of database scoped configurations in Azure should be 
executed inside the target database connection. 

***/
GO

-- ALTER DATABASE SCOPED CONFIGURATION SET MAXDOP = 8;
GO

ALTER DATABASE [LogiMovTransport] SET  READ_WRITE 
GO

```
 
2) Scripts Tabelas

```

/** Drivers **/

SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE TABLE [Drivers](
	[DriverID] [int] NOT NULL,
	[Nome] [varchar](100) NULL,
	[CNH] [varchar](20) NULL,
	[Endereço] [varchar](200) NULL,
	[Contato] [varchar](50) NULL,
PRIMARY KEY CLUSTERED 
(
	[DriverID] ASC
)WITH (STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO


/** DriverQualifications **/


SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE TABLE [DriverQualifications](
	[QualificationID] [int] NOT NULL,
	[DriverID] [int] NULL,
	[Qualificação] [varchar](100) NULL,
	[DataObtenção] [date] NULL,
	[Validade] [date] NULL,
PRIMARY KEY CLUSTERED 
(
	[QualificationID] ASC
)WITH (STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO

ALTER TABLE [DriverQualifications]  WITH CHECK ADD FOREIGN KEY([DriverID])
REFERENCES [Drivers] ([DriverID])
GO

/** DriverTravelHistory **/

SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE TABLE [DriverTravelHistory](
	[TravelID] [int] NOT NULL,
	[DriverID] [int] NULL,
	[DataViagem] [date] NULL,
	[Origem] [varchar](200) NULL,
	[Destino] [varchar](200) NULL,
	[DistanciaPercorrida] [float] NULL,
PRIMARY KEY CLUSTERED 
(
	[TravelID] ASC
)WITH (STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO

ALTER TABLE [DriverTravelHistory]  WITH CHECK ADD FOREIGN KEY([DriverID])
REFERENCES [Drivers] ([DriverID])
GO

/** Clients **/


SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE TABLE [Clients](
	[ClientID] [int] NOT NULL,
	[Nome] [varchar](100) NULL,
	[Empresa] [varchar](100) NULL,
	[Endereço] [varchar](200) NULL,
	[Contato] [varchar](50) NULL,
PRIMARY KEY CLUSTERED 
(
	[ClientID] ASC
)WITH (STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO

/** ClientPreferences **/

SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE TABLE [ClientPreferences](
	[PreferenceID] [int] NOT NULL,
	[ClientID] [int] NULL,
	[Preferencia] [text] NULL,
PRIMARY KEY CLUSTERED 
(
	[PreferenceID] ASC
)WITH (STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO

ALTER TABLE [ClientPreferences]  WITH CHECK ADD FOREIGN KEY([ClientID])
REFERENCES [Clients] ([ClientID])
GO

/** Orders **/


SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE TABLE [Orders](
	[OrderID] [int] NOT NULL,
	[ClientID] [int] NULL,
	[DriverID] [int] NULL,
	[DetalhesPedido] [text] NULL,
	[DataEntrega] [date] NULL,
	[Status] [varchar](50) NULL,
PRIMARY KEY CLUSTERED 
(
	[OrderID] ASC
)WITH (STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO

ALTER TABLE [Orders]  WITH CHECK ADD FOREIGN KEY([ClientID])
REFERENCES [Clients] ([ClientID])
GO

ALTER TABLE [Orders]  WITH CHECK ADD FOREIGN KEY([DriverID])
REFERENCES [Drivers] ([DriverID])
GO

/** OrderStatusHistory **/


SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE TABLE [OrderStatusHistory](
	[StatusHistoryID] [int] NOT NULL,
	[OrderID] [int] NULL,
	[StatusAnterior] [varchar](50) NULL,
	[StatusAtual] [varchar](50) NULL,
	[DataMudança] [date] NULL,
PRIMARY KEY CLUSTERED 
(
	[StatusHistoryID] ASC
)WITH (STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO

ALTER TABLE [OrderStatusHistory]  WITH CHECK ADD FOREIGN KEY([OrderID])
REFERENCES [Orders] ([OrderID])
GO

/** ClientOrderHistory **/


SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE TABLE [ClientOrderHistory](
	[HistoryID] [int] NOT NULL,
	[OrderID] [int] NULL,
	[ClientID] [int] NULL,
	[DataPedido] [date] NULL,
	[ResumoPedido] [text] NULL,
PRIMARY KEY CLUSTERED 
(
	[HistoryID] ASC
)WITH (STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO

ALTER TABLE [ClientOrderHistory]  WITH CHECK ADD FOREIGN KEY([ClientID])
REFERENCES [Clients] ([ClientID])
GO

ALTER TABLE [ClientOrderHistory]  WITH CHECK ADD FOREIGN KEY([OrderID])
REFERENCES [Orders] ([OrderID])
GO
 
```

3) Manipulação de dados (CRUD)

Objetivos

- Inserção e Gestão de Dado
  Dados de teste inseridos nas tabelas, cobrindo diferentes cenários e casos de
uso.

```

### SQL

-- Inserção de Motoristas

INSERT INTO Drivers (DriverID, Nome, CNH, Endereço, Contato) VALUES
(1, 'João Silva', '123456789', 'Rua das Flores, 100', '11987654321'),
(2, 'Maria Oliveira', '987654321', 'Avenida do Sol, 200', '11976543210');

```

<BR>
   
<img src="images/LogiMovTransport.drivers.insert.png" alt="" style="width: 65%; display: block;"/>

<BR>

```
### SQL

-- Inserção de Qualificações dos Motoristas

INSERT INTO DriverQualifications (QualificationID, DriverID, Qualificação, DataObtenção, Validade) VALUES
(1, 1, 'Transporte de Cargas Perigosas', '2023-01-10', '2025-01-10'),
(2, 2, 'Transporte Internacional', '2023-02-15', '2025-02-15');

```
<BR>
   
<img src="images/LogiMovTransport.DriverQualifications.insert.png" alt="" style="width: 65%; display: block;"/>

<BR>

```
### SQL

-- Inserção de Histórico de Viagens

INSERT INTO DriverTravelHistory (TravelID, DriverID, DataViagem, Origem, Destino, DistanciaPercorrida) VALUES
(1, 1, '2024-04-01', 'São Paulo', 'Rio de Janeiro', 430.5),
(2, 2, '2024-04-02', 'Curitiba', 'Porto Alegre', 711.0);

```

<BR>
   
<img src="images/LogiMovTransport.DriverTravelHistory.insert.png" alt="" style="width: 65%; display: block;"/>

<BR>


```
### SQL

-- Inserção de Clientes

INSERT INTO Clients (ClientID, Nome, Empresa, Endereço, Contato) VALUES
(1, 'Empresa A', 'A Ltda', 'Rua A, 50', '11333445566'),
(2, 'Empresa B', 'B S.A.', 'Avenida B, 100', '11222444666');
```


<BR>
   
<img src="images/LogiMovTransport.Clients.insert.png" alt="" style="width: 65%; display: block;"/>

<BR>


```
### SQL

-- Inserção de Preferências dos Clientes

INSERT INTO ClientPreferences (PreferenceID, ClientID, Preferencia) VALUES
(1, 1, 'Preferência por transportes rápidos e seguros'),
(2, 2, 'Preferência por custo baixo');

```


<BR>
   
<img src="images/LogiMovTransport.ClientPreferences.insert.png" alt="" style="width: 65%; display: block;"/>

<BR>




```
### SQL

-- Inserção de Pedidos

INSERT INTO Orders (OrderID, ClientID, DriverID, DetalhesPedido, DataEntrega, Status) VALUES
(1, 1, 1, '50 caixas de material inflamável', '2024-04-05', 'Entregue'),
(2, 2, 2, '100 unidades de eletrônicos', '2024-04-06', 'Em trânsito');
```


<BR>
   
<img src="images/LogiMovTransport.Orders.insert.png" alt="" style="width: 65%; display: block;"/>

<BR>


```
### SQL

-- Inserção de Histórico de Status dos Pedidos

INSERT INTO OrderStatusHistory (StatusHistoryID, OrderID, StatusAnterior, StatusAtual, DataMudança) VALUES
(1, 1, 'Em preparação', 'Entregue', '2024-04-05'),
(2, 2, 'Aguardando coleta', 'Em trânsito', '2024-04-03');
```


<BR>
   
<img src="images/LogiMovTransport.OrderStatusHistory.insert.png" alt="" style="width: 65%; display: block;"/>

<BR>




```
### SQL

-- Inserção de Histórico de Pedidos dos Clientes

INSERT INTO ClientOrderHistory (HistoryID, OrderID, ClientID, DataPedido, ResumoPedido) VALUES
(1, 1, 1, '2024-04-01', 'Pedido de 50 caixas de material inflamável'),
(2, 2, 2, '2024-04-02', 'Pedido de 100 unidades de eletrônicos');
```


<BR>
   
<img src="images/LogiMovTransport.ClientOrderHistory.insert.png" alt="" style="width: 65%; display: block;"/>

<BR>

- Execução e Validação de Consultas:
Consultas T-SQL executadas com sucesso, com capacidade de recuperar, filtrar e ordenar dados conforme necessário.


```
### SQL

-- Consulta para encontrar todos os motoristas com suas qualificações

SELECT d.Nome, dq.Qualificação, dq.DataObtenção, dq.Validade
FROM Drivers d
JOIN DriverQualifications dq ON d.DriverID = dq.DriverID;

```

<BR>
   
<img src="images/LogiMovTransport.select.motoristas_com_suas_qualificacoes.png" alt="" style="width: 65%; display: block;"/>

<BR>


```
### SQL

-- Consulta para listar todos os pedidos e seus status atuais

SELECT o.OrderID, c.Nome as Cliente, d.Nome as Motorista, o.DetalhesPedido, o.Status
FROM Orders o
JOIN Clients c ON o.ClientID = c.ClientID
JOIN Drivers d ON o.DriverID = d.DriverID;

```

<BR>
   
<img src="images/LogiMovTransport.select.pedidos_e_seus_status_atuais.png" alt="" style="width: 65%; display: block;"/>

<BR>



```
### SQL

-- Consulta para encontrar viagens realizadas em um determinado período

SELECT dt.DataViagem, dt.Origem, dt.Destino, dt.DistanciaPercorrida
FROM DriverTravelHistory dt
WHERE dt.DataViagem BETWEEN '2024-04-01' AND '2024-04-30';
```


<BR>
   
<img src="images/LogiMovTransport.select.viagens_realizadas_em_determinado_período.png" alt="" style="width: 65%; display: block;"/>

<BR>



- Operações CRUD Eficientes:
Demonstração de operações CRUD - Criar, Ler, Atualizar e Deletar dados.


#### Criar (Insert)

Já demonstrado acima com a inserção inicial de dados.

#### Ler (Select)

```sql
-- Ler informações de um motorista específico
SELECT * FROM Drivers WHERE DriverID = 1;
```

#### Atualizar (Update)

```sql
-- Atualizar o endereço de um cliente
UPDATE Clients SET Endereço = 'Nova Avenida, 200' WHERE ClientID = 1;
```

#### Deletar (Delete)

```sql
-- Deletar um histórico de viagem
DELETE FROM DriverTravelHistory WHERE TravelID = 1;
```
 






