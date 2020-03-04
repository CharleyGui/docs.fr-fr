---
title: Écrire du code C# sécurisé et efficace
description: Les améliorations récentes apportées au langage C# vous permettent d’écrire du code sécurisé vérifiable que les performances associaient précédemment à du code non sécurisé.
ms.date: 10/23/2018
ms.technology: csharp-advanced-concepts
ms.custom: mvc
ms.openlocfilehash: d4a7916b80e15c7f00fa0a7da213ed0593e0959d
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239974"
---
# <a name="write-safe-and-efficient-c-code"></a>Écrire du code C# sécurisé et efficace

Les nouvelles fonctionnalités de C# vous permettent d’écrire du code sécurisé vérifiable avec de meilleures performances. Si vous appliquez soigneusement ces techniques, les scénarios nécessitant du code non sécurisé sont moins nombreux. Ces fonctionnalités facilitent l’utilisation des références à des types valeur comme arguments de méthode et retours de méthode. Quand elles sont utilisées de façon sécurisée, ces techniques réduisent la copie des types valeur. En utilisant des types valeur, vous pouvez réduire le nombre d’allocations et de passes du garbage collection.

Une grande partie de l’exemple de code de cet article utilise des fonctionnalités ajoutées dans C# 7.2. Pour utiliser ces fonctionnalités, vous devez configurer votre projet pour qu’il utilise C# 7.2 ou ultérieur. Pour plus d’informations sur la définition de la version du langage, consultez [Configurer la version du langage](language-reference/configure-language-version.md).

Cet article met l’accent sur les techniques de gestion efficace des ressources. Un avantage de l’utilisation de types valeur est qu’ils permettent souvent d’éviter les allocations de tas. Mais l’inconvénient, c’est qu’ils sont copiés par valeur. Ce compromis complique l’optimisation des algorithmes qui opèrent sur de grandes quantités de données. Les nouvelles fonctionnalités du langage dans C# 7.2 fournissent des mécanismes qui permettent d’obtenir un code efficace sécurisé en utilisant des références à des types valeur. Utilisez ces fonctionnalités judicieusement pour minimiser à la fois les allocations et les opérations de copie. Cet article explore ces nouvelles fonctionnalités.

Cet article met l’accent sur les techniques de gestion des ressources suivantes :

- Déclarez un [`readonly struct`](language-reference/keywords/readonly.md#readonly-struct-example) pour exprimer qu’un type est **immuable** et qu’il permet au compilateur d’enregistrer des copies lors de l’utilisation de paramètres [`in`](language-reference/keywords/in-parameter-modifier.md).
- Si un type ne peut pas être immuable, déclarez `struct` membres `readonly` pour indiquer que le membre ne modifie pas l’État.
- Utilisez un retour de [`ref readonly`](language-reference/keywords/ref.md#reference-return-values) quand la valeur de retour est un `struct` plus grand que <xref:System.IntPtr.Size?displayProperty=nameWithType> et que la durée de vie du stockage est supérieure à celle de la méthode retournant la valeur.
- Quand la taille d’une `readonly struct` plus grande que <xref:System.IntPtr.Size?displayProperty=nameWithType>, vous devez la passer comme paramètre `in` pour des raisons de performances.
- Ne transmettez jamais un `struct` en tant que paramètre `in`, sauf s’il est déclaré avec le modificateur `readonly` ou si la méthode appelle uniquement `readonly` membres du struct. La violation de ce guide peut avoir un impact négatif sur les performances et peut entraîner un comportement obscur.
- Utilisez un [`ref struct`](language-reference/keywords/ref.md#ref-struct-types), ou un `readonly ref struct` comme <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> pour utiliser la mémoire comme une séquence d’octets.

Ces techniques vous forcent à trouver un équilibre entre deux objectifs concurrents concernant les **références** et les **valeurs**. Les variables qui sont des [types référence](programming-guide/types/index.md#reference-types) contiennent une référence à l’emplacement en mémoire. Les variables qui sont des [types valeur](programming-guide/types/index.md#value-types) contiennent directement leur valeur. Ces différences mettent en évidence les différences importantes pour la gestion des ressources mémoire. Les **types valeur** sont généralement copiés quand ils sont passés à une méthode ou retournés depuis une méthode. Ce comportement comprend la copie de la valeur de `this` lors de l’appel de membres d’un type valeur. Le coût de la copie est lié à la taille du type. Les **types référence** sont alloués sur le tas managé. Chaque nouvel objet nécessite une nouvelle allocation et doit par conséquent être récupéré par la suite. Ces deux opérations prennent du temps. La référence est copiée quand un type référence est passé comme argument à une méthode ou retourné depuis une méthode.

Cet article utilise l’exemple de concept suivant d’une structure de points 3D pour expliquer ces recommandations :

```csharp
public struct Point3D
{
    public double X;
    public double Y;
    public double Z;
}
```

Les différents exemples utilisent des implémentations différentes de ce concept.

## <a name="declare-readonly-structs-for-immutable-value-types"></a>Déclarer des structs en lecture seule pour les types valeur immuables

La déclaration d’une `struct` avec le modificateur `readonly` indique au compilateur que votre intention est de créer un type immuable. Le compilateur applique cette décision de conception avec les règles suivantes :

- Tous les champs membres doivent être `readonly`
- Toutes les propriétés doivent être en lecture seule, y compris les propriétés implémentées automatiquement.

Ces deux règles sont suffisantes pour garantir qu’aucun membre d’une `readonly struct` ne modifie l’état de ce struct. Le `struct` est immuable. La structure `Point3D` peut être définie comme struct immuable, comme le montre l’exemple suivant :

```csharp
readonly public struct ReadonlyPoint3D
{
    public ReadonlyPoint3D(double x, double y, double z)
    {
        this.X = x;
        this.Y = y;
        this.Z = z;
    }

    public double X { get; }
    public double Y { get; }
    public double Z { get; }
}
```

Suivez cette recommandation quand l’intention de votre conception est de créer un type immuable. Toute amélioration des performances est un avantage supplémentaire. Le `readonly struct` exprime clairement l’intention de votre conception.

## <a name="declare-readonly-members-when-a-struct-cant-be-immutable"></a>Déclarer des membres ReadOnly lorsqu’un struct ne peut pas être immuable

Dans C# 8,0 et versions ultérieures, quand un type struct est mutable, vous devez déclarer les membres qui n’entraînent pas la `readonly`de la mutation. Par exemple, voici une variation mutable de la structure de points 3D :

```csharp
public struct Point3D
{
    public Point3D(double x, double y, double z)
    {
        _x = x;
        _y = y;
        _z = z;
    }

    private double _x;
    public double X
    {
        readonly get => _x;
        set => _x = value;
    }

    private double _y;
    public double Y
    {
        readonly get => _y;
        set => _y = value;
    }

    private double _z;
    public double Z
    {
        readonly get => _z;
        set => _z = value;
    }

    public readonly double Distance => Math.Sqrt(X * X + Y * Y + Z * Z);

    public readonly override string ToString() => $"{X}, {Y}, {Z}";
}
```

L’exemple précédent montre un grand nombre d’emplacements où vous pouvez appliquer le modificateur de `readonly` : les méthodes, les propriétés et les accesseurs de propriété. Si vous utilisez des propriétés implémentées automatiquement, le compilateur ajoute le modificateur `readonly` à l’accesseur `get` pour les propriétés en lecture-écriture. Le compilateur ajoute le modificateur `readonly` aux déclarations de propriété implémentées automatiquement pour les propriétés avec un seul accesseur `get`.

L’ajout du modificateur `readonly` aux membres qui n’ont pas de mutation d’État fournit deux avantages connexes. Tout d’abord, le compilateur applique votre intention. Ce membre ne peut pas muter l’état de la structure, ni accéder à un membre qui n’est pas également marqué `readonly`. Deuxièmement, le compilateur ne crée pas de copies défensives de `in` paramètres lors de l’accès à un membre `readonly`. Le compilateur peut effectuer cette optimisation en toute sécurité car elle garantit que le `struct` n’est pas modifié par un membre `readonly`.

## <a name="use-ref-readonly-return-statements-for-large-structures-when-possible"></a>Quand c’est possible, utilisez des instructions `ref readonly return` pour les grandes structures.

Vous pouvez retourner des valeurs par référence quand la valeur retournée n’est pas locale à la méthode effectuant le retour. Un retour par référence signifie que seule la référence est copiée, et non pas la structure. Dans l’exemple suivant, la propriété `Origin` ne peut pas utiliser un retour `ref`, car la valeur retournée est une variable locale :

```csharp
public Point3D Origin => new Point3D(0,0,0);
```

Cependant, la définition de propriété suivante peut être retournée par référence, car la valeur retournée est un membre statique :

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    // Dangerous! returning a mutable reference to internal storage
    public ref Point3D Origin => ref origin;

    // other members removed for space
}
```

Vous ne voulez pas que les appelants modifient la valeur l’origine : vous devez donc retourner la valeur par `ref readonly` :

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    public static ref readonly Point3D Origin => ref origin;

    // other members removed for space
}
```

Retourner `ref readonly` vous permet d’éviter de copier des structures plus grandes et de préserver l’immuabilité de vos membres de données internes.

À l’endroit de l’appel, les appelants font le choix d’utiliser la propriété `Origin` comme `ref readonly` ou comme valeur :

[!code-csharp[AssignRefReadonly](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

La première assignation dans le code précédent effectue une copie de la constante `Origin` et assigne cette copie. La seconde assigne une référence. Notez que le modificateur `readonly` doit faire partie de la déclaration de la variable. La référence à laquelle il fait référence ne peut pas être modifiée. Toute tentative de modification provoque une erreur de compilation.

Le modificateur `readonly` est nécessaire sur la déclaration de `originReference`.

Le compilateur fait en sorte que l’appelant ne puisse pas modifier la référence. Toute tentative d’assignation directe de la valeur génère une erreur de compilation. Cependant, le compilateur ne peut pas savoir si une méthode membre modifie l’état du struct.
Pour garantir que l’objet n’est pas modifié, le compilateur crée une copie et appelle les références de membre en utilisant cette copie. Les modifications sont apportées à cette copie défensive.

## <a name="apply-the-in-modifier-to-readonly-struct-parameters-larger-than-systemintptrsize"></a>Appliquer le modificateur `in` à des paramètres `readonly struct` plus grands que `System.IntPtr.Size`

Le mot clé `in` vient en complément des mots clés `ref` et `out` existants pour passer des arguments par référence. Le mot clé `in` spécifie que l’argument doit être passé par référence, mais la méthode appelée ne modifie pas la valeur.

Vous disposez ainsi d’un vocabulaire complet pour exprimer votre intention de conception.
Les types valeur sont copiés s’ils sont passés à une méthode appelée et que vous ne spécifiez pas l’un des modificateurs suivants dans la signature de la méthode. Chacun de ces modificateurs spécifie qu’une variable est passée par référence, ce qui évite la copie. Chaque modificateur exprime une intention différente :

- `out` : Cette méthode définit la valeur de l’argument utilisé comme paramètre.
- `ref` : Cette méthode peut définir la valeur de l’argument utilisé comme paramètre.
- `in`: cette méthode ne modifie pas la valeur de l’argument utilisé comme paramètre.

Ajoutez le modificateur `in` pour passer un argument par référence et déclarez que votre intention de conception est de passer des arguments par référence afin d’éviter toute copie inutile. Vous n’avez pas l’intention de modifier l’objet utilisé comme argument.

Cette pratique améliore souvent les performances pour les types valeur en lecture seule qui sont plus grands que <xref:System.IntPtr.Size?displayProperty=nameWithType>. Pour les types simples (les types `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, `bool` et `enum`), les gains de performances potentiels sont minimes. En fait, les performances peuvent se dégrader quand le passage par référence est utilisé pour les types plus petits que <xref:System.IntPtr.Size?displayProperty=nameWithType>.

Le code suivant montre un exemple de méthode qui calcule la distance entre deux points dans l’espace 3D.

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Les arguments sont deux structures qui contiennent chacune trois valeurs de type double. Un double représentant 8 octets, chaque argument représente 24 octets. En spécifiant le modificateur `in`, vous passez une référence de 4 ou 8 octets à ces arguments, selon l’architecture de la machine. La différence de taille est minime, mais elle peut s’accentuer si votre application appelle cette méthode dans une boucle dense avec de nombreuses valeurs différentes.

Le modificateur `in` complète aussi `out` et `ref` d’autres façons. Vous ne pouvez pas créer des surcharges de méthode qui diffèrent seulement par la présence de `in`, `out` ou `ref`. Ces nouvelles règles étendent le même comportement qui a toujours été défini pour les paramètres `out` et `ref`. Comme les modificateurs `out` et `ref`, les types valeur ne sont pas convertis (boxed), car le modificateur `in` est appliqué.

Le modificateur `in` peut être appliqué à tout membre acceptant des paramètres : méthodes, délégués, expressions lambda, fonctions locales, indexeurs, opérateurs.

Une autre caractéristique des paramètres `in` est que vous pouvez utiliser des valeurs littérales ou des constantes pour l’argument d’un paramètre `in`. Par ailleurs, contrairement à un paramètre `ref` ou `out`, il est inutile d’appliquer le modificateur `in` au niveau du site d’appel. Le code suivant donne deux exemples d’appel de la méthode `CalculateDistance`. Le premier utilise deux variables locales passées par référence. La deuxième inclut une variable temporaire créée dans le cadre de l’appel de méthode.

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#UseInArgument "Specifying an In argument")]

Le compilateur garantit la nature « en lecture seule » d’un argument `in` de plusieurs façons.  Premièrement, la méthode appelée ne peut rien assigner directement à un paramètre `in`. Elle ne peut rien assigner directement à un champ d’un paramètre `in` quand cette valeur est un type `struct`. De plus, vous ne pouvez pas passer un paramètre `in` à une méthode en utilisant le modificateur `ref` ou `out`.
Ces règles s’appliquent à tout champ d’un paramètre `in`, dans la mesure où le champ est un type `struct` et le paramètre également un type `struct`. En fait, ces règles s’appliquent à plusieurs couches d’accès au membre, dans la mesure où les types situés à tous les niveaux d’accès au membre sont des `structs`.
Le compilateur considère que les types `struct` passés en tant qu’arguments `in` et leurs membres `struct` sont des variables en lecture seule quand ils sont utilisés en tant qu’arguments pour d’autres méthodes.

L’utilisation de paramètres `in` peut éviter les coûts potentiels en termes de performances qui sont liés aux copies. Elle ne change pas la sémantique des appels de méthode. Ainsi, vous n’avez pas besoin de spécifier le modificateur `in` à l’endroit de l’appel. L’omission du modificateur `in` à l’endroit de l’appel indique au compilateur qu’il est autorisé à effectuer une copie de l’argument pour les raisons suivantes :

- Il existe une conversion implicite, mais pas une conversion d’identité du type de l’argument en type du paramètre.
- L’argument est une expression, mais ne dispose pas d’une variable de stockage connue.
- Il existe une surcharge qui diffère selon la présence ou l’absence de `in`. Dans ce cas, la surcharge par valeur convient mieux.

Ces règles s’avèrent utiles quand vous mettez à jour le code existant pour utiliser des arguments de référence en lecture seule. À l’intérieur de la méthode appelée, vous pouvez appeler toute méthode d’instance qui utilise des paramètres par valeur. Dans ces instances, une copie du paramètre `in` est créée. Étant donné que le compilateur peut créer une variable temporaire pour un paramètre `in`, vous pouvez aussi spécifier des valeurs par défaut pour n’importe quel paramètre `in`. Le code suivant spécifie l’origine (point 0,0) comme valeur par défaut du deuxième point :

[!code-csharp[InArgumentDefault](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Pour forcer le compilateur à passer des arguments en lecture seule par référence, spécifiez le modificateur `in` sur les arguments à l’endroit de l’appel, comme indiqué dans le code suivant :

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ExplicitInArgument "Specifying an In argument")]

Ce comportement facilite l’adoption de paramètres `in` au fil du temps dans les codes bases volumineux où des gains de performance sont possibles. Vous commencez par ajouter le modificateur `in` aux signatures de méthode. Ensuite, vous pouvez ajouter le modificateur `in` aux endroits des appels et créer des types `readonly struct` pour permettre au compilateur d’éviter de créer des copies défensives des paramètres `in` à d’autres emplacements.

La désignation du paramètre `in` peut également être utilisée avec des types référence ou des valeurs numériques. Toutefois, les avantages dans les deux cas sont minimes, voire inexistants.

## <a name="never-use-mutable-structs-as-in-in-argument"></a>N’utilisez jamais des structs mutables comme argument `in`

Les techniques décrites ci-dessus expliquent comment éviter les copies en retournant des références et en passant les valeurs par référence. Ces techniques conviennent le mieux quand les types d’arguments sont déclarés comme types `readonly struct`. Sinon, le compilateur doit créer des **copies défensives** dans de nombreuses situations pour garantir la nature « en lecture seule » des arguments. Considérons l’exemple suivant, qui calcule la distance d’un point 3D depuis l’origine :

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

La structure `Point3D` n’est *pas* un struct en lecture seule. Il y a six appels différents d’accès aux propriétés dans le corps de cette méthode. En première approche, vous pouvez penser que ces accès sont sécurisés. Après tout, un accesseur `get` ne devrait pas modifier l’état de l’objet. Mais il n’existe aucune règle du langage qui le garantisse. Il s’agit seulement d’une convention courante. N’importe quel type peut implémenter un accesseur `get` qui a modifié l’état interne. Sans garantie fournie par le langage, le compilateur doit créer une copie temporaire de l’argument avant d’appeler un membre. Le stockage temporaire est créé sur la pile, les valeurs de l’argument sont copiées dans le stockage temporaire et la valeur est copiée sur la pile pour chaque accès au membre en tant qu’argument `this`. Dans de nombreux cas, ces copies nuisent suffisamment aux performances pour que ce passage par valeur soit plus rapide qu’un passage par référence en lecture seule quand le type d’argument n’est pas un `readonly struct`.

Au lieu de cela, si le calcul de la distance utilise le struct immuable, `ReadonlyPoint3D`, les objets temporaires ne sont pas nécessaires :

[!code-csharp[readonlyInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ReadOnlyInArgument "Specifying a readonly in argument")]

Le compilateur génère du code plus efficace lorsque vous appelez les membres d’un `readonly struct`: la référence `this`, au lieu d’une copie du récepteur, est toujours un paramètre `in` passé par référence à la méthode membre. Cette optimisation évite la copie quand vous utilisez un `readonly struct` comme argument `in`.

Vous ne devez pas passer un type valeur Nullable en tant qu’argument `in`. Le type de <xref:System.Nullable%601> n’est pas déclaré en tant que struct en lecture seule. Cela signifie que le compilateur doit générer des copies défensives pour tout argument de type valeur nullable passé à une méthode à l’aide du modificateur `in` sur la déclaration de paramètre.

Vous pouvez voir un exemple de programme qui illustre les différences de performances à l’aide de [BenchmarkDotNet](https://www.nuget.org/packages/BenchmarkDotNet/) dans notre [référentiel d’exemples](https://github.com/dotnet/samples/tree/master/csharp/safe-efficient-code/benchmark) sur GitHub. Il compare le passage d’un struct mutable par valeur et par référence au passage d’un struct immuable par valeur et par référence. L’utilisation du struct immuable et le passage par référence est le plus rapide.

## <a name="use-ref-struct-types-to-work-with-blocks-or-memory-on-a-single-stack-frame"></a>Utilisez des types `ref struct` pour travailler avec des blocs ou de la mémoire sur un frame de pile

Une autre fonctionnalité associée du langage est la possibilité de déclarer un type valeur qui doit être contraint à un seul frame de pile. Cette restriction permet au compilateur d’effectuer plusieurs optimisations. Cette fonctionnalité vise principalement <xref:System.Span%601> et ses structures associées. Vous obtiendrez de meilleures performances de ces améliorations en utilisant les API .NET nouvelles et mises à jour, qui facilitent l’utilisation du type <xref:System.Span%601>.

Vous pouvez avoir des exigences similaires quand vous utilisez de la mémoire créée avec [`stackalloc`](language-reference/operators/stackalloc.md) ou de la mémoire provenant d’API d’interopérabilité. Pour répondre à ces besoins, vous pouvez définir vos propres types `ref struct`.

## <a name="readonly-ref-struct-type"></a>Type`readonly ref struct`

La déclaration d’un struct comme `readonly ref` combine les avantages et les restrictions des déclarations `ref struct` et `readonly struct`. La mémoire utilisée par l’étendue en lecture seule est limitée à un seul frame de pile, et cette mémoire ne peut pas être modifiée.

## <a name="conclusions"></a>Conclusions

L’utilisation de types valeur réduit le nombre d’opérations d’allocation :

- Le stockage pour les types valeur est alloué sur la pile les variables locales et les arguments de méthode.
- Le stockage pour les types valeur qui sont membres d’autres objets est alloué dans le cadre de cet objet, et non pas comme allocation distincte.
- Le stockage pour les valeurs de retour de type valeur est alloué sur la pile.

Comparez cela avec les types référence dans ces mêmes situations :

- Le stockage pour les types référence est alloué sur le tas pour les variables locales et les arguments de méthode. La référence est stockée sur la pile.
- Le stockage pour les types référence qui sont membres d’autres objets sont alloués séparément sur le tas. L’objet conteneur stocke la référence.
- Le stockage des valeurs de retour de type référence est alloué sur le tas. La référence à ce stockage est stockée sur la pile.

La réduction des allocations entraîne des compromis. Vous copiez plus de mémoire quand la taille du `struct` est supérieure à la taille d’une référence. Une référence est généralement sur 64 ou 32 bits, et elle varie en fonction de l’UC de la machine cible.

Ces compromis ont généralement un impact minimal sur les performances. Cependant, pour les grands structs ou des collections plus grandes, l’impact sur les performances augmente. L’impact peut être important dans des boucles denses et des chemins d’exécution intensifs pour les programmes.

Ces améliorations apportées au langage C# sont conçues pour les algorithmes dont les performances sont critiques, dans lesquels la réduction des allocations mémoire est un facteur essentiel pour atteindre le niveau de performance nécessaire. Vous constaterez peut-être que vous n’utilisez pas souvent ces fonctionnalités dans votre code. Cependant, ces améliorations ont été adoptées dans .NET. Comme de plus en plus d’API adoptent ces fonctionnalités, vous verrez les performances de vos applications s’améliorer.

## <a name="see-also"></a>Voir aussi

- [ref, mot clé](language-reference/keywords/ref.md)
- [Retours ref et variables locales ref](programming-guide/classes-and-structs/ref-returns.md)
