---
title: 'Procédure : Réduire et masquer des sections de code (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: 4f11982cc0aa7654c1e456fb15d918a68bc4791b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054120"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Procédure : Réduire et masquer des sections de code (Visual Basic)

La `#Region` directive vous permet de réduire et de masquer des sections de code dans des fichiers de Visual Basic. La `#Region` directive vous permet de spécifier un bloc de code que vous pouvez développer ou réduire lors de l’utilisation de l’éditeur de code Visual Studio. La possibilité de masquer le code de manière sélective rend vos fichiers plus gérables et plus faciles à lire. Pour plus d’informations, voir [Mode Plan](/visualstudio/ide/outlining).

`#Region`les directives prennent en charge la sémantique de `#If...#End If`bloc de code telle que. Cela signifie qu’ils ne peuvent pas commencer dans un bloc et se terminer dans un autre ; le début et la fin doivent se trouver dans le même bloc. `#Region`les directives ne sont pas prises en charge dans les fonctions.

## <a name="to-collapse-and-hide-a-section-of-code"></a>Pour réduire et masquer une section de code

Placez la section de code entre les `#Region` instructions `#End Region` et, comme dans l’exemple suivant :

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

Le `#Region` bloc peut être utilisé plusieurs fois dans un fichier de code. ainsi, les utilisateurs peuvent définir leurs propres blocs de procédures et de classes qui peuvent, à leur tour, être réduits. `#Region`les blocs peuvent également être imbriqués dans `#Region` d’autres blocs.

> [!NOTE]
> Le masquage du code ne l’empêche pas de le compiler et `#If...#End If` n’affecte pas les instructions.

## <a name="see-also"></a>Voir aussi

- [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [#Region (directive)](../../../visual-basic/language-reference/directives/region-directive.md)
- [#If...Then...#Else, directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Mode Plan](/visualstudio/ide/outlining)
