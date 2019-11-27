---
title: 'Comment : réduire et masquer des sections de code'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: e7aacdc3f41199127b00d276b382ec4a5f258da0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347407"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Comment : réduire et masquer des sections de code (Visual Basic)

La directive `#Region` vous permet de réduire et de masquer des sections de code dans des fichiers Visual Basic. La directive `#Region` vous permet de spécifier un bloc de code que vous pouvez développer ou réduire lors de l’utilisation de l’éditeur de code Visual Studio. La possibilité de masquer le code de manière sélective rend vos fichiers plus gérables et plus faciles à lire. Pour plus d’informations, voir [Mode Plan](/visualstudio/ide/outlining).

les directives `#Region` prennent en charge la sémantique de bloc de code telle que `#If...#End If`. Cela signifie qu’ils ne peuvent pas commencer dans un bloc et se terminer dans un autre ; le début et la fin doivent se trouver dans le même bloc. les directives de `#Region` ne sont pas prises en charge dans les fonctions.

## <a name="to-collapse-and-hide-a-section-of-code"></a>Pour réduire et masquer une section de code

Placez la section de code entre les instructions `#Region` et `#End Region`, comme dans l’exemple suivant :

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

Le bloc `#Region` peut être utilisé plusieurs fois dans un fichier de code ; ainsi, les utilisateurs peuvent définir leurs propres blocs de procédures et de classes qui peuvent, à leur tour, être réduits. les blocs de `#Region` peuvent également être imbriqués dans d’autres blocs `#Region`.

> [!NOTE]
> Le masquage du code ne l’empêche pas de le compiler et n’affecte pas les instructions `#If...#End If`.

## <a name="see-also"></a>Voir aussi

- [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [#Region (directive)](../../../visual-basic/language-reference/directives/region-directive.md)
- [#If...Then...#Else, directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Mode Plan](/visualstudio/ide/outlining)
