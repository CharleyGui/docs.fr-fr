---
title: "Comment : déclarer une propriété avec des niveaux d'accès mixtes"
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: 78363f7b2fb5b251f7409e53b2802baf83b05810
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072702"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="50b2c-102">Comment : déclarer une propriété avec des niveaux d'accès mixtes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50b2c-102">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>

<span data-ttu-id="50b2c-103">Si vous souhaitez que `Get` les `Set` procédures et sur une propriété aient des niveaux d’accès différents, vous pouvez utiliser le niveau le plus permissif dans l' `Property` instruction et le niveau le plus restrictif dans l' `Get` `Set` instruction ou.</span><span class="sxs-lookup"><span data-stu-id="50b2c-103">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="50b2c-104">Vous utilisez des niveaux d’accès mixtes sur une propriété lorsque vous souhaitez que certaines parties du code soient en mesure d’obtenir la valeur de la propriété, et que certaines autres parties du code soient en mesure de modifier la valeur.</span><span class="sxs-lookup"><span data-stu-id="50b2c-104">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="50b2c-105">Pour plus d’informations sur les niveaux d’accès, consultez [niveaux d’accès dans Visual Basic](../declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="50b2c-105">For more information on access levels, see [Access levels in Visual Basic](../declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="50b2c-106">Pour déclarer une propriété avec des niveaux d’accès mixtes</span><span class="sxs-lookup"><span data-stu-id="50b2c-106">To declare a property with mixed access levels</span></span>  
  
1. <span data-ttu-id="50b2c-107">Déclarez la propriété de manière normale et spécifiez le niveau d’accès le moins restrictif (tel que `Public` ) dans l' `Property` instruction.</span><span class="sxs-lookup"><span data-stu-id="50b2c-107">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2. <span data-ttu-id="50b2c-108">Déclarez la `Get` procédure ou `Set` en spécifiant le niveau d’accès le plus restrictif (tel que `Friend` ).</span><span class="sxs-lookup"><span data-stu-id="50b2c-108">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3. <span data-ttu-id="50b2c-109">Ne spécifiez pas un niveau d’accès sur l’autre procédure de propriété.</span><span class="sxs-lookup"><span data-stu-id="50b2c-109">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="50b2c-110">Il part du principe que le niveau d’accès est déclaré dans l' `Property` instruction.</span><span class="sxs-lookup"><span data-stu-id="50b2c-110">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="50b2c-111">Vous pouvez restreindre l’accès à une seule des procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="50b2c-111">You can restrict access on only one of the property procedures.</span></span>  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     <span data-ttu-id="50b2c-112">Dans l’exemple précédent, la `Get` procédure a le même `Protected` accès que la propriété elle-même, tandis que la `Set` procédure `Private` y a accès.</span><span class="sxs-lookup"><span data-stu-id="50b2c-112">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="50b2c-113">Une classe dérivée de `employee` peut lire la `salary` valeur, mais seule la `employee` classe peut la définir.</span><span class="sxs-lookup"><span data-stu-id="50b2c-113">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50b2c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50b2c-114">See also</span></span>

- [<span data-ttu-id="50b2c-115">Procédures</span><span class="sxs-lookup"><span data-stu-id="50b2c-115">Procedures</span></span>](./index.md)
- [<span data-ttu-id="50b2c-116">Procédures Property</span><span class="sxs-lookup"><span data-stu-id="50b2c-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="50b2c-117">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="50b2c-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="50b2c-118">Property Statement</span><span class="sxs-lookup"><span data-stu-id="50b2c-118">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="50b2c-119">Différences entre les propriétés et les variables en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="50b2c-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="50b2c-120">Comment : créer une propriété</span><span class="sxs-lookup"><span data-stu-id="50b2c-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="50b2c-121">Comment : appeler une procédure de propriété</span><span class="sxs-lookup"><span data-stu-id="50b2c-121">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="50b2c-122">Comment : déclarer et appeler une propriété par défaut en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="50b2c-122">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="50b2c-123">Comment : placer une valeur dans une propriété</span><span class="sxs-lookup"><span data-stu-id="50b2c-123">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="50b2c-124">Comment : obtenir une valeur d'une propriété</span><span class="sxs-lookup"><span data-stu-id="50b2c-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
