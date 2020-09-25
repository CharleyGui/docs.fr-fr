---
title: Récupération de données à l'aide d'un DataReader
description: Découvrez comment récupérer des données à l’aide d’un DataReader dans ADO.NET avec cet exemple de code. DataReader fournit un flux de données non mis en mémoire tampon.
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 96cc6444b6e4dc2806abffd456d0c2f7533f0009
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204370"
---
# <a name="retrieve-data-using-a-datareader"></a><span data-ttu-id="b7e19-104">Récupérer des données à l’aide d’un DataReader</span><span class="sxs-lookup"><span data-stu-id="b7e19-104">Retrieve data using a DataReader</span></span>

<span data-ttu-id="b7e19-105">Pour récupérer des données à l’aide d’un **DataReader**, créez une instance de l’objet de **commande** , puis créez un **DataReader** en appelant **Command.ExecuteReader** pour récupérer des lignes d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="b7e19-105">To retrieve data using a **DataReader**, create an instance of the **Command** object, and then create a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="b7e19-106">Le **DataReader** fournit un flux de données non mis en mémoire tampon qui permet à la logique procédurale de traiter efficacement les résultats d’une source de données de manière séquentielle.</span><span class="sxs-lookup"><span data-stu-id="b7e19-106">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="b7e19-107">Le **DataReader** est un bon choix lorsque vous récupérez de grandes quantités de données, car les données ne sont pas mises en cache dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="b7e19-107">The **DataReader** is a good choice when you're retrieving large amounts of data because the data is not cached in memory.</span></span>

<span data-ttu-id="b7e19-108">L’exemple suivant illustre l’utilisation d’un **DataReader**, où `reader` représente un DataReader valide et `command` représente un objet Command valide.</span><span class="sxs-lookup"><span data-stu-id="b7e19-108">The following example illustrates using a **DataReader**, where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

<span data-ttu-id="b7e19-109">Utilisez la méthode **DataReader. Read** pour obtenir une ligne à partir des résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="b7e19-109">Use the **DataReader.Read** method to obtain a row from the query results.</span></span> <span data-ttu-id="b7e19-110">Vous pouvez accéder à chaque colonne de la ligne retournée en passant le nom ou le numéro ordinal de la colonne au **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="b7e19-110">You can access each column of the returned row by passing the name or ordinal number of the column to the **DataReader**.</span></span> <span data-ttu-id="b7e19-111">Toutefois, pour de meilleures performances, le **DataReader** fournit une série de méthodes qui vous permettent d’accéder aux valeurs de colonne dans leurs types de données natifs (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, etc.).</span><span class="sxs-lookup"><span data-stu-id="b7e19-111">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="b7e19-112">Pour obtenir la liste des méthodes d’accesseur typées pour les **DataReaders**spécifiques au fournisseur de données, consultez <xref:System.Data.OleDb.OleDbDataReader> et <xref:System.Data.SqlClient.SqlDataReader> .</span><span class="sxs-lookup"><span data-stu-id="b7e19-112">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="b7e19-113">L’utilisation des méthodes d’accesseur typées lorsque vous connaissez le type de données sous-jacent réduit la quantité de conversion de type requise lors de la récupération de la valeur de colonne.</span><span class="sxs-lookup"><span data-stu-id="b7e19-113">Using the typed accessor methods when you know the underlying data type reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
 <span data-ttu-id="b7e19-114">L’exemple suivant itère au sein d’un objet **DataReader** et retourne deux colonnes de chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="b7e19-114">The following example iterates through a **DataReader** object and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="b7e19-115">Fermeture du DataReader</span><span class="sxs-lookup"><span data-stu-id="b7e19-115">Closing the DataReader</span></span>  

 <span data-ttu-id="b7e19-116">Appelez toujours la méthode **Close** lorsque vous avez fini d’utiliser l’objet **DataReader** .</span><span class="sxs-lookup"><span data-stu-id="b7e19-116">Always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="b7e19-117">Si votre **commande** contient des paramètres de sortie ou des valeurs de retour, ces valeurs ne sont pas disponibles tant que le **DataReader** n’est pas fermé.</span><span class="sxs-lookup"><span data-stu-id="b7e19-117">If your **Command** contains output parameters or return values, those values are not available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="b7e19-118">Lorsqu’un **DataReader** est ouvert, la **connexion** est utilisée exclusivement par ce **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="b7e19-118">While a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="b7e19-119">Vous ne pouvez pas exécuter de commandes pour la **connexion**, notamment créer un autre **DataReader**, jusqu’à la fermeture du **DataReader** d’origine.</span><span class="sxs-lookup"><span data-stu-id="b7e19-119">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7e19-120">N’appelez pas **Close** ou **dispose** sur une **connexion**, un **DataReader**ou tout autre objet managé dans la méthode **Finalize** de votre classe.</span><span class="sxs-lookup"><span data-stu-id="b7e19-120">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="b7e19-121">Dans un finaliseur, libérez seulement les ressources non managées que votre classe possède directement.</span><span class="sxs-lookup"><span data-stu-id="b7e19-121">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="b7e19-122">Si votre classe ne possède pas de ressources non managées, n’incluez pas de méthode **Finalize** dans votre définition de classe.</span><span class="sxs-lookup"><span data-stu-id="b7e19-122">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="b7e19-123">Pour plus d’informations, consultez [garbage collection](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="b7e19-123">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="b7e19-124">Récupération de plusieurs jeux de résultats à l’aide de NextResult</span><span class="sxs-lookup"><span data-stu-id="b7e19-124">Retrieving multiple result sets using NextResult</span></span>  

 <span data-ttu-id="b7e19-125">Si le **DataReader** retourne plusieurs jeux de résultats, appelez la méthode **NextResult** pour effectuer une itération dans les jeux de résultats de manière séquentielle.</span><span class="sxs-lookup"><span data-stu-id="b7e19-125">If the **DataReader** returns multiple result sets, call the **NextResult** method to iterate through the result sets sequentially.</span></span> <span data-ttu-id="b7e19-126">L'exemple suivant montre l'objet <xref:System.Data.SqlClient.SqlDataReader> traitant les résultats de deux instructions SELECT utilisant la méthode <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="b7e19-126">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="b7e19-127">Obtention d’informations de schéma à partir du DataReader</span><span class="sxs-lookup"><span data-stu-id="b7e19-127">Getting schema information from the DataReader</span></span>  

 <span data-ttu-id="b7e19-128">Lorsqu’un **DataReader** est ouvert, vous pouvez récupérer des informations de schéma sur le jeu de résultats actuel à l’aide de la méthode **GetSchemaTable** .</span><span class="sxs-lookup"><span data-stu-id="b7e19-128">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="b7e19-129">**GetSchemaTable** retourne un <xref:System.Data.DataTable> objet rempli avec les lignes et les colonnes qui contiennent les informations de schéma pour le jeu de résultats actuel.</span><span class="sxs-lookup"><span data-stu-id="b7e19-129">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="b7e19-130">Le **DataTable** contient une ligne pour chaque colonne du jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="b7e19-130">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="b7e19-131">Chaque colonne de la table de schéma est mappée à une propriété des colonnes retournées dans les lignes du jeu de résultats, où **ColumnName** est le nom de la propriété et la valeur de la colonne est la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="b7e19-131">Each column of the schema table maps to a property of the columns returned in the rows of the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="b7e19-132">L’exemple suivant écrit les informations de schéma pour **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="b7e19-132">The following example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="b7e19-133">Utilisation des chapitres OLE DB</span><span class="sxs-lookup"><span data-stu-id="b7e19-133">Working with OLE DB chapters</span></span>  

 <span data-ttu-id="b7e19-134">Les ensembles de lignes hiérarchiques ou chapitres (OLE DB type **DBTYPE_HCHAPTER**, type ADO **adChapter**), peuvent être récupérés à l’aide du <xref:System.Data.OleDb.OleDbDataReader> .</span><span class="sxs-lookup"><span data-stu-id="b7e19-134">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**), can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="b7e19-135">Lorsqu’une requête qui comprend un chapitre est retournée en tant que **DataReader**, le chapitre est retourné en tant que colonne dans ce **DataReader** et est exposé en tant qu’objet **DataReader** .</span><span class="sxs-lookup"><span data-stu-id="b7e19-135">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="b7e19-136">Le **jeu de données** ADO.net peut également être utilisé pour représenter des ensembles de lignes hiérarchiques à l’aide de relations parent-enfant entre les tables.</span><span class="sxs-lookup"><span data-stu-id="b7e19-136">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets by using parent-child relationships between tables.</span></span> <span data-ttu-id="b7e19-137">Pour plus d’informations, consultez [DataSets, DataTables et DataView](./dataset-datatable-dataview/index.md).</span><span class="sxs-lookup"><span data-stu-id="b7e19-137">For more information, see [DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="b7e19-138">L'exemple de code suivant utilise le fournisseur MSDataShape pour générer une colonne chapitre de commandes pour chaque client d'une liste de clients.</span><span class="sxs-lookup"><span data-stu-id="b7e19-138">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="b7e19-139">Retour de résultats avec des REF CURSOR Oracle</span><span class="sxs-lookup"><span data-stu-id="b7e19-139">Returning results with Oracle REF CURSORs</span></span>  

 <span data-ttu-id="b7e19-140">Le fournisseur de données .NET Framework pour Oracle prend en charge l'utilisation des REF CURSOR Oracle pour retourner le résultat d'une requête.</span><span class="sxs-lookup"><span data-stu-id="b7e19-140">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="b7e19-141">Un REF CURSOR Oracle est retourné en tant qu'objet <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="b7e19-141">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="b7e19-142">Vous pouvez récupérer un <xref:System.Data.OracleClient.OracleDataReader> objet qui représente un REF CURSOR Oracle à l’aide de la <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="b7e19-142">You can retrieve an <xref:System.Data.OracleClient.OracleDataReader> object that represents an Oracle REF CURSOR by using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="b7e19-143">Vous pouvez également spécifier un <xref:System.Data.OracleClient.OracleCommand> qui retourne un ou plusieurs REF CURSOR Oracle comme **SelectCommand** pour un <xref:System.Data.OracleClient.OracleDataAdapter> utilisé pour remplir un <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="b7e19-143">You can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="b7e19-144">Pour accéder à un REF CURSOR retourné à partir d’une source de données Oracle, créez un <xref:System.Data.OracleClient.OracleCommand> pour votre requête et ajoutez un paramètre de sortie qui référence le REF CURSOR à la <xref:System.Data.OracleClient.OracleCommand.Parameters> collection de votre <xref:System.Data.OracleClient.OracleCommand> .</span><span class="sxs-lookup"><span data-stu-id="b7e19-144">To access a REF CURSOR returned from an Oracle data source, create an <xref:System.Data.OracleClient.OracleCommand> for your query and add an output parameter that references the REF CURSOR to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection of your <xref:System.Data.OracleClient.OracleCommand>.</span></span> <span data-ttu-id="b7e19-145">Le nom du paramètre doit correspondre à celui du paramètre REF CURSOR de votre requête.</span><span class="sxs-lookup"><span data-stu-id="b7e19-145">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="b7e19-146">Définissez le type du paramètre sur <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b7e19-146">Set the type of the parameter to <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b7e19-147">La <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> méthode de votre <xref:System.Data.OracleClient.OracleCommand> retourne un <xref:System.Data.OracleClient.OracleDataReader> pour le REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="b7e19-147">The <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method of your <xref:System.Data.OracleClient.OracleCommand> returns an <xref:System.Data.OracleClient.OracleDataReader> for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="b7e19-148">Si votre <xref:System.Data.OracleClient.OracleCommand> retourne plusieurs REF CURSOR, ajoutez plusieurs paramètres de sortie.</span><span class="sxs-lookup"><span data-stu-id="b7e19-148">If your <xref:System.Data.OracleClient.OracleCommand> returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="b7e19-149">Vous pouvez accéder aux différents REF CURSOR en appelant la <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="b7e19-149">You can access the different REF CURSORs by calling the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b7e19-150">L’appel à <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> retourne un qui <xref:System.Data.OracleClient.OracleDataReader> référence le premier REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="b7e19-150">The call to <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> returns an <xref:System.Data.OracleClient.OracleDataReader> referencing the first REF CURSOR.</span></span> <span data-ttu-id="b7e19-151">Vous pouvez ensuite appeler la <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> méthode pour accéder aux REF CURSOR suivants.</span><span class="sxs-lookup"><span data-stu-id="b7e19-151">You can then call the <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="b7e19-152">Bien que les paramètres de votre <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection correspondent aux paramètres de sortie du REF CURSOR par leur nom, le <xref:System.Data.OracleClient.OracleDataReader> accède à ceux-ci dans l’ordre dans lequel ils ont été ajoutés à la <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span><span class="sxs-lookup"><span data-stu-id="b7e19-152">Although the parameters in your <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection match the REF CURSOR output parameters by name, the <xref:System.Data.OracleClient.OracleDataReader> accesses them in the order in which they were added to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span></span>  
  
 <span data-ttu-id="b7e19-153">Considérez, par exemple, le package et le corps de package Oracle suivants.</span><span class="sxs-lookup"><span data-stu-id="b7e19-153">For example, consider the following Oracle package and package body.</span></span>  
  
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
  
 <span data-ttu-id="b7e19-154">Le code suivant crée un <xref:System.Data.OracleClient.OracleCommand> qui retourne les REF CURSOR à partir du package Oracle précédent en ajoutant deux paramètres de type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> à la <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span><span class="sxs-lookup"><span data-stu-id="b7e19-154">The following code creates an <xref:System.Data.OracleClient.OracleCommand> that returns the REF CURSORs from the previous Oracle package by adding two parameters of type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> to the <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span></span>  
  
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
  
 <span data-ttu-id="b7e19-155">Le code suivant retourne les résultats de la commande précédente à l’aide des <xref:System.Data.OracleClient.OracleDataReader.Read> <xref:System.Data.OracleClient.OracleDataReader.NextResult> méthodes et de <xref:System.Data.OracleClient.OracleDataReader> .</span><span class="sxs-lookup"><span data-stu-id="b7e19-155">The following code returns the results of the previous command using the <xref:System.Data.OracleClient.OracleDataReader.Read> and <xref:System.Data.OracleClient.OracleDataReader.NextResult> methods of the <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="b7e19-156">Les paramètres REF CURSOR sont retournés dans l'ordre.</span><span class="sxs-lookup"><span data-stu-id="b7e19-156">The REF CURSOR parameters are returned in order.</span></span>  
  
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
  
 <span data-ttu-id="b7e19-157">L’exemple suivant utilise la commande précédente pour remplir un <xref:System.Data.DataSet> avec les résultats du package Oracle.</span><span class="sxs-lookup"><span data-stu-id="b7e19-157">The following example uses the previous command to populate a <xref:System.Data.DataSet> with the results of the Oracle package.</span></span>  
  
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
> <span data-ttu-id="b7e19-158">Pour éviter une **exception OverflowException**, nous vous recommandons de gérer également toute conversion du type de nombre Oracle en un type de .NET Framework valide avant de stocker la valeur dans un <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="b7e19-158">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="b7e19-159">Vous pouvez utiliser l' <xref:System.Data.Common.DataAdapter.FillError> événement pour déterminer si une **exception OverflowException** s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b7e19-159">You can use the <xref:System.Data.Common.DataAdapter.FillError> event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="b7e19-160">Pour plus d’informations sur l' <xref:System.Data.Common.DataAdapter.FillError> événement, consultez [gestion des événements DataAdapter](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="b7e19-160">For more information on the <xref:System.Data.Common.DataAdapter.FillError> event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e19-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7e19-161">See also</span></span>

- [<span data-ttu-id="b7e19-162">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="b7e19-162">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="b7e19-163">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="b7e19-163">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="b7e19-164">Extraction des informations de schéma de base de données</span><span class="sxs-lookup"><span data-stu-id="b7e19-164">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="b7e19-165">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b7e19-165">ADO.NET Overview</span></span>](ado-net-overview.md)
