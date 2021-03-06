---
description: partial, type - Référence C#
title: partial, type - Référence C#
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 4e73b34390143a2ac9b839e1da79b7894232c4b4
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91437880"
---
# <a name="partial-type-c-reference"></a>partial, type (référence C#)

Les définitions de type partiel permettent de fractionner en plusieurs fichiers la définition d’une classe, d’une structure, d’une interface ou d’un enregistrement.

Dans *file1.cs*:

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

Dans *file2.cs* , la déclaration :

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a>Remarques

Fractionner un type de classe, de struct ou d’interface entre plusieurs fichiers peut être utile si vous travaillez sur des projets volumineux ou des projets contenant du code généré automatiquement, comme celui fourni par le [Concepteur Windows Forms](/dotnet/desktop/winforms/controls/developing-windows-forms-controls-at-design-time). Un type partiel peut contenir une [méthode partielle](partial-method.md). Pour plus d’informations, consultez la page [Classes et méthodes partielles](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Modificateurs](index.md)
- [Introduction aux génériques](../../programming-guide/generics/index.md)
