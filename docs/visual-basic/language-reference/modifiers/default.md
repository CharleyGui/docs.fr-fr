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
ms.openlocfilehash: 0c2808795d6fcbad7892369fd7f460ebf0406093
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372970"
---
# <a name="default-visual-basic"></a>Default (Visual Basic)
Identifie une propriété en tant que propriété par défaut de sa classe, structure ou interface.  
  
## <a name="remarks"></a>Notes  
 Une classe, une structure ou une interface peut désigner au plus l’une de ses propriétés comme *propriété par défaut*, à condition que la propriété prenne au moins un paramètre. Si le code fait référence à une classe ou à une structure sans spécifier de membre, Visual Basic résout cette référence à la propriété par défaut.  
  
 Les propriétés par défaut peuvent entraîner une petite réduction des caractères de code source, mais elles peuvent rendre votre code plus difficile à lire. Si le code appelant n’est pas familiarisé avec votre classe ou structure, lorsqu’il fait référence au nom de la classe ou de la structure, il ne peut pas être certain que cette référence accède à la classe ou à la structure elle-même, ou à une propriété par défaut. Cela peut entraîner des erreurs de compilation ou des erreurs de logique d’exécution subtiles.  
  
 Vous pouvez réduire légèrement les risques d’erreurs de propriété par défaut en utilisant toujours l' [instruction Option Strict](../statements/option-strict-statement.md) pour définir la vérification du type de compilateur sur `On` .  
  
 Si vous envisagez d’utiliser une classe ou une structure prédéfinie dans votre code, vous devez déterminer si elle a une propriété par défaut et, dans ce cas, son nom.  
  
 En raison de ces inconvénients, vous devez envisager de ne pas définir de propriétés par défaut. Pour une meilleure lisibilité du code, vous devez également penser à toujours faire référence à toutes les propriétés explicitement, même les propriétés par défaut.  
  
 Le `Default` modificateur peut être utilisé dans ce contexte :  
  
 [Property Statement](../statements/property-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Comment : déclarer et appeler une propriété par défaut en Visual Basic](../../programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [Mots clés](../keywords/index.md)
