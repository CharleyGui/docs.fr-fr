---
title: "Comment : créer une méthode d'extension Add utilisée par un initialiseur de collection"
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 4dbe6146b70181864a6717146071f9b93a1f583e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414567"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="e8db6-102">Comment : créer une méthode d'extension Add utilisée par un initialiseur de collection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8db6-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="e8db6-103">Lorsque vous utilisez un initialiseur de collection pour créer une collection, le compilateur Visual Basic recherche une `Add` méthode du type de collection pour lequel les paramètres de la `Add` méthode correspondent aux types des valeurs dans l’initialiseur de collection.</span><span class="sxs-lookup"><span data-stu-id="e8db6-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="e8db6-104">Cette `Add` méthode est utilisée pour remplir la collection avec les valeurs de l’initialiseur de collection.</span><span class="sxs-lookup"><span data-stu-id="e8db6-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="e8db6-105">S’il n' `Add` existe aucune méthode correspondante et que vous ne pouvez pas modifier le code de la collection, vous pouvez ajouter une méthode d’extension nommée `Add` qui accepte les paramètres requis par l’initialiseur de collection.</span><span class="sxs-lookup"><span data-stu-id="e8db6-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="e8db6-106">C’est généralement ce que vous devez faire lorsque vous utilisez des initialiseurs de collection pour les collections génériques.</span><span class="sxs-lookup"><span data-stu-id="e8db6-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8db6-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="e8db6-107">Example</span></span>  
 <span data-ttu-id="e8db6-108">L’exemple suivant montre comment ajouter une méthode d’extension au type générique <xref:System.Collections.Generic.List%601> afin qu’un initialiseur de collection puisse être utilisé pour ajouter des objets de type `Employee` .</span><span class="sxs-lookup"><span data-stu-id="e8db6-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="e8db6-109">La méthode d’extension vous permet d’utiliser la syntaxe raccourcie de l’initialiseur de collection.</span><span class="sxs-lookup"><span data-stu-id="e8db6-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e8db6-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8db6-110">See also</span></span>

- [<span data-ttu-id="e8db6-111">Initialiseurs de collection</span><span class="sxs-lookup"><span data-stu-id="e8db6-111">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="e8db6-112">Guide pratique : créer une collection utilisée par un initialiseur de collection</span><span class="sxs-lookup"><span data-stu-id="e8db6-112">How to: Create a Collection Used by a Collection Initializer</span></span>](how-to-create-a-collection-used-by-a-collection-initializer.md)
