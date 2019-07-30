---
title: Délégués
description: Découvrez comment utiliser des délégués dans F#.
ms.date: 05/16/2016
ms.openlocfilehash: 65875897d5fc4b2ac66f1dfbe913f29fb74137cd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630373"
---
# <a name="delegates"></a>Délégués

Un délégué représente un appel de fonction en tant qu’objet. Dans F#, vous devez normalement utiliser des valeurs de fonction pour représenter des fonctions comme valeurs de première classe. Toutefois, les délégués sont utilisés dans le .NET Framework et sont donc nécessaires lorsque vous interagissez avec les API qui les attendent. Ils peuvent également être utilisés lors de la création de bibliothèques conçues pour une utilisation à partir d’autres langages de .NET Framework.

## <a name="syntax"></a>Syntaxe

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a>Notes

Dans la syntaxe précédente, `type1` représente le type d’argument ou les `type2` types et représente le type de retour. Les types d’arguments représentés par `type1` sont automatiquement curryfiés. Cela suggère que pour ce type, vous utilisez un formulaire de tuple si les arguments de la fonction cible sont curryfiés, et un tuple entre parenthèses pour les arguments qui se trouvent déjà dans le formulaire de Tuple. La curryfication automatique supprime un jeu de parenthèses, laissant un argument de tuple qui correspond à la méthode cible. Reportez-vous à l’exemple de code pour la syntaxe que vous devez utiliser dans chaque cas.

Les délégués peuvent être attachés à des valeurs de fonction et à F# des méthodes statiques ou d’instance. F#les valeurs de fonction peuvent être passées directement comme arguments aux constructeurs délégués. Pour une méthode statique, vous construisez le délégué à l’aide du nom de la classe et de la méthode. Pour une méthode d’instance, vous fournissez l’instance d’objet et la méthode dans un seul argument. Dans les deux cas, l’opérateur d’accès`.`aux membres () est utilisé.

La `Invoke` méthode sur le type délégué appelle la fonction encapsulée. En outre, les délégués peuvent être passés en tant que valeurs de fonction en référençant le nom de la méthode Invoke sans les parenthèses.

Le code suivant illustre la syntaxe de création de délégués qui représentent différentes méthodes dans une classe. Selon que la méthode est une méthode statique ou une méthode d’instance, et si elle a des arguments dans le formulaire de tuple ou sous la forme curryfiée, la syntaxe de déclaration et d’assignation du délégué est un peu différente.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

Le code suivant illustre quelques-unes des différentes façons dont vous pouvez travailler avec les délégués.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

La sortie de l’exemple de code précédent est la suivante.

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Paramètres et arguments](parameters-and-arguments.md)
- [Événements](./members/events.md)
