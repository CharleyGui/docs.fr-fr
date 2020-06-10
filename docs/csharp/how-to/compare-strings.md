---
title: Guide pratique pour comparer des chaînes-Guide C#
description: Découvrez comment comparer et trier des valeurs de chaîne, avec ou sans casse, avec ou sans tri propre à la culture
ms.date: 10/03/2018
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.openlocfilehash: 725441f5399f72b6457af461d51419c35077f4c2
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662912"
---
# <a name="how-to-compare-strings-in-c"></a>Comment comparer des chaînes en C\#

Vous comparez des chaînes pour répondre à une des deux questions : « Ces chaînes sont-elle égales ? » ou « Dans quel ordre ces chaînes doivent-elles être placées pendant le tri ? »

Ces deux questions sont compliquées en raison des facteurs qui affectent les comparaisons de chaînes :

- Vous pouvez choisir une comparaison ordinale ou linguistique.
- Vous pouvez choisir si la casse a une incidence.
- Vous pouvez choisir des comparaisons propres à la culture.
- Les comparaisons linguistiques dépendent de la culture et de la plateforme.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Quand vous comparez des chaînes, vous les ordonnez les unes par rapport aux autres. Les comparaisons permettent de trier une séquence de chaînes. Quand la séquence est dans un ordre connu, elle est plus facile à observer, que ce soit pour les logiciels et pour les humains. Les autres comparaisons peuvent vérifier si les chaînes sont identiques. Ces vérifications de similitude se rapprochent de celles d’égalité, sauf que certaines différences, comme celles qui concernent la casse, peuvent être ignorées.

## <a name="default-ordinal-comparisons"></a>Comparaisons ordinales par défaut

Par défaut, les opérations les plus courantes :

- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- <xref:System.String.Equals%2A?displayProperty=nameWithType>
- <xref:System.String.op_Equality%2A?displayProperty=nameWithType>et <xref:System.String.op_Inequality%2A?displayProperty=nameWithType> , autrement dit, [les opérateurs d’égalité `==` et `!=` ](../language-reference/operators/equality-operators.md#string-equality), respectivement

effectue une comparaison ordinale respectant la casse et, si nécessaire, utilise la culture actuelle. L’exemple suivant illustre ce qui suit :

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet1":::

La comparaison ordinale par défaut ne prend pas en compte les règles linguistiques lors de la comparaison de chaînes. Elle compare la valeur binaire de chaque objet <xref:System.Char> dans les deux chaînes. La comparaison ordinale par défaut respecte ainsi également la casse.

Notez que le test d’égalité avec <xref:System.String.Equals%2A?displayProperty=nameWithType> et les `==` `!=` opérateurs et diffère de la comparaison de chaînes à l’aide des <xref:System.String.CompareTo%2A?displayProperty=nameWithType> <xref:System.String.Compare(System.String,System.String)?displayProperty=nameWithType)> méthodes et. Tandis que les tests d’égalité effectuent une comparaison ordinale respectant la casse, les méthodes de comparaison effectuent une comparaison respectant la casse et dépendante de la culture à l’aide de la culture actuelle. Étant donné que les méthodes de comparaison par défaut effectuent souvent différents types de comparaisons, nous vous recommandons de toujours indiquer clairement l’intention de votre code en appelant une surcharge qui spécifie explicitement le type de comparaison à effectuer.

## <a name="case-insensitive-ordinal-comparisons"></a>Comparaisons ordinales ne respectant pas la casse

La méthode <xref:System.String.Equals(System.String,System.StringComparison)?displayProperty=nameWithType> vous permet d’indiquer une valeur <xref:System.StringComparison> de <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>
pour une comparaison ordinale ne respectant pas la casse. Il existe également une méthode <xref:System.String.Compare(System.String,System.String,System.StringComparison)?displayProperty=nameWithType> statique qui effectue une comparaison ordinale ne respectant pas la casse si vous spécifiez la valeur <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pour l’argument <xref:System.StringComparison>. Elles sont représentées dans le code suivant :

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet2":::

Lorsque vous effectuez une comparaison ordinale ne respectant pas la casse, ces méthodes utilisent les conventions de casse de la [culture invariante](xref:System.Globalization.CultureInfo.InvariantCulture).

## <a name="linguistic-comparisons"></a>Comparaisons linguistiques

Les chaînes peuvent aussi être triées à l’aide de règles linguistiques pour la culture actuelle.
C'est ce qu’on appelle parfois « Ordre de tri par mot ». Quand vous effectuez une comparaison linguistique, certains caractères Unicode non alphanumériques peuvent avoir une pondération spéciale. Par exemple, le trait d’union « - » peut avoir une très petite pondération pour que « co-op » et « coop » apparaissent à côté dans l’ordre de tri. Par ailleurs, certains caractères Unicode peuvent être équivalents à une séquence d’instances <xref:System.Char>. L’exemple suivant utilise la phrase « Ils dansent dans la rue » en allemand avec « ss » (U+0073 U+0073) dans une chaîne et « ß » (U+00DF) dans une autre. Du point de vue linguistique (dans Windows), « ss » équivaut à l’Esszet allemand : le caractère « ß » dans les cultures « en-US » et « de-DE ».

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet3":::

Cet exemple illustre les comparaisons linguistiques dépendantes du système d’exploitation. L’hôte de la fenêtre interactive est un hôte Linux. Les comparaisons linguistiques et ordinales produisent les mêmes résultats. Si vous exécutez cet exemple sur un hôte Windows, vous devez voir la sortie suivante :

```console
<coop> is less than <co-op> using invariant culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using invariant culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using invariant culture
<co-op> is less than <cop> using ordinal comparison
```

Sur Windows, l’ordre de tri pour « cop », « coop » et « co-op » change quand vous passez d’une comparaison linguistique à une comparaison ordinale. De même, les deux phrases en allemand ne sont pas comparées de la même façon selon le type de comparaison.

## <a name="comparisons-using-specific-cultures"></a>Comparaisons utilisant des cultures spécifiques

Cet exemple stocke des objets <xref:System.Globalization.CultureInfo> pour les cultures en-US et de-DE.
Les comparaisons sont effectuées à l’aide de l’un objet <xref:System.Globalization.CultureInfo> pour garantir une comparaison propre à la culture.

La culture utilisée affecte les comparaisons linguistiques. L’exemple suivant montre les résultats de la comparaison des deux phrases en allemand avec la culture « en-US » et la culture « de-DE » :

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet4":::

Les comparaisons dépendantes de la culture sont généralement utilisées pour comparer et trier des chaînes entrées par plusieurs utilisateurs. Les caractères et les conventions de tri de ces chaînes peuvent varier selon les paramètres régionaux de l’ordinateur de l’utilisateur. Même les chaînes qui contiennent des caractères identiques peuvent être triées différemment selon la culture du thread actuel. Par ailleurs, essayez cet exemple de code localement sur un ordinateur Windows et vous obtenez les résultats suivants :

```console
<coop> is less than <co-op> using en-US culture
<coop> is greater than <co-op> using ordinal comparison
<coop> is less than <cop> using en-US culture
<coop> is less than <cop> using ordinal comparison
<co-op> is less than <cop> using en-US culture
<co-op> is less than <cop> using ordinal comparison
```

Les comparaisons linguistiques sont dépendantes de la culture actuelle et du système d’exploitation. Vous devez en tenir compte quand vous utilisez les comparaisons de chaînes.

## <a name="linguistic-sorting-and-searching-strings-in-arrays"></a>Tri linguistique et recherche de chaînes dans des tableaux

Les exemples suivants montrent comment trier et rechercher des chaînes dans un tableau à l’aide d’une comparaison linguistique dépendante de la culture actuelle. Vous utilisez les méthodes statiques <xref:System.Array> qui prennent un paramètre <xref:System.StringComparer?displayProperty=nameWithType>.

Cet exemple montre comment trier un tableau de chaînes à l’aide de la culture actuelle :

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet5":::

Une fois que le tableau est trié, vous pouvez rechercher des entrées à l’aide d’une recherche binaire. Une recherche binaire commence au milieu de la collection pour déterminer la moitié de la collection qui doit contenir la chaîne recherchée. Chaque comparaison ultérieure divise à son tour en deux la partie restante de la collection.  Le tableau est trié à l’aide de <xref:System.StringComparer.CurrentCulture?displayProperty=nameWithType>. La fonction locale `ShowWhere` affiche des informations sur l’emplacement de la chaîne. Si la chaîne est introuvable, la valeur retournée indique l’emplacement où elle devrait se trouver.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet6":::

## <a name="ordinal-sorting-and-searching-in-collections"></a>Tri ordinal et recherche dans des collections

Le code suivant utilise la classe de collection <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> pour stocker les chaînes. Les chaînes sont triées à l’aide de la méthode <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>. Cette méthode a besoin d’un délégué qui compare et trie les deux chaînes. La méthode <xref:System.String.CompareTo%2A?displayProperty=nameWithType> fournit cette fonction de comparaison. Exécutez l’exemple et observez l’ordre. Cette opération de tri utilise un tri ordinal respectant la casse. Vous devez utiliser les méthodes statiques <xref:System.String.Compare%2A?displayProperty=nameWithType> pour spécifier des règles de comparaison différentes.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet7":::

Une fois triée, la liste de chaînes peut être parcourue à l’aide d’une recherche binaire. L’exemple suivant montre comment parcourir la liste triée à l’aide de la même fonction de comparaison. La fonction locale `ShowWhere` montre où se trouve le texte recherché ou là où il devrait se trouver :

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet8":::

Vérifiez toujours que vous utilisez le même type de comparaison pour le tri et la recherche. L’utilisation de différents types de comparaison pour le tri et la recherche produit des résultats inattendus.

Les classes de collection telles que <xref:System.Collections.Hashtable?displayProperty=nameWithType>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> et <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> ont des constructeurs qui prennent un paramètre <xref:System.StringComparer?displayProperty=nameWithType> quand le type des éléments ou des clés est `string`. En général, vous devez utiliser ces constructeurs chaque fois que cela vous est possible, et spécifier <xref:System.StringComparer.Ordinal?displayProperty=nameWithType> ou <xref:System.StringComparer.OrdinalIgnoreCase?displayProperty=nameWithType>.

## <a name="reference-equality-and-string-interning"></a>Égalité de référence et centralisation des chaînes

Aucun des exemples n’a utilisé <xref:System.Object.ReferenceEquals%2A>. Cette méthode détermine si deux chaînes sont le même objet. Cela peut entraîner des résultats incohérents dans les comparaisons de chaînes. L’exemple suivant illustre la fonctionnalité de *centralisation des chaînes* du langage C#. Lorsqu’un programme déclare plusieurs variables de chaînes identiques, le compilateur les stocke au même emplacement. En appelant la méthode <xref:System.Object.ReferenceEquals%2A>, vous pouvez voir que les deux chaînes référencent le même objet en mémoire. Utilisez la méthode <xref:System.String.Copy%2A?displayProperty=nameWithType> pour éviter la centralisation. Une fois la copie effectuée, les deux chaînes ont différents emplacements de stockage, même si elles ont la même valeur. Exécutez l’exemple suivant pour montrer que les chaînes `a` et `b` sont *centralisées*, ce qui signifie qu’elles partagent le même stockage. Les chaînes `a` et `c` ne le sont pas.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/CompareStrings.cs" id="Snippet9":::

> [!NOTE]
> Quand vous recherchez l’égalité des chaînes, vous devez utiliser les méthodes qui spécifient explicitement le type de comparaison que vous souhaitez effectuer. Votre code est plus lisible et plus facile à gérer. Utilisez les surcharges des méthodes des classes <xref:System.String?displayProperty=nameWithType> et <xref:System.Array?displayProperty=nameWithType> qui prennent un paramètre d’énumération <xref:System.StringComparison>. Vous spécifiez le type de comparaison à effectuer. Évitez d’utiliser les opérateurs `==` et `!=` dans la recherche d’égalité. Les méthodes d’instance <xref:System.String.CompareTo%2A?displayProperty=nameWithType> effectuent toujours une comparaison ordinale respectant la casse. Elles sont principalement adaptées au classement des chaînes par ordre alphabétique.

Vous pouvez intégrer une chaîne ou récupérer une référence à une chaîne intégrée existante en appelant la méthode <xref:System.String.Intern%2A?displayProperty=nameWithType>. Pour déterminer si une chaîne est intégrée, appelez la méthode <xref:System.String.IsInterned%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Globalization.CultureInfo?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- [Chaînes](../programming-guide/strings/index.md)
- [Comparaison de chaînes](../../standard/base-types/comparing.md)
- [Globalisation et localisation d’applications](/visualstudio/ide/globalizing-and-localizing-applications)
