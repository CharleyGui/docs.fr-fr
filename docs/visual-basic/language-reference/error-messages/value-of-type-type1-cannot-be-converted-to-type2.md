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
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a>Une valeur de type 'type1' ne peut pas être convertie en 'type2'
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
