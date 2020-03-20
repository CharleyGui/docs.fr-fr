---
title: Récupération de données à l'aide d'un DataReader
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 88cd85ce343aaab08b944f81c9659918014da0a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149022"
---
# <a name="retrieve-data-using-a-datareader"></a>Récupérer les données à l’aide d’un lecteur de données
Pour récupérer des données à l’aide **d’un DataReader,** créez une instance de **l’objet de commande,** puis créez un **dataReader** en appelant **Command.ExecuteReader** pour récupérer les lignes d’une source de données. Le **DataReader** fournit un flux inbuffered de données qui permet à la logique procédurale de traiter efficacement les résultats d’une source de données séquentiellement. Le **DataReader** est un bon choix lorsque vous récupérez de grandes quantités de données parce que les données ne sont pas mises en cache dans la mémoire.

L’exemple suivant illustre l’utilisation d’un **DataReader**, où `reader` représente un DataReader valide et `command` représente un objet de commande valide.  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

Utilisez la méthode **DataReader.Read** pour obtenir une ligne à partir des résultats de la requête. Vous pouvez accéder à chaque colonne de la rangée retournée en passant le nom ou le numéro ordinaire de la colonne au **DataReader**. Cependant, pour les meilleures performances, le **DataReader** fournit une série de méthodes qui vous permettent d’accéder aux valeurs de colonne dans leurs types de données natives (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, et ainsi de suite). Pour une liste de méthodes d’accesseur dactylographiées pour **les lecteurs de données**spécifiques aux fournisseurs de données, voir <xref:System.Data.OleDb.OleDbDataReader> et <xref:System.Data.SqlClient.SqlDataReader>. L’utilisation des méthodes d’accesseur dactylographiques lorsque vous connaissez le type de données sous-jacent réduit la quantité de conversion de type requise lors de la récupération de la valeur de la colonne.  
  
 L’exemple suivant s’agite à travers un objet **DataReader** et renvoie deux colonnes de chaque rangée.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>Fermeture du DataReader  
 Appelez toujours la méthode **Close** lorsque vous avez terminé l’utilisation de l’objet **DataReader.**  
  
 Si votre **commande** contient des paramètres de sortie ou des valeurs de retour, ces valeurs ne sont pas disponibles tant que le **DataReader** n’est pas fermé.  
  
 Alors qu’un **DataReader** est ouvert, la **connexion** est utilisée exclusivement par celui **DataReader**. Vous ne pouvez pas exécuter de commandes pour la **connexion,** y compris la création d’un autre **DataReader**, jusqu’à ce que le **DataReader** d’origine soit fermé.  
  
> [!NOTE]
> N’appelez pas **Close** or **Dispose** on a **Connection**, un **DataReader**, ou tout autre objet géré dans la méthode **Finalize** de votre classe. Dans un finaliseur, libérez seulement les ressources non managées que votre classe possède directement. Si votre classe ne possède pas de ressources non gestions, n’incluez pas de méthode **De finalisation** dans votre définition de classe. Pour plus d’informations, voir [Collection des ordures](../../../standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>Récupération de plusieurs ensembles de résultats à l’aide de NextResult  
 Si le **DataReader** renvoie plusieurs ensembles de résultats, appelez la méthode **NextResult** pour itérer à travers les ensembles de résultats séquentiellement. L'exemple suivant montre l'objet <xref:System.Data.SqlClient.SqlDataReader> traitant les résultats de deux instructions SELECT utilisant la méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>Obtenir des informations sur les schémas du DataReader  
 Pendant qu’un **DataReader** est ouvert, vous pouvez récupérer des informations schéma sur l’ensemble de résultats en cours à l’aide de la méthode **GetSchemaTable.** **GetSchemaTable** renvoie un <xref:System.Data.DataTable> objet peuplé de lignes et de colonnes qui contiennent les informations schéma pour l’ensemble de résultats actuel. Le **DataTable** contient une ligne pour chaque colonne de l’ensemble de résultats. Chaque colonne des cartes de table schématique à une propriété des colonnes retournées dans les rangées de l’ensemble de résultat, où le **ColumnName** est le nom de la propriété et la valeur de la colonne est la valeur de la propriété. L’exemple suivant écrit les informations schéma pour **DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>Travailler avec les chapitres OLE DB  
 Les ramets hiérarchiques, ou chapitres **(type DB**OLE DBTYPE_HCHAPTER , ADO type **adChapter**), peuvent être récupérés à l’aide de la <xref:System.Data.OleDb.OleDbDataReader>. Lorsqu’une requête qui comprend un chapitre est retournée comme un **DataReader**, le chapitre est retourné comme une colonne dans celui **DataReader** et est exposé comme un objet **DataReader.**  
  
 Le ADO.NET **DataSet** peut également être utilisé pour représenter des jeux hiérarchiques en utilisant des relations parent-enfant entre les tables. Pour plus d’informations, consultez [DataSets, DataTables et DataViews](./dataset-datatable-dataview/index.md).  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Résultats de retour avec Oracle REF CURSORs  
 Le fournisseur de données .NET Framework pour Oracle prend en charge l'utilisation des REF CURSOR Oracle pour retourner le résultat d'une requête. Un REF CURSOR Oracle est retourné en tant qu'objet <xref:System.Data.OracleClient.OracleDataReader>.  
  
 Vous pouvez <xref:System.Data.OracleClient.OracleDataReader> récupérer un objet qui représente un <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> Oracle REF CURSOR en utilisant la méthode. Vous pouvez également <xref:System.Data.OracleClient.OracleCommand> spécifier un qui renvoie un ou plusieurs <xref:System.Data.OracleClient.OracleDataAdapter> Oracle REF <xref:System.Data.DataSet>CURSORs comme **le SelectCommand** pour un utilisé pour remplir un .  
  
 Pour accéder à un CURSOR REF retourné <xref:System.Data.OracleClient.OracleCommand> d’une source de données Oracle, créez un paramètre de sortie qui fait référence au CURSOR REF à la <xref:System.Data.OracleClient.OracleCommand.Parameters> collecte de votre <xref:System.Data.OracleClient.OracleCommand>. Le nom du paramètre doit correspondre à celui du paramètre REF CURSOR de votre requête. Définissez le type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>de paramètre à . La <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> méthode <xref:System.Data.OracleClient.OracleCommand> de <xref:System.Data.OracleClient.OracleDataReader> vos retours un pour le REF CURSOR.  
  
 Si <xref:System.Data.OracleClient.OracleCommand> vos retours plusieurs REF CURSORS, ajoutez plusieurs paramètres de sortie. Vous pouvez accéder aux différents CURSORs REF en appelant la <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> méthode. L’appel <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> pour <xref:System.Data.OracleClient.OracleDataReader> retourner un référencement du premier REF CURSOR. Vous pouvez ensuite <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> appeler la méthode pour accéder aux CURSORs REF ultérieures. Bien que les <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> paramètres de votre collection correspondent aux paramètres <xref:System.Data.OracleClient.OracleDataReader> de sortie REF CURSOR par leur <xref:System.Data.OracleClient.OracleCommand.Parameters> nom, les accès les accèdent dans l’ordre dans lequel ils ont été ajoutés à la collection.  
  
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
  
 Le code suivant <xref:System.Data.OracleClient.OracleCommand> crée un qui renvoie les CURSORs REF du <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> paquet <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> Oracle précédent en ajoutant deux paramètres de type à la collection.  
  
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
  
 Le code suivant renvoie les résultats <xref:System.Data.OracleClient.OracleDataReader.Read> <xref:System.Data.OracleClient.OracleDataReader.NextResult> de la <xref:System.Data.OracleClient.OracleDataReader>commande précédente en utilisant le et les méthodes de la . Les paramètres REF CURSOR sont retournés dans l'ordre.  
  
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
  
 L’exemple suivant utilise la commande <xref:System.Data.DataSet> précédente pour remplir un avec les résultats du paquet Oracle.  
  
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
> Pour éviter un **OverflowException**, nous vous recommandons également de gérer toute conversion du type Oracle <xref:System.Data.DataRow>NUMBER à un type de cadre .NET valide avant de stocker la valeur dans un . Vous pouvez <xref:System.Data.Common.DataAdapter.FillError> utiliser l’événement pour déterminer si un **DébordementException s’est** produit. Pour plus d’informations sur l’événement, <xref:System.Data.Common.DataAdapter.FillError> voir Handling [DataAdapter Events](handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Voir aussi

- [DataAdapters et DataReaders](dataadapters-and-datareaders.md)
- [Commandes et paramètres](commands-and-parameters.md)
- [Récupération des informations de schéma de base de données](retrieving-database-schema-information.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
