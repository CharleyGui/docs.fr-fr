---
title: Instructions - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- statements [C#], about statements
- C# language, statements
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
ms.openlocfilehash: d50b50bb291d0d087015ea5bd075ae90ced66ff5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711933"
---
# <a name="statements-c-programming-guide"></a>Instructions (Guide de programmation C#)

Les actions qu’un programme effectue sont exprimées dans les instructions. Les actions courantes incluent la déclaration de variables, l’assignation de valeurs, l’appel de méthodes, l’exécution de boucles dans les collections et la création de branches sur des blocs de code, selon une condition donnée. L’ordre dans lequel les instructions sont exécutées dans un programme est appelé le flux de contrôle ou le flux d’exécution. Le flux de contrôle peut varier chaque fois qu’un programme est exécuté, selon la manière dont le programme réagit à l’entrée qu’il reçoit au moment de l’exécution.

Une instruction peut comporter une seule ligne de code terminée par un point-virgule ou une série d’instructions d’une ligne dans un bloc. Un bloc d’instructions est placé entre des accolades ({}) et peut contenir des blocs imbriqués. Le code suivant illustre deux exemples d’instructions d’une ligne, et un bloc d’instructions multiligne :

[!code-csharp[csProgGuideStatements#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#1)]

## <a name="types-of-statements"></a>Types de déclarations

Le tableau suivant répertorie les différents types d’instructions en C# et leurs mots clés associés, avec des liens vers des rubriques contenant plus d’informations :

|Category|Mots clés C# / Remarques|
|--------------|---------------------------|
|[Instructions de déclaration](#declaration-statements)|Une instruction de déclaration introduit une nouvelle variable ou constante. Une déclaration de variable peut éventuellement assigner une valeur à la variable. Dans une déclaration de constante, l’assignation est obligatoire.|
|[Instructions d’expression](expressions.md)|Les instructions d’expression qui calculent une valeur doivent stocker la valeur dans une variable. Pour plus d’informations, consultez [Instructions d’expression](#expression-statements).|
|Instructions de sélection|Les instructions de sélection permettent de créer des branches vers différentes sections de code, selon une ou plusieurs conditions spécifiées. Pour plus d'informations, voir les rubriques suivantes : <ul><li>[Si](../../language-reference/keywords/if-else.md)</li><li>[Autre](../../language-reference/keywords/if-else.md)</li><li>[Interrupteur](../../language-reference/keywords/switch.md)</li><li>[cas](../../language-reference/keywords/switch.md)</li></ul>|
|Instructions d’itération|Les instructions d’itération permettent d’exécuter une boucle dans des collections telles que des tableaux, ou d’effectuer à plusieurs reprises le même jeu d’instructions jusqu’à ce qu’une condition spécifiée soit remplie. Pour plus d'informations, voir les rubriques suivantes : <ul><li>[faire](../../language-reference/keywords/do.md)</li><li>[Pour](../../language-reference/keywords/for.md)</li><li>[Foreach](../../language-reference/keywords/foreach-in.md)</li><li>[Dans](../../language-reference/keywords/foreach-in.md)</li><li>[Tandis que](../../language-reference/keywords/while.md)</li></ul>|
|Instructions de saut|Les instructions de saut transfèrent le contrôle vers une autre section de code. Pour plus d'informations, voir les rubriques suivantes : <ul><li>[Pause](../../language-reference/keywords/break.md)</li><li>[Continuer](../../language-reference/keywords/continue.md)</li><li>[Par défaut](../../language-reference/keywords/switch.md)</li><li>[Goto](../../language-reference/keywords/goto.md)</li><li>[Retour](../../language-reference/keywords/return.md)</li><li>[Rendement](../../language-reference/keywords/yield.md)</li></ul>|
|Instructions de gestion des exceptions|Les instructions de gestion des exceptions permettent de récupérer normalement en cas de conditions exceptionnelles au moment de l’exécution. Pour plus d'informations, voir les rubriques suivantes : <ul><li>[Jeter](../../language-reference/keywords/throw.md)</li><li>[try-catch](../../language-reference/keywords/try-catch.md)</li><li>[try-finally](../../language-reference/keywords/try-finally.md)</li><li>[try-catch-finally](../../language-reference/keywords/try-catch-finally.md)</li></ul>|
|[Checked et unchecked](../../language-reference/keywords/checked-and-unchecked.md)|Les instructions checked et unchecked vous permettent de spécifier si les opérations numériques sont autorisées à provoquer un dépassement de capacité lorsque le résultat est stocké dans une variable trop petite pour contenir la valeur résultante. Pour plus d’informations, consultez [checked](../../language-reference/keywords/checked.md) et [unchecked](../../language-reference/keywords/unchecked.md).|
|Instruction `await`|Si vous marquez une méthode avec le modificateur [async](../../language-reference/keywords/async.md), vous pouvez utiliser l’opérateur [await](../../language-reference/operators/await.md) dans la méthode. Quand le contrôle atteint une expression `await` dans la méthode async, il retourne à l’appelant, et la progression dans la méthode est interrompue jusqu’à ce que la tâche attendue soit terminée. Quand la tâche est terminée, l'exécution peut reprendre dans la méthode.<br /><br /> Pour obtenir un exemple simple, consultez la section « Méthodes async » de [Méthodes](../classes-and-structs/methods.md). Pour plus d’informations, voir [Programmation asynchrone avec async et attendre](../concepts/async/index.md).|
|Instruction `yield return`|Un itérateur exécute une itération personnalisée sur une collection, comme une liste ou un tableau. Un itérateur utilise l'instruction [yield return](../../language-reference/keywords/yield.md) pour retourner chaque élément un par un. Quand une instruction `yield return` est atteinte, l’emplacement actuel dans le code est mémorisé. L'exécution redémarre à partir de cet emplacement au prochain appel de l'itérateur.<br /><br /> Pour plus d’informations, voir [Iterators](../concepts/iterators.md).|
|Instruction `fixed`|L’instruction fixed empêche le récupérateur de mémoire de déplacer une variable mobile. Pour plus d’informations, consultez [fixed](../../language-reference/keywords/fixed-statement.md).|
|Instruction `lock`|L’instruction lock permet de limiter l’accès aux blocs de code à un seul thread à la fois. Pour plus d’informations, consultez [lock](../../language-reference/keywords/lock-statement.md).|
|Instructions étiquetées|Vous pouvez donner une étiquette à une instruction, puis utiliser le mot clé [goto](../../language-reference/keywords/goto.md) pour sauter jusqu’à l’instruction étiquetée. (Examinez l’exemple de la ligne suivante.)|
|La [déclaration vide](#the-empty-statement)|L’instruction vide se compose seulement d’un point-virgule. Elle ne fait rien et peut être utilisée à un emplacement où une instruction est requise alors qu’aucune action ne doit être effectuée.|

## <a name="declaration-statements"></a>Instructions de déclaration

Le code suivant montre des exemples de déclarations de variables avec et sans assignation initiale, ainsi qu’une déclaration de constante avec l’initialisation nécessaire.

[!code-csharp[csProgGuideStatements#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#23)]

## <a name="expression-statements"></a>Instructions d’expression

Le code suivant montre des exemples d’instructions d’expression, y compris l’assignation, la création d’objets avec assignation et l’appel de méthode.

[!code-csharp[csProgGuideStatements#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#24)]

## <a name="the-empty-statement"></a>Instruction vide

Les exemples suivants illustrent deux utilisations d’une instruction vide :

[!code-csharp[csProgGuideStatements#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#25)]

## <a name="embedded-statements"></a>Déclarations intégrées

Certaines instructions, y compris [do](../../language-reference/keywords/do.md), [while](../../language-reference/keywords/while.md), [for](../../language-reference/keywords/for.md) et [foreach](../../language-reference/keywords/foreach-in.md), sont toujours suivies d’une instruction incorporée. Cette instruction incorporée peut être une seule instruction ou plusieurs instructions placées entre des accolades ({}) dans un bloc d’instructions. Même les instructions incorporées d’une seule ligne peuvent être placées entre des accolades ({}), comme illustré dans l’exemple suivant :

[!code-csharp[csProgGuideStatements#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#26)]

Une instruction incorporée qui n’est pas placée entre des accolades ({}) ne peut pas être une instruction de déclaration ni une instruction étiquetée. Ceci est illustré dans l'exemple suivant :

[!code-csharp[csProgGuideStatements#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#27)]

Placez l’instruction incorporée dans un bloc pour corriger l’erreur :

[!code-csharp[csProgGuideStatements#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#28)]

## <a name="nested-statement-blocks"></a>Blocs de déclaration imbriqués

Les blocs d’instructions peuvent être imbriqués, comme illustré dans le code suivant :

[!code-csharp[csProgGuideStatements#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#29)]

## <a name="unreachable-statements"></a>Déclarations inaccessibles

Si le compilateur détermine que le flux de contrôle ne peut jamais atteindre une instruction particulière, il génère l’avertissement CS0162, comme illustré dans l’exemple suivant :

[!code-csharp[csProgGuideStatements#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#22)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Instructions](~/_csharplang/spec/statements.md) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Mots clés des instructions](../../language-reference/keywords/statement-keywords.md)  
- [Expressions](expressions.md)  
