---
title: Fonctions
description: 'En savoir plus sur les fonctions en F # et sur la façon dont F # prend en charge les constructions de programmation fonctionnelle courantes.'
ms.date: 05/16/2016
ms.openlocfilehash: e49183e0634dee1750757abadbfe9e9c824f51a8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596472"
---
# <a name="functions"></a>Fonctions

Les fonctions sont l’unité fondamentale de l’exécution d’un programme dans tout langage de programmation. Comme dans d’autres langages, une fonction F# a un nom, peut avoir des paramètres et accepter des arguments, et contient un corps. F# prend également en charge des constructions de programmation fonctionnelle, telles que le traitement des fonctions comme valeurs, l’utilisation de fonctions sans nom dans les expressions, la composition de fonctions pour former de nouvelles fonctions, les fonctions curryfiées et la définition implicite de fonctions par l’intermédiaire de l’application partielle d’arguments de fonction.

Pour définir des fonctions, utilisez le mot clé `let` ou, si la fonction est récursive, la combinaison de mots clés `let rec`.

## <a name="syntax"></a>Syntaxe

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a>Notes

*function-name* est un identificateur qui représente la fonction. *parameter-list* se compose de paramètres consécutifs séparés par des espaces. Vous pouvez spécifier un type explicite pour chaque paramètre, comme décrit dans la section Paramètres. Si vous ne spécifiez pas un type d’argument spécifique, le compilateur tente de déduire le type du corps de la fonction. *function-body* se compose d’une expression. L’expression qui constitue le corps de la fonction est en général une expression composée comprenant plusieurs expressions qui débouchent sur une expression finale, c’est-à-dire la valeur de retour. *return-type* est un signe deux-points suivi par un type ; son utilisation est facultative. Si vous ne spécifiez pas explicitement le type de la valeur de retour, le compilateur détermine le type de retour à partir de l’expression finale.

Une définition de fonction simple se présente comme suit :

```fsharp
let f x = x + 1
```

Dans l’exemple précédent, le nom de la fonction est `f`, l’argument est `x`, dont le type est `int`, le corps de la fonction est `x + 1`, et la valeur de retour est de type `int`.

Les fonctions peuvent être marquées comme étant `inline`. Pour plus d’informations sur `inline`, consultez [Fonctions inline](inline-functions.md).

## <a name="scope"></a>Étendue

À tout niveau de la portée, sauf dans la portée de module, la réutilisation d’une valeur ou d’un nom de fonction ne constitue pas une erreur. Si vous réutilisez un nom, le nom déclaré en second lieu occulte le nom précédemment déclaré. Toutefois, à la portée de niveau supérieur dans un module, les noms doivent être uniques. Par exemple, le code suivant produit une erreur quand il apparaît au niveau de la portée de module, mais pas quand il apparaît à l’intérieur d’une fonction :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

Mais le code suivant est acceptable à tout niveau de la portée :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a>Paramètres

Les noms des paramètres sont répertoriés après le nom de la fonction. Vous pouvez spécifier un type pour un paramètre, comme indiqué dans l’exemple suivant :

```fsharp
let f (x : int) = x + 1
```

Si vous spécifiez un type, celui-ci suit le nom du paramètre et est séparé du nom par un signe deux-points. Si vous omettez le type du paramètre, celui-ci est déduit par le compilateur. Par exemple, dans la définition de fonction suivante, le type déduit pour l’argument `x` est `int`, car 1 est de type `int`.

```fsharp
let f x = x + 1
```

Toutefois, le compilateur tente de rendre la fonction aussi générique que possible. Observez par exemple le code suivant :

```fsharp
let f x = (x, x)
```

La fonction crée un tuple à partir d’un argument de n’importe quel type. Le type n’étant pas spécifié, la fonction peut être utilisée avec n’importe quel type d’argument. Pour plus d’informations, consultez [Généralisation automatique](../generics/automatic-generalization.md).

## <a name="function-bodies"></a>Corps de fonction

Un corps de fonction peut contenir des définitions de variables et de fonctions locales. Ces variables et fonctions sont dans la portée du corps de la fonction active, et non à l’extérieur. Si l’option de syntaxe simplifiée est activée, vous devez utiliser la mise en retrait pour indiquer qu’une définition se trouve dans un corps de fonction, comme indiqué dans l’exemple suivant :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

Pour plus d’informations, consultez [Indications pour la mise en forme du code](../../style-guide/formatting.md) et [Syntaxe détaillée](../verbose-syntax.md).

## <a name="return-values"></a>Valeurs de retour

Le compilateur utilise l’expression finale dans un corps de fonction pour déterminer la valeur et le type de retour. Il peut déduire le type de l’expression finale à partir d’expressions précédentes. Dans la fonction `cylinderVolume` présentée dans la section précédente, le type de `pi` est déterminé à partir du type du littéral `3.14159` comme étant `float`. Le compilateur utilise le type de `pi` pour déterminer le type de l’expression `h * pi * r * r` comme étant `float`. Par conséquent, le type de retour global de la fonction est `float`.

Pour spécifier la valeur de retour explicitement, écrivez le code comme suit :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

Selon le code ci-dessus, le compilateur applique **float** à la fonction entière ; si vous souhaitez l’appliquer également aux types de paramètre, utilisez le code suivant :

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a>Appel d’une fonction

Pour appeler des fonctions, spécifiez le nom de la fonction, suivi d’un espace et des arguments séparés par des espaces. Par exemple, pour appeler la fonction **cylinderVolume** et assigner le résultat à la valeur **vol**, écrivez le code suivant :

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a>Application partielle d’arguments

Si vous fournissez un nombre d’arguments inférieur à celui spécifié, vous créez une fonction qui attend les arguments restants. Cette méthode de gestion d’arguments, appelée *curryfication*, est une caractéristique des langages de programmation fonctionnelle tels que F#. Par exemple, supposons que vous travaillez avec des tuyaux de deux tailles : l’un d’un rayon de **2.0** et l’autre de **3.0**. Vous pouvez créer des fonctions qui déterminent le volume des tuyaux, comme suit :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

Vous fournissez ensuite, selon vos besoins, l’argument supplémentaire pour les différentes longueurs de tuyau de chaque taille :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a>Fonctions récursives

Les *fonctions récursives* sont des fonctions qui s’appellent. Elles nécessitent la spécification du mot clé **rec** après le mot clé **let**. Appelez la fonction récursive à partir du corps de la fonction, comme vous le feriez pour tout autre appel de fonction. La fonction récursive suivante calcule le *n*<sup>ième</sup> nombre de Fibonacci. La séquence de nombres de Fibonacci est connue depuis l’antiquité ; il s’agit d’une séquence dans laquelle chaque nombre consécutif est la somme des deux nombres précédents dans la séquence.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

Certaines fonctions récursives peuvent entraîner un dépassement de capacité de la pile du programme ou s’exécuter inefficacement si vous ne soignez pas leur écriture ou si vous ne tenez pas compte de techniques spéciales, notamment l’utilisation d’accumulateurs et de continuations.

## <a name="function-values"></a>Valeurs de fonction

En F#, toutes les fonctions sont considérées comme des valeurs ; en fait, elles sont appelées *valeurs de fonction*. Les fonctions étant des valeurs, elles peuvent être utilisées comme arguments d’autres fonctions ou dans d’autres contextes où des valeurs sont utilisées. L’exemple suivant illustre une fonction qui prend une valeur de fonction comme argument :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

Vous spécifiez le type d’une valeur de fonction à l’aide du jeton `->`. Le type de l’argument se trouve à gauche du jeton, et la valeur de retour à droite. Dans l’exemple précédent, `apply1` est une fonction qui prend une fonction `transform` comme argument, où `transform` est une fonction qui prend un entier et qui retourne un autre entier. Le code suivant montre comment utiliser `apply1` :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

La valeur de `result` est 101 au terme de l’exécution du code précédent.

Plusieurs arguments sont séparés par des jetons `->` consécutifs, comme indiqué dans l’exemple suivant :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

Le résultat est 200.

## <a name="lambda-expressions"></a>Expressions lambda

Une *expression lambda* est une fonction sans nom. Dans les exemples précédents, au lieu de définir des fonctions nommées **increment** et **mul**, vous pouvez utiliser des expressions lambda comme suit :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

Pour définir des expressions lambda, utilisez le mot clé `fun`. Une expression lambda ressemble à une définition de fonction, sauf que le jeton `->` est utilisé à la place du jeton `=` pour séparer la liste d’arguments du corps de la fonction. Comme dans une définition de fonction normale, les types d’argument peuvent être déduits ou spécifiés explicitement, et le type de retour de l’expression lambda est déduit du type de la dernière expression dans le corps. Pour plus d’informations, consultez [Expressions lambda : mot clé `fun`](lambda-expressions-the-fun-keyword.md).

## <a name="function-composition-and-pipelining"></a>Composition de fonction et traitement « pipeline »

En F#, des fonctions peuvent être composées d’autres fonctions. La composition de deux fonctions **function1** et **function2** est une autre fonction qui représente l’application de **function1**, suivie de l’application de **function2** :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

Le résultat est 202.

Le traitement « pipeline » permet de chaîner des appels de fonction en tant qu’opérations successives. Le traitement « pipeline » fonctionne comme suit :

```fsharp
let result = 100 |> function1 |> function2
```

Le résultat est encore 202.

Les opérateurs de composition prennent deux fonctions et en retournent une, tandis que les opérateurs de pipeline prennent une fonction et un argument et retournent une valeur. L’exemple de code suivant illustre la différence entre le pipeline et les opérateurs de composition en affichant les différences dans les signatures de la fonction et leur utilisation.

```fsharp
// Function composition and pipeline operators compared.

let addOne x = x + 1
let timesTwo x = 2 * x

// Composition operator
// ( >> ) : ('T1 -> 'T2) -> ('T2 -> 'T3) -> 'T1 -> 'T3
let Compose2 = addOne >> timesTwo

// Backward composition operator
// ( << ) : ('T2 -> 'T3) -> ('T1 -> 'T2) -> 'T1 -> 'T3
let Compose1 = addOne << timesTwo

// Result is 5
let result1 = Compose1 2

// Result is 6
let result2 = Compose2 2

// Pipelining
// Pipeline operator
// ( |> ) : 'T1 -> ('T1 -> 'U) -> 'U
let Pipeline2 x = addOne x |> timesTwo

// Backward pipeline operator
// ( <| ) : ('T -> 'U) -> 'T -> 'U
let Pipeline1 x = addOne <| timesTwo x

// Result is 5
let result3 = Pipeline1 2

// Result is 6
let result4 = Pipeline2 2
```

## <a name="overloading-functions"></a>Surcharge des fonctions

Vous pouvez surcharger les méthodes d’un type, mais pas les fonctions. Pour plus d’informations, consultez [Méthodes](../members/methods.md).

## <a name="see-also"></a>Voir aussi

- [Valeurs](../values/index.md)
- [Informations de référence sur le langage F #](../index.md)
