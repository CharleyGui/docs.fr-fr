---
title: Une valeur de type 'type1' ne peut pas être convertie en 'type2'
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 107936aa969690d0cc9fd4a2605cfceea31eeca8
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161411"
---
# <a name="bc31194-value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="d6162-102">BC31194 : la valeur de type’type1 'ne peut pas être convertie en’type2 '</span><span class="sxs-lookup"><span data-stu-id="d6162-102">BC31194: Value of type 'type1' cannot be converted to 'type2'</span></span>

<span data-ttu-id="d6162-103">Impossible de convertir une valeur de type’type1 'en’type2 '.</span><span class="sxs-lookup"><span data-stu-id="d6162-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="d6162-104">Vous pouvez utiliser la propriété’value’pour récupérer la valeur de chaîne du premier élément de' \<parentElement> '.</span><span class="sxs-lookup"><span data-stu-id="d6162-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>

 <span data-ttu-id="d6162-105">Une tentative de conversion implicite d’un littéral XML vers un type spécifique a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="d6162-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="d6162-106">Le littéral XML ne peut pas être implicitement converti vers le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="d6162-106">The XML literal cannot be implicitly cast to the specified type.</span></span>

 <span data-ttu-id="d6162-107">**ID d’erreur :** BC31194</span><span class="sxs-lookup"><span data-stu-id="d6162-107">**Error ID:** BC31194</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d6162-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="d6162-108">To correct this error</span></span>

- <span data-ttu-id="d6162-109">Utilisez la propriété `Value` du littéral XML pour faire référence à sa valeur comme une `String`.</span><span class="sxs-lookup"><span data-stu-id="d6162-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="d6162-110">Utilisez la fonction `CType` , une autre fonction de conversion de type, ou la classe <xref:System.Convert> pour effectuer un cast de la valeur vers le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="d6162-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6162-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6162-111">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="d6162-112">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="d6162-112">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="d6162-113">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="d6162-113">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="d6162-114">XML</span><span class="sxs-lookup"><span data-stu-id="d6162-114">XML</span></span>](../../programming-guide/language-features/xml/index.md)
