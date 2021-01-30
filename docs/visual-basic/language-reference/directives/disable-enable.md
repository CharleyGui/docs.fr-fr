---
title: Directives d’activation et de désactivation
ms.date: 01/28/2021
helpviewer_keywords:
- directives, enable
- directives, disable
- disable directive
ms.openlocfilehash: 3104b25c903465f3a650304f477b25a74591c8ba
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99217228"
---
# <a name="disable-and-enable-directives-visual-basic"></a>Directives #Disable et #Enable (Visual Basic)

Les `#Disable` `#Enable` directives et sont Visual Basic les directives de compilateur de code source. Ils permettent de désactiver et de réactiver des avertissements spécifiques pour les régions de code.

```vb
' Suppress warning about no awaits in this method.
#Disable Warning BC42356
    Async Function TestAsync() As Task
        Console.WriteLine("testing")
    End Function
#Enable Warning BC42356
```

Vous pouvez également désactiver et activer une liste de codes d’avertissement séparés par des virgules.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage Visual Basic](../index.md)
- [Comment supprimer des avertissements d’analyse du code](../../../fundamentals/code-analysis/suppress-warnings.md)
