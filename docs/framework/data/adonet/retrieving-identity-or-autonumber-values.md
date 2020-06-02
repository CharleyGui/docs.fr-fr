---
title: Extraction de l'identité ou de valeurs à numérotation automatique
description: Découvrez comment récupérer les valeurs d’identité et de numérotation automatique des clés primaires dans les bases de données relationnelles, et comment fusionner les nouvelles valeurs d’identité dans ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6b7f9cb-81be-44e1-bb94-56137954876d
ms.openlocfilehash: dbbc013a5b6c83391a29109beca44120c68d827f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286570"
---
# <a name="retrieving-identity-or-autonumber-values"></a>Extraction de l'identité ou de valeurs à numérotation automatique

Dans une base de données relationnelle, une clé primaire est une colonne ou une combinaison de colonnes qui contient toujours des valeurs uniques. Si vous connaissez la valeur d'une clé primaire, vous pouvez rechercher la ligne qui la contient. Les moteurs de base de données relationnelle, comme SQL Server, Oracle et Microsoft Access/Jet prennent en charge la création de colonnes à incrémentation automatique qui peuvent être désignées comme clés primaires. Ces valeurs sont générées par le serveur lorsque des lignes sont ajoutées à une table. Dans SQL Server, vous définissez la propriété d'identité d'une colonne, dans Oracle vous créez une séquence et dans Microsoft Access vous créez une colonne NuméroAuto.

Un objet <xref:System.Data.DataColumn> peut également être utilisé pour générer des valeurs d'auto-incrémentation en affectant la valeur true à <xref:System.Data.DataColumn.AutoIncrement%2A>. Cependant, vous risquez de vous retrouver avec des valeurs dupliquées dans des instances distinctes d'un objet <xref:System.Data.DataTable>, si plusieurs applications clientes génèrent chacune de leur côté des valeurs d'auto-incrémentation. Le fait de laisser le serveur générer des valeurs d'auto-incrémentation supprime les conflits potentiels en permettant à chaque utilisateur de récupérer la valeur générée pour chaque ligne insérée.

Au cours d'un appel de la méthode `Update` d'un objet `DataAdapter`, la base de données peut renvoyer des données à votre application ADO.NET sous la forme de paramètres de sortie ou de premier enregistrement retourné du jeu de résultats d'une instruction SELECT exécutée dans le même lot que l'instruction INSERT. ADO.NET peut récupérer ces valeurs et mettre à jour les colonnes correspondantes dans l'objet <xref:System.Data.DataRow> en cours de mise à jour.

Certains moteurs de base de données, comme Microsoft Access Jet, ne prennent pas en charge les paramètres de sortie et ne peuvent pas traiter plusieurs instructions dans un même lot. Avec le moteur de base de données Jet, vous pouvez récupérer la nouvelle valeur NuméroAuto générée pour une ligne insérée en exécutant une commande SELECT distincte dans un gestionnaire d'événements pour l'événement `RowUpdated` de l'objet `DataAdapter`.

> [!NOTE]
> Plutôt que d'utiliser une valeur d'auto-incrémentation, vous pouvez utiliser la méthode <xref:System.Guid.NewGuid%2A> d'un objet <xref:System.Guid> pour générer un GUID, ou identificateur global unique, sur l'ordinateur client qui peut être copié sur le serveur dès qu'une nouvelle ligne est insérée. La méthode `NewGuid` génère une valeur binaire encodée sur 16 octets créée à l'aide d'un algorithme qui offre une forte probabilité qu'aucun valeur ne sera dupliquée. Dans une base de données SQL Server, un GUID est stocké dans une colonne `uniqueidentifier` qui peut être générée automatiquement par SQL Server à l'aide de la fonction `NEWID()` Transact-SQL. L'utilisation d'un GUID comme clé primaire peut nuire aux performances. SQL Server prend en charge la `NEWSEQUENTIALID()` fonction, qui génère un GUID séquentiel dont l’unicité globale n’est pas garantie, mais qui peut être indexé de manière plus efficace.

## <a name="retrieving-sql-server-identity-column-values"></a>Extraction de valeurs de colonne d'identité SQL Server

Avec Microsoft SQL Server, vous pouvez créer une procédure stockée contenant un paramètre de sortie qui permet de retourner la valeur d'identité d'une ligne insérée. Le tableau suivant décrit les trois fonctions Transact-SQL disponibles dans SQL Server qui peuvent être utilisées pour récupérer la valeur des colonnes d'identité.

|Fonction|Description|
|--------------|-----------------|
|SCOPE_IDENTITY|Retourne la dernière valeur d'identité de la portée d'exécution actuelle. La fonction SCOPE_IDENTITY est recommandée dans la plupart des scénarios.|
|@@IDENTITY|Contient la dernière valeur d'identité générée dans toute table de la session active. @ @IDENTITY peut être affecté par les déclencheurs et peut ne pas retourner la valeur d’identité que vous attendez.|
|IDENT_CURRENT|Retourne la dernière valeur d'identité générée pour une table spécifique dans toute session et portée.|

 La procédure stockée suivante montre comment insérer une ligne dans la table **categories** et utiliser un paramètre OUTPUT pour retourner la nouvelle valeur d’identité générée par la fonction Transact-SQL SCOPE_IDENTITY ().

```sql
CREATE PROCEDURE dbo.InsertCategory
  @CategoryName nvarchar(15),
  @Identity int OUT
AS
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)
SET @Identity = SCOPE_IDENTITY()
```

La procédure stockée peut ensuite être spécifiée comme source de la propriété <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> d'un objet <xref:System.Data.SqlClient.SqlDataAdapter>. La propriété <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> de la propriété <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> doit avoir la valeur <xref:System.Data.CommandType.StoredProcedure>. La sortie d'identité est récupérée en créant un objet <xref:System.Data.SqlClient.SqlParameter> dont un objet <xref:System.Data.ParameterDirection> a la valeur <xref:System.Data.ParameterDirection.Output>. Lorsque le `InsertCommand` est traité, la valeur d’identité auto-incrémentée est retournée et placée dans la colonne **CategoryID** de la ligne actuelle si vous affectez à la <xref:System.Data.SqlClient.SqlCommand.UpdatedRowSource%2A> propriété de la commande INSERT la valeur `UpdateRowSource.OutputParameters` ou à `UpdateRowSource.Both` .

Si la commande d'insertion exécute un lot qui comprend à la fois une instruction INSERT et une instruction SELECT qui retourne la nouvelle valeur d'identité, vous pouvez alors récupérer la nouvelle valeur en affectant la valeur `UpdatedRowSource` à la propriété `UpdateRowSource.FirstReturnedRecord`.

[!code-csharp[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/VB/source.vb#1)]

## <a name="merging-new-identity-values"></a>Fusion des nouvelles valeurs d'identité

Un scénario courant consiste à appeler la méthode `GetChanges` d'un objet `DataTable` pour créer une copie qui contient uniquement les lignes modifiées et pour utiliser une nouvelle copie lors de l'appel de la méthode `Update` d'un objet `DataAdapter`. Ceci s'avère très utile lorsque vous avez besoin de marshaler les lignes modifiées dans un autre composant qui effectue la mise à jour. Après la mise à jour, la copie peut contenir les nouvelles valeurs d’identité qui doivent ensuite être de nouveau fusionnées dans l’objet `DataTable` d’origine. Il est probable que les nouvelles valeurs d'identité soient différentes des valeurs d'origine de l'objet `DataTable`. Pour effectuer la fusion, les valeurs d’origine des colonnes **AutoIncrement** de la copie doivent être conservées, afin de pouvoir Rechercher et mettre à jour les lignes existantes dans le d’origine `DataTable` , au lieu d’ajouter de nouvelles lignes contenant les nouvelles valeurs d’identité. Pourtant, par défaut ces valeurs d'origine sont perdues après un appel de la méthode `Update` d'un objet `DataAdapter`, car la méthode `AcceptChanges` est appelée implicitement pour chaque objet `DataRow` mis à jour.

Il existe deux façons de conserver les valeurs d'origine d'un objet `DataColumn` dans un objet `DataRow` pendant la mise à jour d'un objet `DataAdapter` :

- La première méthode de conservation des valeurs d'origine consiste à affecter la valeur `AcceptChangesDuringUpdate` à la propriété `DataAdapter` de l'objet `false`. Cela affecte tous les objets `DataRow` de l'objet `DataTable` en cours de mise à jour. Pour obtenir des informations supplémentaires ainsi qu'un exemple de code, consultez <xref:System.Data.Common.DataAdapter.AcceptChangesDuringUpdate%2A>.

- La seconde méthode consiste à écrire du code dans le gestionnaire d'événements `RowUpdated` de l'objet `DataAdapter` de manière à affecter la valeur <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> à la propriété <xref:System.Data.UpdateStatus.SkipCurrentRow>. L'objet `DataRow` est mis à jour mais la valeur d'origine de chaque objet `DataColumn` est conservée. Cette méthode permet de conserver la valeur d'origine de certaines lignes et pas d'autres. Votre code peut par exemple conserver les valeurs d'origine des lignes ajoutées, mais pas des lignes modifiées ou supprimées en vérifiant tout d'abord la propriété <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A>, puis en affectant la valeur <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> à la propriété <xref:System.Data.UpdateStatus.SkipCurrentRow> uniquement pour les lignes dont `StatementType` a la valeur `Insert`.

Si l'une de ces méthodes est utilisée pour conserver les valeurs d'origine dans un objet `DataRow` au cours de la mise à jour d'un objet `DataAdapter`, ADO.NET effectue une série d'actions afin d'affecter à l'objet `DataRow` les nouvelles valeurs retournées par des paramètres de sortie ou par la première ligne retournée d'un jeu de résultats, tout en continuant de conserver la valeur d'origine dans chaque objet `DataColumn`. Dans un premier temps, la méthode `AcceptChanges` de l'objet `DataRow` est appelée pour conserver les valeurs actuelles comme valeurs d'origine, puis les nouvelles valeurs sont assignées. Suite à cela, les objets `DataRows` dont la propriété <xref:System.Data.DataRow.RowState%2A> avait la valeur <xref:System.Data.DataRowState.Added> verront leur propriété `RowState` remplacée par <xref:System.Data.DataRowState.Modified>, ce qui peut être inattendu.

La manière dont les résultats de la commande sont appliqués à chaque objet <xref:System.Data.DataRow> en cours de mise à jour est déterminé par la propriété <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> de chaque <xref:System.Data.Common.DbCommand>. Une valeur de l'énumération `UpdateRowSource` est affectée à cette propriété.

Le tableau suivant décrit comment les valeurs de l'énumération `UpdateRowSource` affectent la propriété <xref:System.Data.DataRow.RowState%2A> des lignes mises à jour.

|Nom de membre|Description|
|-----------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|La méthode `AcceptChanges` est appelée et les valeurs des deux paramètres de sortie et/ou les valeurs de la première ligne de tout jeu de résultats retourné sont placées dans l'objet `DataRow` en cours de mise à jour. S'il n'y a aucune valeur à appliquer, l'objet `RowState` aura la valeur <xref:System.Data.DataRowState.Unchanged>.|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Si une ligne a été retournée, la méthode `AcceptChanges` est appelée et la ligne est mappée à la ligne modifiée dans l'objet `DataTable`, ce qui affecte la valeur `RowState` à `Modified`. Si aucune ligne n'est retournée, la méthode `AcceptChanges` n'est pas appelée et l'objet `RowState` conserve la valeur `Added`.|
|<xref:System.Data.UpdateRowSource.None>|Tous les paramètres et toutes les lignes retournés sont ignorés. La méthode `AcceptChanges` n'est pas appelée et `RowState` conserve la valeur `Added`.|
|<xref:System.Data.UpdateRowSource.OutputParameters>|La méthode `AcceptChanges` est appelée et tout paramètre de sortie est mappé à la ligne modifiée dans l'objet `DataTable`, ce qui affecte la valeur `RowState` à l'objet `Modified`. S'il n'existe aucun paramètres de sortie, l'objet `RowState` aura la valeur `Unchanged`.|

### <a name="example"></a>Exemple

Cet exemple illustre l'extraction des lignes modifiées d'un objet `DataTable` et l'utilisation d'un objet <xref:System.Data.SqlClient.SqlDataAdapter> pour mettre à jour la source de données et récupérer une nouvelle valeur de colonne d'identité. La propriété <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> exécute deux instructions Transact-SQL (INSERT et SELECT) qui utilisent la fonction SCOPE_IDENTITY pour récupérer la valeur d'identité.

```sql
INSERT INTO dbo.Shippers (CompanyName)
VALUES (@CompanyName);
SELECT ShipperID, CompanyName FROM dbo.Shippers
WHERE ShipperID = SCOPE_IDENTITY();
```

La propriété `UpdatedRowSource` de la commande d'insertion a la valeur `UpdateRowSource.FirstReturnedRow` et la propriété <xref:System.Data.MissingSchemaAction> de l'objet `DataAdapter` a la valeur `MissingSchemaAction.AddWithKey`. L'objet `DataTable` est rempli et le code ajoute une nouvelle ligne à l'objet `DataTable`. Les lignes modifiées sont ensuite extraites dans un nouvel objet `DataTable`, qui est passé à l'objet `DataAdapter`, qui met ensuite à jour le serveur.

[!code-csharp[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#1)]

Le gestionnaire d'événements `OnRowUpdated` vérifie la propriété <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> de l'objet <xref:System.Data.SqlClient.SqlRowUpdatedEventArgs> de manière à déterminer si la ligne est une insertion. S'il s'agit d'une insertion, la propriété <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> a la valeur <xref:System.Data.UpdateStatus.SkipCurrentRow>. La ligne est mise à jour, mais ses valeurs d'origine sont conservées. Dans le corps principal de la procédure, la méthode <xref:System.Data.DataSet.Merge%2A> est appelée pour fusionner la nouvelle valeur d’identité dans l’objet `DataTable` d’origine et pour finir la méthode `AcceptChanges` est appelée.

[!code-csharp[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#2)]
[!code-vb[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#2)]

## <a name="retrieving-microsoft-access-autonumber-values"></a>Extraction des valeurs de champs NuméroAuto de Microsoft Access

Cette section comprend un exemple qui montre comment récupérer des valeurs `Autonumber` dans une base de données Jet 4.0. Le moteur de base de données Jet ne prend pas en charge l'exécution de plusieurs instructions dans un lot ni l'utilisation de paramètres de sortie. Il n'est donc pas possible d'utiliser l'une ou l'autre de ces techniques pour retourner la nouvelle valeur `Autonumber` assignée à la ligne insérée. Toutefois, vous pouvez ajouter du code au `RowUpdated` Gestionnaire d’événements qui exécute une instruction SELECT @ distincte @IDENTITY pour récupérer la nouvelle `Autonumber` valeur.

### <a name="example"></a>Exemple

Plutôt que d'ajouter des informations de schéma à l'aide de `MissingSchemaAction.AddWithKey`, cet exemple configure un objet `DataTable` avec le schéma correct avant d'appeler l'objet <xref:System.Data.OleDb.OleDbDataAdapter> pour remplir l'objet `DataTable`. Dans ce cas, la colonne **CategoryID** est configurée de façon à décrémenter la valeur assignée à chaque ligne insérée à partir de zéro, en affectant à la valeur, la valeur 0 à et la valeur <xref:System.Data.DataColumn.AutoIncrement%2A> `true` <xref:System.Data.DataColumn.AutoIncrementSeed%2A> <xref:System.Data.DataColumn.AutoIncrementStep%2A> -1 à. Le code ajoute ensuite deux nouvelles lignes et utilise `GetChanges` pour ajouter les lignes modifiées à un nouvel objet `DataTable` qui est passé à la méthode `Update`.

[!code-csharp[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#1)]
[!code-vb[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#1)]

Le gestionnaire d'événements `RowUpdated` utilise le même objet <xref:System.Data.OleDb.OleDbConnection> ouvert que l'instruction `Update` de l'objet `OleDbDataAdapter`. Il vérifie le `StatementType` de l'objet <xref:System.Data.OleDb.OleDbRowUpdatedEventArgs> pour les lignes insérées. Pour chaque ligne insérée, une nouvelle <xref:System.Data.OleDb.OleDbCommand> est créée pour exécuter l' @IDENTITY instruction SELECT @ sur la connexion, en retournant la nouvelle `Autonumber` valeur, qui est placée dans la colonne **CategoryID** de `DataRow` . La valeur `Status` est ensuite affectée à la propriété `UpdateStatus.SkipCurrentRow` pour supprimer l'appel masqué à la méthode `AcceptChanges`. Dans le corps principal de la procédure, la méthode `Merge` est appelée pour fusionner les deux objets `DataTable` et pour finir la méthode `AcceptChanges` est appelée.

[!code-csharp[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#2)]
[!code-vb[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#2)]

### <a name="retrieving-identity-values"></a>Récupération de valeurs d'identité

Nous définissons souvent la colonne en tant qu'identité lorsque les valeurs de la colonne doivent être uniques. Et nous avons parfois besoin de la valeur d'identité de nouvelles données. Cet exemple montre comment récupérer des valeurs d'identité :

- Il crée une procédure stockée pour insérer des données et retourner une valeur d'identité.

- Il exécute une commande pour insérer les nouvelles données et afficher le résultat.

- Il utilise <xref:System.Data.SqlClient.SqlDataAdapter> pour insérer de nouvelles données et afficher le résultat.

Avant de compiler et d'exécuter l'exemple, vous devez créer l'exemple de base de données, à l'aide du script suivant :

```sql
USE [master]
GO

CREATE DATABASE [MySchool]
GO

USE [MySchool]
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE procedure [dbo].[CourseExtInfo] @CourseId int
as
select c.CourseID,c.Title,c.Credits,d.Name as DepartmentName
from Course as c left outer join Department as d on c.DepartmentID=d.DepartmentID
where c.CourseID=@CourseId

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
create procedure [dbo].[DepartmentInfo] @DepartmentId int,@CourseCount int output
as
select @CourseCount=Count(c.CourseID)
from course as c
where c.DepartmentID=@DepartmentId

select d.DepartmentID,d.Name,d.Budget,d.StartDate,d.Administrator
from Department as d
where d.DepartmentID=@DepartmentId

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
Create PROCEDURE [dbo].[GetDepartmentsOfSpecifiedYear]
@Year int,@BudgetSum money output
AS
BEGIN
        SELECT @BudgetSum=SUM([Budget])
  FROM [MySchool].[dbo].[Department]
  Where YEAR([StartDate])=@Year

SELECT [DepartmentID]
      ,[Name]
      ,[Budget]
      ,[StartDate]
      ,[Administrator]
  FROM [MySchool].[dbo].[Department]
  Where YEAR([StartDate])=@Year

END
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE PROCEDURE [dbo].[GradeOfStudent]
-- Add the parameters for the stored procedure here
@CourseTitle nvarchar(100),@FirstName nvarchar(50),
@LastName nvarchar(50),@Grade decimal(3,2) output
AS
BEGIN
select @Grade=Max(Grade)
from [dbo].[StudentGrade] as s join [dbo].[Course] as c on
s.CourseID=c.CourseID join [dbo].[Person] as p on s.StudentID=p.PersonID
where c.Title=@CourseTitle and p.FirstName=@FirstName
and p.LastName= @LastName
END
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE PROCEDURE [dbo].[InsertPerson]
-- Add the parameters for the stored procedure here
@FirstName nvarchar(50),@LastName nvarchar(50),
@PersonID int output
AS
BEGIN
    insert [dbo].[Person](LastName,FirstName) Values(@LastName,@FirstName)

    set @PersonID=SCOPE_IDENTITY()
END
Go

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Course]([CourseID] [nvarchar](10) NOT NULL,
[Year] [smallint] NOT NULL,
[Title] [nvarchar](100) NOT NULL,
[Credits] [int] NOT NULL,
[DepartmentID] [int] NOT NULL,
 CONSTRAINT [PK_Course] PRIMARY KEY CLUSTERED
(
[CourseID] ASC,
[Year] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Department]([DepartmentID] [int] IDENTITY(1,1) NOT NULL,
[Name] [nvarchar](50) NOT NULL,
[Budget] [money] NOT NULL,
[StartDate] [datetime] NOT NULL,
[Administrator] [int] NULL,
 CONSTRAINT [PK_Department] PRIMARY KEY CLUSTERED
(
[DepartmentID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
SET ANSI_PADDING ON
GO
CREATE TABLE [dbo].[Person]([PersonID] [int] IDENTITY(1,1) NOT NULL,
[LastName] [nvarchar](50) NOT NULL,
[FirstName] [nvarchar](50) NOT NULL,
[HireDate] [datetime] NULL,
[EnrollmentDate] [datetime] NULL,
[Picture] [varbinary](max) NULL,
 CONSTRAINT [PK_School.Student] PRIMARY KEY CLUSTERED
(
[PersonID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[StudentGrade]([EnrollmentID] [int] IDENTITY(1,1) NOT NULL,
[CourseID] [nvarchar](10) NOT NULL,
[StudentID] [int] NOT NULL,
[Grade] [decimal](3, 2) NOT NULL,
 CONSTRAINT [PK_StudentGrade] PRIMARY KEY CLUSTERED
(
[EnrollmentID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
create view [dbo].[EnglishCourse]
as
select c.CourseID,c.Title,c.Credits,c.DepartmentID
from Course as c join Department as d on c.DepartmentID=d.DepartmentID
where d.Name=N'English'

GO
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1045', 2012, N'Calculus', 4, 7)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1061', 2012, N'Physics', 4, 1)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2021', 2012, N'Composition', 3, 2)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2042', 2012, N'Literature', 4, 2)
SET IDENTITY_INSERT [dbo].[Department] ON

INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (1, N'Engineering', 350000.0000, CAST(0x0000999C00000000 AS DateTime), 2)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (2, N'English', 120000.0000, CAST(0x0000999C00000000 AS DateTime), 6)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (4, N'Economics', 200000.0000, CAST(0x0000999C00000000 AS DateTime), 4)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (7, N'Mathematics', 250024.0000, CAST(0x0000999C00000000 AS DateTime), 3)
SET IDENTITY_INSERT [dbo].[Department] OFF
SET IDENTITY_INSERT [dbo].[Person] ON

INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (1, N'Hu', N'Nan', NULL, CAST(0x0000A0BF00000000 AS DateTime))
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (2, N'Norman', N'Laura', NULL, CAST(0x0000A0BF00000000 AS DateTime))
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (3, N'Olivotto', N'Nino', NULL, CAST(0x0000A0BF00000000 AS DateTime))
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (4, N'Anand', N'Arturo', NULL, CAST(0x0000A0BF00000000 AS DateTime))
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (5, N'Jai', N'Damien', NULL, CAST(0x0000A0BF00000000 AS DateTime))
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (6, N'Holt', N'Roger', CAST(0x000097F100000000 AS DateTime), NULL)
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (7, N'Martin', N'Randall', CAST(0x00008B1A00000000 AS DateTime), NULL)
SET IDENTITY_INSERT [dbo].[Person] OFF
SET IDENTITY_INSERT [dbo].[StudentGrade] ON

INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (1, N'C1045', 1, CAST(3.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (2, N'C1045', 2, CAST(3.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (3, N'C1045', 3, CAST(2.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (4, N'C1045', 4, CAST(4.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (5, N'C1045', 5, CAST(3.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (6, N'C1061', 1, CAST(4.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (7, N'C1061', 3, CAST(3.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (8, N'C1061', 4, CAST(2.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (9, N'C1061', 5, CAST(1.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (10, N'C2021', 1, CAST(2.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (11, N'C2021', 2, CAST(3.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (12, N'C2021', 4, CAST(3.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (13, N'C2021', 5, CAST(3.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (14, N'C2042', 1, CAST(2.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (15, N'C2042', 2, CAST(3.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (16, N'C2042', 3, CAST(4.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (17, N'C2042', 5, CAST(3.00 AS Decimal(3, 2)))
SET IDENTITY_INSERT [dbo].[StudentGrade] OFF
ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])
REFERENCES [dbo].[Department] ([DepartmentID])
GO
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]
GO
ALTER TABLE [dbo].[StudentGrade]  WITH CHECK ADD  CONSTRAINT [FK_StudentGrade_Student] FOREIGN KEY([StudentID])
REFERENCES [dbo].[Person] ([PersonID])
GO
ALTER TABLE [dbo].[StudentGrade] CHECK CONSTRAINT [FK_StudentGrade_Student]
GO
```

Voici le code complet :

> [!TIP]
> Le code complet fait référence à un fichier de base de données Access appelé MySchool.mdb. Vous pouvez télécharger MySchool. mdb (dans le cadre de l’exemple de projet C# ou Visual Basic complet) à partir de [code.msdn.Microsoft.com](https://code.msdn.microsoft.com/How-to-Retrieve-the-511acece).

```csharp
using System;
using System.Data;
using System.Data.OleDb;
using System.Data.SqlClient;

class Program {
   static void Main(string[] args) {
      String SqlDbConnectionString = "Data Source=(local);Initial Catalog=MySchool;Integrated Security=True;Asynchronous Processing=true;";

      InsertPerson(SqlDbConnectionString, "Janice", "Galvin");
      Console.WriteLine();

      InsertPersonInAdapter(SqlDbConnectionString, "Peter", "Krebs");
      Console.WriteLine();

      String oledbConnectionString = "Provider=Microsoft.Jet.OLEDB.4.0; Data Source=Database\\MySchool.mdb";
      InsertPersonInJet4Database(oledbConnectionString, "Janice", "Galvin");
      Console.WriteLine();

      Console.WriteLine("Please press any key to exit.....");
      Console.ReadKey();
   }

   // Using stored procedure to insert a new row and retrieve the identity value
   static void InsertPerson(String connectionString, String firstName, String lastName) {
      String commandText = "dbo.InsertPerson";

      using (SqlConnection conn = new SqlConnection(connectionString)) {
         using (SqlCommand cmd = new SqlCommand(commandText, conn)) {
            cmd.CommandType = CommandType.StoredProcedure;

            cmd.Parameters.Add(new SqlParameter("@FirstName", firstName));
            cmd.Parameters.Add(new SqlParameter("@LastName", lastName));
            SqlParameter personId = new SqlParameter("@PersonID", SqlDbType.Int);
            personId.Direction = ParameterDirection.Output;
            cmd.Parameters.Add(personId);

            conn.Open();
            cmd.ExecuteNonQuery();

            Console.WriteLine("Person Id of new person:{0}", personId.Value);
         }
      }
   }

   // Using stored procedure in adapter to insert new rows and update the identity value.
   static void InsertPersonInAdapter(String connectionString, String firstName, String lastName) {
      String commandText = "dbo.InsertPerson";
      using (SqlConnection conn = new SqlConnection(connectionString)) {
         SqlDataAdapter mySchool = new SqlDataAdapter("Select PersonID,FirstName,LastName from [dbo].[Person]", conn);

         mySchool.InsertCommand = new SqlCommand(commandText, conn);
         mySchool.InsertCommand.CommandType = CommandType.StoredProcedure;

         mySchool.InsertCommand.Parameters.Add(
             new SqlParameter("@FirstName", SqlDbType.NVarChar, 50, "FirstName"));
         mySchool.InsertCommand.Parameters.Add(
             new SqlParameter("@LastName", SqlDbType.NVarChar, 50, "LastName"));

         SqlParameter personId = mySchool.InsertCommand.Parameters.Add(new SqlParameter("@PersonID", SqlDbType.Int, 0, "PersonID"));
         personId.Direction = ParameterDirection.Output;

         DataTable persons = new DataTable();
         mySchool.Fill(persons);

         DataRow newPerson = persons.NewRow();
         newPerson["FirstName"] = firstName;
         newPerson["LastName"] = lastName;
         persons.Rows.Add(newPerson);

         mySchool.Update(persons);
         Console.WriteLine("Show all persons:");
         ShowDataTable(persons, 14);
      }
   }

   /// For a Jet 4.0 database, we need use the single statement and event handler to insert new rows and retrieve the identity value.
   static void InsertPersonInJet4Database(String connectionString, String firstName, String lastName) {
      String commandText = "Insert into Person(FirstName,LastName) Values(?,?)";
      using (OleDbConnection conn = new OleDbConnection(connectionString)) {
         OleDbDataAdapter mySchool = new OleDbDataAdapter("Select PersonID,FirstName,LastName from Person", conn);

         // Create Insert Command
         mySchool.InsertCommand = new OleDbCommand(commandText, conn);
         mySchool.InsertCommand.CommandType = CommandType.Text;

         mySchool.InsertCommand.Parameters.Add(new OleDbParameter("@FirstName", OleDbType.VarChar, 50, "FirstName"));
         mySchool.InsertCommand.Parameters.Add(new OleDbParameter("@LastName", OleDbType.VarChar, 50, "LastName"));
         mySchool.InsertCommand.UpdatedRowSource = UpdateRowSource.Both;

         DataTable persons = CreatePersonsTable();

         mySchool.Fill(persons);

         DataRow newPerson = persons.NewRow();
         newPerson["FirstName"] = firstName;
         newPerson["LastName"] = lastName;
         persons.Rows.Add(newPerson);

         DataTable dataChanges = persons.GetChanges();

         mySchool.RowUpdated += OnRowUpdated;

         mySchool.Update(dataChanges);

         Console.WriteLine("Data before merging:");
         ShowDataTable(persons, 14);
         Console.WriteLine();

         persons.Merge(dataChanges);
         persons.AcceptChanges();

         Console.WriteLine("Data after merging");
         ShowDataTable(persons, 14);
      }
   }

   static void OnRowUpdated(object sender, OleDbRowUpdatedEventArgs e) {
      if (e.StatementType == StatementType.Insert) {
         // Retrieve the identity value
         OleDbCommand cmdNewId = new OleDbCommand("Select @@IDENTITY", e.Command.Connection);
         e.Row["PersonID"] = (Int32)cmdNewId.ExecuteScalar();

         // After the status is changed, the original values in the row are preserved. And the
         // Merge method will be called to merge the new identity value into the original DataTable.
         e.Status = UpdateStatus.SkipCurrentRow;
      }
   }

   // Create the Persons table before filling.
   private static DataTable CreatePersonsTable() {
      DataTable persons = new DataTable();

      DataColumn personId = new DataColumn();
      personId.DataType = Type.GetType("System.Int32");
      personId.ColumnName = "PersonID";
      personId.AutoIncrement = true;
      personId.AutoIncrementSeed = 0;
      personId.AutoIncrementStep = -1;
      persons.Columns.Add(personId);

      DataColumn firstName = new DataColumn();
      firstName.DataType = Type.GetType("System.String");
      firstName.ColumnName = "FirstName";
      persons.Columns.Add(firstName);

      DataColumn lastName = new DataColumn();
      lastName.DataType = Type.GetType("System.String");
      lastName.ColumnName = "LastName";
      persons.Columns.Add(lastName);

      DataColumn[] pkey = { personId };
      persons.PrimaryKey = pkey;

      return persons;
   }

   private static void ShowDataTable(DataTable table, Int32 length) {
      foreach (DataColumn col in table.Columns) {
         Console.Write("{0,-" + length + "}", col.ColumnName);
      }
      Console.WriteLine();

      foreach (DataRow row in table.Rows) {
         foreach (DataColumn col in table.Columns) {
            if (col.DataType.Equals(typeof(DateTime)))
               Console.Write("{0,-" + length + ":d}", row[col]);
            else if (col.DataType.Equals(typeof(Decimal)))
               Console.Write("{0,-" + length + ":C}", row[col]);
            else
               Console.Write("{0,-" + length + "}", row[col]);
         }

         Console.WriteLine();
      }
   }
}
```

## <a name="see-also"></a>Voir aussi

- [Extraction et modification de données dans ADO.NET](retrieving-and-modifying-data.md)
- [DataAdapters et DataReaders](dataadapters-and-datareaders.md)
- [États des lignes et versions des lignes](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [AcceptChanges et RejectChanges](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [Fusion de contenu de DataSet](./dataset-datatable-dataview/merging-dataset-contents.md)
- [Mise à jour des sources de données avec les DataAdapter](updating-data-sources-with-dataadapters.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
