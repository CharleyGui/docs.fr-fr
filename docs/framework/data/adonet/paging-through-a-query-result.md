---
title: Pagination à travers un résultat de requête
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 065b509d8385ee37b2a86587f520b5fd3207ceff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186950"
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="89922-102">Pagination à travers un résultat de requête</span><span class="sxs-lookup"><span data-stu-id="89922-102">Paging Through a Query Result</span></span>

<span data-ttu-id="89922-103">Ce mode d'affichage consiste à retourner les résultats d'une requête sous forme de sous-ensembles, plus petits, de données, aussi appelés pages.</span><span class="sxs-lookup"><span data-stu-id="89922-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="89922-104">Cette façon de procéder est courante lorsqu'il s'agit de présenter à l'utilisateur un affichage des résultats par petits segments, plus faciles à gérer.</span><span class="sxs-lookup"><span data-stu-id="89922-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="89922-105">Le **DataAdapter** fournit une fonctionnalité permettant de retourner uniquement une page de données, par le biais de surcharges de la méthode **Fill** .</span><span class="sxs-lookup"><span data-stu-id="89922-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="89922-106">Toutefois, ce n’est peut-être pas le meilleur choix pour la pagination via des résultats de requête volumineux, car même si le **DataAdapter** remplit la cible <xref:System.Data.DataTable> ou <xref:System.Data.DataSet> avec uniquement les enregistrements demandés, les ressources pour retourner l’intégralité de la requête sont toujours utilisées.</span><span class="sxs-lookup"><span data-stu-id="89922-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="89922-107">Pour retourner une page de données provenant d'une source de donnée sans solliciter les ressources requises pour retourner l'intégralité de la requête, spécifiez des critères supplémentaires pour votre requête afin de limiter le nombre de lignes retournées à celles qui sont requises.</span><span class="sxs-lookup"><span data-stu-id="89922-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="89922-108">Pour utiliser la méthode **Fill** pour retourner une page de données, spécifiez un paramètre **startRecord** , pour le premier enregistrement de la page de données, et un paramètre **maxRecords** , pour le nombre d’enregistrements dans la page de données.</span><span class="sxs-lookup"><span data-stu-id="89922-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="89922-109">L’exemple de code suivant montre comment utiliser la méthode **Fill** pour retourner la première page d’un résultat de requête où la taille de la page est de cinq enregistrements.</span><span class="sxs-lookup"><span data-stu-id="89922-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
```vb  
Dim currentIndex As Integer = 0  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT * FROM dbo.Orders ORDER BY OrderID"  
' Assumes that connection is a valid SqlConnection object.  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
int currentIndex = 0;  
int pageSize = 5;  
  
string orderSQL = "SELECT * FROM Orders ORDER BY OrderID";  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 <span data-ttu-id="89922-110">Dans l’exemple précédent, le **jeu de données** ne contient que cinq enregistrements, mais l’intégralité de la table **Orders** est retournée.</span><span class="sxs-lookup"><span data-stu-id="89922-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="89922-111">Pour remplir le **DataSet** avec ces cinq mêmes enregistrements, mais ne retournent que cinq enregistrements, utilisez les clauses Top et Where dans votre instruction SQL, comme dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="89922-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
```vb  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT TOP " & pageSize & _  
  " * FROM Orders ORDER BY OrderID"  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Orders")
```  
  
```csharp  
int pageSize = 5;  
  
string orderSQL = "SELECT TOP " + pageSize +
  " * FROM Orders ORDER BY OrderID";  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Orders");  
```  
  
 <span data-ttu-id="89922-112">Notez que, lorsque vous choisissez ce mode d'affichage par pages des résultats d'une requête, vous devez conserver l'identificateur unique en fonction duquel les lignes sont organisées, afin de passer cet identificateur unique à la commande pour retourner la page d'enregistrements suivante, comme le montre l'exemple de code ci-après.</span><span class="sxs-lookup"><span data-stu-id="89922-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="89922-113">Pour retourner la page d’enregistrements suivante à l’aide de la surcharge de la méthode **Fill** qui accepte les paramètres **startRecord** et **maxRecords** , incrémentez l’index actuel de l’enregistrement en utilisant la taille de la page et remplissez la table.</span><span class="sxs-lookup"><span data-stu-id="89922-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="89922-114">N’oubliez pas que le serveur de base de données renvoie l’intégralité des résultats de la requête, même si une seule page d’enregistrements est ajoutée au **jeu**de données.</span><span class="sxs-lookup"><span data-stu-id="89922-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="89922-115">Dans l'exemple de code suivant, les lignes de la table sont vidées de leur contenu avant de recevoir la page de données suivante.</span><span class="sxs-lookup"><span data-stu-id="89922-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="89922-116">Vous avez la possibilité de conserver dans un cache local un certain nombre de lignes retournées afin de limiter les sollicitations du serveur de base de données.</span><span class="sxs-lookup"><span data-stu-id="89922-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
```vb  
currentIndex = currentIndex + pageSize  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
currentIndex += pageSize;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 <span data-ttu-id="89922-117">Pour retourner la page d'enregistrements suivante sans que le serveur de base de données ne retourne l'intégralité de la requête, spécifiez des critères restrictifs pour l'instruction SELECT.</span><span class="sxs-lookup"><span data-stu-id="89922-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="89922-118">Parce que l'exemple précédent conservait le dernier enregistrement retourné, vous pouvez l'utiliser dans la clause WHERE afin de spécifier le point de départ de la requête, comme le montre l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="89922-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
```vb  
orderSQL = "SELECT TOP " & pageSize & _  
  " * FROM Orders WHERE OrderID > " & lastRecord & " ORDER BY OrderID"  
adapter.SelectCommand.CommandText = orderSQL  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, "Orders")  
```  
  
```csharp  
orderSQL = "SELECT TOP " + pageSize +
  " * FROM Orders WHERE OrderID > " + lastRecord + " ORDER BY OrderID";  
adapter.SelectCommand.CommandText = orderSQL;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, "Orders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="89922-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89922-119">See also</span></span>

- [<span data-ttu-id="89922-120">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="89922-120">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="89922-121">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="89922-121">ADO.NET Overview</span></span>](ado-net-overview.md)
