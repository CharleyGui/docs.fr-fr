---
title: System.Delegate et le mot clé `delegate`
description: Découvrez les classes dans .NET qui prennent en charge les délégués et comment ces derniers sont mappés au mot clé’Delegate'.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 3cfc9925be0f191dc3fc93c02f4a8f9a40b71895
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450919"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a>System.Delegate et le mot clé `delegate`

[Précédent](delegates-overview.md)

Cet article décrit les classes dans .NET qui prennent en charge les délégués et comment elles sont mappées au mot clé `delegate`.

## <a name="define-delegate-types"></a>Définir les types délégués

Commençons par le mot clé 'delegate', car c’est l’élément principal que vous utilisez quand vous travaillez avec des délégués. Le code que le compilateur génère quand vous utilisez le mot clé `delegate` mappe aux appels de méthode qui appellent des membres des classes <xref:System.Delegate> et <xref:System.MulticastDelegate>. 

Vous définissez un type délégué à l’aide d’une syntaxe similaire à la définition d’une signature de méthode. Vous venez d’ajouter le mot clé `delegate` à la définition.

Continuons à utiliser la méthode List.Sort() comme dans notre exemple. La première étape consiste à créer un type pour le délégué de comparaison :

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

Le compilateur génère une classe, dérivée de `System.Delegate`, qui correspond à la signature utilisée (dans le cas présent, une méthode qui retourne un entier et qui a deux arguments). Le type de ce délégué est `Comparison`. Le type délégué `Comparison` est un type générique. Pour plus d’informations sur les génériques, cliquez [ici](programming-guide/generics/index.md).

Notez que la syntaxe peut sembler déclarer une variable, alors qu’elle déclare en fait un *type*. Vous pouvez définir des types délégués dans des classes, directement dans des espaces de noms, ou même dans l’espace de noms global.

> [!NOTE]
> La déclaration de types délégués (ou d’autres types) directement dans l’espace de noms global n’est pas recommandée. 

Le compilateur génère également des gestionnaires d’ajout et de suppression pour ce nouveau type, afin que les clients de cette classe puissent ajouter et supprimer des méthodes dans la liste d’invocation d’une instance. Le compilateur exige que la signature de la méthode ajoutée ou supprimée corresponde à la signature utilisée lors de la déclaration de la méthode. 

## <a name="declare-instances-of-delegates"></a>Déclarer des instances de délégués

Après avoir défini le délégué, vous pouvez créer une instance de ce type.
Comme pour toutes les variables en C#, vous ne pouvez pas déclarer d’instances de délégué directement dans un espace de noms, ni dans l’espace de noms global.

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

Le type de la variable est le type délégué défini précédemment, `Comparison<T>`. Le nom de la variable est `comparator`.
 
 Cet extrait de code ci-dessus a déclaré une variable membre à l’intérieur d’une classe. Vous pouvez également déclarer des variables de délégués qui sont des variables locales, ou bien des arguments de méthodes.

## <a name="invoke-delegates"></a>Appeler des délégués

Vous appelez les méthodes qui se trouvent dans la liste d’invocation d’un délégué en appelant ce dernier. À l’intérieur de la méthode `Sort()`, le code appelle la méthode de comparaison pour déterminer l’ordre dans lequel placer les objets :

```csharp
int result = comparator(left, right);
```

Dans la ligne ci-dessus, le code *appelle* la méthode attachée au délégué.
Vous traitez la variable comme un nom de méthode et vous l’appelez à l’aide de la syntaxe d’appel de méthode normale.

Cette ligne de code effectue une hypothèse hasardeuse : il n’existe aucune garantie qu’une cible a été ajoutée au délégué. Si aucune cible n’a été attachée, la ligne ci-dessus entraîne la levée de `NullReferenceException`. Les idiomes utilisés pour résoudre ce problème sont plus compliqués qu’un simple contrôle de valeur Null. Ils sont traités plus loin dans cette [série](delegates-patterns.md).

## <a name="assign-add-and-remove-invocation-targets"></a>Assigner, ajouter et supprimer des cibles d’appel

Voyons comment un type délégué est défini et comment les instances de délégué sont déclarées et appelées.

Les développeurs qui souhaitent utiliser la méthode `List.Sort()` doivent définir une méthode dont la signature correspond à la définition du type délégué, puis l’assigner au délégué utilisé par la méthode sort. Cette assignation ajoute la méthode à la liste d’invocation de cet objet délégué.

Supposons que vous souhaitiez trier une liste de chaînes en fonction de leur longueur. Votre fonction de comparaison peut être la suivante :

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

La méthode est déclarée en tant que méthode privée. C’est parfait. Vous ne voulez peut-être pas que cette méthode fasse partie de votre interface publique. Elle peut toujours être utilisée comme méthode de comparaison quand elle est attachée à un délégué. Cette méthode est attachée à la liste cible de l’objet délégué dans le code appelant, qui peut y accéder par l’intermédiaire de ce délégué.

Vous créez cette relation en passant cette méthode à la méthode `List.Sort()` :

```csharp
phrases.Sort(CompareLength);
```

Notez que le nom de la méthode est utilisé sans parenthèses. L’utilisation de la méthode comme argument indique au compilateur de convertir la référence de méthode en une référence pouvant être utilisée comme cible d’invocation de délégué, puis d’attacher cette méthode comme cible d’invocation.

Vous pouvez également avoir déclaré explicitement une variable de type `Comparison<string>` et effectué une assignation :

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

Quand la méthode utilisée comme cible du délégué est petite, il est courant d’utiliser la syntaxe des [expressions lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) pour effectuer l’assignation :

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

L’utilisation d’expressions lambda pour les cibles de délégués est traitée plus en détail dans une [section ultérieure](delegates-patterns.md).

L’exemple Sort() attache généralement une méthode cible unique au délégué. Toutefois, les objets délégués prennent en charge les listes d’invocation comprenant plusieurs méthodes cibles attachées à un objet délégué.

## <a name="delegate-and-multicastdelegate-classes"></a>Classes Delegate et MulticastDelegate

La prise en charge du langage décrite ci-dessus fournit les fonctionnalités et la prise en charge généralement nécessaires pour utiliser des délégués. Ces fonctionnalités sont basées sur deux classes du framework .NET Core : <xref:System.Delegate> et <xref:System.MulticastDelegate>.

La classe `System.Delegate` et sa sous-classe directe unique, `System.MulticastDelegate`fournissent la prise en charge de l’infrastructure pour la création de délégués, l’inscription de méthodes en tant que cibles de délégué et l’appel de toutes les méthodes inscrites en tant que cible de délégué. 

Il est intéressant de noter que les classes `System.Delegate` et `System.MulticastDelegate` ne sont pas elles-mêmes des types délégués. Elles servent de base à tous les types délégués spécifiques. Ce même processus de conception du langage a stipulé que vous ne pouvez pas déclarer une classe qui dérive de `Delegate` ou de `MulticastDelegate`. Les règles du langage C# l’interdisent.
 
À la place, le compilateur C# crée des instances d’une classe dérivée de `MulticastDelegate` quand vous utilisez le mot clé du langage C# pour déclarer des types délégués.

Cette conception trouve ses racines dans la première version Release de C# et du .NET. L’équipe de conception avait pour objectif de s’assurer que le langage appliquait la cohérence des types lors de l’utilisation de délégués. Il était important de garantir que les délégués étaient appelés avec le type et le nombre d’arguments appropriés. Et que tout type de retour était correctement indiqué au moment de la compilation. Les délégués faisaient partie de la version Release du .NET 1.0, qui était antérieure aux génériques.

La création, par le compilateur, des classes déléguées concrètes qui représentaient la signature de méthode utilisée constituait la meilleure façon d’appliquer la cohérence des types.

Même si vous ne pouvez pas créer des classes dérivées directement, vous utiliserez les méthodes définies sur ces classes. Examinons les méthodes les plus courantes que vous utiliserez quand vous travaillerez avec des délégués.

Le premier et le plus important point à retenir est que chaque délégué avec lequel vous travaillez est dérivé de `MulticastDelegate`. Un délégué multicast signifie que plusieurs méthodes cibles peuvent être appelées lors d’un appel par l’intermédiaire d’un délégué. La conception d’origine envisageait de distinguer les délégués où une seule méthode cible pouvait être attachée et appelée, et les délégués où plusieurs méthodes cibles pouvaient être attachées et appelées. En réalité, cette distinction s’est avérée moins utile que prévu. Les deux différentes classes étaient déjà créées et sont présentes dans le framework depuis la première version Release publique de celui-ci.

Les méthodes que vous utiliserez le plus avec les délégués sont `Invoke()` et `BeginInvoke()` / `EndInvoke()`. `Invoke()` appelle toutes les méthodes qui ont été attachées à une instance de délégué particulière. Comme vous l’avez vu ci-dessus, vous appelez généralement des délégués à l’aide de la syntaxe d’appel de méthode sur la variable de délégué. Comme vous le verrez [plus loin dans cette série](delegates-patterns.md), il existe des modèles qui fonctionnent directement avec ces méthodes.

Maintenant que vous avez vu la syntaxe du langage et les classes qui prennent en charge les délégués, examinons la façon dont les délégués fortement typés sont utilisés, créés et appelés.

[Next](delegates-strongly-typed.md)
