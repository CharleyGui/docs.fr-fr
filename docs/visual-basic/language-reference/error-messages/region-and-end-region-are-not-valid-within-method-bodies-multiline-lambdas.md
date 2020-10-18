---
title: Les instructions « #Region » et « #End Region » ne sont pas valides dans le corps des méthodes ou les expressions lambda multiligne
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: c792fa1a42bde22959ae21439cb2a0a1e4be343f
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162282"
---
# <a name="bc32025-region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>BC32025 : les instructions' #Region’et' #End Region’ne sont pas valides dans les corps de méthode/expressions lambda multiligne

Le `#Region` bloc doit être déclaré au niveau d’un classe, d’un module ou d’un espace de noms. Une région réductible peut inclure une ou plusieurs procédures, mais elle ne peut pas commencer ni se terminer à l’intérieur d’une procédure.

 **ID d’erreur :** BC32025

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Vérifiez que la procédure précédente est correctement terminée par une `End Function` instruction ou `End Sub` .

2. Vérifiez que les `#Region` `#End Region` directives et se trouvent dans le même bloc de code.

## <a name="see-also"></a>Voir aussi

- [#Region directive](../directives/region-directive.md)
