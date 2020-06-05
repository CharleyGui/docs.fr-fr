---
title: NotOverridable
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: 463dd2454aafebf11554fb7bacdb73724c3130d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392156"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
Spécifie qu’une propriété ou procédure ne peut pas être substituée dans une classe dérivée.  
  
## <a name="remarks"></a>Notes  
 Le `NotOverridable` modificateur empêche une propriété ou une méthode d’être substituée dans une classe dérivée.  Le modificateur [Overridable](overridable.md) permet à une propriété ou à une méthode d’une classe d’être substituée dans une classe dérivée. Pour plus d’informations, consultez [Concepts de base de l’héritage](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Si le `Overridable` `NotOverridable` modificateur ou n’est pas spécifié, le paramètre par défaut varie selon que la propriété ou la méthode substitue une propriété ou une méthode de classe de base. Si la propriété ou la méthode substitue une propriété ou une méthode de classe de base, la valeur par défaut est `Overridable` ; sinon, elle a la valeur `NotOverridable` .  
  
 Un élément qui ne peut pas être substitué est parfois appelé élément *sealed* .  
  
 Vous pouvez utiliser `NotOverridable` uniquement dans une instruction de déclaration de propriété ou de procédure. Vous pouvez spécifier `NotOverridable` uniquement sur une propriété ou une procédure qui remplace une autre propriété ou procédure, autrement dit, uniquement en association avec `Overrides` .  
  
## <a name="combined-modifiers"></a>Modificateurs combinés  
 Vous ne pouvez pas spécifier `Overridable` ou `NotOverridable` pour une `Private` méthode.  
  
 Vous ne pouvez pas spécifier `NotOverridable` avec `MustOverride` , `Overridable` ou `Shared` dans la même déclaration.  
  
## <a name="usage"></a>Utilisation  
 Le modificateur `NotOverridable` peut être utilisé dans les contextes suivants :  
  
 [Function (instruction)](../statements/function-statement.md)  
  
 [Property Statement](../statements/property-statement.md)  
  
 [Sub (instruction)](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Modificateurs](index.md)
- [Éléments fondamentaux de l’héritage](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](mustoverride.md)
- [Overridable](overridable.md)
- [Remplacements](overrides.md)
- [Mots clés](../keywords/index.md)
- [Occultation dans Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
