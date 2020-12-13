---
title: Introduction à la programmation fonctionnelle en F#
description: 'Découvrez les principes de base de la programmation fonctionnelle en F #.'
ms.date: 10/29/2018
ms.openlocfilehash: 44242a4319a331312a003a555d1483f2a3f1a90d
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110583"
---
# <a name="introduction-to-functional-programming-in-f"></a>Présentation de la programmation fonctionnelle en F\#

La programmation fonctionnelle est un style de programmation qui met l’accent sur l’utilisation de fonctions et de données immuables. La programmation fonctionnelle typée est lorsque la programmation fonctionnelle est combinée à des types statiques, tels que F #. En général, les concepts suivants sont mis en évidence dans la programmation fonctionnelle :

* Fonctionne comme les constructions principales que vous utilisez
* Expressions au lieu d’instructions
* Valeurs immuables sur les variables
* Programmation déclarative sur la programmation impérative

Tout au long de cette série, vous allez explorer les concepts et les modèles de la programmation fonctionnelle à l’aide de F #. En cours de route, vous apprendrez également un F #.

## <a name="terminology"></a>Terminologie

La programmation fonctionnelle, comme d’autres paradigmes de programmation, est fournie avec un vocabulaire que vous devrez finalement apprendre. Voici quelques termes courants que vous verrez tout le temps :

* **Function** : une fonction est une construction qui produit une sortie quand une entrée est fournie. Plus formellement, il _mappe_ un élément d’un jeu à un autre jeu. Ce formalisme est intégré au béton de nombreuses façons, en particulier lors de l’utilisation de fonctions qui opèrent sur des collections de données. Il s’agit du concept le plus simple (et le plus important) de la programmation fonctionnelle.
* **Expression** : une expression est une construction dans le code qui produit une valeur. En F #, cette valeur doit être liée ou explicitement ignorée. Une expression peut être remplacée par un appel de fonction.
* **Pureté** -pureté est une propriété d’une fonction de telle sorte que sa valeur de retour est toujours la même pour les mêmes arguments, et que son évaluation n’a aucun effet secondaire. Une fonction pure dépend entièrement de ses arguments.
* **Transparence référentielle** : la transparence référentielle est une propriété d’expressions telle qu’elles peuvent être remplacées par leur sortie sans affecter le comportement d’un programme.
* **Immuabilité** -immuabilité signifie qu’une valeur ne peut pas être modifiée sur place. Cela diffère avec les variables, qui peuvent changer en place.

## <a name="examples"></a>Exemples

Les exemples suivants illustrent ces concepts fondamentaux.

### <a name="functions"></a>Fonctions

La construction la plus courante et la plus fondamentale de la programmation fonctionnelle est la fonction. Voici une fonction simple qui ajoute 1 à un entier :

```fsharp
let addOne x = x + 1
```

Sa signature de type est la suivante :

```fsharp
val addOne: x:int -> int
```

La signature peut être lue en tant que, « `addOne` accepte un `int` nommé `x` et produira un `int` ». Plus formellement `addOne` , _mappe_ une valeur de l’ensemble d’entiers à l’ensemble d’entiers. Le `->` jeton désigne ce mappage. En F #, vous pouvez généralement examiner la signature de la fonction pour avoir une idée de ce qu’elle fait.

Pourquoi la signature est-elle importante ? Dans la programmation fonctionnelle typée, l’implémentation d’une fonction est souvent moins importante que la signature de type réelle ! Le fait `addOne` d’ajouter la valeur 1 à un entier est intéressant lors de l’exécution, mais lorsque vous construisez un programme, le fait qu’il accepte et retourne un `int` est ce qui indique comment vous allez utiliser cette fonction. En outre, une fois que vous utilisez cette fonction correctement (par rapport à sa signature de type), le diagnostic de tout problème peut être effectué uniquement dans le corps de la `addOne` fonction. Il s’agit de l’impulsion derrière la programmation fonctionnelle typée.

### <a name="expressions"></a>Expressions

Les expressions sont des constructions qui évaluent une valeur. Contrairement aux instructions qui exécutent une action, les expressions peuvent être considérées comme effectuant une action qui renvoie une valeur. Les expressions sont presque toujours utilisées dans la programmation fonctionnelle au lieu des instructions.

Examinez la fonction précédente, `addOne` . Le corps de `addOne` est une expression :

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

C’est le résultat de cette expression qui définit le type de résultat de la `addOne` fonction. Par exemple, l’expression qui compose cette fonction peut être changée en un type différent, tel que `string` :

```fsharp
let addOne x = x.ToString() + "1"
```

La signature de la fonction est désormais :

```fsharp
val addOne: x:'a -> string
```

Étant donné que tout type en F # peut avoir `ToString()` été appelé sur celui-ci, le type de `x` a été rendu générique (appelé [généralisation automatique](../language-reference/generics/automatic-generalization.md)) et le type résultant est un `string` .

Les expressions ne sont pas uniquement les corps des fonctions. Vous pouvez avoir des expressions qui produisent une valeur que vous utilisez ailleurs. La première est la `if` suivante :

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result
```

L' `if` expression produit une valeur appelée `result` . Notez que vous pouvez omettre `result` complètement, en faisant de l' `if` expression le corps de la `addOneIfOdd` fonction. La principale chose à savoir sur les expressions est qu’elles produisent une valeur.

Il existe un type spécial, `unit` , qui est utilisé lorsqu’il n’y a rien à retourner. Par exemple, considérez cette fonction simple :

```fsharp
let printString (str: string) =
    printfn $"String is: {str}"
```

La signature ressemble à ceci :

```fsharp
val printString: str:string -> unit
```

Le `unit` type indique qu’aucune valeur réelle n’est retournée. Cela est utile lorsque vous avez une routine qui doit « faire fonctionner » malgré l’absence de valeur à retourner à la suite de ce travail.

Cela contraste nettement avec la programmation impérative, où la construction équivalente `if` est une instruction, et la production de valeurs est souvent effectuée avec des variables mutantes. Par exemple, en C#, le code peut être écrit comme suit :

```csharp
bool IsOdd(int x) => x % 2 != 0;

int AddOneIfOdd(int input)
{
    var result = input;

    if (IsOdd(input))
    {
        result = input + 1;
    }

    return result;
}
```

Il est à noter que C# et d’autres langages de style C prennent en charge l' [expression ternaire](../../csharp/language-reference/operators/conditional-operator.md), qui permet la programmation conditionnelle basée sur une expression.

Dans la programmation fonctionnelle, il est rare de faire muter des valeurs avec des instructions. Bien que certains langages fonctionnels prennent en charge les instructions et la mutation, il n’est pas courant d’utiliser ces concepts dans la programmation fonctionnelle.

### <a name="pure-functions"></a>Fonctions pures

Comme mentionné précédemment, les fonctions pures sont des fonctions qui :

* Évaluez toujours à la même valeur pour la même entrée.
* N’ont pas d’effets secondaires.

Il est utile de considérer les fonctions mathématiques dans ce contexte. En mathématiques, les fonctions dépendent uniquement de leurs arguments et n’ont pas d’effets secondaires. Dans la fonction mathématique `f(x) = x + 1` , la valeur de `f(x)` dépend uniquement de la valeur de `x` . Les fonctions pures de la programmation fonctionnelle sont de la même façon.

Lors de l’écriture d’une fonction pure, la fonction doit dépendre uniquement de ses arguments et n’exécute aucune action qui produit un effet secondaire.

Voici un exemple de fonction non pure, car elle dépend de l’état global et mutable :

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

La `addOneToValue` fonction est clairement impure, car `value` peut être modifiée à tout moment pour avoir une valeur différente de 1. Ce modèle de selon une valeur globale doit être évité dans la programmation fonctionnelle.

Voici un autre exemple de fonction non pure, car elle effectue un effet secondaire :

```fsharp
let addOneToValue x =
    printfn $"x is %d{x}"
    x + 1
```

Bien que cette fonction ne dépende pas d’une valeur globale, elle écrit la valeur de `x` dans la sortie du programme. Bien qu’il n’y ait rien de mal à faire, cela signifie que la fonction n’est pas pure. Si une autre partie de votre programme dépend d’un élément externe au programme, tel que la mémoire tampon de sortie, l’appel de cette fonction peut affecter l’autre partie de votre programme.

La suppression de l' `printfn` instruction rend la fonction pure :

```fsharp
let addOneToValue x = x + 1
```

Même si cette fonction n’est pas fondamentalement _meilleure_ que la version précédente avec l' `printfn` instruction, elle garantit que toutes les fonctions retournent une valeur. L’appel de cette fonction un nombre quelconque de fois génère le même résultat : elle produit simplement une valeur. La prévisibilité donnée par la pureté est un grand nombre de programmeurs fonctionnels.

### <a name="immutability"></a>Immuabilité

Enfin, l’un des concepts les plus fondamentaux de la programmation fonctionnelle typée est l’immuabilité. En F #, toutes les valeurs sont immuables par défaut. Cela signifie qu’ils ne peuvent pas être mutés sur place, à moins que vous les Marquez explicitement comme mutable.

En pratique, l’utilisation de valeurs immuables signifie que vous modifiez votre approche de programmation à partir de, « je dois modifier un nom » en « je dois produire une nouvelle valeur ».

Par exemple, l’ajout de 1 à une valeur signifie produire une nouvelle valeur, sans muter la valeur existante :

```fsharp
let value = 1
let secondValue = value + 1
```

En F #, le code suivant ne fait **pas** muter la `value` fonction ; à la place, il effectue une vérification d’égalité :

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

Certains langages de programmation fonctionnelle ne prennent pas du tout en charge la mutation. En F #, il est pris en charge, mais il ne s’agit pas du comportement par défaut pour les valeurs.

Ce concept s’étend encore davantage aux structures de données. Dans la programmation fonctionnelle, les structures de données immuables, telles que les ensembles (et bien d’autres), ont une implémentation différente de celle que vous pourriez attendre initialement. D’un point de vue conceptuel, un élément tel que l’ajout d’un élément à un ensemble ne change pas le jeu, il produit un _nouvel_ ensemble avec la valeur ajoutée. En coulisses, il s’agit souvent d’une structure de données différente qui permet de suivre efficacement une valeur afin que la représentation appropriée des données puisse être donnée en conséquence.

Ce style de travail avec les valeurs et les structures de données est essentiel, car il vous oblige à traiter toute opération qui modifie quelque chose comme si elle crée une nouvelle version de cette chose. Cela permet d’assurer la cohérence de l’égalité et de la comparabilité dans vos programmes.

## <a name="next-steps"></a>Étapes suivantes

La section suivante traite en détail les fonctions, en explorant les différentes façons de les utiliser dans la programmation fonctionnelle.

Les [fonctions de première classe](first-class-functions.md) explorent les fonctions en profondeur, en vous expliquant comment vous pouvez les utiliser dans différents contextes.

## <a name="further-reading"></a>Pour aller plus loin

La série de [réflexion](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) fonctionnelle est une autre formidable ressource pour en savoir plus sur la programmation fonctionnelle avec F #. Il couvre les principes fondamentaux de la programmation fonctionnelle de manière pragmatique et facile à lire, en utilisant les fonctionnalités F # pour illustrer les concepts.
