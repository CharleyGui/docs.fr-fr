---
title: Formuler des projections
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: f0bc6dfcff7778ebc7156cbb039e13570c90467b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194399"
---
# <a name="formulate-projections"></a><span data-ttu-id="bcb8b-102">Formuler des projections</span><span class="sxs-lookup"><span data-stu-id="bcb8b-102">Formulate Projections</span></span>

<span data-ttu-id="bcb8b-103">Les exemples suivants montrent comment l' `select` instruction en C# et l' `Select` instruction dans Visual Basic peuvent être combinées avec d’autres fonctionnalités pour former des projections de requête.</span><span class="sxs-lookup"><span data-stu-id="bcb8b-103">The following examples show how the `select` statement in C# and `Select` statement in Visual Basic can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcb8b-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="bcb8b-104">Example</span></span>  

 <span data-ttu-id="bcb8b-105">L’exemple suivant utilise la `Select` clause dans Visual Basic ( `select` clause dans C#) pour retourner une séquence de noms de contact pour `Customers` .</span><span class="sxs-lookup"><span data-stu-id="bcb8b-105">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="bcb8b-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="bcb8b-106">Example</span></span>  

 <span data-ttu-id="bcb8b-107">L’exemple suivant utilise la `Select` clause dans Visual Basic ( `select` clause en C#) et des *types anonymes* pour retourner une séquence de noms de contact et de numéros de téléphone pour `Customers` .</span><span class="sxs-lookup"><span data-stu-id="bcb8b-107">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="bcb8b-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="bcb8b-108">Example</span></span>  

 <span data-ttu-id="bcb8b-109">L’exemple suivant utilise la `Select` clause dans Visual Basic ( `select` clause en C#) et des *types anonymes* pour retourner une séquence de noms et de numéros de téléphone pour les employés.</span><span class="sxs-lookup"><span data-stu-id="bcb8b-109">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="bcb8b-110">Les `FirstName` `LastName` champs et sont combinés en un champ unique ( `Name` ) et le `HomePhone` champ est renommé `Phone` dans la séquence résultante.</span><span class="sxs-lookup"><span data-stu-id="bcb8b-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="bcb8b-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="bcb8b-111">Example</span></span>  

 <span data-ttu-id="bcb8b-112">L’exemple suivant utilise la `Select` clause dans Visual Basic ( `select` clause en C#) et des *types anonymes* pour retourner une séquence de tous les `ProductID` et une valeur calculée nommée `HalfPrice` .</span><span class="sxs-lookup"><span data-stu-id="bcb8b-112">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="bcb8b-113">Cette valeur correspond à `UnitPrice` divisé par 2.</span><span class="sxs-lookup"><span data-stu-id="bcb8b-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="bcb8b-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="bcb8b-114">Example</span></span>  

 <span data-ttu-id="bcb8b-115">L’exemple suivant utilise la `Select` clause dans Visual Basic ( `select` clause en C#) et une *instruction conditionnelle* pour retourner une séquence de nom de produit et de disponibilité du produit.</span><span class="sxs-lookup"><span data-stu-id="bcb8b-115">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="bcb8b-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="bcb8b-116">Example</span></span>  

 <span data-ttu-id="bcb8b-117">L’exemple suivant utilise une `Select` clause Visual Basic ( `select` clause en C#) et un *type connu* (nom) pour retourner une séquence des noms des employés.</span><span class="sxs-lookup"><span data-stu-id="bcb8b-117">The following example uses a Visual Basic `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="bcb8b-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="bcb8b-118">Example</span></span>  

 <span data-ttu-id="bcb8b-119">L’exemple suivant utilise `Select` et `Where` dans Visual Basic ( `select` et `where` en C#) pour retourner une *séquence filtrée* de noms de contact pour les clients de Londres.</span><span class="sxs-lookup"><span data-stu-id="bcb8b-119">The following example uses `Select` and `Where` in Visual Basic (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="bcb8b-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="bcb8b-120">Example</span></span>  

 <span data-ttu-id="bcb8b-121">L’exemple suivant utilise une `Select` clause dans Visual Basic ( `select` clause en C#) et des *types anonymes* pour retourner un *sous-ensemble mis en forme* des données sur les clients.</span><span class="sxs-lookup"><span data-stu-id="bcb8b-121">The following example uses a `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="bcb8b-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="bcb8b-122">Example</span></span>  

 <span data-ttu-id="bcb8b-123">L'exemple suivant utilise des requêtes imbriquées pour retourner les résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="bcb8b-123">The following example uses nested queries to return the following results:</span></span>  
  
- <span data-ttu-id="bcb8b-124">Séquence de toutes les commandes et des `OrderID` correspondants.</span><span class="sxs-lookup"><span data-stu-id="bcb8b-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
- <span data-ttu-id="bcb8b-125">Sous-séquence des éléments dans la commande pour laquelle il existe une remise.</span><span class="sxs-lookup"><span data-stu-id="bcb8b-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
- <span data-ttu-id="bcb8b-126">Montant enregistré si le coût d'expédition n'est pas inclus.</span><span class="sxs-lookup"><span data-stu-id="bcb8b-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="bcb8b-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcb8b-127">See also</span></span>

- [<span data-ttu-id="bcb8b-128">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="bcb8b-128">Query Examples</span></span>](query-examples.md)
