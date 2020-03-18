---
title: params, mot clé - Référence C#
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: f462ccc2421fef3ea111d263ec035a701cf04775
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173547"
---
# <a name="params-c-reference"></a>params (référence C#)

Avec le mot clé `params`, vous pouvez spécifier un [paramètre de méthode](method-parameters.md) qui prend un nombre variable d’arguments.

Vous pouvez envoyer une liste séparée par des virgules d’arguments du type spécifié dans la déclaration du paramètre ou envoyer un tableau d’arguments du type spécifié. Vous pouvez aussi ne pas envoyer d’arguments. Si vous n’envoyez aucun argument, la longueur de la liste `params` est égale à zéro.

Dans une déclaration de méthode, vous ne pouvez pas spécifier de paramètre supplémentaire après le mot clé `params` et vous pouvez utiliser un seul mot clé `params`.

Le type déclaré du paramètre `params` doit être un tableau unidimensionnel, comme le montre l’exemple suivant. Sinon, une erreur du compilateur [CS0225](../../misc/cs0225.md) se produit.

## <a name="example"></a> Exemple

L’exemple suivant montre différentes façons d’envoyer des arguments à un paramètre `params`.

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Paramètres de méthodes](method-parameters.md)
