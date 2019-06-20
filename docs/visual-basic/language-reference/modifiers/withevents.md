---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: e8a8fb571fa65228f3a0acec1f902d21eb9bfe04
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268303"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Spécifie qu’une ou plusieurs variables membres déclarées font référence à une instance d’une classe qui peut déclencher des événements.  
  
## <a name="remarks"></a>Notes  
 Lorsqu’une variable est définie à l’aide de `WithEvents`, vous pouvez spécifier de manière déclarative qu’une méthode gère les événements de la variable à l’aide de la `Handles` mot clé.  
  
 Vous pouvez utiliser `WithEvents` uniquement au niveau de la classe ou le module. Cela signifie que le contexte de déclaration pour un `WithEvents` variable doit être une classe ou un module et ne peut pas être un fichier source, un espace de noms, une structure ou une procédure.  
  
 Vous ne pouvez pas utiliser `WithEvents` sur un membre de structure.  
  
 Vous pouvez déclarer des variables individuelles, pas les tableaux — avec `WithEvents`.  
  
## <a name="rules"></a>Règles  
  
- **Types d’éléments.** Vous devez déclarer `WithEvents` variables comme des variables d’objet afin qu’ils acceptent les instances de la classe. Toutefois, vous ne pouvez pas déclarer en tant que `Object`. Vous devez les déclarer en tant que la classe spécifique capable de déclencher les événements.  
  
 Le `WithEvents` modificateur peut être utilisé dans ce contexte : [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)  
 
## <a name="example"></a>Exemple

```VB
Dim WithEvents app As Application
```
  
## <a name="see-also"></a>Voir aussi

- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
- [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)
