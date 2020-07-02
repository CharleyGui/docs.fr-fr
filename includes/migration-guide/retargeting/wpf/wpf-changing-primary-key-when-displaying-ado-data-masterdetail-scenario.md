---
ms.openlocfilehash: 35fc4782ebbba33f5fc6668712af9d89d00cafe9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614619"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a><span data-ttu-id="5a49a-101">WPF : Modification d’une clé primaire lors de l’affichage de données ADO dans un scénario maître/détail</span><span class="sxs-lookup"><span data-stu-id="5a49a-101">WPF Changing a primary key when displaying ADO data in a Master/Detail scenario</span></span>

#### <a name="details"></a><span data-ttu-id="5a49a-102">Détails</span><span class="sxs-lookup"><span data-stu-id="5a49a-102">Details</span></span>

<span data-ttu-id="5a49a-103">Supposez que vous avez une collection ADO d’éléments de type `Order` avec une relation nommée &quot;OrderDetails&quot; mise en relation avec une collection d’éléments de type `Detail` via la clé primaire &quot;OrderID&quot;.</span><span class="sxs-lookup"><span data-stu-id="5a49a-103">Suppose you have an ADO collection of items of type `Order`, with a relation named &quot;OrderDetails&quot; relating it to a collection of items of type `Detail` via the primary key &quot;OrderID&quot;.</span></span> <span data-ttu-id="5a49a-104">Dans votre application WPF, vous pouvez lier un contrôle de liste aux détails d’un ordre spécifique :</span><span class="sxs-lookup"><span data-stu-id="5a49a-104">In your WPF app, you can bind a list control to the details for a given order:</span></span>

```xaml
<ListBox ItemsSource="{Binding Path=OrderDetails}" >
```

<span data-ttu-id="5a49a-105">où DataContext est un `Order`.</span><span class="sxs-lookup"><span data-stu-id="5a49a-105">where the DataContext is an `Order`.</span></span> <span data-ttu-id="5a49a-106">WPF obtient la valeur de la `OrderDetails` propriété : une collection D de tous les `Detail` éléments dont `OrderID` la correspond à la valeur `OrderID` de l’élément maître.</span><span class="sxs-lookup"><span data-stu-id="5a49a-106">WPF gets the value of the `OrderDetails` property - a collection D of all the `Detail` items whose `OrderID` matches the `OrderID` of the master item.</span></span> <span data-ttu-id="5a49a-107">Le changement de comportement se produit lorsque vous modifiez la clé primaire `OrderID` de l’élément maître.</span><span class="sxs-lookup"><span data-stu-id="5a49a-107">The behavior change arises when you change the primary key `OrderID` of the master item.</span></span> <span data-ttu-id="5a49a-108">ADO modifie automatiquement le `OrderID` de chacun des enregistrements concernés dans la collection de détails (à savoir les enregistrements copiés dans la collection D).</span><span class="sxs-lookup"><span data-stu-id="5a49a-108">ADO automatically changes the `OrderID` of each of the affected records in the Details collection (namely the ones copied into collection D).</span></span>  <span data-ttu-id="5a49a-109">Qu'advient-il ensuite de la collection D ?</span><span class="sxs-lookup"><span data-stu-id="5a49a-109">But what happens to D?</span></span>

- <span data-ttu-id="5a49a-110">Ancien comportement : la collection D est effacée.</span><span class="sxs-lookup"><span data-stu-id="5a49a-110">Old behavior: Collection D is cleared.</span></span> <span data-ttu-id="5a49a-111">L’élément principal ne déclenche *aucune* notification de modification pour la propriété `OrderDetails`.</span><span class="sxs-lookup"><span data-stu-id="5a49a-111">The master item does *not* raise a change notification for property `OrderDetails`.</span></span> <span data-ttu-id="5a49a-112">La zone de liste continue d’utiliser la collection D, qui est maintenant vide.</span><span class="sxs-lookup"><span data-stu-id="5a49a-112">The ListBox continues to use collection D, which is now empty.</span></span>
- <span data-ttu-id="5a49a-113">Nouveau comportement : la collection D reste inchangée.</span><span class="sxs-lookup"><span data-stu-id="5a49a-113">New behavior:  Collection D is unchanged.</span></span> <span data-ttu-id="5a49a-114">Chacun de ses éléments déclenche une notification de modification pour la propriété `OrderID`.</span><span class="sxs-lookup"><span data-stu-id="5a49a-114">Each of its items raises a change notification for the `OrderID` property.</span></span> <span data-ttu-id="5a49a-115">La zone de liste continue d’utiliser la collection D et affiche les détails avec le nouveau `OrderID`.</span><span class="sxs-lookup"><span data-stu-id="5a49a-115">The ListBox continues to use collection D, and displays the details with the new `OrderID`.</span></span> <span data-ttu-id="5a49a-116">WPF implémente le nouveau comportement en créant la collection D d’une autre manière : en appelant la méthode ADO <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> avec l’argument `followParent` défini sur `true`.</span><span class="sxs-lookup"><span data-stu-id="5a49a-116">WPF implements the new behavior by creating collection D in a different way:  by calling the ADO method <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> with the `followParent` argument set to `true`.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5a49a-117">Suggestion</span><span class="sxs-lookup"><span data-stu-id="5a49a-117">Suggestion</span></span>

<span data-ttu-id="5a49a-118">Une application obtient le nouveau comportement à l’aide du commutateur AppContext suivant.</span><span class="sxs-lookup"><span data-stu-id="5a49a-118">An app gets the new behavior by using the following AppContext switch.</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false"/>
  </runtime>
</configuration>
```

<span data-ttu-id="5a49a-119">Le commutateur par défaut est `true` (ancien comportement) pour les applications qui ciblent .NET 4.7.1 ou version antérieure, et `false` (nouveau comportement) pour les applications qui ciblent .NET 4.7.2 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="5a49a-119">The switch defaults to `true` (old behavior) for apps that target .NET 4.7.1 or below, and to `false` (new behavior) for apps that target .NET 4.7.2 or above.</span></span>

| <span data-ttu-id="5a49a-120">Nom</span><span class="sxs-lookup"><span data-stu-id="5a49a-120">Name</span></span>    | <span data-ttu-id="5a49a-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="5a49a-121">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5a49a-122">Étendue</span><span class="sxs-lookup"><span data-stu-id="5a49a-122">Scope</span></span>   | <span data-ttu-id="5a49a-123">Secondaire</span><span class="sxs-lookup"><span data-stu-id="5a49a-123">Minor</span></span>       |
| <span data-ttu-id="5a49a-124">Version</span><span class="sxs-lookup"><span data-stu-id="5a49a-124">Version</span></span> | <span data-ttu-id="5a49a-125">4.7.2</span><span class="sxs-lookup"><span data-stu-id="5a49a-125">4.7.2</span></span>       |
| <span data-ttu-id="5a49a-126">Type</span><span class="sxs-lookup"><span data-stu-id="5a49a-126">Type</span></span>    | <span data-ttu-id="5a49a-127">Reciblage</span><span class="sxs-lookup"><span data-stu-id="5a49a-127">Retargeting</span></span> |
