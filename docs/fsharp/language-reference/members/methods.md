---
title: Méthodes
description: Découvrez comment une méthode F est une fonction associée à un type qui sont utilisés pour exposer et mettre en œuvre la fonctionnalité et le comportement des objets et des types.
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400210"
---
# <a name="methods"></a>Méthodes

Une *méthode* est une fonction qui est associée à un type. Dans la programmation orientée objet, des méthodes sont utilisées pour exposer et implémenter la fonctionnalité et le comportement des objets et des types.

## <a name="syntax"></a>Syntaxe

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-name parameter-list [ : return-type ] =
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member method-name : type-signature
[ attributes ]
default self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue( default-value )>] input) [ : return-type ]
```

## <a name="remarks"></a>Notes 

Dans la syntaxe précédente, vous pouvez voir les différentes formes de déclarations et de définitions de méthode. Dans les corps de méthode plus longs, une rupture de ligne suit le signe égal (MD), et tout le corps de méthode est en retrait.

Les attributs peuvent être appliqués à n’importe quelle déclaration de méthode. Ils précèdent la syntaxe pour une définition de méthode et sont généralement répertoriés sur une ligne séparée. Pour plus d’informations, consultez [Attributs](../attributes.md).

Les méthodes `inline`peuvent être marquées . Pour plus d’informations sur `inline`, consultez [Fonctions inline](../functions/inline-functions.md).

Les méthodes non-inline peuvent être utilisées de façon récursive dans le type; il n’est pas `rec` nécessaire d’utiliser explicitement le mot clé.

## <a name="instance-methods"></a>Méthodes d’instance

Les méthodes d’instance sont déclarées avec le `member` mot clé et un *auto-identifiant,* suivie d’une période (.) et le nom et les paramètres de la méthode. Comme c’est `let` le cas pour les fixations, la *liste des paramètres* peut être un modèle. Typiquement, vous enfermez les paramètres de méthode entre parenthèses sous une forme de tuple, qui est la façon dont les méthodes apparaissent dans F quand ils sont créés dans d’autres langues cadre .NET. Cependant, la forme au curry (paramètres séparés par des espaces) est également commune, et d’autres modèles sont soutenus aussi.

L’exemple suivant illustre la définition et l’utilisation d’une méthode d’instance non abstraite.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

Dans les méthodes d’instance, n’utilisez pas l’auto-identifiant pour accéder aux champs définis en utilisant des reliures de laisser. Utilisez l’auto-identifiant lorsque vous accédez à d’autres membres et propriétés.

## <a name="static-methods"></a>Méthodes statiques

Le `static` mot clé est utilisé pour spécifier qu’une méthode peut être appelée sans instance et n’est pas associée à une instance d’objet. Sinon, les méthodes sont des méthodes d’instance.

L’exemple de la section suivante `let` montre les champs `member` déclarés avec le mot-clé, les membres de la propriété déclarés avec le mot clé, et une méthode statique déclarée avec le `static` mot clé.

L’exemple suivant illustre la définition et l’utilisation de méthodes statiques. Supposons que ces définitions `SomeType` de méthode sont dans la classe dans la section précédente.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Méthodes abstraites et virtuelles

Le `abstract` mot clé indique qu’une méthode a une fente de répartition virtuelle et pourrait ne pas avoir de définition dans la classe. Une *fente de répartition virtuelle* est une entrée dans une table interne de fonctions qui est utilisée au moment de l’exécution pour rechercher des appels de fonction virtuelle dans un type orienté objet. Le mécanisme de répartition virtuelle est le mécanisme qui met en œuvre le *polymorphisme*, une caractéristique importante de la programmation orientée objet. Une classe qui a au moins une méthode abstraite sans définition est une *classe abstraite,* ce qui signifie qu’aucun cas ne peut être créé de cette classe. Pour plus d’informations sur les classes abstraites, voir [Classes abstraites](../abstract-classes.md).

Les déclarations de méthode abstraites n’incluent pas un corps de méthode. Au lieu de cela, le nom de la méthode est suivi d’un côlon (:) et une signature type pour la méthode. La signature type d’une méthode est la même que celle montrée par IntelliSense lorsque vous mettez en pause le pointeur de la souris sur un nom de méthode dans l’éditeur de code visual studio, sauf sans noms de paramètres. Les signatures de type sont également affichées par l’interprète, fsi.exe, lorsque vous travaillez de façon interactive. La signature type d’une méthode est formée en énumérant les types des paramètres, suivi par le type de retour, avec des symboles de séparateur appropriés. Les paramètres au curry `->` sont séparés par et `*`les paramètres de tuple sont séparés par . La valeur de retour est toujours `->` séparée des arguments par un symbole. Les parenthèses peuvent être utilisées pour regrouper des paramètres complexes, par exemple lorsqu’un type de fonction est un paramètre, ou pour indiquer quand un tuple est traité comme un seul paramètre plutôt que comme deux paramètres.

Vous pouvez également donner des définitions par défaut de `default` méthodes abstraites en ajoutant la définition à la classe et en utilisant le mot clé, comme indiqué dans le bloc de syntaxe dans ce sujet. Une méthode abstraite qui a une définition dans la même classe équivaut à une méthode virtuelle dans d’autres langues cadre .NET. Qu’une définition existe ou `abstract` non, le mot clé crée une nouvelle fente de répartition dans le tableau de fonction virtuel pour la classe.

Qu’une classe de base implémente ses méthodes abstraites, les classes dérivées peuvent fournir des implémentations de méthodes abstraites. Pour implémenter une méthode abstraite dans une classe dérivée, définir une `override` méthode `default` qui a le même nom et la signature dans la classe dérivée, sauf utiliser le ou le mot clé, et fournir le corps de méthode. Les mots-clés `override` et `default` signifient exactement la même chose. Utiliser `override` si la nouvelle méthode l’emporte sur une mise en œuvre de la classe de base; lorsque `default` vous créez une implémentation dans la même classe que la déclaration abstraite originale. N’utilisez `abstract` pas le mot clé sur la méthode qui implémente la méthode qui a été déclarée abstraite dans la classe de base.

L’exemple suivant illustre `Rotate` une méthode abstraite qui a une implémentation par défaut, l’équivalent d’une méthode virtuelle .NET Framework.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

L’exemple suivant illustre une classe dérivée qui l’emporte sur une méthode de classe de base. Dans ce cas, le remplacement modifie le comportement de sorte que la méthode ne fait rien.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Méthodes surchargées

Les méthodes surchargées sont des méthodes qui ont des noms identiques dans un type donné, mais qui ont des arguments différents. Dans le F, les arguments facultatifs sont généralement utilisés au lieu de méthodes surchargées. Cependant, les méthodes surchargées sont autorisées dans la langue, à condition que les arguments soient sous forme de tuple, et non sous forme de cari.

## <a name="optional-arguments"></a>Arguments facultatifs

En commençant par F 4.1, vous pouvez également avoir des arguments facultatifs avec une valeur de paramètre par défaut dans les méthodes.  Il s’agit d’aider à faciliter l’interopération avec le code C.  L’exemple suivant montre la syntaxe :

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

Notez que la `DefaultParameterValue` valeur transmise pour doit correspondre au type d’entrée.  Dans l’échantillon ci-dessus, il s’agit d’un `int`.  Tenter de faire passer une valeur `DefaultParameterValue` non-integer dans entraînerait une erreur de compilation.

## <a name="example-properties-and-methods"></a>Exemple : Propriétés et méthodes

L’exemple suivant contient un type qui a des exemples de champs, fonctions privées, propriétés, et une méthode statique.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Voir aussi

- [Membres](index.md)
