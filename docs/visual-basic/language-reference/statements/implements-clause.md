---
title: Implements (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
ms.openlocfilehash: 7c95cf76b1bac24e2a0f20857b8984d54ebbea85
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866159"
---
# <a name="implements-clause-visual-basic"></a>Implements, clause (Visual Basic)

Indique qu’un membre de classe ou de structure fournit l’implémentation d’un membre défini dans une interface.  
  
## <a name="remarks"></a>Notes  

Le `Implements` mot clé n’est pas le même que l' [instruction Implements](implements-statement.md). Utilisez l' `Implements` instruction pour spécifier qu’une classe ou une structure implémente une ou plusieurs interfaces, puis, pour chaque membre, vous utilisez le `Implements` mot clé pour spécifier l’interface et le membre qu’elle implémente.

Si une classe ou une structure implémente une interface, elle doit inclure l' `Implements` instruction immédiatement après l’instruction de la [classe](class-statement.md) ou de la [structure](structure-statement.md), et elle doit implémenter tous les membres définis par l’interface.

## <a name="reimplementation"></a>Réimplémentation  

Dans une classe dérivée, vous pouvez réimplémenter un membre d’interface que la classe de base a déjà implémenté. Cela diffère de la substitution du membre de classe de base dans les aspects suivants :

- Le membre de la classe de base n’a pas besoin d’être [substituable](../modifiers/overridable.md) pour être réimplémenté.
- Vous pouvez réimplémenter le membre avec un nom différent.

Le `Implements` mot clé peut être utilisé dans les contextes suivants :

- [Event, instruction](event-statement.md)
- [Function (instruction)](function-statement.md)
- [Property Statement](property-statement.md)
- [Sub (instruction)](sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Implements, instruction](implements-statement.md)
- [Interface (instruction)](interface-statement.md)
- [Class (instruction)](class-statement.md)
- [Structure, instruction](structure-statement.md)
