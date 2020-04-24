---
title: 'Comment : créer des cordes à l’aide d’un StringBuilder'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: c41db584df83782dab99b90043045aa2cabcb6ff
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645324"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Comment : créer des cordes à l’aide d’un StringBuilder dans Visual Basic

Cet exemple construit une longue chaîne à <xref:System.Text.StringBuilder> partir de nombreuses chaînes plus petites en utilisant la classe. La <xref:System.Text.StringBuilder> classe est plus `&=` efficace que l’opérateur pour concatenating de nombreuses chaînes.

## <a name="example"></a>Exemple

L’exemple suivant crée <xref:System.Text.StringBuilder> une instance de la classe, annexe 1 000 cordes à cette instance, puis retourne sa représentation des cordes :

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a>Voir aussi

- [Utilisation de la classe StringBuilder](../../../../standard/base-types/stringbuilder.md)
- [&et opérateur](../../../language-reference/operators/and-assignment-operator.md)
- [Chaînes](index.md)
- [Création de chaînes](../../../../standard/base-types/creating-new.md)
- [Manipulation de chaînes](../../../../standard/base-types/best-practices-strings.md)
