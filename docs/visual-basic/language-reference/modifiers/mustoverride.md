---
title: MustOverride
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: cf73f07b6e13d524281129e3c5d8dceceb90764c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867950"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)

Spécifie qu’une propriété ou procédure n’est pas implémentée dans cette classe et qu’elle doit être substituée dans une classe dérivée avant de pouvoir être utilisée.  
  
## <a name="remarks"></a>Notes  

 Vous pouvez utiliser `MustOverride` uniquement dans une instruction de déclaration de propriété ou de procédure. La propriété ou la procédure qui spécifie `MustOverride` doit être membre d’une classe, et la classe doit être marquée [MustInherit](mustinherit.md).  
  
## <a name="rules"></a>Règles  
  
- **Déclaration incomplète.** Lorsque vous spécifiez `MustOverride` , vous ne fournissez pas de lignes de code supplémentaires pour la propriété ou la procédure, pas même l' `End Function` `End Property` instruction, ou `End Sub` .  
  
- **Modificateurs combinés.** Vous ne pouvez pas spécifier `MustOverride` avec `NotOverridable` , `Overridable` ou `Shared` dans la même déclaration.  
  
- **Occultation et substitution.** L'occultation et la substitution redéfinissent toutes les deux un élément hérité, mais il existe des différences importantes entre ces deux approches. Pour plus d’informations, consultez [occultation dans Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).  
  
- **Autres termes.** Un élément qui ne peut pas être utilisé sauf dans une substitution est parfois appelé élément *virtuel pur* .  
  
 Le modificateur `MustOverride` peut être utilisé dans les contextes suivants :  
  
 [Function (instruction)](../statements/function-statement.md)  
  
 [Property Statement](../statements/property-statement.md)  
  
 [Sub (instruction)](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [NotOverridable](notoverridable.md)
- [Overridable](overridable.md)
- [Remplacements](overrides.md)
- [MustInherit](mustinherit.md)
- [Mots clés](../keywords/index.md)
- [Occultation dans Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
