---
title: La procédure Property Let n'est pas définie et la procédure Property Get n'a pas retourné d'objet
ms.date: 07/20/2015
f1_keywords:
- vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
ms.openlocfilehash: fbeaa224ea9e095f86c37e571492d83bc98b4397
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871096"
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a><span data-ttu-id="bbdeb-102">La procédure Property Let n'est pas définie et la procédure Property Get n'a pas retourné d'objet</span><span class="sxs-lookup"><span data-stu-id="bbdeb-102">Property let procedure not defined and property get procedure did not return an object</span></span>

<span data-ttu-id="bbdeb-103">Certaines propriétés, méthodes et opérations ne peuvent s’appliquer qu’à des `Collection` objets.</span><span class="sxs-lookup"><span data-stu-id="bbdeb-103">Certain properties, methods, and operations can only apply to `Collection` objects.</span></span> <span data-ttu-id="bbdeb-104">Vous avez spécifié une opération ou une propriété qui est exclusive aux collections, mais l’objet n’est pas une collection.</span><span class="sxs-lookup"><span data-stu-id="bbdeb-104">You specified an operation or property that is exclusive to collections, but the object is not a collection.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bbdeb-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="bbdeb-105">To correct this error</span></span>  
  
1. <span data-ttu-id="bbdeb-106">Vérifiez l’orthographe du nom de l’objet ou de la propriété, ou vérifiez que l’objet est un `Collection` objet.</span><span class="sxs-lookup"><span data-stu-id="bbdeb-106">Check the spelling of the object or property name, or verify that the object is a `Collection` object.</span></span>  
  
2. <span data-ttu-id="bbdeb-107">Examinez la `Add` méthode utilisée pour ajouter l’objet à la collection afin de vérifier que la syntaxe est correcte et que tous les identificateurs ont été correctement orthographiés.</span><span class="sxs-lookup"><span data-stu-id="bbdeb-107">Look at the `Add` method used to add the object to the collection to be sure the syntax is correct and that any identifiers were spelled correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbdeb-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbdeb-108">See also</span></span>

- <xref:Microsoft.VisualBasic.Collection>
