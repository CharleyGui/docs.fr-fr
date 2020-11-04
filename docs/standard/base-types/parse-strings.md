---
title: Techniques d’analyse de chaîne dans .NET
description: Découvrez les différentes techniques permettant d’extraire des parties d’une chaîne, notamment String. Split, les expressions régulières et String. Substring.
ms.date: 10/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], breaking up
ms.openlocfilehash: de979b711a850bbb9ce91e1f1704d40a2f78f363
ms.sourcegitcommit: ffd4d5e824db6c5f0c3521c0e802fd9e8f0edcbe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93343362"
---
# <a name="extract-elements-from-a-string"></a>Extraire des éléments d’une chaîne

Cet article présente des techniques différentes pour l’extraction de parties d’une chaîne.

- Utilisez la [méthode Split](#stringsplit-method) lorsque les sous-chaînes que vous souhaitez sont séparées par un ou des caractères de délimitation connus.
- Les [expressions régulières](#regular-expressions) sont utiles lorsque la chaîne est conforme à un modèle fixe.
- Utilisez les [méthodes IndexOf et substring](#stringindexof-and-stringsubstring-methods) conjointement lorsque vous ne souhaitez pas extraire *toutes* les sous-chaînes d’une chaîne.

## <a name="stringsplit-method"></a>String. Split, méthode

<xref:System.String.Split%2A?displayProperty=nameWithType> fournit quelques surcharges pour vous aider à diviser une chaîne en un groupe de sous-chaînes en fonction d’un ou de plusieurs caractères de délimitation que vous spécifiez. Vous pouvez choisir de limiter le nombre total de sous-chaînes dans le résultat final, de supprimer les espaces blancs des sous-chaînes ou d’exclure les sous-chaînes vides.

Les exemples suivants illustrent trois surcharges différentes de `String.Split()` . Le premier exemple appelle la <xref:System.String.Split(System.Char[])> surcharge sans passer de caractères de séparation. Lorsque vous ne spécifiez pas de caractères de délimitation, `String.Split()` utilise des délimiteurs par défaut, qui sont des espaces blancs, pour fractionner la chaîne.

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#1)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="1":::

Comme vous pouvez le voir, les caractères de période ( `.` ) sont inclus dans deux des sous-chaînes. Si vous souhaitez exclure les caractères de période, vous pouvez ajouter le point comme caractère de délimitation supplémentaire. L’exemple suivant montre comment procéder.

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#2)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="2":::

Les points sont supprimés des sous-chaînes, mais maintenant deux sous-chaînes vides supplémentaires ont été incluses. Ces sous-chaînes vides représentent la sous-chaîne entre le mot et le point qui le suit. Pour omettre les sous-chaînes vides du tableau résultant, vous pouvez appeler la <xref:System.String.Split(System.Char[],System.StringSplitOptions)> surcharge et spécifier <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> pour le `options` paramètre.

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#3)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="3":::

## <a name="regular-expressions"></a>Expressions régulières

Si votre chaîne est conforme à un modèle fixe, vous pouvez utiliser une expression régulière pour extraire et gérer ses éléments. Par exemple, si les chaînes prennent la forme « *Number* *Operand* *Number* », vous pouvez utiliser une [expression régulière](regular-expressions.md) pour extraire et gérer les éléments de la chaîne. Voici un exemple :

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="1":::

Le modèle d’expression régulière `(\d+)\s+([-+*/])\s+(\d+)` est défini comme suit :

|Modèle|Description|
|-------------|-----------------|
|`(\d+)`|Mettre en correspondance un ou plusieurs chiffres décimaux. Il s'agit du premier groupe de capture.|
|`\s+`|Correspond à un ou plusieurs espaces blancs.|
|`([-+*/])`|Correspond à un signe d’opérateur arithmétique (+,-, * ou/). Il s'agit du deuxième groupe de capture.|
|`\s+`|Correspond à un ou plusieurs espaces blancs.|
|`(\d+)`|Mettre en correspondance un ou plusieurs chiffres décimaux. Il s'agit du troisième groupe de capture.|

Vous pouvez également utiliser une expression régulière pour extraire des sous-chaînes d’une chaîne basée sur un modèle plutôt qu’un ensemble fixe de caractères. Il s’agit d’un scénario courant lorsque l’une des conditions suivantes se produit :

- Un ou plusieurs des caractères de délimiteur ne servent pas *toujours* de délimiteur dans l' <xref:System.String> instance.

- La séquence et le nombre de caractères de délimitation est variable ou inconnu.

Par exemple, la <xref:System.String.Split%2A> méthode ne peut pas être utilisée pour fractionner la chaîne suivante, car le nombre de `\n` caractères (de saut de ligne) est variable et ils ne servent pas toujours de délimiteurs.

```text
[This is captured\ntext.]\n\n[\n[This is more captured text.]\n]
\n[Some more captured text:\n   Option1\n   Option2][Terse text.]
```

Une expression régulière peut fractionner cette chaîne facilement, comme le montre l’exemple suivant.

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="2" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="2":::

Le modèle d’expression régulière `\[([^\[\]]+)\]` est défini comme suit :

|Modèle|Description|
|-------------|-----------------|
|`\[`|Mettre en correspondance un crochet ouvrant.|
|`([^\[\]]+)`|Correspond à n’importe quel caractère qui n’est pas une ouverture ou un crochet fermant une ou plusieurs fois. Il s'agit du premier groupe de capture.|
|`\]`|Mettre en correspondance un crochet fermant.|

La <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> méthode est presque identique à <xref:System.String.Split%2A?displayProperty=nameWithType> , à ceci près qu’elle fractionne une chaîne basée sur un modèle d’expression régulière au lieu d’un jeu de caractères fixe. Par exemple, l’exemple suivant utilise la <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> méthode pour fractionner une chaîne qui contient des sous-chaînes délimitées par différentes combinaisons de tirets et d’autres caractères.

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="3" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="3":::

Le modèle d’expression régulière `\s-\s?[+*]?\s?-\s` est défini comme suit :

|Modèle|Description|
|-------------|-----------------|
|`\s-`|Correspond à un espace blanc suivi d’un trait d’Union.|
|`\s?`|Mettre en correspondance zéro ou un espace blanc.|
|`[+*]?`|Correspond à zéro ou à une occurrence du caractère + ou *.|
|`\s?`|Mettre en correspondance zéro ou un espace blanc.|
|`-\s`|Faire correspondre un trait d’Union suivi d’un espace blanc.|

## <a name="stringindexof-and-stringsubstring-methods"></a>Méthodes String. IndexOf et String. Substring

Si vous n’êtes pas intéressé par toutes les sous-chaînes d’une chaîne, vous préférerez peut-être utiliser l’une des méthodes de comparaison de chaînes qui retourne l’index auquel la correspondance commence. Vous pouvez ensuite appeler la <xref:System.String.Substring%2A> méthode pour extraire la sous-chaîne de votre choix. Les méthodes de comparaison de chaînes sont les suivantes :

- <xref:System.String.IndexOf%2A>, qui retourne l’index de base zéro de la première occurrence d’un caractère ou d’une chaîne dans une instance de chaîne.

- <xref:System.String.IndexOfAny%2A>, qui retourne l’index de base zéro dans l’instance de chaîne actuelle de la première occurrence d’un caractère dans un tableau de caractères.

- <xref:System.String.LastIndexOf%2A>, qui retourne l’index de base zéro de la dernière occurrence d’un caractère ou d’une chaîne dans une instance de chaîne.

- <xref:System.String.LastIndexOfAny%2A>, qui retourne un index de base zéro dans l’instance de chaîne actuelle de la dernière occurrence d’un caractère dans un tableau de caractères.

L’exemple suivant utilise la <xref:System.String.IndexOf%2A> méthode pour rechercher les points dans une chaîne. Il utilise ensuite la <xref:System.String.Substring%2A> méthode pour retourner des phrases complètes.

:::code language="csharp" source="snippets/parse-strings/csharp/indexof.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/indexof.vb" id="1":::

## <a name="see-also"></a>Voir également

- [Opérations de chaînes de base dans .NET](basic-string-operations.md)
- [Expressions régulières .NET](regular-expressions.md)
- [Comment analyser des chaînes à l’aide de String. Split en C #](../../csharp/how-to/parse-strings-using-split.md)
