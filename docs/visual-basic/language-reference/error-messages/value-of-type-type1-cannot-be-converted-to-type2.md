---
title: Une valeur de type 'type1' ne peut pas être convertie en 'type2'
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: f19f157bd4c76f481aa3232bc33c2a0c6ac21367
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400277"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="61a67-102">Une valeur de type 'type1' ne peut pas être convertie en 'type2'</span><span class="sxs-lookup"><span data-stu-id="61a67-102">Value of type 'type1' cannot be converted to 'type2'</span></span>
<span data-ttu-id="61a67-103">Impossible de convertir une valeur de type’type1 'en’type2 '.</span><span class="sxs-lookup"><span data-stu-id="61a67-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="61a67-104">Vous pouvez utiliser la propriété’value’pour récupérer la valeur de chaîne du premier élément de' \<parentElement> '.</span><span class="sxs-lookup"><span data-stu-id="61a67-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="61a67-105">Une tentative de conversion implicite d’un littéral XML vers un type spécifique a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="61a67-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="61a67-106">Le littéral XML ne peut pas être implicitement converti vers le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="61a67-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="61a67-107">**ID d’erreur :** BC31194</span><span class="sxs-lookup"><span data-stu-id="61a67-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="61a67-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="61a67-108">To correct this error</span></span>  
  
- <span data-ttu-id="61a67-109">Utilisez la propriété `Value` du littéral XML pour faire référence à sa valeur comme une `String`.</span><span class="sxs-lookup"><span data-stu-id="61a67-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="61a67-110">Utilisez la fonction `CType` , une autre fonction de conversion de type, ou la classe <xref:System.Convert> pour effectuer un cast de la valeur vers le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="61a67-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61a67-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61a67-111">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="61a67-112">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="61a67-112">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="61a67-113">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="61a67-113">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="61a67-114">XML</span><span class="sxs-lookup"><span data-stu-id="61a67-114">XML</span></span>](../../programming-guide/language-features/xml/index.md)
