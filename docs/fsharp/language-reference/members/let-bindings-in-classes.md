---
title: Liaisons let dans des classes
description: Découvrez comment définir des champs privés et des fonctions privées F# pour les classes en utilisant des liaisons’Let’dans la définition de classe.
ms.date: 05/16/2016
ms.openlocfilehash: 0086d3a91f85395c2bd0555f978c5d951c363357
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627484"
---
# <a name="let-bindings-in-classes"></a>Liaisons let dans des classes

Vous pouvez définir des champs privés et des fonctions F# privées pour les `let` classes en utilisant des liaisons dans la définition de classe.

## <a name="syntax"></a>Syntaxe

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>Notes

La syntaxe précédente apparaît après l’en-tête de classe et les déclarations d’héritage, mais avant les définitions de membre. La syntaxe est similaire à celle `let` des liaisons en dehors des classes, mais les noms définis dans une classe ont une portée limitée à la classe. Une `let` liaison crée une fonction ou un champ privé; pour exposer publiquement des données ou des fonctions, déclarez une propriété ou une méthode de membre.

Une `let` liaison qui n’est pas statique est appelée liaison `let` d’instance. Les `let` liaisons d’instance s’exécutent lorsque des objets sont créés. Les `let` liaisons statiques font partie de l’initialiseur statique de la classe, dont l’exécution est garantie avant que le type ne soit utilisé pour la première fois.

Le code dans les `let` liaisons d’instance peut utiliser les paramètres du constructeur principal.

Les attributs et les modificateurs d’accessibilité ne `let` sont pas autorisés sur les liaisons dans les classes.

Les exemples de code suivants illustrent plusieurs `let` types de liaisons dans des classes.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

La sortie est la suivante.

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>Autres façons de créer des champs

Vous pouvez également utiliser le `val` mot clé pour créer un champ privé. Quand vous utilisez `val` le mot clé, le champ n’a pas de valeur lorsque l’objet est créé, mais est initialisé avec une valeur par défaut. Pour plus d’informations, [consultez champs explicites: Mot clé](explicit-fields-the-val-keyword.md)Val.

Vous pouvez également définir des champs privés dans une classe en utilisant une définition de membre et en `private` ajoutant le mot clé à la définition. Cela peut être utile si vous envisagez de modifier l’accessibilité d’un membre sans réécrire votre code. Pour plus d’informations, consultez [Contrôle d’accès](../access-control.md).

## <a name="see-also"></a>Voir aussi

- [Membres](index.md)
- [Liaisons `do` dans des classes](do-bindings-in-classes.md)
- [`let`Liaisons](../functions/let-bindings.md)
