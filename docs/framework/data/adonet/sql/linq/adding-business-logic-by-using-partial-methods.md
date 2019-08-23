---
title: Ajout d'une logique métier à l'aide de méthodes partielles
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: e3f82c260a2cab85270a9f33a87eb9a9f04b72c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964144"
---
# <a name="adding-business-logic-by-using-partial-methods"></a><span data-ttu-id="8a1fd-102">Ajout d'une logique métier à l'aide de méthodes partielles</span><span class="sxs-lookup"><span data-stu-id="8a1fd-102">Adding Business Logic By Using Partial Methods</span></span>
<span data-ttu-id="8a1fd-103">Vous pouvez personnaliser Visual Basic et C# le code généré dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vos projets à l’aide de *méthodes partielles*.</span><span class="sxs-lookup"><span data-stu-id="8a1fd-103">You can customize Visual Basic and C# generated code in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects by using *partial methods*.</span></span> <span data-ttu-id="8a1fd-104">Le code généré par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] définit des signatures comme faisant partie d'une méthode partielle.</span><span class="sxs-lookup"><span data-stu-id="8a1fd-104">The code that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates defines signatures as one part of a partial method.</span></span> <span data-ttu-id="8a1fd-105">Si vous souhaitez implémenter la méthode, vous pouvez ajouter votre propre méthode partielle.</span><span class="sxs-lookup"><span data-stu-id="8a1fd-105">If you want to implement the method, you can add your own partial method.</span></span> <span data-ttu-id="8a1fd-106">Si vous n'ajoutez pas votre propre implémentation, le compilateur ignore la signature de méthodes partielles et appelle les méthodes par défaut dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8a1fd-106">If you do not add your own implementation, the compiler discards the partial methods signature and calls the default methods in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a1fd-107">Si vous utilisez Visual Studio, vous pouvez utiliser la Concepteur Objet Relationnel pour ajouter la validation et d’autres personnalisations aux classes d’entité.</span><span class="sxs-lookup"><span data-stu-id="8a1fd-107">If you are using Visual Studio, you can use the Object Relational Designer to add validation and other customizations to entity classes.</span></span>  
  
 <span data-ttu-id="8a1fd-108">Par exemple, le mappage par défaut pour la classe `Customer` dans l'exemple de base de données Northwind inclut la méthode partielle suivante :</span><span class="sxs-lookup"><span data-stu-id="8a1fd-108">For example, the default mapping for the `Customer` class in the Northwind sample database includes the following partial method:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 <span data-ttu-id="8a1fd-109">Vous pouvez implémenter votre propre méthode en ajoutant du code tel que le suivant à votre propre classe `Customer` partielle :</span><span class="sxs-lookup"><span data-stu-id="8a1fd-109">You can implement your own method by adding code such as the following to your own partial `Customer` class:</span></span>  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 <span data-ttu-id="8a1fd-110">Cette approche est généralement utilisée dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour substituer des méthodes par défaut `Update`pour `Delete`,, et pour valider des propriétés pendant des `Insert`événements de cycle de vie d’objet.</span><span class="sxs-lookup"><span data-stu-id="8a1fd-110">This approach is typically used in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to override default methods for `Insert`, `Update`, `Delete`, and to validate properties during object life-cycle events.</span></span>  
  
 <span data-ttu-id="8a1fd-111">Pour plus d’informations, consultez [méthodes partielles](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) ou [Partial (méthodeC# ) (référence)](../../../../../csharp/language-reference/keywords/partial-method.md) (C#).</span><span class="sxs-lookup"><span data-stu-id="8a1fd-111">For more information, see [Partial Methods](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) or [partial (Method) (C# Reference)](../../../../../csharp/language-reference/keywords/partial-method.md) (C#).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a1fd-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="8a1fd-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8a1fd-113">Description</span><span class="sxs-lookup"><span data-stu-id="8a1fd-113">Description</span></span>  
 <span data-ttu-id="8a1fd-114">L'exemple suivant montre d'abord `ExampleClass` tel qu'il pourrait être défini par un outil de génération de code tel que SQLMetal, puis comment vous pouvez implémenter l'une des deux méthodes seulement.</span><span class="sxs-lookup"><span data-stu-id="8a1fd-114">The following example shows `ExampleClass` first as it might be defined by a code-generating tool such as SQLMetal, and then how you might implement only one of the two methods.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a1fd-115">Code</span><span class="sxs-lookup"><span data-stu-id="8a1fd-115">Code</span></span>  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="8a1fd-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="8a1fd-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8a1fd-117">Description</span><span class="sxs-lookup"><span data-stu-id="8a1fd-117">Description</span></span>  
 <span data-ttu-id="8a1fd-118">L'exemple suivant utilise la relation entre les entités `Shipper` et `Order`.</span><span class="sxs-lookup"><span data-stu-id="8a1fd-118">The following example uses the relationship between `Shipper` and `Order` entities.</span></span> <span data-ttu-id="8a1fd-119">Notez parmi les méthodes celles qui sont partielles, `InsertShipper` et `DeleteShipper`.</span><span class="sxs-lookup"><span data-stu-id="8a1fd-119">Note among the methods the partial methods, `InsertShipper` and `DeleteShipper`.</span></span> <span data-ttu-id="8a1fd-120">Ces méthodes remplacent les méthodes partielles par défaut [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournies par le mappage.</span><span class="sxs-lookup"><span data-stu-id="8a1fd-120">These methods override the default partial methods supplied by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapping.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a1fd-121">Code</span><span class="sxs-lookup"><span data-stu-id="8a1fd-121">Code</span></span>  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8a1fd-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a1fd-122">See also</span></span>

- [<span data-ttu-id="8a1fd-123">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="8a1fd-123">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="8a1fd-124">Personnalisation des opérations d’insertion, de mise à jour et de suppression</span><span class="sxs-lookup"><span data-stu-id="8a1fd-124">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
