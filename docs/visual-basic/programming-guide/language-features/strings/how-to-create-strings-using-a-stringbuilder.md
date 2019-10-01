---
title: 'Comment : créer des chaînes à l’aide d’un StringBuilder dans Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 19e036abc9d25ec7fdfd6c33ebb420ec4f503cbc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700107"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Comment : créer des chaînes à l’aide d’un StringBuilder dans Visual Basic

Cet exemple construit une longue chaîne à partir de plusieurs chaînes plus petites à l’aide de la classe <xref:System.Text.StringBuilder>. La classe <xref:System.Text.StringBuilder> est plus efficace que l’opérateur `&=` pour concaténer de nombreuses chaînes.

## <a name="example"></a>Exemple

L’exemple suivant crée une instance de la classe <xref:System.Text.StringBuilder>, ajoute 1 000 chaînes à cette instance, puis retourne sa représentation sous forme de chaîne :

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a>Voir aussi

- [Utilisation de la classe StringBuilder](../../../../standard/base-types/stringbuilder.md)
- [&= (opérateur)](../../../language-reference/operators/and-assignment-operator.md)
- [Chaînes](index.md)
- [Création de chaînes](../../../../standard/base-types/creating-new.md)
- [Manipulation de chaînes](../../../../standard/base-types/manipulating-strings.md)
