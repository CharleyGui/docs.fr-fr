---
title: Valeurs
description: Découvrez comment les valeurs F# de sont des quantités qui ont un type spécifique.
ms.date: 05/16/2016
ms.openlocfilehash: ed7a5b069a5a47aacf0cce4cfa754ded46f6e84a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630799"
---
# <a name="values"></a>Valeurs

En F#, les valeurs sont des quantités qui ont un type spécifique ; les valeurs peuvent être des nombres intégraux ou à virgule flottante, des caractères ou du texte, des listes, des séquences, des tableaux, des tuples, des unions discriminées, des enregistrements, des types de classe ou des valeurs de fonction.

## <a name="binding-a-value"></a>Liaison d’une valeur

Le terme *liaison* signifie l’association d’un nom à une définition. Le mot clé `let` lie une valeur, comme dans les exemples suivants :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet601.fs)]

Le type d’une valeur est déduit de la définition. Pour un type primitif, tel qu’un nombre intégral ou à virgule flottante, le type est déterminé à partir du type du littéral. Par conséquent, dans l’exemple précédent, le compilateur déduit que le type de `b` est `unsigned int`, alors qu’il déduit que le type de `a` est `int`. Le type d’une valeur de fonction est déterminé à partir de la valeur de retour dans le corps de la fonction. Pour plus d’informations sur les types de valeurs de fonction, consultez [Fonctions](../functions/index.md). Pour plus d’informations sur les types de littéraux, consultez [Littéraux](../literals.md).

Par défaut, le compilateur n’émet pas de diagnostics sur les liaisons inutilisées. Pour recevoir ces messages, activez l’avertissement 1182 dans votre fichier projet ou lorsque vous appelez le compilateur ( `--warnon` consultez sous [Options du compilateur](../compiler-options.md)).

## <a name="why-immutable"></a>Pourquoi immuables ?

Des valeurs immuables sont des valeurs qui ne peuvent pas être modifiées durant toute l’exécution d’un programme. Si vous travaillez d’habitude avec des langages tels que C++, Visual Basic ou C#, vous pourrez être surpris de constater que F# donne la primauté aux valeurs immuables, et non aux variables auxquelles de nouvelles valeurs peuvent être assignées pendant l’exécution d’un programme. Les données immuables sont un élément important de la programmation fonctionnelle. Dans un environnement multithread, des variables mutables partagées qui peuvent être modifiées par différents threads sont difficiles à gérer. Par ailleurs, avec des variables mutables, il peut parfois être difficile de savoir si une variable peut être modifiée quand elle est passée à une autre fonction.

Dans les langages fonctionnels purs, il n’y a pas de variables, les fonctions se comportent strictement comme des fonctions mathématiques. Là où le code dans un langage procédural utilise une assignation de variable pour modifier une valeur, le code équivalent dans un langage fonctionnel comprend une valeur immuable comme entrée, une fonction immuable et différentes valeurs immuables comme sortie. Cette rigueur mathématique donne lieu à un raisonnement plus carré sur le comportement du programme, ce qui permet aux compilateurs de vérifier le code plus rigoureusement et de l’optimiser plus efficacement. Pour les développeurs, il est plus facile de comprendre le code et de l’écrire correctement. Le code fonctionnel est donc probablement plus facile à déboguer que le code procédural ordinaire.

F# n’est pas un langage fonctionnel pur ; toutefois, il prend entièrement en charge la programmation fonctionnelle. L’utilisation de valeurs immuables est conseillée, car votre code bénéficie ainsi d’un aspect important de la programmation fonctionnelle.

## <a name="mutable-variables"></a>Variables mutables

Vous pouvez utiliser le mot clé `mutable` pour spécifier une variable pouvant être modifiée. En F#, les variables mutables doivent généralement avoir une portée limitée, soit comme champ d’un type, soit comme valeur locale. Des variables mutables avec une portée limitée sont plus faciles à contrôler et moins susceptibles d’être modifiées de manière incorrecte.

Vous pouvez assigner une valeur initiale à une variable mutable à l’aide du mot clé `let`, de la même façon que vous définissez une valeur. Toutefois, la différence est que vous pouvez assigner par la suite de nouvelles valeurs à des variables mutables à l’aide de l’opérateur `<-`, comme dans l’exemple suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet602.fs)]

Les valeurs `mutable` marquées peuvent être promues automatiquement en `'a ref` si elles sont capturées par une fermeture, y compris les `seq` formulaires qui créent des fermetures, tels que les générateurs. Si vous souhaitez être averti lorsque cela se produit, activez l’avertissement 3180 dans votre fichier projet ou lors de l’appel du compilateur.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----|-----------|
|[Liaisons let](../functions/let-bindings.md)|Fournit des informations sur l' `let` utilisation du mot clé pour lier des noms à des valeurs et des fonctions.|
|[Fonctions](../functions/index.md)|Fournit une vue d’ensemble des fonctions en F#.|

## <a name="see-also"></a>Voir aussi

- [Valeurs Null](null-Values.md)
- [Informations de référence du langage F#](../index.md)
