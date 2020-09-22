---
title: Privées
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 59f1c1666ce38923a2861244fb377007cd0fa992
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874975"
---
# <a name="private-visual-basic"></a>Private (Visual Basic)

Spécifie qu’un ou plusieurs éléments de programmation déclarés sont accessibles uniquement à partir de leur contexte de déclaration, y compris à partir de tous les types contenus.  
  
## <a name="remarks"></a>Notes  

 Si un élément de programmation représente une fonctionnalité propriétaire ou contient des données confidentielles, vous souhaitez généralement limiter l’accès à celui-ci aussi strictement que possible. Vous atteignez la limite maximale en autorisant uniquement le module, la classe ou la structure qui le définit à y accéder. Pour limiter l’accès à un élément de cette manière, vous pouvez le déclarer avec `Private` .  

> [!NOTE]
> Vous pouvez également utiliser le modificateur d’accès [protected Private](private-protected.md) , qui rend un membre accessible à partir de cette classe et à partir de classes dérivées situées dans son assembly conteneur.

## <a name="rules"></a>Règles  

- **Contexte de déclaration.** Vous pouvez utiliser `Private` seulement au niveau du module. Cela signifie que le contexte de déclaration pour un `Private` élément doit être un module, une classe ou une structure, et ne peut pas être un fichier source, un espace de noms, une interface ou une procédure.  
  
## <a name="behavior"></a>Comportement  
  
- **Niveau d’accès.** Tout le code dans un contexte de déclaration peut accéder à ses `Private` éléments. Cela comprend le code dans un type contenu, tel qu’une classe imbriquée ou une expression d’assignation dans une énumération. Aucun code en dehors du contexte de déclaration ne peut accéder à ses `Private` éléments.  
  
- **Modificateurs d’accès.** Les mots clés qui spécifient le niveau d’accès sont appelés *modificateurs d’accès*. Pour une comparaison des modificateurs d’accès, consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
 Le modificateur `Private` peut être utilisé dans les contextes suivants :  
  
 [Class (instruction)](../statements/class-statement.md)  
  
 [Const (instruction)](../statements/const-statement.md)  
  
 [Declare Statement](../statements/declare-statement.md)  
  
 [Delegate, instruction](../statements/delegate-statement.md)  
  
 [Dim (instruction)](../statements/dim-statement.md)  
  
 [Enum (instruction)](../statements/enum-statement.md)  
  
 [Event, instruction](../statements/event-statement.md)  
  
 [Function (instruction)](../statements/function-statement.md)  
  
 [Interface (instruction)](../statements/interface-statement.md)  
  
 [Property Statement](../statements/property-statement.md)  
  
 [Structure, instruction](../statements/structure-statement.md)  
  
 [Sub (instruction)](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Public](public.md)
- [Protect](protected.md)
- [Friend](friend.md)
- [Protégé privé](./private-protected.md)
- [Protected Friend](./protected-friend.md)
- [Niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Procédures](../../programming-guide/language-features/procedures/index.md)
- [Structures](../../programming-guide/language-features/data-types/structures.md)
- [Objets et classes](../../programming-guide/language-features/objects-and-classes/index.md)
