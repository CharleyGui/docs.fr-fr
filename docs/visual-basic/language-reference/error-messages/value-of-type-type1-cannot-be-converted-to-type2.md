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
# <a name="bc31194-value-of-type-type1-cannot-be-converted-to-type2"></a>BC31194 : la valeur de type’type1 'ne peut pas être convertie en’type2 '

Impossible de convertir une valeur de type’type1 'en’type2 '. Vous pouvez utiliser la propriété’value’pour récupérer la valeur de chaîne du premier élément de' \<parentElement> '.

 Une tentative de conversion implicite d’un littéral XML vers un type spécifique a été effectuée. Le littéral XML ne peut pas être implicitement converti vers le type spécifié.

 **ID d’erreur :** BC31194

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Utilisez la propriété `Value` du littéral XML pour faire référence à sa valeur comme une `String`. Utilisez la fonction `CType` , une autre fonction de conversion de type, ou la classe <xref:System.Convert> pour effectuer un cast de la valeur vers le type spécifié.

## <a name="see-also"></a>Voir aussi

- <xref:System.Convert>
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [Littéraux XML](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
