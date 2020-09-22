---
title: Les constantes doivent être de type intrinsèque ou énuméré, et non de type classe, structure, paramètre de type ou tableau
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: a9bbf27615233f4282e481710a0234b2fa589f63
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874558"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="f6b74-102">Les constantes doivent être de type intrinsèque ou énuméré, et non de type classe, structure, paramètre de type ou tableau</span><span class="sxs-lookup"><span data-stu-id="f6b74-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>

<span data-ttu-id="f6b74-103">Vous avez tenté de déclarer une constante en tant que type de classe, de structure ou de tableau, ou en tant que paramètre de type défini par un type générique conteneur.</span><span class="sxs-lookup"><span data-stu-id="f6b74-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="f6b74-104">Les constantes doivent être de type intrinsèque ( `Boolean` , `Byte` , `Date` , `Decimal` , `Double` , `Integer` , `Long` , `Object` , `SByte` , `Short` , `Single` , `String` , `UInteger` , `ULong` ou `UShort` ) ou d’un `Enum` type basé sur l’un des types intégraux.</span><span class="sxs-lookup"><span data-stu-id="f6b74-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="f6b74-105">**ID d’erreur :** BC30424</span><span class="sxs-lookup"><span data-stu-id="f6b74-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f6b74-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="f6b74-106">To correct this error</span></span>  
  
1. <span data-ttu-id="f6b74-107">Déclarez la constante en tant que `Enum` type intrinsèque ou.</span><span class="sxs-lookup"><span data-stu-id="f6b74-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2. <span data-ttu-id="f6b74-108">Une constante peut également être une valeur spéciale telle que `True` , `False` ou `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="f6b74-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="f6b74-109">Le compilateur considère ces valeurs prédéfinies comme étant du type intrinsèque approprié.</span><span class="sxs-lookup"><span data-stu-id="f6b74-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6b74-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6b74-110">See also</span></span>

- [<span data-ttu-id="f6b74-111">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="f6b74-111">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
- [<span data-ttu-id="f6b74-112">Data types</span><span class="sxs-lookup"><span data-stu-id="f6b74-112">Data Types</span></span>](../../programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="f6b74-113">Data types</span><span class="sxs-lookup"><span data-stu-id="f6b74-113">Data Types</span></span>](../data-types/index.md)
