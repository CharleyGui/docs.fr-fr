---
description: value, mot clé contextuel - Référence C#
title: value, mot clé contextuel - Référence C#
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: f72e9f097880d9de725a85a0973001baaefd9a9c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141736"
---
# <a name="value-c-reference"></a>value (référence C#)

Le mot clé contextuel `value` est utilisé dans l' `set` accesseur dans les déclarations de [propriété](../../programming-guide/classes-and-structs/properties.md) et d' [indexeur](../../programming-guide/indexers/index.md) . Elle est similaire à un paramètre d’entrée d’une méthode. Le mot `value` fait référence à la valeur que le code client tente d’assigner à la propriété ou à l’indexeur. Dans l’exemple suivant, `MyDerivedClass` a une propriété appelée `Name` qui utilise le paramètre `value` pour assigner une nouvelle chaîne au `name` du champ de stockage. Du point de vue du code client, l’opération est écrite comme une assignation simple.

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Pour plus d’informations, consultez les articles [Propriétés](../../programming-guide/classes-and-structs/properties.md) et [Indexeres](../../programming-guide/indexers/index.md) .

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
