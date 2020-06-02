---
title: Mise à jour des sources de données avec les DataAdapter
description: Découvrez comment la méthode de mise à jour de DataAdapter résout les modifications apportées à un jeu de données dans la source de données dans les applications ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: e2348a3a89aa1c28856bfc21aaa25f2c8327aac7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286182"
---
# <a name="updating-data-sources-with-dataadapters"></a>Mise à jour des sources de données avec les DataAdapter

La méthode `Update` de l'objet <xref:System.Data.Common.DataAdapter> est appelée pour répercuter les modifications d'un objet <xref:System.Data.DataSet> dans la source de données. La méthode `Update`, comme la méthode `Fill`, prend comme arguments une instance d’un `DataSet` et un objet <xref:System.Data.DataTable> optionnel ou un nom de `DataTable`. L'instance `DataSet` est le `DataSet` qui contient les modifications apportées et le `DataTable` identifie la table de laquelle les modifications doivent être récupérées. Si aucun `DataTable` n'est spécifié, le premier `DataTable` du `DataSet` est utilisé.

Lorsque vous appelez la méthode `Update`, le `DataAdapter` analyse les modifications apportées et exécute la commande appropriée (INSERT, UPDATE ou DELETE). Lorsque le `DataAdapter` rencontre une modification apportée à un objet <xref:System.Data.DataRow>, il utilise la propriété <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, ou <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> pour traiter la modification. Cela vous permet d'optimiser les performances de votre application ADO.NET en spécifiant la syntaxe de commande au moment du design et, si possible, par le biais de l'utilisation de procédures stockées. Vous devez explicitement définir les commandes avant d'appeler la méthode `Update`. Si la méthode `Update` est appelée et si la commande appropriée n'existe pas pour une mise à jour particulière (par exemple, pas de `DeleteCommand` pour les lignes supprimées), une exception est levée.

> [!NOTE]
> Si vous utilisez des procédures stockées SQL Server pour modifier ou supprimer des données à l'aide de `DataAdapter`, assurez-vous que vous n'utilisez pas SET NOCOUNT ON dans la définition de procédure stockée. En effet, le nombre de lignes affectées retourné serait alors la valeur zéro, ce que `DataAdapter` interprète comme un conflit d'accès concurrentiel. Dans ce cas, l'exception <xref:System.Data.DBConcurrencyException> est levée.

Des paramètres de commande peuvent être utilisés pour spécifier les valeurs d'entrée et de sortie d'une instruction SQL ou d'une procédure stockée pour chaque ligne modifiée dans un `DataSet`. Pour plus d’informations, consultez [paramètres DataAdapter](dataadapter-parameters.md).

> [!NOTE]
> Il est important de comprendre la différence entre la suppression d'une ligne dans un objet <xref:System.Data.DataTable> et la suppression de la ligne. Lorsque vous appelez la méthode `Remove` ou `RemoveAt`, la ligne est immédiatement supprimée. Aucune ligne correspondante dans la source de données principale ne sera affectée si vous passez ensuite le `DataTable` ou le `DataSet` à un `DataAdapter` et appelez la méthode `Update`. Lorsque vous utilisez la méthode `Delete`, la ligne reste dans le `DataTable` et est marquée pour suppression. Si vous passez ensuite le `DataTable` ou le `DataSet` à un `DataAdapter` et appelez la méthode `Update`, la ligne correspondante dans la source de données principale est supprimée.

Si votre `DataTable` est mappé à une table de base de données unique ou est généré par celle-ci, vous pouvez tirer parti de l'objet <xref:System.Data.Common.DbCommandBuilder> pour générer automatiquement les objets `DeleteCommand`, `InsertCommand` et `UpdateCommand` du `DataAdapter`. Pour plus d’informations, consultez [génération de commandes avec CommandBuilders](generating-commands-with-commandbuilders.md).

## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a>Utilisation d'UpdatedRowSource pour mapper des valeurs à un DataSet

Vous pouvez contrôler la façon dont les valeurs retournées depuis la source de données sont de nouveau mappées au `DataTable` suite à un appel de la méthode Update d'un `DataAdapter`, en utilisant la propriété <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> d'un objet <xref:System.Data.Common.DbCommand>. En affectant l'une des valeurs d'énumération `UpdatedRowSource` à la propriété <xref:System.Data.UpdateRowSource>, vous pouvez contrôler si les paramètres de sortie retournés par les commandes `DataAdapter` sont ignorés ou appliqués à la ligne modifiée dans le `DataSet`. Vous pouvez aussi spécifier si la première ligne retournée (si elle existe) doit être appliquée à la ligne modifiée dans le `DataTable`.

Le tableau suivant décrit les différentes valeurs de l'énumération `UpdateRowSource` et la façon dont elles affectent le comportement d'une commande utilisée avec un `DataAdapter`.

|Énumération UpdatedRowSource|Description|
|----------------------------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|Les paramètres de sortie et la première ligne d'un jeu de résultats retourné peuvent être mappés à la ligne modifiée dans le `DataSet`.|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Seules les données de la première ligne d'un jeu de résultats retourné peuvent être mappées à la ligne modifiée dans le `DataSet`.|
|<xref:System.Data.UpdateRowSource.None>|Les paramètres de sortie ou les lignes d'un jeu de résultats retourné sont ignorés.|
|<xref:System.Data.UpdateRowSource.OutputParameters>|Seuls les paramètres de sortie peuvent être mappés à la ligne modifiée dans le `DataSet`.|

La méthode `Update` répercute vos modifications dans la source de données, cependant d'autres clients peuvent avoir modifié les données au niveau de la source depuis la dernière fois où vous avez rempli le `DataSet`. Pour actualiser votre `DataSet` avec des données en cours, utilisez le `DataAdapter` et la méthode `Fill`. De nouvelles lignes seront ajoutées à la table et les informations mises à jour seront incorporées dans les lignes existantes. La méthode `Fill` détermine si une nouvelle ligne sera ajoutée ou si une ligne existante sera mise à jour en se basant sur les valeurs de clé primaire des lignes du `DataSet` et des lignes retournées par `SelectCommand`. Si une valeur de clé primaire d'une ligne du `Fill` correspond à celle d'une ligne des résultats retournés par `DataSet`, la méthode `SelectCommand` met à jour la ligne existante en y insérant les informations de la ligne retournée par `SelectCommand` et affecte la valeur <xref:System.Data.DataRow.RowState%2A> à la propriété `Unchanged`. Si la valeur de clé primaire d'une ligne retournée par `SelectCommand` n'a pas de correspondance dans les lignes du `DataSet`, la méthode `Fill` ajoute une nouvelle ligne avec un `RowState` ayant la valeur `Unchanged`.

> [!NOTE]
> Si `SelectCommand` retourne les résultats d'un OUTER JOIN, le `DataAdapter` ne définit pas la valeur `PrimaryKey` du `DataTable` résultant. Vous devez définir vous-même la `PrimaryKey` pour garantir une résolution correcte des lignes dupliquées. Pour plus d’informations, consultez [définition des clés primaires](./dataset-datatable-dataview/defining-primary-keys.md).

Pour gérer les exceptions qui peuvent se produire lors de l’appel de la `Update` méthode, vous pouvez utiliser l' `RowUpdated` événement pour répondre aux erreurs de mise à jour de ligne dès qu’elles se produisent (consultez [gestion des événements DataAdapter](handling-dataadapter-events.md)), ou vous pouvez affecter la valeur `DataAdapter.ContinueUpdateOnError` avant d' `true` appeler `Update` et répondre aux informations d’erreur stockées dans la `RowError` propriété d’une ligne particulière lorsque la mise à jour est terminée [Row Error Information](./dataset-datatable-dataview/row-error-information.md)

> [!NOTE]
> L’appel `AcceptChanges` de sur `DataSet` , `DataTable` ou `DataRow` entraîne le remplacement de toutes les `Original` valeurs d’un par `DataRow` les `Current` valeurs de `DataRow` . Si les valeurs de champ qui identifient la ligne comme étant unique ont été modifiées, après l'appel de `AcceptChanges`, les valeurs `Original` ne correspondront plus aux valeurs de la source de données. `AcceptChanges` est appelé automatiquement pour chaque ligne au cours de l'appel de la méthode Update d'un `DataAdapter`. Vous pouvez conserver les valeurs d'origine au cours d'un appel de la méthode Update en commençant par affecter la valeur false à la propriété `AcceptChangesDuringUpdate` du `DataAdapter`, ou en créant un gestionnaire d'événements pour l'événement `RowUpdated` et en affectant la valeur <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> à <xref:System.Data.UpdateStatus.SkipCurrentRow>. Pour plus d’informations, consultez [fusion du contenu des datasets](./dataset-datatable-dataview/merging-dataset-contents.md) et [gestion des événements DataAdapter](handling-dataadapter-events.md).

## <a name="example"></a>Exemple

Les exemples suivants montrent comment effectuer des mises à jour vers des lignes modifiées en définissant explicitement le `UpdateCommand` d’un `DataAdapter` et en appelant sa `Update` méthode. Notez que le paramètre spécifié dans la clause WHERE de l'instruction UPDATE est défini pour utiliser la valeur `Original` du `SourceColumn`. Cela est important car la valeur `Current` peut avoir été modifiée et ne pas correspondre à la valeur dans la source de données. La valeur `Original` est la valeur qui a été utilisée pour remplir le `DataTable` à partir de la source de données.

[!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]

## <a name="autoincrement-columns"></a>Colonnes AutoIncrement

Si les tables de votre source de données ont des colonnes à incrémentation automatique, vous pouvez remplir les colonnes de votre `DataSet` soit en retournant la valeur d'auto-incrémentation comme paramètre de sortie d'une procédure stockée et en la mappant à une colonne dans une table, soit en utilisant l'événement `RowUpdated` du `DataAdapter` pour exécuter une instruction SELECT supplémentaire. Pour plus d’informations et pour obtenir un exemple, consultez [extraction des valeurs d’identité ou de numérotation NuméroAuto](retrieving-identity-or-autonumber-values.md).

## <a name="ordering-of-inserts-updates-and-deletes"></a>Ordre des insertions, mises à jour et suppressions

Dans de nombreuses circonstances, l'ordre dans lequel les modifications apportées dans le `DataSet` sont transmises à la source de données est important. Par exemple, si une valeur de clé primaire d'une ligne existante est mise à jour et qu'une nouvelle ligne est ajoutée avec la nouvelle valeur de clé primaire en tant que clé primaire, il est important de traiter la mise à jour avant l'insertion.

Vous pouvez utiliser la méthode `Select` du `DataTable` pour retourner un tableau `DataRow` qui fait uniquement référence à des lignes ayant un `RowState` particulier. Vous pouvez ensuite passer le tableau `DataRow` retourné à la méthode `Update` du `DataAdapter` pour traiter les lignes modifiées. En spécifiant un sous-ensemble des lignes à mettre à jour, vous pouvez contrôler l'ordre dans lequel les insertions, mises à jour et suppressions sont traitées.

## <a name="example"></a>Exemple

Le code suivant garantit, par exemple, que seront d'abord traitées les lignes supprimées de la table puis les lignes mises à jour et enfin les lignes insérées.

```vb
Dim table As DataTable = dataSet.Tables("Customers")

' First process deletes.
dataSet.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Deleted))

' Next process updates.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.ModifiedCurrent))

' Finally, process inserts.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Added))
```

```csharp
DataTable table = dataSet.Tables["Customers"];

// First process deletes.
adapter.Update(table.Select(null, null, DataViewRowState.Deleted));

// Next process updates.
adapter.Update(table.Select(null, null,
  DataViewRowState.ModifiedCurrent));

// Finally, process inserts.
adapter.Update(table.Select(null, null, DataViewRowState.Added));
```

## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a>Utiliser un DataAdapter pour récupérer et mettre à jour des données

Vous pouvez utiliser un DataAdapter pour récupérer et mettre à jour les données.

- Cet exemple utilise DataAdapter.AcceptChangesDuringFill pour cloner les données dans la base de données. Si la propriété a la valeur False, AcceptChanges n'est pas appelé lors du remplissage de la table, et les lignes récemment ajoutées sont traitées comme des lignes insérées. Ainsi, l'exemple utilise ces lignes pour insérer de nouvelles lignes dans la base de données.

- Cet exemple utilise DataAdapter.TableMappings pour définir le mappage entre la table source et DataTable.

- Cet exemple utilise DataAdapter.FillLoadOption pour déterminer comment l'adaptateur remplit DataTable à partir de DbDataReader. Lorsque vous créez un DataTable, vous pouvez uniquement écrire les données de la base de données dans la version actuelle ou la version d'origine en définissant la propriété comme LoadOption.Upsert ou LoadOption.PreserveChanges.

- L'exemple met également à jour la table à l'aide de DbDataAdapter.UpdateBatchSize pour effectuer des opérations par lots.

Avant de compiler et d'exécuter l'exemple, vous devez créer l'exemple de base de données :

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

ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])
REFERENCES [dbo].[Department] ([DepartmentID])
GO
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]
GO
```

Vous trouverez des projets C# et Visual Basic avec cet exemple de code dans les [exemples de code pour développeurs](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).

```csharp
using System;
using System.Data;
using System.Data.Common;
using System.Data.SqlClient;
using System.Linq;
using CSDataAdapterOperations.Properties;

namespace CSDataAdapterOperations.Properties {
   internal sealed partial class Settings : global::System.Configuration.ApplicationSettingsBase {

      private static Settings defaultInstance = ((Settings)(global::System.Configuration.ApplicationSettingsBase.Synchronized(new Settings())));

      public static Settings Default {
         get {
            return defaultInstance;
         }
      }

      [global::System.Configuration.ApplicationScopedSettingAttribute()]
      [global::System.Configuration.DefaultSettingValueAttribute("Data Source=(local);Initial Catalog=MySchool;Integrated Security=True")]
      public string MySchoolConnectionString {
         get {
            return ((string)(this["MySchoolConnectionString"]));
         }
      }
   }
}

class Program {
   static void Main(string[] args) {
      Settings settings = new Settings();

      // Copy the data from the database.  Get the table Department and Course from the database.
      String selectString = @"SELECT [DepartmentID],[Name],[Budget],[StartDate],[Administrator]
                                     FROM [MySchool].[dbo].[Department];

                                   SELECT [CourseID],@Year as [Year],Max([Title]) as [Title],
                                   Max([Credits]) as [Credits],Max([DepartmentID]) as [DepartmentID]
                                   FROM [MySchool].[dbo].[Course]
                                   Group by [CourseID]";

      DataSet mySchool = new DataSet();

      SqlCommand selectCommand = new SqlCommand(selectString);
      SqlParameter parameter = selectCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2);
      parameter.Value = new Random(DateTime.Now.Millisecond).Next(9999);

      // Use DataTableMapping to map the source tables and the destination tables.
      DataTableMapping[] tableMappings = {new DataTableMapping("Table", "Department"), new DataTableMapping("Table1", "Course")};
      CopyData(mySchool, settings.MySchoolConnectionString, selectCommand, tableMappings);

      Console.WriteLine("The following tables are from the database.");
      foreach (DataTable table in mySchool.Tables) {
         Console.WriteLine(table.TableName);
         ShowDataTable(table);
      }

      // Roll back the changes
      DataTable department = mySchool.Tables["Department"];
      DataTable course = mySchool.Tables["Course"];

      department.Rows[0]["Name"] = "New" + department.Rows[0][1];
      course.Rows[0]["Title"] = "New" + course.Rows[0]["Title"];
      course.Rows[0]["Credits"] = 10;

      Console.WriteLine("After we changed the tables:");
      foreach (DataTable table in mySchool.Tables) {
         Console.WriteLine(table.TableName);
         ShowDataTable(table);
      }

      department.RejectChanges();
      Console.WriteLine("After use the RejectChanges method in Department table to roll back the changes:");
      ShowDataTable(department);

      DataColumn[] primaryColumns = { course.Columns["CourseID"] };
      DataColumn[] resetColumns = { course.Columns["Title"] };
      ResetCourse(course, settings.MySchoolConnectionString, primaryColumns, resetColumns);
      Console.WriteLine("After use the ResetCourse method in Course table to roll back the changes:");
      ShowDataTable(course);

      // Batch update the table.
      String insertString = @"Insert into [MySchool].[dbo].[Course]([CourseID],[Year],[Title],
                                   [Credits],[DepartmentID])
             values (@CourseID,@Year,@Title,@Credits,@DepartmentID)";
      SqlCommand insertCommand = new SqlCommand(insertString);
      insertCommand.Parameters.Add("@CourseID", SqlDbType.NVarChar, 10, "CourseID");
      insertCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2, "Year");
      insertCommand.Parameters.Add("@Title", SqlDbType.NVarChar, 100, "Title");
      insertCommand.Parameters.Add("@Credits", SqlDbType.Int, 4, "Credits");
      insertCommand.Parameters.Add("@DepartmentID", SqlDbType.Int, 4, "DepartmentID");

      const Int32 batchSize = 10;
      BatchInsertUpdate(course, settings.MySchoolConnectionString, insertCommand, batchSize);
   }

   private static void CopyData(DataSet dataSet, String connectionString, SqlCommand selectCommand, DataTableMapping[] tableMappings) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         selectCommand.Connection = connection;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {adapter.TableMappings.AddRange(tableMappings);
            // If set the AcceptChangesDuringFill as the false, AcceptChanges will not be called on a
            // DataRow after it is added to the DataTable during any of the Fill operations.
            adapter.AcceptChangesDuringFill = false;

            adapter.Fill(dataSet);
         }
      }
   }

   // Roll back only one column or several columns data of the Course table by call ResetDataTable method.
   private static void ResetCourse(DataTable table, String connectionString,
       DataColumn[] primaryColumns, DataColumn[] resetColumns) {
      table.PrimaryKey = primaryColumns;

      // Build the query string
      String primaryCols = String.Join(",", primaryColumns.Select(col => col.ColumnName));
      String resetCols = String.Join(",", resetColumns.Select(col => $"Max({col.ColumnName}) as {col.ColumnName}"));

      String selectString = $"Select {primaryCols},{resetCols} from Course Group by {primaryCols}");

      SqlCommand selectCommand = new SqlCommand(selectString);

      ResetDataTable(table, connectionString, selectCommand);
   }

   // RejectChanges will roll back all changes made to the table since it was loaded, or the last time AcceptChanges
   // was called. When you copy from the database, you can lose all the data after calling RejectChanges
   // The ResetDataTable method rolls back one or more columns of data.
   private static void ResetDataTable(DataTable table, String connectionString,
       SqlCommand selectCommand) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         selectCommand.Connection = connection;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {
            // The incoming values for this row will be written to the current version of each
            // column. The original version of each column's data will not be changed.
            adapter.FillLoadOption = LoadOption.Upsert;

            adapter.Fill(table);
         }
      }
   }

   private static void BatchInsertUpdate(DataTable table, String connectionString,
       SqlCommand insertCommand, Int32 batchSize) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         insertCommand.Connection = connection;
         // When setting UpdateBatchSize to a value other than 1, all the commands
         // associated with the SqlDataAdapter have to have their UpdatedRowSource
         // property set to None or OutputParameters. An exception is thrown otherwise.
         insertCommand.UpdatedRowSource = UpdateRowSource.None;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter()) {
            adapter.InsertCommand = insertCommand;
            // Gets or sets the number of rows that are processed in each round-trip to the server.
            // Setting it to 1 disables batch updates, as rows are sent one at a time.
            adapter.UpdateBatchSize = batchSize;

            adapter.Update(table);

            Console.WriteLine("Successfully to update the table.");
         }
      }
   }

   private static void ShowDataTable(DataTable table) {
      foreach (DataColumn col in table.Columns) {
         Console.Write("{0,-14}", col.ColumnName);
      }
      Console.WriteLine("{0,-14}", "RowState");

      foreach (DataRow row in table.Rows) {
         foreach (DataColumn col in table.Columns) {
            if (col.DataType.Equals(typeof(DateTime)))
               Console.Write("{0,-14:d}", row[col]);
            else if (col.DataType.Equals(typeof(Decimal)))
               Console.Write("{0,-14:C}", row[col]);
            else
               Console.Write("{0,-14}", row[col]);
         }
         Console.WriteLine("{0,-14}", row.RowState);
      }
   }
}
```

## <a name="see-also"></a>Voir aussi

- [DataAdapters et DataReaders](dataadapters-and-datareaders.md)
- [États des lignes et versions des lignes](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [AcceptChanges et RejectChanges](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [Fusion de contenu de DataSet](./dataset-datatable-dataview/merging-dataset-contents.md)
- [Récupération de valeurs d’identité ou de numérotation automatique](retrieving-identity-or-autonumber-values.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
