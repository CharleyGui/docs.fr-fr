---
title: Une valeur de type 'type1' ne peut pas être convertie en 'type2'
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 8c80429db618e1bcadce1a58a6514d625f0b3cf1
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870236"
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
