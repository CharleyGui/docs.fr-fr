---
title: Default
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: ad4c9528f208cc2c31f07b0506d1b049a7568c86
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351583"
---
# <a name="default-visual-basic"></a><span data-ttu-id="09821-102">Default (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09821-102">Default (Visual Basic)</span></span>
<span data-ttu-id="09821-103">Identifie une propriété en tant que propriété par défaut de sa classe, structure ou interface.</span><span class="sxs-lookup"><span data-stu-id="09821-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09821-104">Notes</span><span class="sxs-lookup"><span data-stu-id="09821-104">Remarks</span></span>  
 <span data-ttu-id="09821-105">Une classe, une structure ou une interface peut désigner au plus l’une de ses propriétés comme *propriété par défaut*, à condition que la propriété prenne au moins un paramètre.</span><span class="sxs-lookup"><span data-stu-id="09821-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="09821-106">Si le code fait référence à une classe ou à une structure sans spécifier de membre, Visual Basic résout cette référence à la propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="09821-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="09821-107">Les propriétés par défaut peuvent entraîner une petite réduction des caractères de code source, mais elles peuvent rendre votre code plus difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="09821-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="09821-108">Si le code appelant n’est pas familiarisé avec votre classe ou structure, lorsqu’il fait référence au nom de la classe ou de la structure, il ne peut pas être certain que cette référence accède à la classe ou à la structure elle-même, ou à une propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="09821-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="09821-109">Cela peut entraîner des erreurs de compilation ou des erreurs de logique d’exécution subtiles.</span><span class="sxs-lookup"><span data-stu-id="09821-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="09821-110">Vous pouvez réduire légèrement les risques d’erreurs de propriété par défaut en utilisant toujours l' [instruction Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) pour définir la vérification du type de compilateur sur `On`.</span><span class="sxs-lookup"><span data-stu-id="09821-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="09821-111">Si vous envisagez d’utiliser une classe ou une structure prédéfinie dans votre code, vous devez déterminer si elle a une propriété par défaut et, dans ce cas, son nom.</span><span class="sxs-lookup"><span data-stu-id="09821-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="09821-112">En raison de ces inconvénients, vous devez envisager de ne pas définir de propriétés par défaut.</span><span class="sxs-lookup"><span data-stu-id="09821-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="09821-113">Pour une meilleure lisibilité du code, vous devez également penser à toujours faire référence à toutes les propriétés explicitement, même les propriétés par défaut.</span><span class="sxs-lookup"><span data-stu-id="09821-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="09821-114">Le modificateur `Default` peut être utilisé dans ce contexte :</span><span class="sxs-lookup"><span data-stu-id="09821-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="09821-115">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="09821-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="09821-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09821-116">See also</span></span>

- [<span data-ttu-id="09821-117">Comment : déclarer et appeler une propriété par défaut dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="09821-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="09821-118">Mots clés</span><span class="sxs-lookup"><span data-stu-id="09821-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
