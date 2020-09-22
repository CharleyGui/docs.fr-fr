---
title: Overridable
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: 8506aba7e64f2dbd975cc275cefb7b5bb1aefda5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875006"
---
# <a name="overridable-visual-basic"></a>Overridable (Visual Basic)

Spécifie qu’une propriété ou procédure peut être substituée par une propriété ou procédure portant le même nom dans une classe dérivée.  
  
## <a name="remarks"></a>Notes  

 Le `Overridable` modificateur permet à une propriété ou une méthode d’une classe d’être substituée dans une classe dérivée. Le modificateur [NotOverridable](notoverridable.md) empêche une propriété ou une méthode d’être substituée dans une classe dérivée.  Pour plus d’informations, consultez [Concepts de base de l’héritage](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Si le `Overridable` `NotOverridable` modificateur ou n’est pas spécifié, le paramètre par défaut varie selon que la propriété ou la méthode substitue une propriété ou une méthode de classe de base. Si la propriété ou la méthode substitue une propriété ou une méthode de classe de base, la valeur par défaut est `Overridable` ; sinon, elle a la valeur `NotOverridable` .  
  
 Vous pouvez masquer ou substituer pour redéfinir un élément hérité, mais il existe des différences significatives entre les deux approches. Pour plus d’informations, consultez [occultation dans Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).  
  
 Un élément qui peut être substitué est parfois appelé élément *virtuel* . S’il peut être substitué, mais n’est pas nécessaire, il est parfois également appelé élément *concret* .  
  
 Vous pouvez utiliser `Overridable` uniquement dans une instruction de déclaration de propriété ou de procédure.  
  
## <a name="combined-modifiers"></a>Modificateurs combinés  

 Vous ne pouvez pas spécifier `Overridable` ou `NotOverridable` pour une `Private` méthode.  
  
 Vous ne pouvez pas spécifier `Overridable` avec `MustOverride` , `NotOverridable` ou `Shared` dans la même déclaration.  
  
 Comme un élément de substitution est implicitement substituable, vous ne pouvez pas combiner `Overridable` avec `Overrides`.  
  
## <a name="usage"></a>Usage  

 Le modificateur `Overridable` peut être utilisé dans les contextes suivants :  
  
 [Function (instruction)](../statements/function-statement.md)  
  
 [Property Statement](../statements/property-statement.md)  
  
 [Sub (instruction)](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Modificateurs](index.md)
- [Éléments fondamentaux de l’héritage](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](mustoverride.md)
- [NotOverridable](notoverridable.md)
- [Remplacements](overrides.md)
- [Mots clés](../keywords/index.md)
- [Occultation dans Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
