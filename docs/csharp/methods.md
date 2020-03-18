---
title: Méthodes - Guide du C#
description: Vue d’ensemble des méthodes, des paramètres de méthode et des valeurs de retour des méthodes
ms.technology: csharp-fundamentals
ms.date: 05/21/2018
ms.assetid: 577a8527-1081-4b36-9b9e-0685b6553c6e
ms.openlocfilehash: f44c83408e884d76eef5e2b5abbca511fbae2a1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399447"
---
# <a name="methods"></a>Méthodes

Une méthode est un bloc de code qui contient une série d'instructions. Un programme provoque l'exécution des instructions en appelant la méthode et en spécifiant les éventuels arguments de méthode requis. En C#, chaque instruction exécutée est effectuée dans le contexte d'une méthode. La méthode `Main` est le point d’entrée de chaque application C# et elle est appelée par le Common Language Runtime (CLR) au démarrage du programme.

> [!NOTE]
> Cette rubrique décrit les méthodes nommées. Pour plus d’informations sur les fonctions anonymes, consultez [Fonctions anonymes](programming-guide/statements-expressions-operators/anonymous-functions.md).

<a name="signatures"></a>

## <a name="method-signatures"></a>Signatures de méthode

Les méthodes sont déclarées dans une `class` ou une `struct` en spécifiant :

- Un niveau d’accès facultatif, comme `public` ou `private`. Par défaut, il s’agit de `private`.
- Des modificateurs facultatifs, comme `abstract` ou `sealed`.
- La valeur de retour, ou `void` si la méthode n’en a pas.
- Le nom de la méthode.
- Des paramètres de méthodes. Les paramètres de méthode sont placés entre parenthèses et séparés par des virgules. Des parenthèses vides indiquent que la méthode ne requiert aucun paramètre.

Ces parties forment ensemble la signature de la méthode.

> [!NOTE]
> Un type de retour d'une méthode ne fait pas partie de la signature de la méthode à des fins de surcharge de méthode. Toutefois, il fait partie de la signature de la méthode lors de la détermination de la compatibilité entre un délégué et la méthode vers laquelle il pointe.

L’exemple suivant définit une classe nommée `Motorcycle` qui contient cinq méthodes :

[!code-csharp[csSnippets.Methods#40](../../samples/snippets/csharp/concepts/methods/methods40.cs#40)]

Notez que la classe `Motorcycle` inclut une méthode surchargée, `Drive`. Deux méthodes ont le même nom, mais doivent être différenciées par leurs types de paramètre.

<a name="invocation"></a>

## <a name="method-invocation"></a>Appel de méthode

Les méthodes peuvent être *d’instance* ou *statiques*. L’appel d’une méthode d’instance nécessite l’instanciation d’un objet et l’appel de la méthode sur cet objet ; une méthode d’instance agit sur cette instance et sur ses données. Vous appelez une méthode statique en référençant le nom du type auquel la méthode appartient ; les méthodes statiques n’agissent pas sur les données d’une instance. Une tentative d’appeler une méthode statique via une instance d’objet génère une erreur du compilateur.

Appeler une méthode est comme accéder à un champ. Après le nom d’objet (si vous appelez une méthode d’instance) ou le nom de type (si vous appelez une méthode `static`), ajoutez un point, le nom de la méthode et des parenthèses. Les arguments sont répertoriés entre les parenthèses et séparés par des virgules.

La définition de la méthode spécifie les noms et types des paramètres requis. Quand un appelant appelle la méthode, il fournit des valeurs réelles, appelées « arguments », pour chaque paramètre. Les arguments doivent être compatibles avec le type de paramètre, mais le nom de l’argument, si un nom est utilisé dans le code appelant, ne doit pas nécessairement être le même que celui du paramètre défini dans la méthode. Dans l’exemple suivant, la méthode `Square` comprend un seul paramètre de type `int` nommé *i*. Le premier appel de la méthode passe à la méthode `Square` une variable de type `int` nommée *num*, le deuxième appel passe une constante numérique et le troisième appel passe une expression.

[!code-csharp[csSnippets.Methods#74](../../samples/snippets/csharp/concepts/methods/params74.cs#74)]

La forme la plus courante des appels de méthode utilise des arguments de position ; elle fournit les arguments dans le même ordre que celui des paramètres de la méthode. Les méthodes de la classe `Motorcycle` peuvent donc être appelées comme dans l’exemple suivant. Par exemple, l’appel à la méthode `Drive` comprend deux arguments qui correspondent aux deux paramètres de la syntaxe de la méthode. Le premier devient la valeur du paramètre `miles` et le deuxième devient la valeur du paramètre `speed`.

[!code-csharp[csSnippets.Methods#41](../../samples/snippets/csharp/concepts/methods/methods40.cs#41)]

Vous pouvez également utiliser des *arguments nommés* au lieu d’arguments positionnels lors de l’appel d’une méthode. Lors de l’utilisation d’arguments nommés, vous spécifiez le nom du paramètre suivi de deux-points (« : ») et de l’argument. Les arguments de la méthode peuvent apparaître dans n’importe quel ordre, dès lors que tous les arguments nécessaires sont présents. L’exemple suivant utilise des arguments nommés pour appeler la méthode `TestMotorcycle.Drive`. Dans cet exemple, les arguments nommés sont passés dans l’ordre inverse de celui de la liste des paramètres de la méthode.

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/named1.cs#45)]

Vous pouvez appeler une méthode en utilisant à la fois des arguments positionnels et des arguments nommés. Cependant, un argument positionnel ne peut pas suivre un argument nommé. L’exemple suivant appelle la méthode `TestMotorcycle.Drive` de l’exemple précédent en utilisant un argument positionnel et un argument nommé.

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/named2.cs#46)]

<a name="inherited"></a>

## <a name="inherited-and-overridden-methods"></a>Méthodes hérités et remplacées

En plus des membres qui sont définis explicitement dans un type, un type hérite des membres définis dans ses classes de base. Comme tous les types du système de types managés héritent directement ou indirectement de la classe <xref:System.Object>, tous les types héritent ses membres, comme <xref:System.Object.Equals(System.Object)>, <xref:System.Object.GetType> et <xref:System.Object.ToString>. L’exemple suivant définit une classe `Person`, instancie deux objets `Person` et appelle la méthode `Person.Equals` pour déterminer si les deux objets sont égaux. La méthode `Equals` n’est cependant pas définie dans la classe `Person` ; elle est héritée de <xref:System.Object>.

[!code-csharp[csSnippets.Methods#104](../../samples/snippets/csharp/concepts/methods/inherited1.cs#104)]

Vous pouvez remplacer des membres hérités par des types en utilisant le mot clé `override` et en fournissant une implémentation de la méthode remplacée. La signature de la méthode doit être identique à celle de la méthode remplacée. L’exemple suivant est semblable au précédent, sauf qu’il remplace la méthode <xref:System.Object.Equals(System.Object)>. (Il remplace aussi la méthode <xref:System.Object.GetHashCode>, car les deux méthodes sont destinées à fournir des résultats cohérents.)

[!code-csharp[csSnippets.Methods#105](../../samples/snippets/csharp/concepts/methods/overridden1.cs#105)]

<a name="passing"></a>

## <a name="passing-parameters"></a>Transmission des paramètres

Les types en C# sont des *types valeur* ou des *types référence*. Pour obtenir la liste des types valeur prédéfinis, consultez [Types et variables](./tour-of-csharp/types-and-variables.md). Par défaut, les types valeur et les types référence sont passés par valeur à une méthode.

<a name="byval"></a>

### <a name="passing-parameters-by-value"></a>Passage de paramètres par valeur

Quand un type valeur est passé par valeur à une méthode, c’est une copie de l’objet, et non pas l’objet lui-même, qui est passée à la méthode. Par conséquent, les modifications de l’objet dans la méthode appelée n’ont pas d’effet sur l’objet d’origine quand le contrôle retourne à l’appelant.

L’exemple suivant passe un type valeur à une méthode par valeur, et la méthode appelée tente de changer la valeur du type valeur. Il définit une variable de type `int`, qui est un type valeur, initialise sa valeur à 20 et la passe à une méthode nommée `ModifyValue` qui change la valeur de la variable en 30. Quand la méthode retourne, la valeur de la variable reste cependant inchangée.

[!code-csharp[csSnippets.Methods#10](../../samples/snippets/csharp/concepts/methods/byvalue10.cs#10)]

Quand un objet d’un type référence est passé par valeur à une méthode, c’est une référence à l’objet qui est passée par valeur. Autrement dit, la méthode ne reçoit pas l’objet lui-même mais un argument qui indique l’emplacement de l’objet. Si vous modifiez un membre de l’objet en utilisant cette référence, la modification est répercutée dans l’objet quand le contrôle retourne à la méthode appelante. Cependant, remplacer l’objet passé à la méthode n’a pas d’effet sur l’objet d’origine quand le contrôle retourne à l’appelant.

L’exemple suivant définit une classe (qui est un type référence) nommée `SampleRefType`. Il instancie un objet `SampleRefType`, affecte la valeur 44 à son champ `value` et passe l’objet à la méthode `ModifyObject`. L’exemple fait essentiellement la même chose que l’exemple précédent : il passe un argument par valeur à une méthode. Cependant, comme il utilise un type référence, le résultat est différent. La modification apportée dans `ModifyObject` au champ `obj.value` change également en 33 le champ `value` de l’argument `rt` dans la méthode `Main`, comme le montre le résultat de l’exemple.

[!code-csharp[csSnippets.Methods#42](../../samples/snippets/csharp/concepts/methods/byvalue42.cs#42)]

<a name="byref"></a>

### <a name="passing-parameters-by-reference"></a>Passage de paramètres par référence

On passe un paramètre par référence quand on souhaite changer la valeur d’un argument dans une méthode et refléter cette modification lorsque le contrôle revient à la méthode appelante. Pour passer un paramètre par [`ref`](language-reference/keywords/ref.md) référence, vous utilisez le ou [`out`](language-reference/keywords/out-parameter-modifier.md) le mot clé. Vous pouvez également passer une valeur par référence pour éviter [`in`](language-reference/keywords/in-parameter-modifier.md) la copie, mais tout de même empêcher les modifications à l’aide du mot clé.

L’exemple suivant est identique au précédent, sauf que la valeur est passée par référence à la méthode `ModifyValue`. Quand la valeur du paramètre est modifiée dans la méthode `ModifyValue`, le changement de la valeur est reflété quand le contrôle retourne à l’appelant.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref106.cs#106)]

Un modèle courant qui utilise des paramètres par référence implique la permutation des valeurs des variables. Vous passez deux variables à une méthode par référence, et la méthode permute leur contenu. L’exemple suivant permute des valeurs d’entier.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/swap107.cs#107)]

Passer un paramètre de type référence vous permet de changer la valeur de la référence elle-même, au lieu de la valeur de ses éléments ou champs individuels.

<a name="paramarray"></a>

### <a name="parameter-arrays"></a>Tableaux de paramètres

Parfois, l’obligation de spécifier le nombre exact d’arguments de votre méthode est restrictive. En utilisant le mot clé `params` pour indiquer qu’un paramètre est un tableau de paramètres, vous permettez que votre méthode soit appelée avec un nombre variable d’arguments. Le paramètre marqué avec le mot clé `params` doit être un type tableau. Ce doit être le dernier paramètre de la liste de paramètres de la méthode.

Un appelant peut alors appeler la méthode de trois façons :

- En passant un tableau du type approprié, qui contient le nombre d’éléments souhaité.
- En passant une liste d’arguments individuels séparés par des virgules et du type approprié à la méthode.
- En ne fournissant pas d’argument au tableau de paramètres.

L’exemple suivant définit une méthode nommée `GetVowels` qui retourne toutes les voyelles à partir d’un tableau de paramètres. La méthode `Main` montre les trois façons d’appeler la méthode. Les appelants n’ont pas nécessairement à fournir tous les arguments pour les paramètres qui incluent le modificateur `params`. Dans ce cas, le paramètre est `null`.

[!code-csharp[csSnippets.Methods#75](~/samples/snippets/csharp/concepts/methods/params75.cs#75)]

<a name="optional"></a>

## <a name="optional-parameters-and-arguments"></a>Paramètres et arguments facultatifs

Une définition de méthode peut spécifier que ses paramètres sont obligatoires ou facultatifs. Par défaut, les paramètres sont obligatoires. Vous spécifiez des paramètres facultatifs en incluant la valeur par défaut du paramètre dans la définition de la méthode. Quand la méthode est appelée, si aucun argument n’est fourni pour un paramètre facultatif, c’est la valeur par défaut qui est utilisée à la place.

La valeur par défaut du paramètre doit être affectée par un des types d’expressions suivants :

- Une constante, comme une chaîne littérale ou un nombre.
- Une expression de la forme `new ValType()`, où `ValType` est un type valeur. Notez que ceci appelle le constructeur sans paramètre implicite du type valeur, qui n’est pas un membre réel du type.
- Une expression de la forme `default(ValType)`, où `ValType` est un type valeur.

Si une méthode comprend à la fois des paramètres obligatoires et des paramètres facultatifs, les paramètres facultatifs sont définis à la fin de la liste des paramètres, après tous les paramètres obligatoires.

L’exemple suivant définit une méthode, `ExampleMethod`, qui a un paramètre obligatoire et deux paramètres facultatifs.

[!code-csharp[csSnippets.Methods#21](../../samples/snippets/csharp/concepts/methods/optional1.cs#21)]

Si une méthode avec plusieurs arguments facultatifs est appelée en utilisant des arguments positionnels, l’appelant doit fournir un argument pour tous les paramètres facultatifs, du premier au dernier pour lequel un argument est fourni. Par exemple, dans le cas de la méthode `ExampleMethod`, si l’appelant fournit un argument pour le paramètre `description`, il doit également en fournir un pour le paramètre `optionalInt`. `opt.ExampleMethod(2, 2, "Addition of 2 and 2");` est un appel de méthode valide. `opt.ExampleMethod(2, , "Addition of 2 and 0");` génère une erreur du compilateur « Argument manquant ».

Si une méthode est appelée en utilisant des arguments nommés ou une combinaison d’arguments positionnels et nommés, l’appelant peut omettre les arguments qui suivent le dernier argument positionnel dans l’appel de la méthode.

L’exemple suivant appelle la méthode `ExampleMethod` trois fois.  Les deux premiers appels de la méthode utilisent des arguments positionnels. Le premier omet les deux arguments facultatifs, tandis que le deuxième omet le dernier argument. Le troisième appel de la méthode fournit un argument positionnel pour le paramètre obligatoire, mais utilise un argument nommé pour fournir une valeur au paramètre `description` tout en omettant l’argument `optionalInt`.

[!code-csharp[csSnippets.Methods#22](../../samples/snippets/csharp/concepts/methods/optional1.cs#22)]

L’utilisation de paramètres facultatifs affecte la *résolution de la surcharge*, qui est la façon dont le compilateur C# détermine quelle surcharge particulière doit être appelée par un appel de méthode, comme suit :

- Une méthode, un indexeur ou un constructeur est un candidat pour l’exécution si chacun de ses paramètres est facultatif ou correspond, par nom ou par position, à un seul argument dans l’instruction appelante, et que cet argument peut être converti vers le type du paramètre.
- Si plusieurs candidats sont trouvés, les règles de résolution de surcharge des conversions préférées sont appliquées aux arguments qui sont explicitement spécifiés. Les arguments omis pour les paramètres facultatifs sont ignorés.
- Si deux candidats sont jugés de qualité équivalente, la préférence va à celui qui n’a pas de paramètres facultatifs pour lesquels des arguments ont été omis dans l’appel. Ceci est une conséquence d’une préférence générale dans la résolution de la surcharge pour les candidats qui ont le moins de paramètres.

<a name="return"></a>

## <a name="return-values"></a>Valeurs retournées

Les méthodes peuvent retourner une valeur à l'appelant. Si le type de retour (le type qui figure avant le nom de la méthode) n’est pas `void`, la méthode peut retourner la valeur en utilisant le mot clé `return`. Une instruction avec le mot clé `return` suivi d’une variable, d’une constante ou d’une expression qui correspond au type de retour retourne cette valeur à l’appelant de la méthode. Les méthodes dotées d'un type de retour non void doivent utiliser le mot clé `return` pour retourner une valeur. Le mot clé `return` arrête également l'exécution de la méthode.

Si le type de retour est `void`, une instruction `return` sans valeur est quand même utile pour arrêter l'exécution de la méthode. Sans le mot clé `return` , la méthode arrête de s'exécuter quand elle atteint la fin du bloc de code.

Par exemple, ces deux méthodes utilisent le mot clé `return` pour retourner des entiers :

[!code-csharp[csSnippets.Methods#44](../../samples/snippets/csharp/concepts/methods/return44.cs#44)]

Pour utiliser une valeur retournée à partir d'une méthode, la méthode d'appel peut utiliser l'appel de méthode proprement dit partout où une valeur du même type peut suffire. Vous pouvez également affecter la valeur de retour à une variable. Par exemple, les deux exemples de code suivants remplissent le même objectif :

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/return44.cs#45)]

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/return44.cs#46)]

L'utilisation d'une variable locale, dans cet exemple, `result`, pour stocker une valeur est facultative. Elle peut favoriser la lisibilité du code ou s'avérer nécessaire si vous avez besoin de stocker la valeur d'origine de l'argument pour la portée entière de la méthode.

Vous voulez parfois que votre méthode retourne plusieurs valeurs. À compter de C# 7.0, vous pouvez faire cela facilement en utilisant des *types tuple* et des *littéraux de tuple*. Le type tuple définit les types de données des éléments du tuple. Les littéraux de tuple fournissent les valeurs réelles du tuple retourné. Dans l’exemple suivant, `(string, string, string, int)` définit le type tuple retourné par la méthode `GetPersonalInfo`. L’expression `(per.FirstName, per.MiddleName, per.LastName, per.Age)` est le littéral de tuple ; la méthode retourne le prénom, le deuxième prénom et le nom, ainsi que l’âge pour un objet `PersonInfo`.

```csharp
public (string, string, string, int) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

L’appelant peut alors consommer le tuple retourné avec du code comme celui-ci :

```csharp
var person = GetPersonalInfo("111111111")
Console.WriteLine("{person.Item1} {person.Item3}: age = {person.Item4}");
```

Vous pouvez aussi affecter des noms aux éléments du tuple dans la définition du type tuple. L’exemple suivant montre une autre version de la méthode `GetPersonalInfo` qui utilise des éléments nommés :

```csharp
public (string FName, string MName, string LName, int Age) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

L’appel précédent de la méthode `GetPersonInfo` peut alors être modifié comme suit :

```csharp
var person = GetPersonalInfo("111111111");
Console.WriteLine("{person.FName} {person.LName}: age = {person.Age}");
```

Si un tableau est passé comme argument à une méthode et que celle-ci modifie la valeur d’éléments individuels, il n’est pas nécessaire que la méthode retourne le tableau, même si vous pouvez choisir de le faire pour la qualité du style ou pour obtenir un flux fonctionnel de valeurs.  La raison en est que C# passe tous les types référence par valeur et que la valeur d’une référence de tableau est le pointeur vers ce tableau. Dans l’exemple suivant, les modifications apportées au contenu du tableau `values` qui sont effectuées dans la méthode `DoubleValues` sont observables par tout code ayant une référence au tableau.

[!code-csharp[csSnippets.Methods#101](../../samples/snippets/csharp/concepts/methods/returnarray1.cs#101)]

<a name="extension"></a>

## <a name="extension-methods"></a>Méthodes d’extension

En règle générale, il existe deux façons d’ajouter une méthode à un type existant :

- Modifier le code source pour ce type. Vous ne pouvez évidemment pas le faire si vous ne disposez pas du code source du type. D’autre part, ceci devient une modification d’importance si vous ajoutez aussi des champs de données privés pour prendre en charge la méthode.
- Définir la nouvelle méthode dans une classe dérivée. Vous ne pouvez pas ajouter une méthode de cette façon en utilisant l’héritage pour d’autres types, comme des structures et des énumérations. Vous ne pouvez pas non plus l’utiliser pour « ajouter » une méthode à une classe scellée.

Les méthodes d’extension vous permettent d’« ajouter » une méthode à un type existant sans modifier le type lui-même, ou en implémentant la nouvelle méthode dans un type hérité. La méthode d’extension ne doit pas non plus nécessairement se trouver dans le même assembly que le type qu’elle étend. Vous appelez une méthode d’extension comme si elle était un membre défini d’un type.

Pour plus d’informations, consultez [Méthodes d’extension](programming-guide/classes-and-structs/extension-methods.md).

<a name="async"></a>

## <a name="async-methods"></a>Méthodes async

La fonctionnalité async vous permet d'appeler des méthodes asynchrones sans utiliser de rappels explicites ni fractionner manuellement votre code entre plusieurs méthodes ou expressions lambda.

Si vous marquez une méthode avec le modificateur [async](language-reference/keywords/async.md), vous pouvez utiliser l’opérateur [await](language-reference/operators/await.md) dans la méthode. Quand le contrôle atteint une expression `await` dans la méthode async, il retourne à l’appelant si la tâche attendue n’est pas terminée, et la progression dans la méthode avec le mot clé `await` est interrompue jusqu’à ce que la tâche attendue se termine. Quand la tâche est terminée, l'exécution peut reprendre dans la méthode.

> [!NOTE]
> Une méthode async retourne à l'appelant quand elle rencontre le premier objet await qui n'est pas encore terminé ou quand elle atteint la fin de la méthode async, selon la première éventualité.

Une méthode async peut avoir un type de retour <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task> ou `void`. Le type de retour `void` est essentiellement utilisé pour définir les gestionnaires d’événements, où un type de retour `void` est obligatoire. Une méthode async qui retourne `void` ne peut pas être attendue, et l’appelant d’une méthode retournant void ne peut intercepter aucune exception levée par la méthode. À compter de C# 7.0, une méthode asynchrone peut avoir [n’importe quel type de retour de type tâche](./whats-new/csharp-7.md#generalized-async-return-types).

Dans l’exemple suivant, `DelayAsync` est une méthode async contenant une instruction return qui retourne un entier. Comme il s’agit d’une méthode async, la déclaration de sa méthode doit avoir un type de retour `Task<int>`. Comme le type de retour est `Task<int>`, l’évaluation de l’expression `await` dans `DoSomethingAsync` produit un entier, comme l’instruction `int result = await delayTask` suivante le montre.

[!code-csharp[csSnippets.Methods#102](../../samples/snippets/csharp/concepts/methods/async1.cs#102)]

Une méthode async ne peut pas déclarer de paramètres [in](language-reference/keywords/in-parameter-modifier.md), [ref](language-reference/keywords/ref.md) ou [out](language-reference/keywords/out-parameter-modifier.md), mais elle peut appeler des méthodes qui ont ces paramètres.

 Pour plus d’informations sur les méthodes async, consultez [Programmation asynchrone avec Async et Await](async.md), [Flux de contrôle dans les programmes Async](programming-guide/concepts/async/control-flow-in-async-programs.md) et [Types de retour Async](programming-guide/concepts/async/async-return-types.md).

<a name="expr"></a>

## <a name="expression-bodied-members"></a>Membres expression-bodied

Il est courant d'avoir des définitions de méthode qui retournent tout simplement le résultat d'une expression immédiatement, ou qui ont une seule instruction en tant que corps de la méthode.  Il existe un raccourci de syntaxe pour définir de telles méthodes en utilisant `=>`:

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Si la méthode retourne `void` ou est une méthode async, alors le corps de la méthode doit être une expression d’instruction (comme avec les expressions lambda).  Les propriétés et les indexeurs doivent être en lecture seule, et vous n’y utilisez pas le mot clé d’accesseur `get`.

<a name="iterators"></a>

## <a name="iterators"></a>Iterators

Un itérateur exécute une itération personnalisée sur une collection, comme une liste ou un tableau. Un itérateur utilise l'instruction [yield return](language-reference/keywords/yield.md) pour retourner chaque élément un par un. Quand une instruction `yield return` est atteinte, l’emplacement actif est mémorisé pour que l’appelant puisse demander l’élément suivant dans la séquence.

Le type de retour d'un itérateur peut être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.

Pour plus d’informations, voir [Iterators](programming-guide/concepts/iterators.md).

## <a name="see-also"></a>Voir aussi

- [Modificateurs d’accès](language-reference/keywords/access-modifiers.md)
- [Classes statiques et membres de classe statique](programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Héritage](programming-guide/classes-and-structs/inheritance.md)
- [Classes abstract et sealed et membres de classe](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [Params](language-reference/keywords/params.md)
- [out](language-reference/keywords/out-parameter-modifier.md)
- [ref](language-reference/keywords/ref.md)
- [Dans](language-reference/keywords/in-parameter-modifier.md)
- [Paramètres de passage](programming-guide/classes-and-structs/passing-parameters.md)
