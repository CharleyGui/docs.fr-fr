---
title: Tri et filtre de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 89e2fdf656fb06ee545ba936f033646ad86182d4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183375"
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="72cff-102">Tri et filtre de données</span><span class="sxs-lookup"><span data-stu-id="72cff-102">Sorting and Filtering Data</span></span>

<span data-ttu-id="72cff-103">L'objet <xref:System.Data.DataView> offre plusieurs méthodes de tri et de filtrage de données dans un objet <xref:System.Data.DataTable> :</span><span class="sxs-lookup"><span data-stu-id="72cff-103">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
- <span data-ttu-id="72cff-104">Vous pouvez utiliser la propriété <xref:System.Data.DataView.Sort%2A> pour spécifier un ordre de tri en fonction d'une ou de plusieurs colonnes et inclure des paramètres ASC (ordre croissant) et DESC (ordre décroissant).</span><span class="sxs-lookup"><span data-stu-id="72cff-104">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
- <span data-ttu-id="72cff-105">Vous pouvez utiliser la propriété <xref:System.Data.DataView.ApplyDefaultSort%2A> pour créer automatiquement un ordre de tri, croissant, basé sur la ou les colonnes de clé primaire de la table.</span><span class="sxs-lookup"><span data-stu-id="72cff-105">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <span data-ttu-id="72cff-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> s’applique uniquement lorsque la propriété **sort** est une référence null ou une chaîne vide et lorsque la table a une clé primaire définie.</span><span class="sxs-lookup"><span data-stu-id="72cff-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
- <span data-ttu-id="72cff-107">Vous pouvez utiliser la propriété <xref:System.Data.DataView.RowFilter%2A> pour spécifier des sous-ensembles de lignes basés sur les valeurs de colonne.</span><span class="sxs-lookup"><span data-stu-id="72cff-107">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="72cff-108">Pour plus d’informations sur les expressions valides pour la propriété **RowFilter** , consultez les informations de référence pour la <xref:System.Data.DataColumn.Expression%2A> propriété de la <xref:System.Data.DataColumn> classe.</span><span class="sxs-lookup"><span data-stu-id="72cff-108">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="72cff-109">Si vous souhaitez retourner les résultats d’une requête particulière sur les données, au lieu de fournir une vue dynamique d’un sous-ensemble des données, utilisez les <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> méthodes ou du **DataView** pour obtenir des performances optimales au lieu de définir la propriété **RowFilter** .</span><span class="sxs-lookup"><span data-stu-id="72cff-109">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="72cff-110">La définition de la propriété **RowFilter** reconstruit l’index pour les données, en ajoutant une surcharge à votre application et en diminuant les performances.</span><span class="sxs-lookup"><span data-stu-id="72cff-110">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="72cff-111">La propriété **RowFilter** est mieux utilisée dans une application liée aux données, où un contrôle lié affiche des résultats filtrés.</span><span class="sxs-lookup"><span data-stu-id="72cff-111">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="72cff-112">Les méthodes **Find** et **FindRows** tirent parti de l’index actuel sans nécessiter la reconstruction de l’index.</span><span class="sxs-lookup"><span data-stu-id="72cff-112">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="72cff-113">Pour plus d’informations sur les méthodes **Find** et **FindRows** , consultez [recherche de lignes](finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="72cff-113">For more information about the **Find** and **FindRows** methods, see [Finding Rows](finding-rows.md).</span></span>  
  
- <span data-ttu-id="72cff-114">Vous pouvez utiliser la propriété <xref:System.Data.DataView.RowStateFilter%2A> pour spécifier les versions de ligne à afficher.</span><span class="sxs-lookup"><span data-stu-id="72cff-114">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="72cff-115">Le **DataView** gère implicitement la version de ligne à exposer en fonction du **RowState** de la ligne sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="72cff-115">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="72cff-116">Par exemple, si la valeur **RowStateFilter** est définie sur **DataViewRowState. Deleted**, le **DataView** expose la version de ligne d' **origine** de toutes les lignes **supprimées** , car il n’y a pas de version de ligne **actuelle** .</span><span class="sxs-lookup"><span data-stu-id="72cff-116">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="72cff-117">Vous pouvez déterminer la version de ligne d’une ligne qui est exposée à l’aide de la propriété **rowversion** du **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="72cff-117">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="72cff-118">Le tableau suivant présente les options de **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="72cff-118">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="72cff-119">Options DataViewRowState</span><span class="sxs-lookup"><span data-stu-id="72cff-119">DataViewRowState options</span></span>|<span data-ttu-id="72cff-120">Description</span><span class="sxs-lookup"><span data-stu-id="72cff-120">Description</span></span>|  
    |------------------------------|-----------------|  
    |<span data-ttu-id="72cff-121">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="72cff-121">**CurrentRows**</span></span>|<span data-ttu-id="72cff-122">Version de ligne **actuelle** de toutes les lignes non **modifiées**, **ajoutées**et **modifiées** .</span><span class="sxs-lookup"><span data-stu-id="72cff-122">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="72cff-123">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="72cff-123">This is the default.</span></span>|  
    |<span data-ttu-id="72cff-124">**Ajouté**</span><span class="sxs-lookup"><span data-stu-id="72cff-124">**Added**</span></span>|<span data-ttu-id="72cff-125">Version de ligne **actuelle** de toutes les lignes **ajoutées** .</span><span class="sxs-lookup"><span data-stu-id="72cff-125">The **Current** row version of all **Added** rows.</span></span>|  
    |<span data-ttu-id="72cff-126">**Supprimé**</span><span class="sxs-lookup"><span data-stu-id="72cff-126">**Deleted**</span></span>|<span data-ttu-id="72cff-127">Version de ligne d' **origine** de toutes les lignes **supprimées** .</span><span class="sxs-lookup"><span data-stu-id="72cff-127">The **Original** row version of all **Deleted** rows.</span></span>|  
    |<span data-ttu-id="72cff-128">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="72cff-128">**ModifiedCurrent**</span></span>|<span data-ttu-id="72cff-129">Version de ligne **actuelle** de toutes les lignes **modifiées** .</span><span class="sxs-lookup"><span data-stu-id="72cff-129">The **Current** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="72cff-130">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="72cff-130">**ModifiedOriginal**</span></span>|<span data-ttu-id="72cff-131">Version de ligne d' **origine** de toutes les lignes **modifiées** .</span><span class="sxs-lookup"><span data-stu-id="72cff-131">The **Original** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="72cff-132">**Aucun**</span><span class="sxs-lookup"><span data-stu-id="72cff-132">**None**</span></span>|<span data-ttu-id="72cff-133">Aucune ligne.</span><span class="sxs-lookup"><span data-stu-id="72cff-133">No rows.</span></span>|  
    |<span data-ttu-id="72cff-134">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="72cff-134">**OriginalRows**</span></span>|<span data-ttu-id="72cff-135">Version de ligne d' **origine** de toutes les lignes **inchangées**, **modifiées**et **supprimées** .</span><span class="sxs-lookup"><span data-stu-id="72cff-135">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |<span data-ttu-id="72cff-136">**Inchangé**</span><span class="sxs-lookup"><span data-stu-id="72cff-136">**Unchanged**</span></span>|<span data-ttu-id="72cff-137">Version de ligne **actuelle** de toutes les lignes **inchangées** .</span><span class="sxs-lookup"><span data-stu-id="72cff-137">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="72cff-138">Pour plus d’informations sur les États de ligne et les versions de ligne, consultez [États de ligne et versions de ligne](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="72cff-138">For more information about row states and row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="72cff-139">L'exemple de code suivant crée une vue faisant apparaître tous les produits pour lesquels la quantité en stock est inférieure ou égale au niveau de passage d'une nouvelle commande, triés d'abord par ID de fournisseur, puis par nom de produit.</span><span class="sxs-lookup"><span data-stu-id="72cff-139">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a><span data-ttu-id="72cff-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72cff-140">See also</span></span>

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="72cff-141">DataViews</span><span class="sxs-lookup"><span data-stu-id="72cff-141">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="72cff-142">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="72cff-142">ADO.NET Overview</span></span>](../ado-net-overview.md)
