---
title: 'Comment : effectuer une recherche dans une chaîne-Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: fe9e50dc5458fdf8546094e5f41c2f001f1d2791
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700060"
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Procédure : effectuer une recherche dans une chaîne (Visual Basic)

Cet article montre un exemple de recherche dans une chaîne dans Visual Basic.

## <a name="example"></a>Exemple

Cet exemple appelle la méthode <xref:System.String.IndexOf%2A> sur un objet <xref:System.String> pour signaler l’index de la première occurrence d’une sous-chaîne :

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a>Programmation fiable

La méthode <xref:System.String.IndexOf%2A> retourne l’emplacement du premier caractère de la première occurrence de la sous-chaîne. L’index est basé sur 0, ce qui signifie que le premier caractère d’une chaîne a un index égal à 0.

Si <xref:System.String.IndexOf%2A> ne trouve pas la sous-chaîne, elle retourne-1.

La méthode <xref:System.String.IndexOf%2A> est sensible à la casse et utilise la culture actuelle.

Pour un contrôle optimal des erreurs, vous souhaiterez peut-être encadrer la recherche de chaîne dans le bloc `Try` d’un bloc [try... Catch... Finalisation](../../../language-reference/statements/try-catch-finally-statement.md) de la construction de l’instruction.

## <a name="see-also"></a>Voir aussi

- <xref:System.String.IndexOf%2A>
- [Try...Catch...Finally (instruction)](../../../language-reference/statements/try-catch-finally-statement.md)
- [Introduction aux chaînes en Visual Basic](introduction-to-strings.md)
- [Chaînes](index.md)
