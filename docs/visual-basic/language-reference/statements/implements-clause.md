---
title: Implements, clause (Visual Basic)
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
ms.openlocfilehash: dcd20f21a989c327dcfcf27d5638d500b6e4b6da
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929320"
---
# <a name="implements-clause-visual-basic"></a>Implements, clause (Visual Basic)
Indique qu’un membre de classe ou de structure fournit l’implémentation d’un membre défini dans une interface.  
  
## <a name="remarks"></a>Notes  
Le `Implements` mot clé n’est pas le même que l' [instruction Implements](../../../visual-basic/language-reference/statements/implements-statement.md). Utilisez l' `Implements` instruction pour spécifier qu’une classe ou une structure implémente une ou plusieurs interfaces, puis, pour chaque membre, vous utilisez `Implements` le mot clé pour spécifier l’interface et le membre qu’elle implémente.

Si une classe ou une structure implémente une interface, elle doit inclure `Implements` l’instruction immédiatement après l’instruction de la [classe](../../../visual-basic/language-reference/statements/class-statement.md) ou de la [structure](../../../visual-basic/language-reference/statements/structure-statement.md), et elle doit implémenter tous les membres définis par l’interface.

## <a name="reimplementation"></a>Réimplémentation  
Dans une classe dérivée, vous pouvez réimplémenter un membre d’interface que la classe de base a déjà implémenté. Cela diffère de la substitution du membre de classe de base dans les aspects suivants :

- Le membre de la classe de base n’a pas besoin d’être [substituable](../../../visual-basic/language-reference/modifiers/overridable.md) pour être réimplémenté.
- Vous pouvez réimplémenter le membre avec un nom différent.

Le `Implements` mot clé peut être utilisé dans les contextes suivants :

- [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)
- [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)
- [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Implements (instruction)](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interface (instruction)](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)
