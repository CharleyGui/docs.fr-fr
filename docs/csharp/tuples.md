---
title: Types tuple - Guide C#
description: En savoir plus sur les types tuple nommés et sans nom en C#
ms.date: 05/15/2018
ms.technology: csharp-fundamentals
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: 497f95811677c300e1fadad65eb495dced7f2da3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374614"
---
# <a name="c-tuple-types"></a>Types tuple C#

Les tuples C# sont des types que vous définissez à l’aide d’une syntaxe simplifiée. Les avantages incluent une syntaxe simplifiée, des règles de conversion basées sur le nombre (appelé « cardinalité ») et les types d’éléments, ainsi que des règles cohérentes pour les copies, les tests d’égalité et les affectations. En échange, les tuples ne prennent pas en charge certains idiomes orientés objet associés à l’héritage. Vous pouvez bénéficier d’une présentation des tuples dans la section correspondante de l’article [Nouveautés de C# 7.0](whats-new/csharp-7.md#tuples).

Dans cet article, vous allez apprendre les règles de langage régissant les tuples dans C# 7.0 et ultérieur, découvrir différentes façons de les utiliser et bénéficier de conseils de base sur l’utilisation des tuples.

> [!NOTE]
> Les nouvelles fonctionnalités des tuples exigent les types <xref:System.ValueTuple>.
> Vous devez ajouter le package NuGet [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) pour pouvoir l’utiliser sur des plateformes qui n’incluent pas les types.
>
> Ces fonctionnalités sont semblables à celles d’autres langages qui reposent sur les types fournis dans le framework. `async` et `await` qui reposent sur l’interface `INotifyCompletion`, et LINQ qui repose sur `IEnumerable<T>` en sont des exemples. Toutefois, le mécanisme de remise change à mesure que le .NET dépend de moins en moins de la plateforme. Le .NET Framework n’est pas toujours émis à la même cadence que le compilateur de langage. Quand les nouvelles fonctionnalités de langage reposent sur de nouveaux types, ces types sont disponibles sous la forme de packages NuGet au moment de l’émission des fonctionnalités de langage. À mesure que ces nouveaux types sont ajoutés à l’API .NET Standard et remis dans le cadre du framework, les packages NuGet ne sont plus obligatoires.

Commençons par passer en revue les raisons d’ajouter la nouvelle prise en charge des tuples. Les méthodes retournent un objet unique. Les tuples vous permettent d’empaqueter plus aisément plusieurs valeurs dans cet objet unique.

Le .NET Framework possède déjà des classes `Tuple` génériques. Ces classes, toutefois, présentaient deux limitations majeures. Premièrement, les classes `Tuple` nommaient leurs propriétés `Item1`, `Item2`, etc. Ces noms ne comportent aucune information sémantique. L’utilisation de ces types `Tuple` ne permet pas de communiquer la signification de chacune de ces propriétés. Les nouvelles fonctionnalités de langage vous permettent de déclarer et d’utiliser des noms sémantiquement explicites pour les éléments d’un tuple.

Les classes `Tuple` entraînent des problèmes de performances car elles sont des types référence. Utiliser un des types `Tuple` signifie allouer des objets. Sur des chemins réactifs, l’allocation de nombreux petits objets peut avoir un impact mesurable sur les performances de votre application. Par conséquent, la prise en charge du langage pour les tuples tire parti des nouveaux structs `ValueTuple`.

Pour éviter ces faiblesses, vous pouvez créer une `class` ou un `struct` pour fournir plusieurs éléments. Malheureusement, cela génère un surplus de travail et masque votre intention de conception. La création d’un `struct` ou d’une `class` implique la définition d’un type avec des données et un comportement. Souvent, vous souhaitez simplement stocker plusieurs valeurs dans un objet unique.

Les fonctionnalités du langage et les structs génériques `ValueTuple` appliquent la règle stipulant que vous ne pouvez pas ajouter de comportement (méthodes) à ces types tuple.
Tous les types `ValueTuple` sont des *structs mutables*. Chaque champ de membre est un champ public. Cela les rend très légers. Toutefois, cela signifie que les tuples ne doivent pas être utilisés quand l’immuabilité est importante.

Les tuples sont des conteneurs de données plus simples et plus flexibles que les types `class` et `struct`. Examinons ces différences.

## <a name="named-and-unnamed-tuples"></a>Tuples nommés et sans nom

Le struct `ValueTuple` possède des champs nommés `Item1`, `Item2`, `Item3`, etc., similaires aux propriétés définies dans les types `Tuple` existants.
Ces noms sont les seuls noms que vous pouvez utiliser pour les *tuples sans nom*. Quand vous ne fournissez pas de nom de champ alternatif à un tuple, vous avez créé un tuple sans nom :

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

Le tuple de l’exemple précédent a été initialisé à l’aide de constantes littérales et n’a pas de noms d’éléments créés à l’aide de *projections de nom de champ de tuple* en C# 7,1.

Toutefois, quand vous initialisez un tuple, vous pouvez utiliser les nouvelles fonctionnalités de langage qui donnent de meilleurs noms aux différents champs. Cette opération crée un *tuple nommé*.
Les tuples nommés ont toujours des éléments appelés `Item1`, `Item2`, `Item3`, etc.
Cependant, ils ont également des synonymes pour tous les éléments que vous avez nommés.
Vous créez un tuple nommé en spécifiant le nom de chaque élément. Une méthode consiste à spécifier les noms dans le cadre de l’initialisation du tuple :

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/program.cs#02_NamedTuple "Named tuple")]

Ces synonymes sont gérés par le compilateur et le langage pour vous permettre d’utiliser efficacement les tuples nommés. Les IDE et les éditeurs peuvent lire ces noms sémantiques à l’aide des API Roslyn. Vous pouvez référencer les éléments d’un tuple nommé par ces noms sémantiques n’importe où dans le même assembly. Le compilateur remplace les noms que vous avez définis par les équivalents `Item*` lors de la génération de la sortie compilée. Le langage MSIL (Microsoft Intermediate Language) compilé n’inclut pas les noms que vous avez donnés à ces éléments.

À partir de C# 7.1, les noms de champ d’un tuple peuvent être fournis à partir de variables utilisées pour initialiser le tuple. Ils sont appelés **[initialiseurs de projection de tuple](#tuple-projection-initializers)**. Le code suivant crée un tuple nommé `accumulation` avec les éléments `count` (un entier) et `sum` (un double).

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectedTupleNames "Named tuple")]

Le compilateur doit communiquer les noms que vous avez créés pour les tuples qui sont retournés à partir des propriétés et méthodes publiques. Dans ces cas, le compilateur ajoute un attribut <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> sur la méthode. Cet attribut contient une propriété de liste <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> qui contient les noms attribués à chacun des éléments du tuple.

> [!NOTE]
> Les outils de développement, tels que Visual Studio, lisent également ces métadonnées et fournissent IntelliSense et d’autres fonctionnalités qui utilisent les noms des champs de métadonnées.

Il est important de comprendre les notions de base sous-jacentes des nouveaux tuples et du type `ValueTuple` afin de comprendre les règles d’affectation des tuples nommés entre eux.

## <a name="tuple-projection-initializers"></a>Initialiseurs de projection de tuple

En général, les initialiseurs de projection de tuple fonctionnent en utilisant les noms de champ ou de variable de la partie droite d’une instruction d’initialisation de tuple.
Si un nom explicite est fourni, il est prioritaire sur n’importe quel nom projeté. Par exemple, dans l’initialiseur suivant, les éléments sont `explicitFieldOne` et `explicitFieldTwo`, et non `localVariableOne` et `localVariableTwo`:

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

Pour tous les champs où un nom explicite n’est pas spécifié, un nom implicite applicable est projeté. Il n’existe aucune obligation de fournir des noms sémantiques, explicitement ou implicitement. L’initialiseur suivant a des noms de champ `Item1` dont la valeur est `42`, et `stringContent` dont la valeur est « The answer to everything » :

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/program.cs#MixedTuple "mixed tuple")]

Il existe deux conditions où les noms de champ de candidat ne sont pas projetés sur le champ de tuple :

1. Lorsque le nom du candidat est un nom de tuple réservé. Exemples : `Item3` , `ToString` ou `Rest` .
1. Lorsque le nom du candidat est un doublon d’un autre nom de champ de tuple, explicite ou implicite.

Ces conditions évitent toute ambiguïté. Ces noms provoqueraient une ambiguïté s’ils étaient utilisés comme noms de champ pour un champ dans un tuple. Aucune de ces conditions n’entraîne d’erreur au moment de la compilation. Au lieu de cela, les éléments sans noms projetés n’ont pas de noms sémantiques projetés.  Les exemples suivants illustrent ces conditions :

[!code-csharp-interactive[Ambiguity](../../samples/snippets/csharp/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

Ces cas de figure n’entraînent aucune erreur du compilateur, car ce serait une modification avec rupture du code écrit en C# 7.0 si les projections de nom de champ de tuple n’étaient pas disponibles.

## <a name="equality-and-tuples"></a>Égalité et tuples

À compter de C# 7.3, les types tuple prennent en charge les opérateurs `==` et `!=`. Ces opérateurs fonctionnent en comparant, dans l’ordre, chaque membre de l’argument de gauche à chaque membre de l’argument de droite. Ces comparaisons se court-circuitent. Elles arrêtent l’évaluation des membres dès qu’une paire n’est pas égale. Les exemples de code suivants utilisent `==`, mais toutes les règles de comparaison s’appliquent à `!=`. L’exemple de code suivant montre une comparaison d’égalité pour deux paires d’entiers :

[!code-csharp-interactive[TupleEquality](../../samples/snippets/csharp/tuples/program.cs#Equality "Testing tuples for equality")]

Il existe plusieurs règles qui rendent les tests d’égalité de tuple plus pratiques. L’égalité de tuple effectue des [conversions de type «lifted»](~/_csharplang/spec/conversions.md#lifted-conversion-operators) si un des tuples est un tuple nullable, comme indiqué dans le code suivant :

[!code-csharp-interactive[NullableTupleEquality](../../samples/snippets/csharp/tuples/program.cs#NullableEquality "Comparing Tuples and nullable tuples")]

L’égalité de tuple effectue également des conversions implicites sur chaque membre de deux tuples. Cela inclut les conversions « lifted », les conversions étendues ou d’autres conversions implicites. Les exemples suivants montrent qu'un tuple entier à 2 éléments peut être comparé à un tuple long à 2 éléments en raison de la conversion implicite d'entier à long :

[!code-csharp-interactive[SnippetMemberConversions](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberConversions "converting tuples for equality tests")]

Les noms des membres du tuple ne participent pas aux tests d'égalité. Cependant, si l'un des opérandes est un tuple littéral avec des noms explicites, le compilateur génère une alerte CS8383 si ces noms ne correspondent pas aux noms des autres opérandes.
Si les deux opérandes sont des tuples littéraux, l'avertissement est généré pour l'opérande de droite, comme le montre l'exemple ci-dessous :

[!code-csharp-interactive[MemberNames](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberNames "Tuple member names do not participate in equality tests")]

Enfin, les tuples peuvent contenir des tuples imbriqués. L’égalité de tuple compare la « forme » de chaque opérande via des tuples imbriqués, comme le montre l’exemple suivant :

[!code-csharp-interactive[NestedTuples](../../samples/snippets/csharp/tuples/program.cs#SnippetNestedTuples "Tuples may contain nested tuples that participate in tuple equality.")]

Comparer deux tuples pour vérifier leur égalité (ou leur inégalité) lorsqu’ils ont des formes différentes est une erreur de compilation. Le compilateur ne tentera pas de déconstruire des tuples imbriqués afin de les comparer.

## <a name="assignment-and-tuples"></a>Affectation et tuples

Le langage prend en charge l’affectation entre les types de tuples ayant le même nombre d’éléments, où chaque élément de la partie droite peut être converti implicitement en son élément correspondant de la partie gauche. D’autres conversions ne sont pas prises en compte pour les affectations. Affecter un tuple à un autre lorsqu’ils ont des formes différentes est une erreur de compilation. Le compilateur ne tentera pas de déconstruire des tuples imbriqués afin de les affecter.
Examinons les types d’affectation qui sont autorisés entre les types tuple.

Prenez en compte les variables utilisées dans les exemples suivants :

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/program.cs#03_VariableCreation "Variable creation")]

Les deux premières variables, `unnamed` et `anonymous`, n’ont pas de noms sémantiques fournis pour les éléments. Les noms des champs sont `Item1` et `Item2`.
Les deux dernières variables, `named` et `differentName`, ont des noms sémantiques fournis pour les éléments. Ces deux tuples ont des noms différents pour les éléments.

Ces quatre tuples ont le même nombre d’éléments (appelé « cardinalité ») et les types de ces éléments sont identiques. Par conséquent, toutes ces affectations fonctionnent :

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/program.cs#04_VariableAssignment "Variable assignment")]

Notez que les noms des tuples ne sont pas affectés. Les valeurs des éléments sont affectées suivant l’ordre des éléments dans le tuple.

Des tuples de types différents ou n’ayant pas le même nombre d’éléments ne sont pas attribuables :

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Tuples comme valeurs de retour de méthode

L’une des utilisations les plus courantes des tuples est en tant que valeur de retour de méthode. Examinons en détail un exemple. Considérons cette méthode qui calcule l’écart type d’une suite de nombres :

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> Ces exemples calculent l’écart-type empirique non corrigé.
> La formule de l’écart-type empirique corrigé diviserait la somme des écarts au carré par rapport à la moyenne par (N-1) au lieu de N, comme avec la méthode d’extension `Average`. Pour plus d’informations sur les différences entre ces formules de calcul d’écart-type, consultez un texte de statistiques.

Le code précédent utilise la formule classique de calcul de l’écart-type. Elle génère la réponse correcte, mais constitue une implémentation peu efficace. Cette méthode énumère deux fois la suite : une fois pour générer la moyenne et une fois pour générer la moyenne quadratique des écarts par rapport à la moyenne.
(Souvenez-vous que les requêtes LINQ sont évaluées de manière différée, de sorte que le calcul des écarts par rapport à la moyenne et de la moyenne de ces écarts effectue une seule énumération.)

Il existe une formule alternative qui calcule l’écart-type à l’aide d’une seule énumération de la suite.  Ce calcul génère deux valeurs en énumérant la suite : la somme de tous les éléments de la suite et la somme de chaque valeur au carré :

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

Cette version énumère une seule fois la séquence. Toutefois, ce code n’est pas réutilisable. En poursuivant votre travail, vous trouverez que de nombreux calculs statistiques différents utilisent le nombre d’éléments dans la suite, la somme de la suite et la somme des carrés de la suite. Refactorisons cette méthode et écrivons une méthode utilitaire qui génère ces trois valeurs. Les trois valeurs peuvent toutes être retournées sous forme de tuple.

Mettons à jour cette méthode afin de stocker dans un tuple les trois valeurs calculées pendant l’énumération. La version suivante est créée :

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

La prise en charge de la refactorisation par Visual Studio facilite l’extraction des fonctionnalités pour les statistiques principales dans une méthode privée. Cela vous donne une méthode `private static` qui retourne le type tuple avec les trois valeurs de `Sum`, `SumOfSquares` et `Count` :

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]

Le langage met à votre disposition plusieurs autres options, si vous souhaitez apporter quelques modifications rapides à la main. Tout d’abord, vous pouvez utiliser la déclaration `var` pour initialiser le résultat de tuple à partir de l’appel de la méthode `ComputeSumAndSumOfSquares`. Vous pouvez également créer trois variables discrètes à l’intérieur de la méthode `ComputeSumAndSumOfSquares`. Le code suivant montre la version finale :

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

Cette version finale peut être utilisée pour toute méthode qui a besoin de ces trois valeurs ou d’un sous-ensemble quelconque d’entre elles.

Le langage prend en charge d’autres options pour gérer les noms des éléments dans ces méthodes retournant des tuples.

Vous pouvez supprimer les noms des champs de la déclaration de la valeur de retour et retourner un tuple sans nom :

```csharp
private static (double, double, int) ComputeSumAndSumOfSquares(IEnumerable<double> sequence)
{
    double sum = 0;
    double sumOfSquares = 0;
    int count = 0;

    foreach (var item in sequence)
    {
        count++;
        sum += item;
        sumOfSquares += item * item;
    }

    return (sum, sumOfSquares, count);
}
```

Les champs de ce tuple sont nommés `Item1`, `Item2`, et `Item3`.
Il est recommandé de fournir des noms sémantiques aux éléments de tuples retournés par les méthodes.

Un autre idiome pour lequel les tuples peuvent être très utiles est lorsque vous créez des requêtes LINQ. Le résultat final est une projection qui contient certaines propriétés des objets sélectionnés, mais pas toutes.

En règle générale, vous devez projeter les résultats de la requête dans une suite d’objets constituant un type anonyme. Cela présentait de nombreuses limitations, principalement parce que les types anonymes ne pouvaient pas facilement être nommés dans le type de retour pour une méthode. Des coûts importants accompagnaient les alternatives utilisant `object` ou `dynamic` comme type du résultat.

Il est aisé de retourner une séquence d’un type tuple, et les noms et types des éléments sont disponibles au moment de la compilation et via les outils de l’IDE.
Considérons, par exemple, une application d’agenda. Vous pouvez définir une classe similaire à la suivante pour représenter une entrée unique dans la liste des tâches :

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

Vos applications mobiles peuvent prendre en charge une forme compacte des éléments de tâche en cours qui affiche uniquement le titre. Cette requête LINQ effectuerait une projection incluant uniquement l’ID et le titre. Une méthode retournant une suite de tuples exprime bien cette conception :

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> Dans C# 7.1, les projections de tuple vous permettent de créer des tuples nommés à l’aide d’éléments, d’une manière semblable au nommage des propriétés dans les types anonymes. Dans le code ci-dessus, l’instruction `select` dans la projection de requête crée un tuple qui a les éléments `ID` et `Title`.

Le tuple nommé peut faire partie de la signature. Il permet au compilateur et aux outils de l’IDE de vérifier de façon statique que vous utilisez correctement le résultat. Le tuple nommé contient également les informations de type statique, si bien qu’il n’est pas nécessaire d’utiliser des fonctionnalités d’exécution coûteuses telles que la réflexion ou la liaison dynamique pour utiliser les résultats.

## <a name="deconstruction"></a>Déconstruction

Vous pouvez désassembler tous les éléments d’un tuple en *déconstruisant* le tuple retourné par une méthode. Il existe trois approches différentes de la déconstruction des tuples.  Tout d’abord, vous pouvez déclarer explicitement le type de chacun des champs à l’intérieur des parenthèses afin de créer des variables discrètes pour tous les éléments du tuple :

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

Vous pouvez également déclarer des variables implicitement typées pour chaque champ d’un tuple à l’aide du mot clé `var` en dehors des parenthèses :

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

Il est également possible d’utiliser le mot clé `var` avec une ou toutes les déclarations de variables à l’intérieur des parenthèses.

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

Vous ne pouvez pas utiliser un type spécifique en dehors des parenthèses, même si tous les champs du tuple ont le même type.

Vous pouvez également déconstruire des tuple avec des déclarations existantes :

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
> Vous ne pouvez pas mélanger des déclarations existantes avec des déclarations à l’intérieur des parenthèses. Par exemple, ce qui suit n’est pas autorisé : `(var x, y) = MyMethod();`. L’erreur CS8184 est générée, car *x* est déclaré à l’intérieur des parenthèses et *y* a été précédemment déclaré ailleurs.

### <a name="deconstructing-user-defined-types"></a>Déconstruction de types définis par l’utilisateur

N’importe quel type tuple peut être déconstruit comme indiqué ci-dessus. Il est également facile d’activer la déconstruction sur n’importe quel type défini par l’utilisateur (classes, structs ou même interfaces).

L’auteur du type peut définir une ou plusieurs `Deconstruct` méthodes qui affectent des valeurs à un nombre quelconque de [ `out` variables](language-reference/keywords/out-parameter-modifier.md) représentant les éléments de données qui composent le type. Par exemple, le type `Person` suivant définit une méthode `Deconstruct` qui déconstruit un objet person en éléments représentant le prénom et le nom de famille :

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

La méthode deconstruct permet l’attribution à partir d’un objet `Person` de deux chaînes représentant les propriétés `FirstName` et `LastName` :

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

Vous pouvez activer la déconstruction même pour des types que vous n’avez pas créés.
La méthode `Deconstruct` peut être une méthode d’extension qui désassemble les membres de données accessibles d’un objet. L’exemple ci-dessous montre un type `Student`, dérivé du type `Person`, et une méthode d’extension qui déconstruit un objet `Student` en trois variables, qui représentent les propriétés `FirstName`, `LastName` et `GPA` :

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

Un objet `Student` a désormais deux méthodes `Deconstruct` accessibles : la méthode d’extension déclarée pour les types `Student` et le membre du type `Person`. Les deux sont dans la portée et cela permet à un objet `Student` d’être déconstruit en deux ou trois variables.
Si vous affectez un étudiant à trois variables, le prénom, le nom de famille et la moyenne pondérée cumulative (GPA) sont tous retournés. Si vous affectez un étudiant à deux variables, seuls le prénom et le nom de famille sont retournés.

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

Vous devez être prudent en définissant plusieurs méthodes `Deconstruct` dans une classe ou une hiérarchie de classes. Plusieurs méthodes `Deconstruct` ayant le même nombre de paramètres `out` peuvent rapidement entraîner des ambiguïtés. Les appelants peuvent ne pas être en mesure d’appeler facilement la méthode `Deconstruct` souhaitée.

Cet exemple présente un risque minimal d’appel ambigu, car la méthode `Deconstruct` pour `Person` a deux paramètres de sortie, et la méthode `Deconstruct` pour `Student` en a trois.

Les opérateurs de déconstruction ne participent pas aux tests d’égalité. L’exemple suivant génère une erreur de compilation CS0019 :

```csharp
Person p = new Person("Althea", "Goodwin");
if (("Althea", "Goodwin") == p)
    Console.WriteLine(p);
```

La méthode `Deconstruct` pourrait convertir l’objet `Person``p` en un tuple contenant les deux chaînes, mais elle ne s’applique pas dans le contexte des tests d’égalité.

## <a name="tuples-as-out-parameters"></a>Tuples en tant que paramètres de sortie

Les tuples peuvent être utilisés en tant que [ `out` paramètres](language-reference/keywords/out-parameter-modifier.md) *.* À ne pas confondre avec toute ambiguïté mentionnée précédemment dans la section de [déconstruction](#deconstruction) . Dans un appel de méthode, vous devez uniquement décrire la forme du tuple :

[!code-csharp[TuplesAsOutParameters](~/samples/snippets/csharp/tuples/program.cs#01_TupleAsOutVariable "Tuples as out parameters")]

Vous pouvez également utiliser un Tuple [_sans nom_](#named-and-unnamed-tuples) et faire référence à ses champs comme `Item1` et `Item2` :

```csharp
dict.TryGetValue(2, out (int, string) pair);
// ...
Console.WriteLine($"{pair.Item1}: {pair.Item2}");
```

## <a name="conclusion"></a>Conclusion

La nouvelle prise en charge du langage et de la bibliothèque pour les tuples nommés facilite grandement l’utilisation de conceptions utilisant des structures de données qui stockent plusieurs éléments mais ne définissent pas de comportement, telles que les classes et les structs. Il est facile et rapide d’utiliser des tuples pour ces types. Vous obtenez tous les avantages d’une vérification de type statique, sans avoir à créer de types au moyen de la syntaxe `class` ou `struct` plus détaillée. Même ainsi, ils sont particulièrement utiles pour les méthodes utilitaires `private` ou `internal`. Créez des types définis par l’utilisateur, des types `class` ou `struct`, quand vos méthodes publiques retournent une valeur comportant plusieurs éléments.
