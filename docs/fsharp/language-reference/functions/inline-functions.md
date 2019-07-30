---
title: Fonctions inline
description: Découvrez comment utiliser F# des fonctions inline intégrées directement dans le code appelant.
ms.date: 05/16/2016
ms.openlocfilehash: 2830d1ada5b3005c3fcae975a44e85a7c84554f7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630676"
---
# <a name="inline-functions"></a>Fonctions inline

Les *fonctions inline* sont des fonctions qui sont intégrées directement dans le code appelant.

## <a name="using-inline-functions"></a>Utilisation de fonctions inline

Quand vous utilisez des paramètres de type statique, toutes les fonctions qui sont paramétrables par des paramètres de type doivent être Inline. Cela garantit que le compilateur peut résoudre ces paramètres de type. Lorsque vous utilisez des paramètres de type générique ordinaires, il n’existe aucune restriction de ce type.

Outre l’activation de l’utilisation de contraintes de membre, les fonctions inline peuvent être utiles pour optimiser le code. Toutefois, l’utilisation abusive des fonctions inline peut rendre votre code moins résistant aux modifications des optimisations du compilateur et à l’implémentation des fonctions de la bibliothèque. Pour cette raison, vous devez éviter d’utiliser des fonctions inline pour l’optimisation, sauf si vous avez essayé toutes les autres techniques d’optimisation. La création d’une fonction ou d’une méthode en ligne peut parfois améliorer les performances, mais ce n’est pas toujours le cas. Par conséquent, vous devez également utiliser des mesures de performances pour vérifier que l’exécution d’une fonction inline donnée a un effet positif.

Le `inline` modificateur peut être appliqué aux fonctions au niveau supérieur, au niveau du module ou au niveau de la méthode dans une classe.

L’exemple de code suivant illustre une fonction inline au niveau supérieur, une méthode d’instance inline et une méthode statique Inline.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a>Fonctions inline et inférence de type

La présence de `inline` affecte l’inférence de type. Cela est dû au fait que les fonctions inline peuvent avoir des paramètres de type résolus statiquement, alors que les fonctions non inline ne le peuvent pas. L’exemple de code suivant montre un cas `inline` dans lequel est utile, car vous utilisez une fonction qui a un paramètre de type résolu statiquement, l' `float` opérateur de conversion.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

Sans le `inline` modificateur, l’inférence de type force la fonction à prendre un type spécifique, dans `int`ce cas. Toutefois, avec `inline` le modificateur, la fonction est également déduite pour avoir un paramètre de type résolu statiquement. Avec le `inline` modificateur, le type est déduit comme suit:

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

Cela signifie que la fonction accepte tout type qui prend en charge une conversion en **float**.

## <a name="see-also"></a>Voir aussi

- [Fonctions](index.md)
- [Contraintes](../generics/constraints.md)
- [Paramètres de type résolus statiquement](../generics/statically-resolved-type-parameters.md)
