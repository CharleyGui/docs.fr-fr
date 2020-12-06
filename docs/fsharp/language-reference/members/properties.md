---
title: Propriétés
description: 'En savoir plus sur les propriétés F #, qui sont des membres qui représentent des valeurs associées à un objet.'
ms.date: 05/16/2016
ms.openlocfilehash: a2a4fbfc88831dcb5cad7a2da701969b2e98b2e3
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740196"
---
# <a name="properties"></a>Propriétés

Les *Propriétés* sont des membres qui représentent des valeurs associées à un objet.

## <a name="syntax"></a>Syntaxe

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a>Notes

Les propriétés représentent la relation « has a » dans la programmation orientée objet, représentant les données associées aux instances d’objet ou, pour les propriétés statiques, avec le type.

Vous pouvez déclarer des propriétés de deux façons, selon que vous souhaitez spécifier explicitement la valeur sous-jacente (également appelée magasin de stockage) pour la propriété, ou si vous souhaitez autoriser le compilateur à générer automatiquement le magasin de stockage pour vous. En général, vous devez utiliser la méthode la plus explicite si la propriété a une implémentation non triviale et la façon automatique lorsque la propriété est simplement un wrapper simple pour une valeur ou une variable. Pour déclarer explicitement une propriété, utilisez le `member` mot clé. Cette syntaxe déclarative est suivie par la syntaxe qui spécifie les `get` `set` méthodes et, également appelées *accesseurs*. Les différentes formes de syntaxe explicite indiquées dans la section syntaxe sont utilisées pour les propriétés en lecture/écriture, en lecture seule et en écriture seule. Pour les propriétés en lecture seule, vous définissez uniquement une `get` méthode ; pour les propriétés en écriture seule, définissez uniquement une `set` méthode. Notez que lorsqu’une propriété possède des `get` `set` accesseurs et, l’autre syntaxe vous permet de spécifier des attributs et des modificateurs d’accessibilité qui sont différents pour chaque accesseur, comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

Pour les propriétés en lecture/écriture, qui ont à la fois une `get` `set` méthode et, l’ordre de `get` et `set` peut être inversé. Vous pouvez également fournir la syntaxe indiquée pour `get` uniquement et la syntaxe indiquée pour `set` uniquement au lieu d’utiliser la syntaxe combinée. Cela simplifie la procédure de commentaire de la personne `get` ou de la `set` méthode, si c’est une opération que vous devrez peut-être faire. Cette alternative à l’utilisation de la syntaxe combinée est illustrée dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

Les valeurs privées qui contiennent les données pour les propriétés sont appelées *magasins* de stockage. Pour que le compilateur crée automatiquement le magasin de stockage, utilisez les mots clés `member val` , omettez l’auto-identificateur, puis fournissez une expression pour initialiser la propriété. Si la propriété doit être mutable, incluez `with get, set` . Par exemple, le type de classe suivant comprend deux propriétés implémentées automatiquement. `Property1` est en lecture seule et est initialisé à l’argument fourni au constructeur principal, et `Property2` est une propriété définissable initialisée à une chaîne vide :

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

Les propriétés implémentées automatiquement font partie de l’initialisation d’un type. elles doivent donc être incluses avant toute autre définition de membre, tout comme les `let` liaisons et les `do` liaisons dans une définition de type. Notez que l’expression qui initialise une propriété implémentée automatiquement n’est évaluée qu’au moment de l’initialisation, et non à chaque accès à la propriété. Ce comportement diffère du comportement d’une propriété implémentée explicitement. Cela signifie que le code permettant d’initialiser ces propriétés est ajouté au constructeur d’une classe. Prenons le code suivant qui illustre cette différence :

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn $"class1.AutoProperty = %d{class1.AutoProperty}"
printfn $"class1.ExplicitProperty = %d{class1.ExplicitProperty}"
```

**Sortie**

```console
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

La sortie du code précédent indique que la valeur de la propriété autoproperty est inchangée quand elle est appelée à plusieurs reprises, tandis que le ExplicitProperty change chaque fois qu’elle est appelée. Cela démontre que l’expression pour une propriété implémentée automatiquement n’est pas évaluée à chaque fois, comme c’est le cas de la méthode Getter pour la propriété Explicit.

>[!WARNING]
>Certaines bibliothèques, telles que le Entity Framework (), `System.Data.Entity` effectuent des opérations personnalisées dans les constructeurs de classe de base qui ne fonctionnent pas correctement avec l’initialisation des propriétés implémentées automatiquement. Dans ce cas, essayez d’utiliser des propriétés explicites.

Les propriétés peuvent être des membres de classes, de structures, d’unions discriminées, d’enregistrements, d’interfaces et d’extensions de type. elles peuvent également être définies dans des expressions d’objet.

Les attributs peuvent être appliqués aux propriétés. Pour appliquer un attribut à une propriété, écrivez l’attribut sur une ligne distincte avant la propriété. Pour plus d’informations, consultez [Attributs](../attributes.md).

Par défaut, les propriétés sont publiques. Les modificateurs d’accessibilité peuvent également être appliqués aux propriétés. Pour appliquer un modificateur d’accessibilité, ajoutez-le immédiatement avant le nom de la propriété s’il est destiné à s’appliquer aux deux `get` méthodes et. `set` Ajoutez-le avant les `get` `set` Mots clés et si une accessibilité différente est requise pour chaque accesseur. Le *modificateur Accessibility* peut être l’un des suivants : `public` , `private` , `internal` . Pour obtenir plus d'informations, voir [Contrôle d'accès](../access-control.md).

Les implémentations de propriétés sont exécutées chaque fois qu’un utilisateur accède à une propriété.

## <a name="static-and-instance-properties"></a>Propriétés statiques et d’instance

Les propriétés peuvent être des propriétés statiques ou d’instance. Les propriétés statiques peuvent être appelées sans instance et sont utilisées pour les valeurs associées au type, et non avec des objets individuels. Pour les propriétés statiques, omettez l’auto-identificateur. L’auto-identificateur est requis pour les propriétés d’instance.

La définition de propriété statique suivante est basée sur un scénario dans lequel vous avez un champ statique `myStaticValue` qui est le magasin de stockage pour la propriété.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

Les propriétés peuvent également être de type tableau, auquel cas elles sont appelées *propriétés indexées*. Pour plus d’informations, consultez [propriétés indexées](indexed-properties.md).

## <a name="type-annotation-for-properties"></a>Annotation de type pour les propriétés

Dans de nombreux cas, le compilateur dispose de suffisamment d’informations pour déduire le type d’une propriété à partir du type du magasin de stockage, mais vous pouvez définir le type explicitement en ajoutant une annotation de type.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>Utilisation d’accesseurs set de propriété

Vous pouvez définir des propriétés qui fournissent `set` des accesseurs à l’aide de l' `<-` opérateur.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

La sortie est **20**.

## <a name="abstract-properties"></a>Propriétés abstraites

Les propriétés peuvent être abstraites. Comme pour les méthodes, `abstract` signifie simplement qu’il existe une répartition virtuelle associée à la propriété. Les propriétés abstraites peuvent être véritablement abstraites, autrement dit, sans définition dans la même classe. La classe qui contient une telle propriété est par conséquent une classe abstraite. Abstraite peut simplement signifier qu’une propriété est virtuelle, et dans ce cas, une définition doit être présente dans la même classe. Notez que les propriétés abstraites ne doivent pas être privées et, si un accesseur est abstrait, l’autre doit également être abstraite. Pour plus d’informations sur les classes abstraites, consultez [classes abstraites](../abstract-classes.md).

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>Voir aussi

- [Members](index.md) (Membres)
- [Méthodes](methods.md)
