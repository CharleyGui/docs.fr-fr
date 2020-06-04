---
title: 'Procédure : Réduire et masquer des sections de code'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: c11affe9c4dd4251ba8ff4b87029d314970b5fcb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404847"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Comment : réduire et masquer des sections de code (Visual Basic)

La `#Region` directive vous permet de réduire et de masquer des sections de code dans des fichiers de Visual Basic. La `#Region` directive vous permet de spécifier un bloc de code que vous pouvez développer ou réduire lors de l’utilisation de l’éditeur de code Visual Studio. La possibilité de masquer le code de manière sélective rend vos fichiers plus gérables et plus faciles à lire. Pour plus d’informations, voir [Mode Plan](/visualstudio/ide/outlining).

`#Region`les directives prennent en charge la sémantique de bloc de code telle que `#If...#End If` . Cela signifie qu’ils ne peuvent pas commencer dans un bloc et se terminer dans un autre ; le début et la fin doivent se trouver dans le même bloc. `#Region`les directives ne sont pas prises en charge dans les fonctions.

## <a name="to-collapse-and-hide-a-section-of-code"></a>Pour réduire et masquer une section de code

Placez la section de code entre les `#Region` `#End Region` instructions et, comme dans l’exemple suivant :

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

Le `#Region` bloc peut être utilisé plusieurs fois dans un fichier de code. ainsi, les utilisateurs peuvent définir leurs propres blocs de procédures et de classes qui peuvent, à leur tour, être réduits. `#Region`les blocs peuvent également être imbriqués dans d’autres `#Region` blocs.

> [!NOTE]
> Le masquage du code ne l’empêche pas de le compiler et n’affecte pas les `#If...#End If` instructions.

## <a name="see-also"></a>Voir aussi

- [Compilation conditionnelle](conditional-compilation.md)
- [#Region directive](../../language-reference/directives/region-directive.md)
- [#If... Then... #Else directives](../../language-reference/directives/if-then-else-directives.md)
- [mode Plan](/visualstudio/ide/outlining)
