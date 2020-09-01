---
description: mot clé params pour les tableaux de paramètres-référence C#
title: mot clé params pour les tableaux de paramètres-référence C#
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: a2726c725508cd297001aaabddeff414704d1115
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134469"
---
# <a name="params-c-reference"></a>params (référence C#)

Avec le mot clé `params`, vous pouvez spécifier un [paramètre de méthode](method-parameters.md) qui prend un nombre variable d’arguments. Le type de paramètre doit être un tableau unidimensionnel.

Dans une déclaration de méthode, vous ne pouvez pas spécifier de paramètre supplémentaire après le mot clé `params` et vous pouvez utiliser un seul mot clé `params`.

Si le type déclaré du `params` paramètre n’est pas un tableau unidimensionnel, l’erreur de compilateur [CS0225](../../misc/cs0225.md) se produit.

Lorsque vous appelez une méthode avec un `params` paramètre, vous pouvez passer :

- Liste séparée par des virgules des arguments du type des éléments du tableau.
- Tableau d’arguments du type spécifié.
- Aucun argument. Si vous n’envoyez aucun argument, la longueur de la liste `params` est égale à zéro.

## <a name="example"></a>Exemple

L’exemple suivant montre différentes façons d’envoyer des arguments à un paramètre `params`.

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Paramètres de méthodes](method-parameters.md)
