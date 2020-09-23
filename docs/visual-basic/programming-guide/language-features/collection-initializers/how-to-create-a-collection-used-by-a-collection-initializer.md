---
title: 'Comment : créer une collection utilisée par un initialiseur de collection'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: b332ffb44ebc20ce8431e586fc380b8c6a29967d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086372"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="c4b44-102">Comment : créer une collection utilisée par un initialiseur de collection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4b44-102">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>

<span data-ttu-id="c4b44-103">Lorsque vous utilisez un initialiseur de collection pour créer une collection, le compilateur Visual Basic recherche une `Add` méthode du type de collection pour lequel les paramètres de la `Add` méthode correspondent aux types des valeurs dans l’initialiseur de collection.</span><span class="sxs-lookup"><span data-stu-id="c4b44-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="c4b44-104">Cette `Add` méthode est utilisée pour remplir la collection avec les valeurs de l’initialiseur de collection.</span><span class="sxs-lookup"><span data-stu-id="c4b44-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4b44-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="c4b44-105">Example</span></span>  

 <span data-ttu-id="c4b44-106">L’exemple suivant montre une `OrderCollection` collection qui contient une `Add` méthode publique qu’un initialiseur de collection peut utiliser pour ajouter des objets de type `Order` .</span><span class="sxs-lookup"><span data-stu-id="c4b44-106">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="c4b44-107">La `Add` méthode vous permet d’utiliser la syntaxe raccourcie de l’initialiseur de collection.</span><span class="sxs-lookup"><span data-stu-id="c4b44-107">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c4b44-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4b44-108">See also</span></span>

- [<span data-ttu-id="c4b44-109">Initialiseurs de collection</span><span class="sxs-lookup"><span data-stu-id="c4b44-109">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="c4b44-110">Comment : créer une méthode d'extension Add utilisée par un initialiseur de collection</span><span class="sxs-lookup"><span data-stu-id="c4b44-110">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
