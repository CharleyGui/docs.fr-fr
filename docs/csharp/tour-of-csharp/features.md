---
title: Visite guidée de C#-zones de langage majeures
description: Novice en matière de langage C# ? Découvrez les principes de base du langage.
ms.date: 08/06/2020
ms.openlocfilehash: a73399643ada05a4bfb17fadd17bf3267514e99d
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400746"
---
# <a name="major-language-areas"></a>Principales zones de langue

## <a name="arrays-collections-and-linq"></a>Tableaux, collections et LINQ

C# et .NET fournissent de nombreux types de collections différents. Les tableaux ont une syntaxe définie par le langage. Les types de collections génériques sont répertoriés dans l' <xref:System.Collections.Generic?displayProperty=fullName> espace de noms. Les collections spécialisées incluent l' <xref:System.Span%601?displayProperty=nameWithType> accès à la mémoire continue sur le frame de pile et l' <xref:System.Memory%601?displayProperty=nameWithType> accès à la mémoire continue sur le tas managé. Toutes les collections, y compris les tableaux, <xref:System.Span%601> et <xref:System.Memory%601> partagent un principe d’unification pour l’itération. Vous utilisez l' <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface. Ce principe d’unification signifie que tous les types de collections peuvent être utilisés avec des requêtes LINQ ou d’autres algorithmes. Vous écrivez des méthodes à l’aide de <xref:System.Collections.Generic.IEnumerable%601> et ces algorithmes fonctionnent avec n’importe quelle collection.

### <a name="arrays"></a>Tableaux

Un [ * **tableau** _](../programming-guide/arrays/index.md) est une structure de données qui contient un certain nombre de variables accessibles par le biais d’index calculés. Les variables contenues dans un tableau, également appelées _*_éléments_*_ du tableau, sont toutes du même type. Ce type est appelé le _*_type d’élément_*_ du tableau.

Les types tableau sont des types référence, et la déclaration d’une variable tableau réserve simplement un espace pour une référence à une instance de tableau. Les instances de tableau réelles sont créées dynamiquement au moment de l’exécution à l’aide de l' `new` opérateur. L' `new` opération spécifie la _*_longueur_*_ de la nouvelle instance de tableau, qui est ensuite résolue pour la durée de vie de l’instance. Les indices des éléments d’un tableau vont de `0` à `Length - 1`. L’opérateur `new` initialise automatiquement les éléments d’un tableau à leur valeur par défaut, c'est-à-dire, par exemple, zéro pour tous les types numériques et `null` pour tous les types référence.

L’exemple suivant crée un tableau de `int` éléments, initialise le tableau et imprime le contenu du tableau.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="ArraysSample":::

Cet exemple crée et opère sur un _*_tableau unidimensionnel_*_. C# prend également en charge _*_les tableaux multidimensionnels_*_. Le nombre de dimensions d’un type tableau, également appelé _*_rang_*_ du type tableau, est un plus le nombre de virgules écrites entre les crochets du type tableau. L’exemple suivant alloue respectivement des tableaux à une seule, deux et trois dimensions, respectivement.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="DeclareArrays":::

Le tableau `a1` contient 10 éléments, le tableau `a2` en contient 50 (10 x 5) et le tableau `a3` en contient 100 (10 × 5 × 2).
Le type d’élément d’un tableau peut être de n’importe quel type, y compris un type tableau. Un tableau avec des éléments d’un type tableau est parfois appelé _*_tableau en escalier_*_ , car les longueurs des tableaux d’éléments ne doivent pas nécessairement être identiques. L’exemple suivant alloue un tableau de tableaux de `int` :

:::code language="csharp" source="./snippets/shared/Features.cs" ID="ArrayOfArrays":::

La première ligne crée un tableau avec trois éléments, chacun de type `int[]` et chacun avec une valeur initiale de `null`. Les lignes suivantes initialisent ensuite les trois éléments avec des références à des instances de tableau individuelles de longueurs différentes.

L' `new` opérateur permet de spécifier les valeurs initiales des éléments du tableau à l’aide d’un _*_initialiseur de tableau_*_ , qui est une liste d’expressions écrites entre les délimiteurs `{` et `}` . L’exemple suivant alloue et initialise un `int[]` avec trois éléments.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="InitializeArray":::

La longueur du tableau est déduite du nombre d’expressions entre `{` et `}` . L’initialisation de tableau peut être raccourcie de manière à ce que le type de tableau n’ait pas à être retraité.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="InitializeShortened":::

Les deux exemples précédents sont équivalents au code suivant :

:::code language="csharp" source="./snippets/shared/Features.cs" ID="InitializeGenerated":::

L' `foreach` instruction peut être utilisée pour énumérer les éléments d’une collection. Le code suivant énumère le tableau de l’exemple précédent :

:::code language="csharp" source="./snippets/shared/Features.cs" ID="EnumerateArray":::

L' `foreach` instruction utilise l' <xref:System.Collections.Generic.IEnumerable%601> interface, donc peut fonctionner avec n’importe quelle collection.

## <a name="string-interpolation"></a>Interpolation de chaîne

L' [_*_interpolation de chaîne_*_](../language-reference/tokens/interpolated.md) C# vous permet de mettre en forme des chaînes en définissant des expressions dont les résultats sont placés dans une chaîne de format. Par exemple, l’exemple suivant imprime la température d’un jour donné à partir d’un ensemble de données météorologiques :

:::code language="csharp" source="./snippets/shared/Features.cs" ID="StringInterpolation":::

Une chaîne interpolée est déclarée à l’aide du `$` jeton. L’interpolation de chaîne évalue les expressions comprises entre `{` et `}` , puis convertit le résultat en `string` et remplace le texte entre crochets par le résultat de chaîne de l’expression. `:`Dans la première expression, `{weatherData.Date:MM-DD-YYYY}` spécifie le _Format chaîne *. Dans l’exemple précédent, il spécifie que la date doit être imprimée au format « MM-jj-aaaa ».

## <a name="pattern-matching"></a>Critères spéciaux

Le langage C# fournit des expressions de [ * **critères spéciaux**](../pattern-matching.md) pour interroger l’état d’un objet et exécuter du code en fonction de cet État. Vous pouvez inspecter les types et les valeurs des propriétés et des champs pour déterminer l’action à entreprendre. L' `switch` expression est l’expression principale pour les critères spéciaux.

## <a name="delegates-and-lambda-expressions"></a>Délégués et expressions lambda

Un [_*_type délégué_*_](../delegates-overview.md) représente des références aux méthodes avec une liste de paramètres et un type de retour particuliers. Les délégués permettent de traiter les méthodes en tant qu’entités qui peuvent être affectées à des variables et passées comme paramètres. Les délégués sont similaires au concept de pointeurs de fonction trouvés dans d’autres langages. Contrairement aux pointeurs de fonction, les délégués sont orientés objet et de type sécurisé.

L’exemple suivant déclare et utilise un type délégué nommé `Function`.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="DelegateExample":::

Une instance du type délégué `Function` peut faire référence à toute méthode qui accepte un argument `double` et retourne une valeur `double`. La `Apply` méthode applique un donné `Function` aux éléments d’un `double[]` , en retournant un `double[]` avec les résultats. Dans la méthode `Main`, `Apply` sert à appliquer trois fonctions différentes à un `double[]`.

Un délégué peut faire référence à une méthode statique (comme `Square` ou `Math.Sin` dans l’exemple précédent) ou à une méthode d’instance (comme `m.Multiply` dans l’exemple précédent). Un délégué qui référence une méthode d’instance référence aussi un objet particulier, et quand la méthode d’instance est appelée via le délégué, cet objet devient `this` dans l’appel.

Les délégués peuvent également être créés à l’aide de fonctions anonymes, qui sont des « méthodes inline » qui sont créées lorsqu’elles sont déclarées. Les fonctions anonymes peuvent voir les variables locales des méthodes qui l’entourent. L’exemple suivant ne crée pas de classe :

:::code language="csharp" source="./snippets/shared/Features.cs" ID="UseDelegate":::

Un délégué ne connaît pas ou ne tient pas compte de la classe de la méthode à laquelle il fait référence. Il est important que la méthode référencée ait les mêmes paramètres et le même type de retour que le délégué.

## <a name="async--await"></a>Async/await

C# prend en charge les programmes asynchrones avec deux mots clés : `async` et `await` . Vous ajoutez le `async` modificateur à une déclaration de méthode pour déclarer que la méthode est asynchrone. L' `await` opérateur indique au compilateur d’attendre de façon asynchrone qu’un résultat se termine. Le contrôle est retourné à l’appelant, et la méthode retourne une structure qui gère l’état du travail asynchrone. La structure est généralement un <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> , mais peut être n’importe quel type qui prend en charge le modèle d’attente. Ces fonctionnalités vous permettent d’écrire du code qui se lit comme son homologue synchrone, mais qui s’exécute de façon asynchrone. Par exemple, le code suivant télécharge la page d’origine de [Microsoft docs](/):

:::code language="csharp" source="./snippets/shared/Features.cs" ID="AsyncExample":::

Ce petit exemple illustre les principales fonctionnalités de la programmation asynchrone :

- La déclaration de méthode comprend le `async` modificateur.
- Corps de la méthode `await` s le retour de la `GetByteArrayAsync` méthode.
- Le type spécifié dans l' `return` instruction correspond à l’argument de type dans la `Task<T>` déclaration de la méthode. (Une méthode qui retourne un `Task` utilise `return` des instructions sans argument).

## <a name="attributes"></a>Attributs

Les types, membres et autres entités d’un programme C# prennent en charge les modificateurs qui contrôlent certains aspects de leur comportement. Par exemple, l’accessibilité d’une méthode est contrôlée à l’aide des modificateurs `public`, `protected`, `internal` et `private`. C# généralise cette fonctionnalité pour que les types d’informations déclaratives définis par l’utilisateur puissent être associés aux entités de programme et récupérés au moment de l’exécution. Les programmes spécifient ces informations déclaratives supplémentaires en définissant et en utilisant [_ *_attributes_* *](../programming-guide/concepts/attributes/index.md).

L’exemple suivant déclare un attribut `HelpAttribute` qui peut être placé sur des entités de programme pour fournir des liens vers leur documentation associée.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="DefineAttribute":::

Toutes les classes d’attributs dérivent de la <xref:System.Attribute> classe de base fournie par la bibliothèque .net. Les attributs peuvent être appliqués en donnant leur nom, ainsi que les éventuels arguments, à l’intérieur de crochets juste avant la déclaration associée. Si le nom d’un attribut se termine en `Attribute`, cette partie du nom peut être omise lorsque l’attribut est référencé. Par exemple, `HelpAttribute` peut être utilisé comme suit.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="UseAttributes":::

Cet exemple joint un `HelpAttribute` à la classe `Widget`. Il ajoute un autre `HelpAttribute` à la méthode `Display` dans la classe. Les constructeurs publics d’une classe d’attributs contrôlent les informations qui doivent être fournies lorsque l’attribut est joint à une entité de programme. Des informations supplémentaires peuvent être fournies en référençant les propriétés en lecture-écriture publiques de la classe d’attributs (comme la référence à la propriété `Topic`, précédemment).

Les métadonnées définies par les attributs peuvent être lues et manipulées par réflexion lors de l’exécution. Lorsqu’un attribut particulier est demandé à l’aide de cette technique, le constructeur de la classe d’attributs est appelé avec les informations fournies dans la source du programme, et l’instance d’attribut qui en résulte est retournée. Si des informations supplémentaires ont été fournies via les propriétés, ces propriétés sont définies sur les valeurs données avant que le renvoi de l’instance de l’attribut.

L’exemple de code suivant montre comment obtenir les `HelpAttribute` instances associées à la classe `Widget` et sa méthode `Display`.

:::code language="csharp" source="./snippets/shared/Features.cs" ID="ReadAttributes":::

## <a name="learn-more"></a>En savoir plus

Vous pouvez en savoir plus sur C# en essayant l’un de nos [didacticiels](../tutorials/index.md).

>[!div class="step-by-step"]
>[Précédent](program-building-blocks.md)
