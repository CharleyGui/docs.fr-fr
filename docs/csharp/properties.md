---
title: Propriétés
description: En savoir plus sur les propriétés C#, notamment les fonctionnalités liées à la validation, les valeurs calculées, l’évaluation différée et les notifications de modification de propriété.
ms.technology: csharp-fundamentals
ms.date: 04/25/2018
ms.openlocfilehash: 5306650a10a3de0ff208f7c72c0ba520a527e746
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437940"
---
# <a name="properties"></a>Propriétés

Les propriétés sont des éléments de première classe dans C#. Le langage définit la syntaxe que les développeurs utilisent pour écrire du code qui exprime leur intention de conception avec précision.

Les propriétés auxquelles le code accède se comportent comme des champs.
Toutefois, contrairement aux champs, les propriétés sont implémentées avec des accesseurs qui définissent quelles instructions sont exécutées au moment de l’accès à une propriété ou de son assignation.

## <a name="property-syntax"></a>Syntaxe des propriétés

La syntaxe des propriétés est une extension naturelle des champs. Un champ définit un emplacement de stockage :

[!code-csharp[Person class with public fields](../../samples/snippets/csharp/properties/Person.cs#1)]

Une définition de propriété contient les déclarations de l’accesseur `get`, qui récupère la valeur de cette propriété, et de l’accesseur `set`, qui assigne cette valeur :

[!code-csharp[Person class with public properties](../../samples/snippets/csharp/properties/Person.cs#2)]

La syntaxe illustrée ci-dessus est la syntaxe *auto property*. Le compilateur génère l’emplacement de stockage pour le champ qui enregistre la propriété. Le compilateur implémente également le corps des accesseurs `get` et `set`.

Parfois, vous devez initialiser une propriété sur une valeur autre que la valeur par défaut pour son type.  C# permet cette opération en définissant une valeur après l’accolade fermante de la propriété. Vous pouvez choisir comme valeur initiale pour la propriété `FirstName` une chaîne vide au lieu de `null`. Vous pouvez le spécifier comme indiqué ci-dessous :

[!code-csharp[Person class with properties and initializer](../../samples/snippets/csharp/properties/Person.cs#3)]

Une initialisation spécifique est pratique surtout pour les propriétés en lecture seule, comme vous le verrez plus loin dans cet article.

Vous pouvez aussi définir le stockage vous-même, de la manière suivante :

[!code-csharp[Person class with properties and backing field](../../samples/snippets/csharp/properties/Person.cs#4)]

Quand une implémentation de propriété est une expression unique, vous pouvez utiliser des *membres expression-bodied* pour l’accesseur Get ou Set :

[!code-csharp[Person class with properties and expression bodied getters and setters](../../samples/snippets/csharp/properties/Person.cs#5)]

Cette syntaxe simplifiée est utilisée partout où elle est applicable dans cet article.

La définition de propriété présentée ci-dessus est une propriété en lecture-écriture. Notez la présence du mot clé `value` dans l’accesseur set. L’accesseur `set` a toujours un seul paramètre nommé `value`. L’accesseur `get` doit retourner une valeur convertible dans le type de la propriété (`string`, dans cet exemple).

Nous venons de voir les éléments de base de la syntaxe. Il existe beaucoup de variantes de cette syntaxe, qui sont adaptées aux différents idiomes de conception. Nous allons les explorer et découvrir les options syntaxiques de chacune.

## <a name="scenarios"></a>Scénarios

Les exemples ci-dessus ont montré un des cas les plus simples de définition de propriété, à savoir une propriété en lecture-écriture sans validation. En écrivant le code souhaité dans les accesseurs `get` et `set`, vous pouvez créer de nombreux scénarios différents.

### <a name="validation"></a>Validation

Vous pouvez écrire du code dans l’accesseur `set` pour garantir que les valeurs représentées par une propriété sont toujours valides. Par exemple, définissez une règle pour la classe `Person` qui spécifie que le nom ne peut pas être vide, ni contenir d’espace blanc. Le code à écrire est le suivant :

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#6)]

L’exemple précédent peut être simplifié à l’aide d’une `throw` expression dans le cadre de la validation de l’accesseur Set de la propriété :

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#7)]

L’exemple ci-dessus applique la règle selon laquelle le nom ne doit pas être vide, ni contenir d’espace blanc. Supposons qu’un développeur écrive cette ligne de code :

```csharp
hero.FirstName = "";
```

Cette assignation lève une exception `ArgumentException`. Étant donné qu’un accesseur set de propriété doit avoir un type de retour void, vous signalez les erreurs dans l’accesseur set en levant une exception.

Vous pouvez employer cette même syntaxe pour valider d’autres éléments dans votre scénario. Vous pouvez notamment vérifier les relations entre plusieurs propriétés ou effectuer une validation par rapport à des conditions externes. Toute instruction C# valide peut être utilisée dans un accesseur de propriété.

### <a name="read-only"></a>Lecture seule

Jusqu’ici, nous avons vu uniquement des définitions de propriétés qui sont en lecture-écriture dans des accesseurs publics. Ce n’est pas la seule accessibilité valide pour les propriétés.
Vous pouvez créer des propriétés en lecture seule, ou assigner une accessibilité différente aux accesseurs set et get. Supposons que votre classe `Person` doit uniquement autoriser la modification de la valeur de la propriété `FirstName` à partir des autres méthodes de cette classe. Vous pouvez alors assigner l’accessibilité `private` au lieu de `public` à l’accesseur set :

[!code-csharp[Using a private setter for a publicly readonly property](../../samples/snippets/csharp/properties/Person.cs#8)]

À présent, la propriété `FirstName` est accessible à partir de n’importe quel code, mais elle peut uniquement être assignée à partir de code dans la classe `Person`.

Vous pouvez ajouter n’importe quel modificateur d’accès restrictif à l’accesseur set ou get. Le modificateur d’accès que vous ajoutez à un accesseur doit être plus restrictif que le modificateur d’accès spécifié dans la définition de propriété. Le code ci-dessus est autorisé, car la propriété `FirstName` est `public`, mais l’accesseur set est `private`. En revanche, vous ne pouvez pas déclarer une propriété `private` avec un accesseur `public`. Les propriétés peuvent également être déclarées comme `protected`, `internal`, `protected internal` ou même `private`.

Placer le modificateur le plus restrictif sur l’accesseur `get` est également autorisé. Par exemple, vous pouvez avoir une propriété `public`, mais restreindre l’accesseur `get` à `private`. Ce scénario s’observe rarement dans la pratique.

Vous pouvez également limiter les modifications apportées à une propriété pour qu’elle puisse uniquement être définie dans un constructeur ou un initialiseur de propriété. Vous pouvez modifier la classe `Person`, comme suit :

[!code-csharp[A readonly auto implemented property](../../samples/snippets/csharp/properties/Person.cs#9)]

Cette fonctionnalité est généralement utilisée pour initialiser des collections qui sont exposées sous forme de propriétés en lecture seule :

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Propriétés calculées

Une propriété peut faire plus que simplement retourner la valeur d’un champ de membre. Vous pouvez créer des propriétés qui retournent une valeur calculée. L’objet `Person` est étendu pour retourner le nom complet, calculé en concaténant le nom et le prénom :

[!code-csharp[A computed property](../../samples/snippets/csharp/properties/Person.cs#10)]

L’exemple ci-dessus utilise la fonctionnalité d’[interpolation de chaîne](./language-reference/tokens/interpolated.md) pour créer la chaîne mise en forme du nom complet.

Vous pouvez également utiliser un *membre expression-bodied*, qui constitue un moyen plus succinct de créer la propriété `FullName` calculée :

[!code-csharp[A computed property using an expression bodied member](../../samples/snippets/csharp/properties/Person.cs#11)]

Les *membres expression-bodied* utilisent la syntaxe des *expressions lambda* pour définir des méthodes qui contiennent une seule expression. Ici, cette expression retourne le nom complet de l’objet person.

### <a name="cached-evaluated-properties"></a>Propriétés évaluées avec mise en cache

Vous pouvez combiner le concept d’une propriété calculée avec le stockage et créer une *propriété évaluée avec mise en cache*.  Par exemple, vous pouvez mettre à jour la propriété `FullName` pour que la chaîne soit mise en forme uniquement lors du premier accès à cette propriété :

[!code-csharp[Caching the value of a computed property](../../samples/snippets/csharp/properties/Person.cs#12)]

Le code ci-dessus contient toutefois un bogue. Si le code met à jour la valeur de la propriété `FirstName` ou `LastName`, le champ `fullName` qui a été précédemment évalué n’est plus valide. Vous modifiez les accesseurs `set` des propriétés `FirstName` et `LastName` pour que le champ `fullName` soit recalculé :

[!code-csharp[Invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#13)]

Dans cette version finale du code, la propriété `FullName` est évaluée uniquement si cela est nécessaire.
Si la version précédemment calculée est valide, elle est utilisée. Si elle n’est plus valide en raison d’un changement d’état, la version est recalculée. Les développeurs peuvent utiliser cette classe sans connaître les détails de l’implémentation. Ces modifications internes n’ont pas d’impact sur l’utilisation de l’objet Person. C’est l’un des principaux avantages d’utiliser des propriétés pour exposer les membres de données d’un objet.

### <a name="attaching-attributes-to-auto-implemented-properties"></a>Attachement d’attributs à des propriétés implémentées automatiquement

À compter de C# 7.3, les attributs de champ peuvent être attachés au champ de stockage généré par le compilateur dans les propriétés implémentées automatiquement. Par exemple, considérez une révision de la classe `Person` qui ajoute une propriété `Id` unique de type entier.
Vous écrivez la `Id` propriété à l’aide d’une propriété implémentée automatiquement, mais votre conception n’appelle pas pour rendre la propriété persistante `Id` . <xref:System.NonSerializedAttribute> peut être attaché seulement à des champs, et pas à des propriétés. Vous pouvez attacher <xref:System.NonSerializedAttribute> au champ de stockage pour la propriété `Id` en utilisant le spécificateur `field:` sur l’attribut, comme illustré dans l’exemple suivant :

[!code-csharp[Attaching attributes to a backing field](../../samples/snippets/csharp/properties/Person.cs#14)]

Cette technique fonctionne pour tout attribut que vous voulez attacher au champ de stockage sur la propriété implémentée automatiquement.

### <a name="implementing-inotifypropertychanged"></a>Implémentation de INotifyPropertyChanged

Il existe un dernier scénario où vous devrez écrire du code dans un accesseur de propriété : pour prendre en charge l’interface <xref:System.ComponentModel.INotifyPropertyChanged>, qui notifie les changements de valeurs aux clients de liaison de données. Quand la valeur d’une propriété change, l’objet déclenche l’événement <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> pour signaler le changement. Les bibliothèques de liaison de données mettent ensuite à jour les éléments d’affichage en fonction de cette modification. Le code ci-dessous montre comment implémenter `INotifyPropertyChanged` pour la propriété `FirstName` de la classe Person.

[!code-csharp[invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#15)]

L’opérateur `?.` est appelé *opérateur conditionnel Null*. Il recherche une référence null avant d’évaluer le côté droit de l’opérateur. Au final, s’il n’y a pas d’abonné à l’événement `PropertyChanged`, le code devant déclencher l’événement n’est pas exécuté. Dans ce cas précis, il lèverait une exception `NullReferenceException` sans cette vérification. Pour plus d’informations, consultez [`events`](events-overview.md). Cet exemple utilise également le nouvel opérateur `nameof` pour convertir le symbole de nom de propriété en sa représentation textuelle.
L’utilisation de `nameof` peut vous éviter des erreurs dues à la saisie incorrecte du nom de propriété.

L’implémentation de <xref:System.ComponentModel.INotifyPropertyChanged> est un autre exemple de cas où vous pouvez écrire du code dans vos accesseurs pour prendre en charge les scénarios souhaités.

## <a name="summing-up"></a>Résumé

Les propriétés sont une forme de champs intelligents dans une classe ou un objet. De l’extérieur de l’objet, elles apparaissent sous la forme de champs dans l’objet. Toutefois, les propriétés peuvent être implémentées avec toutes les fonctionnalités C#.
Vous pouvez écrire du code qui remplit les exigences de validation, d’accessibilité, d’évaluation différée ou toute autre exigence requise dans vos scénarios.
