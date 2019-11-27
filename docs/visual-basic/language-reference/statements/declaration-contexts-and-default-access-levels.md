---
title: Contextes de déclaration et niveaux d'accès par défaut
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: 1ba25d830b1e7529bdf09c1195cc1fe7f9b2243b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354100"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Contextes de déclaration et niveaux d'accès par défaut (Visual Basic)
Cette rubrique décrit les types de Visual Basic qui peuvent être déclarés dans lesquels d’autres types, et les niveaux d’accès par défaut, s’ils ne sont pas spécifiés.  
  
## <a name="declaration-context-levels"></a>Niveaux de contexte de déclaration  
 Le *contexte de déclaration* d’un élément de programmation est la région de code dans laquelle il est déclaré. Il s’agit souvent d’un autre élément de programmation, qui est ensuite appelé *élément conteneur*.  
  
 Les niveaux des contextes de déclaration sont les suivants :  
  
- *Niveau* de l’espace de noms : dans un fichier source ou un espace de noms, mais pas dans une classe, une structure, un module ou une interface  
  
- *Niveau module* : dans une classe, une structure, un module ou une interface, mais pas dans une procédure ou un bloc  
  
- *Niveau de procédure* : dans une procédure ou un bloc (par exemple, `If` ou `For`)  
  
 Le tableau suivant indique les niveaux d’accès par défaut pour les différents éléments de programmation déclarés, en fonction de leurs contextes de déclaration.  
  
|Élément déclaré|Niveau de l’espace de noms|Niveau de module|Niveau de procédure|  
|----------------------|---------------------|------------------|---------------------|  
|Variable ([instruction Dim](../../../visual-basic/language-reference/statements/dim-statement.md))|Non autorisé|`Private` (`Public` dans `Structure`, non autorisé dans `Interface`)|`Public`|  
|Constant ([instruction Const](../../../visual-basic/language-reference/statements/const-statement.md))|Non autorisé|`Private` (`Public` dans `Structure`, non autorisé dans `Interface`)|`Public`|  
|Enumeration ([instruction enum](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|Non autorisé|  
|Class ([instruction class](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|Non autorisé|  
|Structure ([instruction de structure](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|Non autorisé|  
|Module ([instruction module](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|Non autorisé|Non autorisé|  
|Interface ([instruction interface](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|Non autorisé|  
|Procedure ([instruction Function](../../../visual-basic/language-reference/statements/function-statement.md), [Sub, instruction](../../../visual-basic/language-reference/statements/sub-statement.md))|Non autorisé|`Public`|Non autorisé|  
|Référence externe ([instruction DECLARE](../../../visual-basic/language-reference/statements/declare-statement.md))|Non autorisé|`Public` (non autorisé dans `Interface`)|Non autorisé|  
|Operator ([instruction d’opérateur](../../../visual-basic/language-reference/statements/operator-statement.md))|Non autorisé|`Public` (non autorisé dans `Interface` ou `Module`)|Non autorisé|  
|Property ([instruction Property](../../../visual-basic/language-reference/statements/property-statement.md))|Non autorisé|`Public`|Non autorisé|  
|Propriété par défaut ([par défaut](../../../visual-basic/language-reference/modifiers/default.md))|Non autorisé|`Public` (non autorisé dans `Module`)|Non autorisé|  
|Event ([instruction d’événement](../../../visual-basic/language-reference/statements/event-statement.md))|Non autorisé|`Public`|Non autorisé|  
|Délégué ([instruction Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|Non autorisé|  
  
 Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Voir aussi

- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
