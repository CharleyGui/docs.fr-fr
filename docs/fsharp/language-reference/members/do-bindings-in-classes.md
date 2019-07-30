---
title: Liaisons do dans les classes
description: Apprenez à utiliser une F# liaison’do’dans une définition de classe, qui effectue des actions lorsque l’objet est construit ou lorsque le type est utilisé pour la première fois.
ms.date: 05/16/2016
ms.openlocfilehash: ced4f1bb17d9e23bf51cc79b5a275cc334cca013
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627589"
---
# <a name="do-bindings-in-classes"></a>Liaisons do dans les classes

Une `do` liaison dans une définition de classe effectue des actions lorsque l’objet est construit ou, pour `do` une liaison statique, lorsque le type est utilisé pour la première fois.

## <a name="syntax"></a>Syntaxe

```fsharp
[static] do expression
```

## <a name="remarks"></a>Notes

Une `do` liaison s’affiche avec les liaisons `let` or after, mais avant les définitions de membres dans une définition de classe. Bien que `do` le mot clé soit `do` facultatif pour les liaisons au niveau du module, il n’est `do` pas facultatif pour les liaisons dans une définition de classe.

Pour la construction de chaque objet d’un type donné, les liaisons non `do` statiques et les liaisons non `let` statiques sont exécutées dans l’ordre dans lequel elles apparaissent dans la définition de classe. Plusieurs `do` liaisons peuvent se produire dans un type. Les liaisons non statiques `let` et les liaisons non statiques `do` deviennent le corps du constructeur principal. Le code dans la section liaisons non `do` statiques peut référencer les paramètres du constructeur principal et toutes les valeurs ou fonctions qui sont définies `let` dans la section liaisons.

Les liaisons non `do` statiques peuvent accéder aux membres de la classe tant que la classe a un auto-identificateur défini par un `as` mot clé dans l’en-tête de la classe, et tant que toutes les utilisations de ces membres sont qualifiées avec l’auto-identificateur pour la classe.

Étant `let` donné que les liaisons initialisent les champs privés d’une classe, ce qui est souvent nécessaire pour garantir que les membres `do` se comportent comme prévu `let` , les liaisons sont généralement placées `do` après des liaisons afin que le code de la liaison puisse Exécutez avec un objet entièrement initialisé. Si votre code tente d’utiliser un membre avant la fin de l’initialisation, une exception InvalidOperationException est levée.

Les `do` liaisons statiques peuvent référencer des membres statiques ou des champs de la classe englobante, mais pas des membres d’instance ou des champs. Les `do` liaisons statiques font partie de l’initialiseur statique de la classe, qui est garantie de s’exécuter avant la première utilisation de la classe.

Les attributs sont ignorés pour les liaisons dans les `do` types. Si un attribut est requis pour du code qui s’exécute dans `do` une liaison, il doit être appliqué au constructeur principal.

Dans le code suivant, une classe a une liaison `do` statique et une liaison non statique `do` . L’objet a un constructeur qui a deux paramètres, `a` et `b`, et deux champs privés sont définis dans les `let` liaisons de la classe. Deux propriétés sont également définies. Toutes ces valeurs se trouvent dans la portée de la section `do` liaisons non statiques, comme illustré par la ligne qui imprime toutes ces valeurs.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

La sortie est la suivante.

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a>Voir aussi

- [Membres](index.md)
- [Classes](../classes.md)
- [Constructeurs](constructors.md)
- [Liaisons `let` dans des classes](let-bindings-in-classes.md)
- [`do`Liaisons](../functions/do-Bindings.md)
