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
ms.openlocfilehash: f114aee75356e59eafd9d3ba6af9c64402cb374f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345871"
---
# <a name="implements-clause-visual-basic"></a>Implements, clause (Visual Basic)
Indique qu’un membre de classe ou de structure fournit l’implémentation d’un membre défini dans une interface.  
  
## <a name="remarks"></a>Notes  
Le mot clé `Implements` n’est pas le même que l' [instruction Implements](../../../visual-basic/language-reference/statements/implements-statement.md). Vous utilisez l’instruction `Implements` pour spécifier qu’une classe ou une structure implémente une ou plusieurs interfaces, puis, pour chaque membre, vous utilisez le mot clé `Implements` pour spécifier l’interface et le membre qu’elle implémente.

Si une classe ou une structure implémente une interface, elle doit inclure l’instruction `Implements` immédiatement après l’instruction de [classe](../../../visual-basic/language-reference/statements/class-statement.md) ou de [structure](../../../visual-basic/language-reference/statements/structure-statement.md), et elle doit implémenter tous les membres définis par l’interface.

## <a name="reimplementation"></a>Réimplémentation  
Dans une classe dérivée, vous pouvez réimplémenter un membre d’interface que la classe de base a déjà implémenté. Cela diffère de la substitution du membre de classe de base dans les aspects suivants :

- Le membre de la classe de base n’a pas besoin d’être [substituable](../../../visual-basic/language-reference/modifiers/overridable.md) pour être réimplémenté.
- Vous pouvez réimplémenter le membre avec un nom différent.

Le mot clé `Implements` peut être utilisé dans les contextes suivants :

- [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)
- [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)
- [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Implements (instruction)](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interface (instruction)](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)
