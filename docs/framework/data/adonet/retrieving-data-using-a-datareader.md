---
title: Récupération de données à l'aide d'un DataReader
description: Découvrez comment récupérer des données à l’aide d’un DataReader dans ADO.NET avec cet exemple de code. DataReader fournit un flux de données non mis en mémoire tampon.
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 6e5161cc325bf0379bb9241b99c473c539ad1081
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286596"
---
# <a name="retrieve-data-using-a-datareader"></a>Récupérer des données à l’aide d’un DataReader
Pour récupérer des données à l’aide d’un **DataReader**, créez une instance de l’objet de **commande** , puis créez un **DataReader** en appelant **Command. ExecuteReader** pour récupérer des lignes d’une source de données. Le **DataReader** fournit un flux de données non mis en mémoire tampon qui permet à la logique procédurale de traiter efficacement les résultats d’une source de données de manière séquentielle. Le **DataReader** est un bon choix lorsque vous récupérez de grandes quantités de données, car les données ne sont pas mises en cache dans la mémoire.

L’exemple suivant illustre l’utilisation d’un **DataReader**, où `reader` représente un DataReader valide et `command` représente un objet Command valide.  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

Utilisez la méthode **DataReader. Read** pour obtenir une ligne à partir des résultats de la requête. Vous pouvez accéder à chaque colonne de la ligne retournée en passant le nom ou le numéro ordinal de la colonne au **DataReader**. Toutefois, pour de meilleures performances, le **DataReader** fournit une série de méthodes qui vous permettent d’accéder aux valeurs de colonne dans leurs types de données natifs (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, etc.). Pour obtenir la liste des méthodes d’accesseur typées pour les **DataReaders**spécifiques au fournisseur de données, consultez <xref:System.Data.OleDb.OleDbDataReader> et <xref:System.Data.SqlClient.SqlDataReader> . L’utilisation des méthodes d’accesseur typées lorsque vous connaissez le type de données sous-jacent réduit la quantité de conversion de type requise lors de la récupération de la valeur de colonne.  
  
 L’exemple suivant itère au sein d’un objet **DataReader** et retourne deux colonnes de chaque ligne.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>Fermeture du DataReader  
 Appelez toujours la méthode **Close** lorsque vous avez fini d’utiliser l’objet **DataReader** .  
  
 Si votre **commande** contient des paramètres de sortie ou des valeurs de retour, ces valeurs ne sont pas disponibles tant que le **DataReader** n’est pas fermé.  
  
 Lorsqu’un **DataReader** est ouvert, la **connexion** est utilisée exclusivement par ce **DataReader**. Vous ne pouvez pas exécuter de commandes pour la **connexion**, notamment créer un autre **DataReader**, jusqu’à la fermeture du **DataReader** d’origine.  
  
> [!NOTE]
> N’appelez pas **Close** ou **dispose** sur une **connexion**, un **DataReader**ou tout autre objet managé dans la méthode **Finalize** de votre classe. Dans un finaliseur, libérez seulement les ressources non managées que votre classe possède directement. Si votre classe ne possède pas de ressources non managées, n’incluez pas de méthode **Finalize** dans votre définition de classe. Pour plus d’informations, consultez [garbage collection](../../../standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>Récupération de plusieurs jeux de résultats à l’aide de NextResult  
 Si le **DataReader** retourne plusieurs jeux de résultats, appelez la méthode **NextResult** pour effectuer une itération dans les jeux de résultats de manière séquentielle. L'exemple suivant montre l'objet <xref:System.Data.SqlClient.SqlDataReader> traitant les résultats de deux instructions SELECT utilisant la méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>Obtention d’informations de schéma à partir du DataReader  
 Lorsqu’un **DataReader** est ouvert, vous pouvez récupérer des informations de schéma sur le jeu de résultats actuel à l’aide de la méthode **GetSchemaTable** . **GetSchemaTable** retourne un <xref:System.Data.DataTable> objet rempli avec les lignes et les colonnes qui contiennent les informations de schéma pour le jeu de résultats actuel. Le **DataTable** contient une ligne pour chaque colonne du jeu de résultats. Chaque colonne de la table de schéma est mappée à une propriété des colonnes retournées dans les lignes du jeu de résultats, où **ColumnName** est le nom de la propriété et la valeur de la colonne est la valeur de la propriété. L’exemple suivant écrit les informations de schéma pour **DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>Utilisation des chapitres OLE DB  
 Les ensembles de lignes hiérarchiques ou chapitres (OLE DB type **DBTYPE_HCHAPTER**, type ADO **adChapter**), peuvent être récupérés à l’aide du <xref:System.Data.OleDb.OleDbDataReader> . Lorsqu’une requête qui comprend un chapitre est retournée en tant que **DataReader**, le chapitre est retourné en tant que colonne dans ce **DataReader** et est exposé en tant qu’objet **DataReader** .  
  
 Le **jeu de données** ADO.net peut également être utilisé pour représenter des ensembles de lignes hiérarchiques à l’aide de relations parent-enfant entre les tables. Pour plus d’informations, consultez [DataSets, DataTables et DataView](./dataset-datatable-dataview/index.md).  
  
 L'exemple de code suivant utilise le fournisseur MSDataShape pour générer une colonne chapitre de commandes pour chaque client d'une liste de clients.  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" &
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")

    Using custCMD As OleDbCommand = New OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " &
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " &
        "RELATE CustomerID TO CustomerID)", connection)

        connection.Open()

        Using custReader As OleDbDataReader = custCMD.ExecuteReader()

            Do While custReader.Read()
                Console.WriteLine("Orders for " & custReader.GetString(1))
                ' custReader.GetString(1) = CompanyName  

                Using orderReader As OleDbDataReader = custReader.GetValue(2)
                    ' custReader.GetValue(2) = Orders chapter as DataReader  

                    Do While orderReader.Read()
                        Console.WriteLine(vbTab & orderReader.GetInt32(1))
                        ' orderReader.GetInt32(1) = OrderID  
                    Loop
                    orderReader.Close()
                End Using
            Loop
            ' Make sure to always close readers and connections.  
            custReader.Close()
        End Using
    End Using
End Using
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" +
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"))
{
    using (OleDbCommand custCMD = new OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +
        "RELATE CustomerID TO CustomerID)", connection))
    {
        connection.Open();

        using (OleDbDataReader custReader = custCMD.ExecuteReader())
        {

            while (custReader.Read())
            {
                Console.WriteLine("Orders for " + custReader.GetString(1));
                // custReader.GetString(1) = CompanyName  

                using (OleDbDataReader orderReader = (OleDbDataReader)custReader.GetValue(2))
                {
                    // custReader.GetValue(2) = Orders chapter as DataReader  

                    while (orderReader.Read())
                        Console.WriteLine("\t" + orderReader.GetInt32(1));
                    // orderReader.GetInt32(1) = OrderID  
                    orderReader.Close();
                }
            }
            // Make sure to always close readers and connections.  
            custReader.Close();
        }
    }
}
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Retour de résultats avec des REF CURSOR Oracle  
 Le fournisseur de données .NET Framework pour Oracle prend en charge l'utilisation des REF CURSOR Oracle pour retourner le résultat d'une requête. Un REF CURSOR Oracle est retourné en tant qu'objet <xref:System.Data.OracleClient.OracleDataReader>.  
  
 Vous pouvez récupérer un <xref:System.Data.OracleClient.OracleDataReader> objet qui représente un REF CURSOR Oracle à l’aide de la <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> méthode. Vous pouvez également spécifier un <xref:System.Data.OracleClient.OracleCommand> qui retourne un ou plusieurs REF CURSOR Oracle comme **SelectCommand** pour un <xref:System.Data.OracleClient.OracleDataAdapter> utilisé pour remplir un <xref:System.Data.DataSet> .  
  
 Pour accéder à un REF CURSOR retourné à partir d’une source de données Oracle, créez un <xref:System.Data.OracleClient.OracleCommand> pour votre requête et ajoutez un paramètre de sortie qui référence le REF CURSOR à la <xref:System.Data.OracleClient.OracleCommand.Parameters> collection de votre <xref:System.Data.OracleClient.OracleCommand> . Le nom du paramètre doit correspondre à celui du paramètre REF CURSOR de votre requête. Définissez le type du paramètre sur <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> . La <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> méthode de votre <xref:System.Data.OracleClient.OracleCommand> retourne un <xref:System.Data.OracleClient.OracleDataReader> pour le REF CURSOR.  
  
 Si votre <xref:System.Data.OracleClient.OracleCommand> retourne plusieurs REF CURSOR, ajoutez plusieurs paramètres de sortie. Vous pouvez accéder aux différents REF CURSOR en appelant la <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> méthode. L’appel à <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> retourne un qui <xref:System.Data.OracleClient.OracleDataReader> référence le premier REF CURSOR. Vous pouvez ensuite appeler la <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> méthode pour accéder aux REF CURSOR suivants. Bien que les paramètres de votre <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection correspondent aux paramètres de sortie du REF CURSOR par leur nom, le <xref:System.Data.OracleClient.OracleDataReader> accède à ceux-ci dans l’ordre dans lequel ils ont été ajoutés à la <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.  
  
 Considérez, par exemple, le package et le corps de package Oracle suivants.  
  
```sql
CREATE OR REPLACE PACKAGE CURSPKG AS
  TYPE T_CURSOR IS REF CURSOR;
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,
    DEPTCURSOR OUT T_CURSOR);
END CURSPKG;  
  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,
    DEPTCURSOR OUT T_CURSOR)
  IS
  BEGIN
    OPEN EMPCURSOR FOR SELECT * FROM DEMO.EMPLOYEE;
    OPEN DEPTCURSOR FOR SELECT * FROM DEMO.DEPARTMENT;
  END OPEN_TWO_CURSORS;
END CURSPKG;
```  
  
 Le code suivant crée un <xref:System.Data.OracleClient.OracleCommand> qui retourne les REF CURSOR à partir du package Oracle précédent en ajoutant deux paramètres de type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> à la <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.  
  
```vb  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
```  
  
```csharp  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
```  
  
 Le code suivant retourne les résultats de la commande précédente à l’aide des <xref:System.Data.OracleClient.OracleDataReader.Read> <xref:System.Data.OracleClient.OracleDataReader.NextResult> méthodes et de <xref:System.Data.OracleClient.OracleDataReader> . Les paramètres REF CURSOR sont retournés dans l'ordre.  
  
```vb  
oraConn.Open()  
  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.CommandType = CommandType.StoredProcedure  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
  
Dim reader As OracleDataReader = cursCmd.ExecuteReader()  
  
Console.WriteLine(vbCrLf & "Emp ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2))  
Loop  
  
reader.NextResult()  
  
Console.WriteLine(vbCrLf & "Dept ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}", reader.GetOracleNumber(0), reader.GetString(1))  
Loop  
' Make sure to always close readers and connections.  
reader.Close()  
oraConn.Close()  
```  
  
```csharp  
oraConn.Open();  
  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.CommandType = CommandType.StoredProcedure;  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
  
OracleDataReader reader = cursCmd.ExecuteReader();  
  
Console.WriteLine("\nEmp ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2));  
  
reader.NextResult();  
  
Console.WriteLine("\nDept ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}", reader.GetOracleNumber(0), reader.GetString(1));  
// Make sure to always close readers and connections.  
reader.Close();  
oraConn.Close();  
```  
  
 L’exemple suivant utilise la commande précédente pour remplir un <xref:System.Data.DataSet> avec les résultats du package Oracle.  
  
```vb  
Dim ds As DataSet = New DataSet()  
  
Dim adapter As OracleDataAdapter = New OracleDataAdapter(cursCmd)  
adapter.TableMappings.Add("Table", "Employees")  
adapter.TableMappings.Add("Table1", "Departments")  
  
adapter.Fill(ds)  
```  
  
```csharp  
DataSet ds = new DataSet();  
  
OracleDataAdapter adapter = new OracleDataAdapter(cursCmd);  
adapter.TableMappings.Add("Table", "Employees");  
adapter.TableMappings.Add("Table1", "Departments");  
  
adapter.Fill(ds);  
```

> [!NOTE]
> Pour éviter une **exception OverflowException**, nous vous recommandons de gérer également toute conversion du type de nombre Oracle en un type de .NET Framework valide avant de stocker la valeur dans un <xref:System.Data.DataRow> . Vous pouvez utiliser l' <xref:System.Data.Common.DataAdapter.FillError> événement pour déterminer si une **exception OverflowException** s’est produite. Pour plus d’informations sur l' <xref:System.Data.Common.DataAdapter.FillError> événement, consultez [gestion des événements DataAdapter](handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Voir aussi

- [DataAdapters et DataReaders](dataadapters-and-datareaders.md)
- [Commandes et paramètres](commands-and-parameters.md)
- [Récupération des informations de schéma de base de données](retrieving-database-schema-information.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
