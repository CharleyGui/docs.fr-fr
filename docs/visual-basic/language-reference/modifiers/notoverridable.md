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
ms.openlocfilehash: c55d57bb3008b2825fe5382844908ea32f0d500c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351445"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
Spécifie qu’une propriété ou procédure ne peut pas être substituée dans une classe dérivée.  
  
## <a name="remarks"></a>Notes  
 Le modificateur `NotOverridable` empêche une propriété ou une méthode d’être substituée dans une classe dérivée.  Le modificateur [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) permet à une propriété ou à une méthode d’une classe d’être substituée dans une classe dérivée. Pour plus d’informations, consultez [Concepts de base de l’héritage](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Si le modificateur `Overridable` ou `NotOverridable` n’est pas spécifié, le paramètre par défaut varie selon que la propriété ou la méthode substitue une propriété ou une méthode de classe de base. Si la propriété ou la méthode substitue une propriété ou une méthode de classe de base, la valeur par défaut est `Overridable`; dans le cas contraire, il est `NotOverridable`.  
  
 Un élément qui ne peut pas être substitué est parfois appelé élément *sealed* .  
  
 Vous pouvez utiliser `NotOverridable` uniquement dans une instruction de déclaration de propriété ou de procédure. Vous pouvez spécifier `NotOverridable` uniquement sur une propriété ou une procédure qui remplace une autre propriété ou procédure, autrement dit, uniquement en association avec `Overrides`.  
  
## <a name="combined-modifiers"></a>Modificateurs combinés  
 Vous ne pouvez pas spécifier `Overridable` ou `NotOverridable` pour une méthode `Private`.  
  
 Vous ne pouvez pas spécifier `NotOverridable` avec `MustOverride`, `Overridable`ou `Shared` dans la même déclaration.  
  
## <a name="usage"></a>Utilisation  
 Le modificateur `NotOverridable` peut être utilisé dans les contextes suivants :  
  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Modificateurs](../../../visual-basic/language-reference/modifiers/index.md)
- [Éléments fondamentaux de l’héritage](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
- [Occultation dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
