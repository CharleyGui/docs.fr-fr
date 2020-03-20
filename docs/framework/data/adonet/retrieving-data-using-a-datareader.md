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
# <a name="retrieve-data-using-a-datareader"></a><span data-ttu-id="7952d-102">Récupérer les données à l’aide d’un lecteur de données</span><span class="sxs-lookup"><span data-stu-id="7952d-102">Retrieve data using a DataReader</span></span>
<span data-ttu-id="7952d-103">Pour récupérer des données à l’aide **d’un DataReader,** créez une instance de **l’objet de commande,** puis créez un **dataReader** en appelant **Command.ExecuteReader** pour récupérer les lignes d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="7952d-103">To retrieve data using a **DataReader**, create an instance of the **Command** object, and then create a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="7952d-104">Le **DataReader** fournit un flux inbuffered de données qui permet à la logique procédurale de traiter efficacement les résultats d’une source de données séquentiellement.</span><span class="sxs-lookup"><span data-stu-id="7952d-104">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="7952d-105">Le **DataReader** est un bon choix lorsque vous récupérez de grandes quantités de données parce que les données ne sont pas mises en cache dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="7952d-105">The **DataReader** is a good choice when you're retrieving large amounts of data because the data is not cached in memory.</span></span>

<span data-ttu-id="7952d-106">L’exemple suivant illustre l’utilisation d’un **DataReader**, où `reader` représente un DataReader valide et `command` représente un objet de commande valide.</span><span class="sxs-lookup"><span data-stu-id="7952d-106">The following example illustrates using a **DataReader**, where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

<span data-ttu-id="7952d-107">Utilisez la méthode **DataReader.Read** pour obtenir une ligne à partir des résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="7952d-107">Use the **DataReader.Read** method to obtain a row from the query results.</span></span> <span data-ttu-id="7952d-108">Vous pouvez accéder à chaque colonne de la rangée retournée en passant le nom ou le numéro ordinaire de la colonne au **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="7952d-108">You can access each column of the returned row by passing the name or ordinal number of the column to the **DataReader**.</span></span> <span data-ttu-id="7952d-109">Cependant, pour les meilleures performances, le **DataReader** fournit une série de méthodes qui vous permettent d’accéder aux valeurs de colonne dans leurs types de données natives (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, et ainsi de suite).</span><span class="sxs-lookup"><span data-stu-id="7952d-109">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="7952d-110">Pour une liste de méthodes d’accesseur dactylographiées pour **les lecteurs de données**spécifiques aux fournisseurs de données, voir <xref:System.Data.OleDb.OleDbDataReader> et <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="7952d-110">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="7952d-111">L’utilisation des méthodes d’accesseur dactylographiques lorsque vous connaissez le type de données sous-jacent réduit la quantité de conversion de type requise lors de la récupération de la valeur de la colonne.</span><span class="sxs-lookup"><span data-stu-id="7952d-111">Using the typed accessor methods when you know the underlying data type reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
 <span data-ttu-id="7952d-112">L’exemple suivant s’agite à travers un objet **DataReader** et renvoie deux colonnes de chaque rangée.</span><span class="sxs-lookup"><span data-stu-id="7952d-112">The following example iterates through a **DataReader** object and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="7952d-113">Fermeture du DataReader</span><span class="sxs-lookup"><span data-stu-id="7952d-113">Closing the DataReader</span></span>  
 <span data-ttu-id="7952d-114">Appelez toujours la méthode **Close** lorsque vous avez terminé l’utilisation de l’objet **DataReader.**</span><span class="sxs-lookup"><span data-stu-id="7952d-114">Always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="7952d-115">Si votre **commande** contient des paramètres de sortie ou des valeurs de retour, ces valeurs ne sont pas disponibles tant que le **DataReader** n’est pas fermé.</span><span class="sxs-lookup"><span data-stu-id="7952d-115">If your **Command** contains output parameters or return values, those values are not available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="7952d-116">Alors qu’un **DataReader** est ouvert, la **connexion** est utilisée exclusivement par celui **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="7952d-116">While a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="7952d-117">Vous ne pouvez pas exécuter de commandes pour la **connexion,** y compris la création d’un autre **DataReader**, jusqu’à ce que le **DataReader** d’origine soit fermé.</span><span class="sxs-lookup"><span data-stu-id="7952d-117">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7952d-118">N’appelez pas **Close** or **Dispose** on a **Connection**, un **DataReader**, ou tout autre objet géré dans la méthode **Finalize** de votre classe.</span><span class="sxs-lookup"><span data-stu-id="7952d-118">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="7952d-119">Dans un finaliseur, libérez seulement les ressources non managées que votre classe possède directement.</span><span class="sxs-lookup"><span data-stu-id="7952d-119">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="7952d-120">Si votre classe ne possède pas de ressources non gestions, n’incluez pas de méthode **De finalisation** dans votre définition de classe.</span><span class="sxs-lookup"><span data-stu-id="7952d-120">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="7952d-121">Pour plus d’informations, voir [Collection des ordures](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="7952d-121">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="7952d-122">Récupération de plusieurs ensembles de résultats à l’aide de NextResult</span><span class="sxs-lookup"><span data-stu-id="7952d-122">Retrieving multiple result sets using NextResult</span></span>  
 <span data-ttu-id="7952d-123">Si le **DataReader** renvoie plusieurs ensembles de résultats, appelez la méthode **NextResult** pour itérer à travers les ensembles de résultats séquentiellement.</span><span class="sxs-lookup"><span data-stu-id="7952d-123">If the **DataReader** returns multiple result sets, call the **NextResult** method to iterate through the result sets sequentially.</span></span> <span data-ttu-id="7952d-124">L'exemple suivant montre l'objet <xref:System.Data.SqlClient.SqlDataReader> traitant les résultats de deux instructions SELECT utilisant la méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="7952d-124">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="7952d-125">Obtenir des informations sur les schémas du DataReader</span><span class="sxs-lookup"><span data-stu-id="7952d-125">Getting schema information from the DataReader</span></span>  
 <span data-ttu-id="7952d-126">Pendant qu’un **DataReader** est ouvert, vous pouvez récupérer des informations schéma sur l’ensemble de résultats en cours à l’aide de la méthode **GetSchemaTable.**</span><span class="sxs-lookup"><span data-stu-id="7952d-126">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="7952d-127">**GetSchemaTable** renvoie un <xref:System.Data.DataTable> objet peuplé de lignes et de colonnes qui contiennent les informations schéma pour l’ensemble de résultats actuel.</span><span class="sxs-lookup"><span data-stu-id="7952d-127">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="7952d-128">Le **DataTable** contient une ligne pour chaque colonne de l’ensemble de résultats.</span><span class="sxs-lookup"><span data-stu-id="7952d-128">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="7952d-129">Chaque colonne des cartes de table schématique à une propriété des colonnes retournées dans les rangées de l’ensemble de résultat, où le **ColumnName** est le nom de la propriété et la valeur de la colonne est la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="7952d-129">Each column of the schema table maps to a property of the columns returned in the rows of the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="7952d-130">L’exemple suivant écrit les informations schéma pour **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="7952d-130">The following example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="7952d-131">Travailler avec les chapitres OLE DB</span><span class="sxs-lookup"><span data-stu-id="7952d-131">Working with OLE DB chapters</span></span>  
 <span data-ttu-id="7952d-132">Les ramets hiérarchiques, ou chapitres **(type DB**OLE DBTYPE_HCHAPTER , ADO type **adChapter**), peuvent être récupérés à l’aide de la <xref:System.Data.OleDb.OleDbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="7952d-132">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**), can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="7952d-133">Lorsqu’une requête qui comprend un chapitre est retournée comme un **DataReader**, le chapitre est retourné comme une colonne dans celui **DataReader** et est exposé comme un objet **DataReader.**</span><span class="sxs-lookup"><span data-stu-id="7952d-133">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="7952d-134">Le ADO.NET **DataSet** peut également être utilisé pour représenter des jeux hiérarchiques en utilisant des relations parent-enfant entre les tables.</span><span class="sxs-lookup"><span data-stu-id="7952d-134">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets by using parent-child relationships between tables.</span></span> <span data-ttu-id="7952d-135">Pour plus d’informations, consultez [DataSets, DataTables et DataViews](./dataset-datatable-dataview/index.md).</span><span class="sxs-lookup"><span data-stu-id="7952d-135">For more information, see [DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="7952d-136">L'exemple de code suivant utilise le fournisseur MSDataShape pour générer une colonne chapitre de commandes pour chaque client d'une liste de clients.</span><span class="sxs-lookup"><span data-stu-id="7952d-136">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="7952d-137">Résultats de retour avec Oracle REF CURSORs</span><span class="sxs-lookup"><span data-stu-id="7952d-137">Returning results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="7952d-138">Le fournisseur de données .NET Framework pour Oracle prend en charge l'utilisation des REF CURSOR Oracle pour retourner le résultat d'une requête.</span><span class="sxs-lookup"><span data-stu-id="7952d-138">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="7952d-139">Un REF CURSOR Oracle est retourné en tant qu'objet <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="7952d-139">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="7952d-140">Vous pouvez <xref:System.Data.OracleClient.OracleDataReader> récupérer un objet qui représente un <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> Oracle REF CURSOR en utilisant la méthode.</span><span class="sxs-lookup"><span data-stu-id="7952d-140">You can retrieve an <xref:System.Data.OracleClient.OracleDataReader> object that represents an Oracle REF CURSOR by using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="7952d-141">Vous pouvez également <xref:System.Data.OracleClient.OracleCommand> spécifier un qui renvoie un ou plusieurs <xref:System.Data.OracleClient.OracleDataAdapter> Oracle REF <xref:System.Data.DataSet>CURSORs comme **le SelectCommand** pour un utilisé pour remplir un .</span><span class="sxs-lookup"><span data-stu-id="7952d-141">You can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="7952d-142">Pour accéder à un CURSOR REF retourné <xref:System.Data.OracleClient.OracleCommand> d’une source de données Oracle, créez un paramètre de sortie qui fait référence au CURSOR REF à la <xref:System.Data.OracleClient.OracleCommand.Parameters> collecte de votre <xref:System.Data.OracleClient.OracleCommand>.</span><span class="sxs-lookup"><span data-stu-id="7952d-142">To access a REF CURSOR returned from an Oracle data source, create an <xref:System.Data.OracleClient.OracleCommand> for your query and add an output parameter that references the REF CURSOR to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection of your <xref:System.Data.OracleClient.OracleCommand>.</span></span> <span data-ttu-id="7952d-143">Le nom du paramètre doit correspondre à celui du paramètre REF CURSOR de votre requête.</span><span class="sxs-lookup"><span data-stu-id="7952d-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="7952d-144">Définissez le type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>de paramètre à .</span><span class="sxs-lookup"><span data-stu-id="7952d-144">Set the type of the parameter to <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7952d-145">La <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> méthode <xref:System.Data.OracleClient.OracleCommand> de <xref:System.Data.OracleClient.OracleDataReader> vos retours un pour le REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="7952d-145">The <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method of your <xref:System.Data.OracleClient.OracleCommand> returns an <xref:System.Data.OracleClient.OracleDataReader> for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="7952d-146">Si <xref:System.Data.OracleClient.OracleCommand> vos retours plusieurs REF CURSORS, ajoutez plusieurs paramètres de sortie.</span><span class="sxs-lookup"><span data-stu-id="7952d-146">If your <xref:System.Data.OracleClient.OracleCommand> returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="7952d-147">Vous pouvez accéder aux différents CURSORs REF en appelant la <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="7952d-147">You can access the different REF CURSORs by calling the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7952d-148">L’appel <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> pour <xref:System.Data.OracleClient.OracleDataReader> retourner un référencement du premier REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="7952d-148">The call to <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> returns an <xref:System.Data.OracleClient.OracleDataReader> referencing the first REF CURSOR.</span></span> <span data-ttu-id="7952d-149">Vous pouvez ensuite <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> appeler la méthode pour accéder aux CURSORs REF ultérieures.</span><span class="sxs-lookup"><span data-stu-id="7952d-149">You can then call the <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="7952d-150">Bien que les <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> paramètres de votre collection correspondent aux paramètres <xref:System.Data.OracleClient.OracleDataReader> de sortie REF CURSOR par leur <xref:System.Data.OracleClient.OracleCommand.Parameters> nom, les accès les accèdent dans l’ordre dans lequel ils ont été ajoutés à la collection.</span><span class="sxs-lookup"><span data-stu-id="7952d-150">Although the parameters in your <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection match the REF CURSOR output parameters by name, the <xref:System.Data.OracleClient.OracleDataReader> accesses them in the order in which they were added to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span></span>  
  
 <span data-ttu-id="7952d-151">Considérez, par exemple, le package et le corps de package Oracle suivants.</span><span class="sxs-lookup"><span data-stu-id="7952d-151">For example, consider the following Oracle package and package body.</span></span>  
  
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
  
 <span data-ttu-id="7952d-152">Le code suivant <xref:System.Data.OracleClient.OracleCommand> crée un qui renvoie les CURSORs REF du <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> paquet <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> Oracle précédent en ajoutant deux paramètres de type à la collection.</span><span class="sxs-lookup"><span data-stu-id="7952d-152">The following code creates an <xref:System.Data.OracleClient.OracleCommand> that returns the REF CURSORs from the previous Oracle package by adding two parameters of type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> to the <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span></span>  
  
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
  
 <span data-ttu-id="7952d-153">Le code suivant renvoie les résultats <xref:System.Data.OracleClient.OracleDataReader.Read> <xref:System.Data.OracleClient.OracleDataReader.NextResult> de la <xref:System.Data.OracleClient.OracleDataReader>commande précédente en utilisant le et les méthodes de la .</span><span class="sxs-lookup"><span data-stu-id="7952d-153">The following code returns the results of the previous command using the <xref:System.Data.OracleClient.OracleDataReader.Read> and <xref:System.Data.OracleClient.OracleDataReader.NextResult> methods of the <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="7952d-154">Les paramètres REF CURSOR sont retournés dans l'ordre.</span><span class="sxs-lookup"><span data-stu-id="7952d-154">The REF CURSOR parameters are returned in order.</span></span>  
  
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
  
 <span data-ttu-id="7952d-155">L’exemple suivant utilise la commande <xref:System.Data.DataSet> précédente pour remplir un avec les résultats du paquet Oracle.</span><span class="sxs-lookup"><span data-stu-id="7952d-155">The following example uses the previous command to populate a <xref:System.Data.DataSet> with the results of the Oracle package.</span></span>  
  
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
> <span data-ttu-id="7952d-156">Pour éviter un **OverflowException**, nous vous recommandons également de gérer toute conversion du type Oracle <xref:System.Data.DataRow>NUMBER à un type de cadre .NET valide avant de stocker la valeur dans un .</span><span class="sxs-lookup"><span data-stu-id="7952d-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="7952d-157">Vous pouvez <xref:System.Data.Common.DataAdapter.FillError> utiliser l’événement pour déterminer si un **DébordementException s’est** produit.</span><span class="sxs-lookup"><span data-stu-id="7952d-157">You can use the <xref:System.Data.Common.DataAdapter.FillError> event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="7952d-158">Pour plus d’informations sur l’événement, <xref:System.Data.Common.DataAdapter.FillError> voir Handling [DataAdapter Events](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="7952d-158">For more information on the <xref:System.Data.Common.DataAdapter.FillError> event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7952d-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7952d-159">See also</span></span>

- [<span data-ttu-id="7952d-160">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="7952d-160">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="7952d-161">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="7952d-161">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="7952d-162">Récupération des informations de schéma de base de données</span><span class="sxs-lookup"><span data-stu-id="7952d-162">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="7952d-163">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7952d-163">ADO.NET Overview</span></span>](ado-net-overview.md)
