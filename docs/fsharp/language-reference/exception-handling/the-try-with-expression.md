---
title: 'Exceptions : try...with (expression)'
description: Découvrez comment utiliser la F# procédure «try... avec’expression pour la gestion des exceptions.
ms.date: 05/16/2016
ms.openlocfilehash: e4d615086a93e26b76cca460e797659ca13792b5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630250"
---
# <a name="exceptions-the-trywith-expression"></a>Exceptions : try...with (expression)

Cette rubrique décrit l' `try...with` expression, qui est utilisée pour la gestion des exceptions dans le F# langage.

## <a name="syntax"></a>Syntaxe

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a>Notes

L' `try...with` expression est utilisée pour gérer les exceptions F#dans. Elle est similaire à l' `try...catch` instruction dans C#. Dans la syntaxe précédente, le code de *expression1* peut générer une exception. L' `try...with` expression retourne une valeur. Si aucune exception n’est levée, l’expression entière retourne la valeur de *expression1*. Si une exception est levée, chaque *modèle* est comparé à son tour à l’exception, et pour le premier modèle correspondant, l' *expression*correspondante, appelée *Gestionnaire d’exceptions*, pour cette branche est exécutée et l’expression globale retourne la valeur de l’expression dans ce gestionnaire d’exceptions. Si aucun modèle ne correspond, l’exception se propage vers le haut de la pile des appels jusqu’à ce qu’un gestionnaire correspondant soit trouvé. Les types des valeurs retournées à partir de chaque expression dans les gestionnaires d’exceptions doivent correspondre au type retourné par l' `try` expression dans le bloc.

Souvent, le fait qu’une erreur s’est produite signifie également qu’il n’y a pas de valeur valide pouvant être retournée par les expressions de chaque gestionnaire d’exceptions. Un modèle fréquent consiste à avoir le type de l’expression comme type d’option. L’exemple de code suivant illustre ce modèle.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

Il F# peut s’agir d’exceptions .net ou d’exceptions. Vous pouvez définir F# des exceptions à l' `exception` aide du mot clé.

Vous pouvez utiliser divers modèles pour filtrer sur le type d’exception et d’autres conditions; les options sont résumées dans le tableau suivant.

|Motif|Description|
|-------|-----------|
|:? *exception-type*|Correspond au type d’exception .NET spécifié.|
|:? *exception-type* en tant qu' *identificateur*|Correspond au type d’exception .NET spécifié, mais donne à l’exception une valeur nommée.|
|*nom de l’exception* (*arguments*)|Correspond à F# un type d’exception et lie les arguments.|
|*identifier*|Représente n’importe quelle exception et lie le nom à l’objet exception. Équivalent à **:? System. exception en**tant qu'_identificateur_|
|*identificateur* lorsque la *condition*|Correspond à toute exception si la condition est true.|

## <a name="examples"></a>Exemples

Les exemples de code suivants illustrent l’utilisation des différents modèles de gestionnaire d’exceptions.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> La `try...with` construction est une expression distincte de l' `try...finally` expression. Par conséquent, si votre code nécessite à `with` la fois un `finally` bloc et un bloc, vous devrez imbriquer les deux expressions.

> [!NOTE]
> Vous pouvez utiliser `try...with` dans les flux de travail asynchrones et d’autres expressions de calcul, auquel cas une version `try...with` personnalisée de l’expression est utilisée. Pour plus d’informations, consultez [flux de travail asynchrones](../asynchronous-workflows.md)et expressions de [calcul](../computation-expressions.md).

## <a name="see-also"></a>Voir aussi

- [Gestion des exceptions](index.md)
- [Types d'exceptions](exception-types.md)
- [Exceptions : L' `try...finally` expression](the-try-finally-expression.md)
