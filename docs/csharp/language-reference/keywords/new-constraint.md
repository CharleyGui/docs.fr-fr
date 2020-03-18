---
title: new, contrainte - Référence C#
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: cd67aeb82d736b8941b0637494089723e7815505
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713355"
---
# <a name="new-constraint-c-reference"></a>new, contrainte (référence C#)

La contrainte `new` spécifie que tout argument de type dans une déclaration de classe générique doit avoir un constructeur sans paramètre public. Pour utiliser la contrainte `new`, le type ne doit pas être abstract.

Appliquez la contrainte `new` à un paramètre de type quand une classe générique crée des instances du type, comme illustré dans l’exemple suivant :

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

Si vous utilisez la contrainte `new()` avec d’autres contraintes, spécifiez-la en dernier :

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

Pour plus d’informations, consultez [Contraintes sur les paramètres de type](../../programming-guide/generics/constraints-on-type-parameters.md).

Vous pouvez également utiliser le mot clé `new` pour [créer une instance d’un type](../operators/new-operator.md) ou l’utiliser comme un [modificateur de déclaration de membre](new-modifier.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Contraintes de paramètre de type](~/_csharplang/spec/classes.md#type-parameter-constraints) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Référence C](../../language-reference/index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Génériques](../../programming-guide/generics/index.md)
