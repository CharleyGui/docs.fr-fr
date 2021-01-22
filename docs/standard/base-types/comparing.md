---
title: Comparer des chaînes dans . NET
description: En savoir plus sur les méthodes de comparaison de chaînes dans .NET. En savoir plus sur les méthodes compare, CompareOrdinal, CompareTo, StartsWith, EndsWith, Equals, IndexOf, & LastIndexOf.
ms.date: 03/30/2017
ms.topic: conceptual
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- value comparisons of strings
- LastIndexOf method
- CompareTo method
- IndexOf method
- Compare method
- strings [.NET], comparing
- CompareOrdinal method
- EndsWith method
- Equals method
- StartsWith method
ms.assetid: 977dc094-fe19-4955-98ec-d2294d04a4ba
ms.openlocfilehash: ca2e89fa8c42807757f4ed004c8f8ddaaeafba3b
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98693070"
---
# <a name="compare-strings-in-net"></a>Comparer des chaînes dans .NET

.NET fournit plusieurs méthodes permettant de comparer les valeurs de chaînes. Le tableau suivant répertorie et décrit les méthodes de comparaison de valeurs.

|Nom de la méthode|Utilisation|
|-----------------|---------|
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|Compare les valeurs de deux chaînes. Retourne une valeur entière.|
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|Compare deux chaînes sans tenir compte de la culture locale. Retourne une valeur entière.|
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|Compare l'objet chaîne actif à une autre chaîne. Retourne une valeur entière.|
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|Détermine si une chaîne commence par la chaîne passée. Retourne une valeur booléenne.|
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|Détermine si une chaîne se termine par la chaîne passée. Retourne une valeur booléenne.|
|<xref:System.String.Contains%2A?displayProperty=nameWithType>|Détermine si un caractère ou une chaîne se produit dans une autre chaîne. Retourne une valeur booléenne.|
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|Détermine si deux chaînes sont identiques. Retourne une valeur booléenne.|
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|Retourne la position d'index d'un caractère ou d'une chaîne, en commençant par le début de la chaîne que vous examinez. Retourne une valeur entière.|
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|Retourne la position d'index d'un caractère ou d'une chaîne, en commençant par la fin de la chaîne que vous examinez. Retourne une valeur entière.|

## <a name="compare-method"></a>Compare (méthode)

La méthode statique <xref:System.String.Compare%2A?displayProperty=nameWithType> fournit un moyen de comparer deux chaînes de façon approfondie. Cette méthode prend en compte la culture. Vous pouvez utiliser cette fonction pour comparer deux chaînes ou les sous-chaînes de deux chaînes. En outre, des surcharges sont fournies, qui prennent ou non en compte les différences de casse et de culture. Le tableau suivant montre les trois valeurs entières que cette méthode peut retourner.

|Valeur de retour|Condition|
|------------------|---------------|
|Entier négatif|La première chaîne précède la seconde chaîne dans l'ordre de tri.<br /><br /> - ou -<br /><br /> La première chaîne est `null`.|
|0|La première chaîne et la seconde chaîne sont égales.<br /><br /> - ou -<br /><br /> Les deux chaînes sont `null`.|
|Entier positif<br /><br /> - ou -<br /><br /> 1|La première chaîne suit la seconde chaîne dans l'ordre de tri.<br /><br /> - ou -<br /><br /> La seconde chaîne est `null`.|

> [!IMPORTANT]
> La méthode <xref:System.String.Compare%2A?displayProperty=nameWithType> est principalement destinée à être utilisée lors du classement ou du tri de chaînes. Vous ne devez pas utiliser la méthode <xref:System.String.Compare%2A?displayProperty=nameWithType> pour tester l'égalité (c'est-à-dire rechercher explicitement une valeur de retour égale à 0 sans savoir si une chaîne est inférieure ou supérieure à l'autre). Pour déterminer si deux chaînes sont égales, utilisez à la place la méthode <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> .

 L'exemple suivant utilise la méthode <xref:System.String.Compare%2A?displayProperty=nameWithType> pour déterminer les valeurs relatives de deux chaînes.

 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]

 Cet exemple affiche `-1` sur la console.

 L'exemple précédent tient compte par défaut de la culture. Pour effectuer une comparaison de chaînes indépendantes de la culture, utilisez une surcharge de la méthode <xref:System.String.Compare%2A?displayProperty=nameWithType> qui vous permet de spécifier la culture à utiliser en fournissant un paramètre *culture*. Pour obtenir un exemple qui montre comment utiliser la <xref:System.String.Compare%2A?displayProperty=nameWithType> méthode pour effectuer une comparaison indépendante de la culture, consultez [comparaisons de chaînes](../globalization-localization/performing-culture-insensitive-string-comparisons.md)indépendantes de la culture.

## <a name="compareordinal-method"></a>CompareOrdinal (méthode)

La méthode <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> compare deux objets chaîne sans prendre en compte la culture locale. Les valeurs de retour de cette méthode sont identiques aux valeurs retournées par la méthode `Compare` du tableau précédent.

> [!IMPORTANT]
> La méthode <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> est principalement destinée à être utilisée lors du classement ou du tri de chaînes. Vous ne devez pas utiliser la méthode <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> pour tester l'égalité (c'est-à-dire rechercher explicitement une valeur de retour égale à 0 sans savoir si une chaîne est inférieure ou supérieure à l'autre). Pour déterminer si deux chaînes sont égales, utilisez à la place la méthode <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> .

 L’exemple suivant utilise la méthode `CompareOrdinal` pour comparer les valeurs de deux chaînes.

 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]

 Cet exemple affiche `-32` sur la console.

## <a name="compareto-method"></a>CompareTo (méthode)

La méthode <xref:System.String.CompareTo%2A?displayProperty=nameWithType> compare la chaîne encapsulée par l'objet chaîne actif à une autre chaîne ou un autre objet. Les valeurs de retour de cette méthode sont identiques aux valeurs retournées par la méthode <xref:System.String.Compare%2A?displayProperty=nameWithType> du tableau précédent.

> [!IMPORTANT]
> La méthode <xref:System.String.CompareTo%2A?displayProperty=nameWithType> est principalement destinée à être utilisée lors du classement ou du tri de chaînes. Vous ne devez pas utiliser la méthode <xref:System.String.CompareTo%2A?displayProperty=nameWithType> pour tester l'égalité (c'est-à-dire rechercher explicitement une valeur de retour égale à 0 sans savoir si une chaîne est inférieure ou supérieure à l'autre). Pour déterminer si deux chaînes sont égales, utilisez à la place la méthode <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> .

 L’exemple suivant utilise la méthode <xref:System.String.CompareTo%2A?displayProperty=nameWithType> pour comparer l’objet `string1` à l’objet `string2`.

 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]

 Cet exemple affiche `-1` sur la console.

 Toutes les surcharges de la méthode <xref:System.String.CompareTo%2A?displayProperty=nameWithType> effectuent par défaut des comparaisons dépendantes de la culture et qui respectent la casse. Aucune surcharge de cette méthode n'est fournie pour vous permettre d'effectuer une comparaison indépendante de la culture. Pour la clarté du code, nous vous recommandons d’utiliser la `String.Compare` méthode à la place, en spécifiant pour les opérations dépendantes <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> de la culture ou <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> pour les opérations indépendantes de la culture. Pour obtenir des exemples qui montrent comment utiliser la méthode pour effectuer des comparaisons dépendantes de la culture et indépendantes de la `String.Compare` culture, consultez [réalisation de comparaisons de chaînes Culture-Insensitive](../globalization-localization/performing-culture-insensitive-string-comparisons.md).

## <a name="equals-method"></a>Equals (méthode)

La <xref:System.String.Equals%2A?displayProperty=nameWithType> méthode peut facilement déterminer si deux chaînes sont identiques. Cette méthode respectant la casse retourne une valeur booléenne `true` ou `false`. Elle peut être utilisée à partir d'une classe existante, comme illustré dans l'exemple suivant. L’exemple suivant utilise la méthode `Equals` pour déterminer si un objet String contient la phrase « Hello World ».

 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]

 Cet exemple affiche `True` sur la console.

 Cette méthode peut également être utilisée comme une méthode statique. L'exemple suivant compare deux objets chaîne à l'aide d'une méthode statique.

 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]

 Cet exemple affiche `True` sur la console.

## <a name="startswith-and-endswith-methods"></a>Méthodes StartsWith et EndsWith

Vous pouvez utiliser la <xref:System.String.StartsWith%2A?displayProperty=nameWithType> méthode pour déterminer si un objet String commence par les mêmes caractères qui englobent une autre chaîne. Cette méthode qui respecte la casse retourne `true` si l’objet String actif commence par la chaîne passée et `false` si ce n’est pas le cas. L'exemple suivant utilise cette méthode pour déterminer si un objet chaîne commence par "Hello".

 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]

 Cet exemple affiche `True` sur la console.

 La <xref:System.String.EndsWith%2A?displayProperty=nameWithType> méthode compare une chaîne passée aux caractères qui existent à la fin de l’objet String actuel. Elle retourne également une valeur booléenne. L’exemple suivant vérifie la fin d’une chaîne à l’aide de la méthode `EndsWith`.

 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]

 Cet exemple affiche `False` sur la console.

## <a name="indexof-and-lastindexof-methods"></a>Méthodes IndexOf et LastIndexOf

Vous pouvez utiliser la <xref:System.String.IndexOf%2A?displayProperty=nameWithType> méthode pour déterminer la position de la première occurrence d’un caractère particulier dans une chaîne. Cette méthode qui respecte la casse commence à compter à partir du début d'une chaîne et retourne la position d'un caractère passé en utilisant un index de base zéro. Si le caractère est introuvable, la valeur -1 est retournée.

L’exemple suivant utilise la méthode `IndexOf` pour rechercher la première occurrence du caractère '`l`' dans une chaîne.

 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]

 Cet exemple affiche `2` sur la console.

 La <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> méthode est semblable à la `String.IndexOf` méthode, à ceci près qu’elle retourne la position de la dernière occurrence d’un caractère particulier dans une chaîne. Elle respecte la casse et utilise un index de base zéro.

 L’exemple suivant utilise la méthode `LastIndexOf` pour rechercher la dernière occurrence du caractère '`l`' dans une chaîne.

 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]

 Cet exemple affiche `9` sur la console.

 Les deux méthodes sont utiles quand elles sont utilisées conjointement avec la <xref:System.String.Remove%2A?displayProperty=nameWithType> méthode. Vous pouvez utiliser les `IndexOf` méthodes ou `LastIndexOf` pour récupérer la position d’un caractère, puis fournir cette position à la `Remove` méthode pour supprimer un caractère ou un mot commençant par ce caractère.

## <a name="see-also"></a>Voir aussi

- [Bonnes pratiques pour l’utilisation de chaînes dans .NET](best-practices-strings.md)
- [Opérations de chaînes de base](basic-string-operations.md)
- [Exécution d'opérations de chaînes indépendantes de la culture](../globalization-localization/performing-culture-insensitive-string-operations.md)
- [Tables de pondération de tri](https://www.microsoft.com/download/details.aspx?id=10921) -utilisées par .NET Framework et .net Core 1.0-3.1 sur Windows
- [Table d’éléments de classement Unicode par défaut](https://www.unicode.org/Public/UCA/latest/allkeys.txt) , utilisée par .net 5 sur toutes les plateformes, et par .net Core sur Linux et MacOS
