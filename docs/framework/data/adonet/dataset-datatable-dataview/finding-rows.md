---
title: Recherche de lignes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: dc0661e29e6d3ee5aa3f54179e8abf265cd67d58
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186976"
---
# <a name="finding-rows"></a><span data-ttu-id="f322c-102">Recherche de lignes</span><span class="sxs-lookup"><span data-stu-id="f322c-102">Finding Rows</span></span>

<span data-ttu-id="f322c-103">Vous pouvez rechercher des lignes en fonction des valeurs de leur clé de tri en utilisant les méthodes <xref:System.Data.DataView.Find%2A> et <xref:System.Data.DataView.FindRows%2A> de l'objet <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="f322c-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="f322c-104">Le respect de la casse des valeurs de recherche dans les méthodes **Find** et **FindRows** est déterminé par la propriété **CaseSensitive** de l’objet sous-jacent <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="f322c-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="f322c-105">Pour qu'un résultat soit retourné, les valeurs de recherche doivent correspondre aux valeurs des clés de tri existantes dans leur intégralité.</span><span class="sxs-lookup"><span data-stu-id="f322c-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="f322c-106">La méthode **Find** retourne un entier avec l’index du <xref:System.Data.DataRowView> qui correspond aux critères de recherche.</span><span class="sxs-lookup"><span data-stu-id="f322c-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="f322c-107">Si plusieurs lignes correspondent aux critères de recherche, seul l’index du premier **DataRowView** correspondant est retourné.</span><span class="sxs-lookup"><span data-stu-id="f322c-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="f322c-108">Si aucune correspondance n’est trouvée, **Find** retourne-1.</span><span class="sxs-lookup"><span data-stu-id="f322c-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="f322c-109">Pour retourner des résultats de recherche qui correspondent à plusieurs lignes, utilisez la méthode **FindRows** .</span><span class="sxs-lookup"><span data-stu-id="f322c-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="f322c-110">**FindRows** fonctionne comme la méthode **Find** , à la différence qu’elle retourne un tableau **DataRowView** qui fait référence à toutes les lignes correspondantes dans le **DataView**.</span><span class="sxs-lookup"><span data-stu-id="f322c-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="f322c-111">Si aucune correspondance n’est trouvée, le tableau **DataRowView** sera vide.</span><span class="sxs-lookup"><span data-stu-id="f322c-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="f322c-112">Pour utiliser les méthodes **Find** ou **FindRows** , vous devez spécifier un ordre de tri en affectant à **ApplyDefaultSort** la **valeur true** ou en utilisant la propriété **sort** .</span><span class="sxs-lookup"><span data-stu-id="f322c-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="f322c-113">Si aucun ordre de tri n'est spécifié, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="f322c-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="f322c-114">Les méthodes **Find** et **FindRows** prennent un tableau de valeurs comme entrée dont la longueur correspond au nombre de colonnes dans l’ordre de tri.</span><span class="sxs-lookup"><span data-stu-id="f322c-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="f322c-115">Si un tri doit s'effectuer sur une seule colonne, vous pouvez passer une seule valeur.</span><span class="sxs-lookup"><span data-stu-id="f322c-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="f322c-116">Pour les ordres de tri incluant plusieurs colonnes, vous passez un tableau d'objets.</span><span class="sxs-lookup"><span data-stu-id="f322c-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="f322c-117">Notez que, pour un tri sur plusieurs colonnes, les valeurs du tableau d’objets doivent correspondre à l’ordre des colonnes spécifiées dans la propriété **sort** du **DataView**.</span><span class="sxs-lookup"><span data-stu-id="f322c-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="f322c-118">L’exemple de code suivant montre la méthode **Find** appelée sur un **DataView** avec un ordre de tri de colonne unique.</span><span class="sxs-lookup"><span data-stu-id="f322c-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 <span data-ttu-id="f322c-119">Si votre propriété de **Tri** spécifie plusieurs colonnes, vous devez passer un tableau d’objets avec les valeurs de recherche de chaque colonne dans l’ordre spécifié par la propriété de **Tri** , comme dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="f322c-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a><span data-ttu-id="f322c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f322c-120">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="f322c-121">DataViews</span><span class="sxs-lookup"><span data-stu-id="f322c-121">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="f322c-122">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f322c-122">ADO.NET Overview</span></span>](../ado-net-overview.md)
