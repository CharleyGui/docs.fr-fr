---
title: Méthodes
description: 'Découvrez comment une méthode F # est une fonction associée à un type qui est utilisé pour exposer et implémenter les fonctionnalités et le comportement d’objets et de types.'
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224103"
---
# <a name="methods"></a>Méthodes

Une *méthode* est une fonction associée à un type. Dans la programmation orientée objet, les méthodes sont utilisées pour exposer et implémenter les fonctionnalités et le comportement des objets et des types.

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

Dans la syntaxe précédente, vous pouvez voir les différentes formes de déclarations et de définitions de méthode. Dans les corps de méthode plus longs, un saut de ligne suit le signe égal (=) et le corps de la méthode entière est mis en retrait.

Les attributs peuvent être appliqués à toute déclaration de méthode. Elles précèdent la syntaxe d’une définition de méthode et sont généralement listées sur une ligne distincte. Pour plus d’informations, consultez [Attributs](../attributes.md).

Les méthodes peuvent être marquées `inline` . Pour plus d’informations sur `inline`, consultez [Fonctions inline](../functions/inline-functions.md).

Les méthodes non inline peuvent être utilisées de manière récursive dans le type ; Il n’est pas nécessaire d’utiliser explicitement le `rec` mot clé.

## <a name="instance-methods"></a>Méthodes d’instance

Les méthodes d’instance sont déclarées avec le `member` mot clé et un *auto-identificateur*, suivis d’un point (.) et du nom et des paramètres de la méthode. Comme c’est le cas pour les `let` liaisons, la *liste de paramètres* peut être un modèle. En général, les paramètres de méthode sont placés entre parenthèses sous forme de tuple, ce qui correspond à la façon dont les méthodes s’affichent en F # lorsqu’elles sont créées dans d’autres langages de .NET Framework. Toutefois, la forme curryfiée (les paramètres séparés par des espaces) est également courante, et les autres modèles sont également pris en charge.

L’exemple suivant illustre la définition et l’utilisation d’une méthode d’instance non abstraite.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

Dans les méthodes d’instance, n’utilisez pas l’auto-identificateur pour accéder aux champs définis à l’aide de liaisons Let. Utilisez l’auto-identificateur lors de l’accès à d’autres membres et propriétés.

## <a name="static-methods"></a>Méthodes statiques

Le mot clé `static` est utilisé pour spécifier qu’une méthode peut être appelée sans instance et qu’elle n’est pas associée à une instance d’objet. Sinon, les méthodes sont des méthodes d’instance.

L’exemple de la section suivante montre les champs déclarés avec le `let` mot clé, les membres de propriété déclarés avec le `member` mot clé et une méthode statique déclarée avec le `static` mot clé.

L’exemple suivant illustre la définition et l’utilisation de méthodes statiques. Supposons que ces définitions de méthode se trouvent dans la `SomeType` classe de la section précédente.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Méthodes abstraites et virtuelles

Le mot clé `abstract` indique qu’une méthode a un emplacement de dispatch virtuel et peut ne pas avoir de définition dans la classe. Un *emplacement de dispatch virtuel* est une entrée dans une table de fonctions gérée en interne qui est utilisée au moment de l’exécution pour rechercher des appels de fonction virtuelle dans un type orienté objet. Le mécanisme de répartition virtuelle est le mécanisme qui implémente le *polymorphisme*, une fonctionnalité importante de la programmation orientée objet. Une classe qui a au moins une méthode abstraite sans définition est une *classe abstraite*, ce qui signifie qu’aucune instance de cette classe ne peut être créée. Pour plus d’informations sur les classes abstraites, consultez [classes abstraites](../abstract-classes.md).

Les déclarations de méthode abstraite n’incluent pas de corps de méthode. Au lieu de cela, le nom de la méthode est suivi d’un signe deux-points ( :) et une signature de type pour la méthode. La signature de type d’une méthode est la même que celle indiquée par IntelliSense lorsque vous placez le pointeur de la souris sur un nom de méthode dans l’éditeur de Visual Studio Code, sauf sans nom de paramètre. Les signatures de type sont également affichées par l’interpréteur, fsi.exe, quand vous travaillez de manière interactive. La signature de type d’une méthode est formée en répertoriant les types des paramètres, suivis du type de retour, avec les symboles de séparateur appropriés. Les paramètres curryfiés sont séparés par `->` et les paramètres de tuple sont séparés par `*` . La valeur de retour est toujours séparée des arguments par un `->` symbole. Les parenthèses peuvent être utilisées pour regrouper des paramètres complexes, par exemple lorsqu’un type de fonction est un paramètre, ou pour indiquer quand un tuple est traité comme un paramètre unique plutôt que comme deux paramètres.

Vous pouvez également fournir des méthodes abstraites default Definitions en ajoutant la définition à la classe et en utilisant le `default` mot clé, comme indiqué dans le bloc de syntaxe de cette rubrique. Une méthode abstraite qui a une définition dans la même classe est équivalente à une méthode virtuelle dans d’autres langages de .NET Framework. Qu’une définition existe ou non, le `abstract` mot clé crée un emplacement de dispatch dans la table de fonctions virtuelles pour la classe.

Indépendamment du fait qu’une classe de base implémente ses méthodes abstraites, les classes dérivées peuvent fournir des implémentations de méthodes abstraites. Pour implémenter une méthode abstraite dans une classe dérivée, définissez une méthode qui a le même nom et la même signature dans la classe dérivée, à l’exception du `override` `default` mot clé ou, et fournissez le corps de la méthode. Les mots clés `override` et `default` signifient exactement la même chose. Utilisez `override` si la nouvelle méthode substitue une implémentation de classe de base ; utilisez `default` lorsque vous créez une implémentation dans la même classe que la déclaration abstraite d’origine. N’utilisez pas le `abstract` mot clé sur la méthode qui implémente la méthode qui a été déclarée abstraite dans la classe de base.

L’exemple suivant illustre une méthode abstraite `Rotate` qui a une implémentation par défaut, l’équivalent d’une .NET Framework méthode virtuelle.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

L’exemple suivant illustre une classe dérivée qui substitue une méthode de classe de base. Dans ce cas, le remplacement modifie le comportement afin que la méthode ne fasse rien.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Méthodes surchargées

Les méthodes surchargées sont des méthodes qui ont des noms identiques dans un type donné, mais qui ont des arguments différents. En F #, les arguments facultatifs sont généralement utilisés à la place des méthodes surchargées. Toutefois, les méthodes surchargées sont autorisées dans le langage, à condition que les arguments soient sous forme de tuple, et non sous forme curryfiée.

## <a name="optional-arguments"></a>Arguments facultatifs

À compter de F # 4,1, vous pouvez également avoir des arguments facultatifs avec une valeur de paramètre par défaut dans les méthodes.  Cela permet de faciliter l’interopérabilité avec le code C#.  L’exemple suivant illustre la syntaxe :

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

Notez que la valeur passée pour `DefaultParameterValue` doit correspondre au type d’entrée.  Dans l’exemple ci-dessus, il s’agit d’un `int` .  Si vous tentez de passer une valeur non entière dans, `DefaultParameterValue` une erreur de compilation se produit.

## <a name="example-properties-and-methods"></a>Exemple : propriétés et méthodes

L’exemple suivant contient un type qui contient des exemples de champs, de fonctions privées, de propriétés et de méthodes statiques.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Voir aussi

- [Members](index.md) (Membres)
