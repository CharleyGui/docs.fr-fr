---
title: value, mot clé contextuel - Référence C#
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 84d0c51ddafb59144f4ba8c6e73412642fa8fa28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712895"
---
# <a name="value-c-reference"></a>value (référence C#)

`value` Le mot-clé contextuel `set` est utilisé dans l’accesseur dans les déclarations [d’indexeurs](../../programming-guide/indexers/index.md) et [de propriétés.](../../programming-guide/classes-and-structs/properties.md) Il est similaire à un paramètre d’entrée d’une méthode. Le `value` mot fait référence à la valeur que le code client tente d’attribuer à la propriété ou à l’indexeur. Dans l’exemple suivant, `MyDerivedClass` a une propriété appelée `Name` qui utilise le paramètre `value` pour assigner une nouvelle chaîne au `name` du champ de stockage. Du point de vue du code client, l’opération est écrite comme une assignation simple.

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Pour plus d’informations, consultez les articles [Propriétés](../../programming-guide/classes-and-structs/properties.md) et [Indexeres.](../../programming-guide/indexers/index.md)

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
