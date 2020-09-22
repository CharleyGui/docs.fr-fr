---
title: Contextes de déclaration et niveaux d’accès par défaut
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: a659481b34b8b44f1f387b464d5d9656ed98ab3f
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874955"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Contextes de déclaration et niveaux d'accès par défaut (Visual Basic)

Cette rubrique décrit les types de Visual Basic qui peuvent être déclarés dans lesquels d’autres types, et les niveaux d’accès par défaut, s’ils ne sont pas spécifiés.  
  
## <a name="declaration-context-levels"></a>Niveaux de contexte de déclaration  

 Le *contexte de déclaration* d’un élément de programmation est la région de code dans laquelle il est déclaré. Il s’agit souvent d’un autre élément de programmation, qui est ensuite appelé *élément conteneur*.  
  
 Les niveaux des contextes de déclaration sont les suivants :  
  
- *Niveau* de l’espace de noms : dans un fichier source ou un espace de noms, mais pas dans une classe, une structure, un module ou une interface  
  
- *Niveau module* : dans une classe, une structure, un module ou une interface, mais pas dans une procédure ou un bloc  
  
- *Niveau de procédure* : dans une procédure ou un bloc (tel que `If` ou `For` )  
  
 Le tableau suivant indique les niveaux d’accès par défaut pour les différents éléments de programmation déclarés, en fonction de leurs contextes de déclaration.  
  
|Élément déclaré|Niveau de l’espace de noms|Niveau de module|Niveau de procédure|  
|----------------------|---------------------|------------------|---------------------|  
|Variable ([instruction Dim](dim-statement.md))|Non autorisé|`Private` ( `Public` dans `Structure` , non autorisé dans `Interface` )|`Public`|  
|Constant ([instruction Const](const-statement.md))|Non autorisé|`Private` ( `Public` dans `Structure` , non autorisé dans `Interface` )|`Public`|  
|Enumeration ([instruction enum](enum-statement.md))|`Friend`|`Public`|Non autorisé|  
|Class ([instruction class](class-statement.md))|`Friend`|`Public`|Non autorisé|  
|Structure ([instruction de structure](structure-statement.md))|`Friend`|`Public`|Non autorisé|  
|Module ([instruction module](module-statement.md))|`Friend`|Non autorisé|Non autorisé|  
|Interface ([instruction interface](interface-statement.md))|`Friend`|`Public`|Non autorisé|  
|Procedure ([instruction Function](function-statement.md), [Sub, instruction](sub-statement.md))|Non autorisé|`Public`|Non autorisé|  
|Référence externe ([instruction DECLARE](declare-statement.md))|Non autorisé|`Public` (non autorisé dans `Interface` )|Non autorisé|  
|Operator ([instruction d’opérateur](operator-statement.md))|Non autorisé|`Public` (non autorisé dans `Interface` ou `Module` )|Non autorisé|  
|Property ([instruction Property](property-statement.md))|Non autorisé|`Public`|Non autorisé|  
|Propriété par défaut ([par défaut](../modifiers/default.md))|Non autorisé|`Public` (non autorisé dans `Module` )|Non autorisé|  
|Event ([instruction d’événement](event-statement.md))|Non autorisé|`Public`|Non autorisé|  
|Délégué ([instruction Delegate](delegate-statement.md))|`Friend`|`Public`|Non autorisé|  
  
 Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Voir aussi

- [Friend](../modifiers/friend.md)
- [Privé](../modifiers/private.md)
- [Public](../modifiers/public.md)
