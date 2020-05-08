---
title: Mettre à jour votre code base pour utiliser des types référence Nullable
description: Choisissez la meilleure stratégie pour mettre à niveau votre base de code afin d’utiliser des types de référence Nullable.
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: 5909eb9ffe1f5398fc2eb74848b82f8fe9516548
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975332"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Mettre à jour les bibliothèques pour utiliser des types référence Nullable et communiquer des règles Nullable aux appelants

L’ajout de [types de référence Nullable](nullable-references.md) signifie que vous pouvez déclarer si une `null` valeur est autorisée ou non pour chaque variable. En outre, vous pouvez appliquer un certain nombre d’attributs `AllowNull`: `DisallowNull`, `MaybeNull`, `NotNull`, `NotNullWhen`, `MaybeNullWhen`, et `NotNullIfNotNull` pour décrire complètement les États null de l’argument et les valeurs de retour. Cela offre une excellente expérience lorsque vous écrivez du code. Vous recevez des avertissements si une variable qui `null`n’accepte pas les valeurs NULL peut avoir la valeur. Vous recevez des avertissements si une variable Nullable n’est pas vérifiée par null avant d’être déréférencée. La mise à jour de vos bibliothèques peut prendre du temps, mais les avantages le justifient. Plus d’informations que vous fournissez au compilateur sur les `null` *cas où* une valeur est autorisée ou interdite, les meilleurs avertissements que les utilisateurs de votre API obtiendront. Commençons par un exemple familier. Imaginez que votre bibliothèque possède l’API suivante pour récupérer une chaîne de ressource :

```csharp
bool TryGetMessage(string key, out string message)
```

L’exemple précédent suit le modèle `Try*` familier dans .net. Il existe deux arguments de référence pour cette API : `key` et le `message` paramètre. Cette API comporte les règles suivantes relatives à la valeur null de ces arguments :

- Les appelants ne `null` doivent pas passer comme `key`argument pour.
- Les appelants peuvent passer une variable dont la `null` valeur est l’argument `message`pour.
- Si la `TryGetMessage` méthode retourne `true`, la valeur de `message` n’est pas null. Si la valeur de retour `false,` est la valeur `message` de (et son état null) est null.

La règle pour `key` peut être entièrement exprimée par le type de variable `key` : doit être un type de référence non Nullable. Le `message` paramètre est plus complexe. Elle autorise `null` comme argument, mais garantit que, en cas de réussite, `out` cet argument n’est pas null. Pour ces scénarios, vous avez besoin d’un vocabulaire plus riche pour décrire les attentes.

La mise à jour de votre bibliothèque pour les références Nullable nécessite `?` plus que l’extinction sur certaines variables et certains noms de types. L’exemple précédent montre que vous devez examiner vos API et prendre en compte vos attentes pour chaque argument d’entrée. Considérez les garanties pour la valeur de retour et `out` les `ref` arguments ou sur le retour de la méthode. Ensuite, communiquez ces règles au compilateur et le compilateur fournira des avertissements quand les appelants ne respectent pas ces règles.

Ce travail prend du temps. Commençons par des stratégies pour rendre votre bibliothèque ou votre application prenant en charge les valeurs NULL, tout en équilibrant d’autres exigences et livrables. Vous verrez comment équilibrer le développement en cours et activer les types de référence Nullable. Vous découvrirez les défis liés aux définitions de type générique. Vous apprendrez à appliquer des attributs pour décrire des conditions préalables et postérieures à des API individuelles.

## <a name="choose-a-strategy-for-nullable-reference-types"></a>Choisir une stratégie pour les types de référence Nullable

Le premier choix est si les types de référence Nullable doivent être activés ou désactivés par défaut. Vous avez deux stratégies :

- Activez les types de référence Nullable pour l’ensemble du projet et désactivez-le dans le code qui n’est pas prêt.
- Activez uniquement les types référence Nullable pour le code qui a été annoté pour les types référence Nullable.

La première stratégie fonctionne mieux lorsque vous ajoutez d’autres fonctionnalités à la bibliothèque lors de sa mise à jour pour les types de référence Nullable. Tout nouveau développement prend en charge les valeurs NULL. Lorsque vous mettez à jour le code existant, vous activez les types de référence Nullable dans ces classes.

Après cette première stratégie, vous procédez comme suit :

1. Activez les types de référence Nullable pour l’ensemble du projet `<Nullable>enable</Nullable>` en ajoutant l’élément à vos fichiers *csproj* .
1. Ajoutez le `#nullable disable` pragma à chaque fichier source de votre projet.
1. Lorsque vous travaillez sur chaque fichier, supprimez le pragma et résolvez tous les avertissements.

Cette première stratégie a plus de travail initial pour ajouter le pragma à chaque fichier. L’avantage est que chaque nouveau fichier de code ajouté au projet sera activé pour la valeur null. Tout nouveau travail prend en charge les valeurs null ; seul le code existant doit être mis à jour.

La deuxième stratégie fonctionne mieux si la bibliothèque est généralement stable, et l’objectif principal du développement est d’adopter des types de référence Nullable. Vous activez les types de référence Nullable quand vous annotez des API. Lorsque vous avez terminé, vous activez les types de référence Nullable pour l’ensemble du projet.

Après cette seconde stratégie, vous effectuez les opérations suivantes :

1. Ajoutez le `#nullable enable` pragma au fichier que vous souhaitez rendre compatible avec la valeur null.
1. Résolvez tous les avertissements.
1. Poursuivez ces deux premières étapes jusqu’à ce que vous ayez pris en charge la valeur null de la bibliothèque entière.
1. Activez les types Nullable pour l’ensemble du projet en `<Nullable>enable</Nullable>` ajoutant l’élément à vos fichiers *csproj* .
1. Supprimez `#nullable enable` les pragmas, car ils ne sont plus nécessaires.

Cette deuxième stratégie a moins de travail avant. Le compromis est que la première tâche lorsque vous créez un nouveau fichier consiste à ajouter le pragma et à le rendre compatible avec la valeur null. Si des développeurs de votre équipe oublient, ce nouveau code est désormais dans le backlog de travail pour rendre tout le code prenant en charge la valeur null.

Les stratégies que vous choisissez dépendent de la quantité de développement actif dans votre projet. Plus votre projet est mature et stable, plus la seconde stratégie est performante. Plus vous développez de fonctionnalités, mieux la première stratégie.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Les avertissements de type Nullable introduisent-ils des modifications avec rupture ?

Avant d’activer les types de référence Nullable, les variables sont considérées comme *Nullable oublie*. Une fois que vous activez les types de référence Nullable, toutes ces variables ne peuvent pas avoir la valeur *null*. Le compilateur émet des avertissements si ces variables ne sont pas initialisées à des valeurs non null.

Une autre source probable d’avertissements est celle des valeurs de retour lorsque la valeur n’a pas été initialisée.

La première étape de la résolution des avertissements du compilateur consiste `?` à utiliser des annotations sur les types de paramètres et de retour pour indiquer quand les arguments ou les valeurs de retour peuvent être null. Lorsque les variables de référence ne doivent pas avoir la valeur null, la déclaration d’origine est correcte. Dans ce cas, votre objectif n’est pas simplement de corriger les avertissements. L’objectif le plus important est de faire en sorte que le compilateur comprenne votre intention pour les valeurs NULL potentielles. Lorsque vous examinez les avertissements, vous atteignez votre prochaine décision majeure pour votre bibliothèque. Voulez-vous envisager de modifier les signatures d’API pour communiquer plus clairement votre intention de conception ? Une meilleure signature d’API pour `TryGetMessage` la méthode examinée précédemment peut être :

```csharp
string? TryGetMessage(string key);
```

La valeur de retour indique la réussite ou l’échec et transporte la valeur si la valeur a été trouvée. Dans de nombreux cas, la modification des signatures d’API peut améliorer la façon dont elles communiquent les valeurs NULL.

Toutefois, pour les bibliothèques publiques ou les bibliothèques avec des bases d’utilisateurs volumineuses, vous préférerez peut-être ne pas introduire de modifications de signature d’API. Dans ces cas-là, et d’autres modèles courants, vous pouvez appliquer des attributs pour définir plus clairement quand un argument ou `null`une valeur de retour peut être. Si vous envisagez de modifier la surface de votre API, vous constaterez sans doute que les annotations de type `null` ne suffisent pas pour décrire les valeurs des arguments ou des valeurs de retour. Dans ces instances, vous pouvez appliquer des attributs pour décrire plus clairement une API.

## <a name="attributes-extend-type-annotations"></a>Les attributs étendent les annotations de type

Plusieurs attributs ont été ajoutés pour exprimer des informations supplémentaires sur l’État null des variables. Tout le code que vous avez écrit avant C# 8 a introduit des types de référence Nullable était *null oublie*. Cela signifie que toute variable de type référence peut avoir la valeur null, mais que les vérifications de valeur NULL ne sont pas requises. Une fois que votre code prend en *charge les valeurs NULL*, ces règles changent. Les types référence ne doivent jamais `null` être la valeur, et les types référence Nullable doivent `null` être vérifiés avant d’être déréférencés.

Les règles de vos API sont probablement plus compliquées, comme vous l’avez `TryGetValue` vu dans le scénario d’API. La plupart de vos API ont des règles plus complexes pour le moment où les `null`variables peuvent ou ne peuvent pas être. Dans ce cas, vous utiliserez des attributs pour exprimer ces règles. Les attributs qui décrivent la sémantique de votre API se trouvent dans l’article sur les [attributs qui affectent l’analyse Nullable](./language-reference/attributes/nullable-analysis.md).

## <a name="generic-definitions-and-nullability"></a>Définitions génériques et possibilité de valeur null

La communication correcte de l’État null des types génériques et des méthodes génériques requiert une attention particulière. Cela découle du fait qu’un type valeur Nullable et un type référence Nullable sont fondamentalement différents. Un `int?` est un synonyme de `Nullable<int>`, `string?` tandis `string` que est associé à un attribut ajouté par le compilateur. Le résultat est que le compilateur ne peut pas générer de `T?` code correct pour `T` sans savoir `class` si est `struct`un ou un.

Cela ne signifie pas que vous ne pouvez pas utiliser un type Nullable (type valeur ou type référence) comme argument de type pour un type générique fermé. Et sont des instanciations valides de `List<T>` `List<string?>` `List<int?>`

Cela signifie que vous ne pouvez pas utiliser `T?` dans une déclaration de classe ou de méthode générique sans contraintes. Par exemple, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> ne peut pas être modifié `T?`pour retourner. Vous pouvez contourner cette limitation en ajoutant la `struct` contrainte `class` ou. Avec l’une de ces contraintes, le compilateur sait comment générer du code pour `T` et `T?`.

Vous pouvez restreindre les types utilisés pour un argument de type générique à des types non nullables. Pour ce faire, vous pouvez ajouter `notnull` la contrainte sur cet argument de type. Quand cette contrainte est appliquée, l’argument de type ne doit pas être un type Nullable.

## <a name="late-initialized-properties-data-transfer-objects-and-nullability"></a>Propriétés initialisées tardivement, objets Transfert de données et possibilité de valeur null

Indiquant la possibilité de valeur null des propriétés qui sont initialisées tardivement, ce qui signifie qu’elles sont définies après la construction, peut nécessiter une attention particulière afin de garantir que votre classe continue d’exprimer correctement l’intention de conception d’origine.

Les types qui contiennent des propriétés initialisées tardivement, telles que les objets Transfert de données (DTO), sont souvent instanciés par une bibliothèque externe, comme un ORM de base de données (mappage relationnel d’objets), un désérialiseur ou un autre composant qui remplit automatiquement les propriétés d’une autre source.

Considérez la classe DTO suivante, avant d’activer les types de référence Nullable, qui représente un Student :

```csharp
class Student
{
    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string VehicleRegistration { get; set; }
}
```

L’intention de conception (indiquée dans ce cas par `Required` l’attribut) suggère que dans ce système, `FirstName` les `LastName` propriétés et sont **obligatoires**et, par conséquent, non null.

La `VehicleRegistration` propriété n’étant **pas obligatoire**, elle peut avoir la valeur null.

Quand vous activez les types de référence Nullable, vous souhaitez indiquer sur notre DTO les propriétés qui peuvent être Nullable, conformément à votre intention d’origine :

```csharp
class Student
{
    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string? VehicleRegistration { get; set; }
}
```

Pour ce DTO, la seule propriété qui peut être null est ``VehicleRegistration``.

Toutefois, le compilateur déclenche `CS8618` des avertissements pour `FirstName` et `LastName`, indiquant que les propriétés non Nullable ne sont pas initialisées.

Trois options sont à votre disposition pour résoudre les avertissements du compilateur de manière à conserver l’intention d’origine. L’une de ces options est valide. vous devez choisir celui qui convient le mieux à vos exigences de style et de conception de codage.

### <a name="initialize-in-the-constructor"></a>Initialiser dans le constructeur

Pour résoudre les avertissements non initialisés, la méthode idéale consiste à initialiser les propriétés dans le constructeur :

```csharp
class Student
{
    public Student(string firstName, string lastName)
    {
        FirstName = firstName;
        LastName = lastName;
    }

    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string? VehicleRegistration { get; set; }
}
```

Cette approche fonctionne uniquement si la bibliothèque que vous utilisez pour instancier la classe prend en charge le passage de paramètres dans le constructeur.

En outre, une bibliothèque peut prendre en charge la transmission de *certaines* propriétés dans le constructeur, mais pas toutes.
Par exemple, EF Core prend en charge la [liaison de constructeur](/ef/core/modeling/constructors) pour les propriétés de colonne normales, mais pas pour les propriétés de navigation.

Consultez la documentation sur la bibliothèque qui instancie votre classe pour comprendre la portée à laquelle elle prend en charge la liaison de constructeur.

### <a name="property-with-nullable-backing-field"></a>Propriété avec champ de stockage Nullable

Si la liaison de constructeur ne fonctionne pas pour vous, une façon de traiter ce problème consiste à avoir une propriété qui n’accepte pas les valeurs NULL avec un champ de stockage Nullable :

```csharp
private string? _firstName;

[Required]
public string FirstName
{
    set => _firstName = value;
    get => _firstName
           ?? throw new InvalidOperationException("Uninitialized " + nameof(FirstName))
}
```

Dans ce scénario, si vous `FirstName` accédez à la propriété avant qu’elle n’ait été initialisée, le code lève `InvalidOperationException`une, car le contrat d’API a été utilisé de façon incorrecte.

Vous devez considérer que certaines bibliothèques peuvent avoir des considérations particulières lors de l’utilisation de champs de stockage. Par exemple, EF Core devrez peut-être être configuré pour utiliser correctement les [champs de sauvegarde](/ef/core/modeling/backing-field) .

### <a name="initialize-the-property-to-null"></a>Initialise la propriété avec la valeur null

Comme une alternative terser à l’utilisation d’un champ de stockage Nullable, ou si la bibliothèque qui instancie votre classe n’est pas compatible avec cette approche, vous pouvez simplement initialiser `null` la propriété directement, à l’aide de l’opérateur null-`!`indulgent avec () :

```csharp
[Required]
public string FirstName { get; set; } = null!;

[Required]
public string LastName { get; set; } = null!;

public string? VehicleRegistration { get; set; }
```

Vous n’observerez jamais une valeur null réelle au moment de l’exécution sauf en raison d’un bogue de programmation, en accédant à la propriété avant qu’elle ait été correctement initialisée.

## <a name="see-also"></a>Voir aussi

- [Migration d’une base de code existante vers des références nullables](tutorials/upgrade-to-nullable-references.md)
- [Utilisation des types de référence Nullable dans EF Core](/ef/core/miscellaneous/nullable-reference-types)
