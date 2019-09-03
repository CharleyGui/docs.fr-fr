---
title: Mettre à niveau les API avec des attributs pour définir des attentes null
description: Cet article explique les motivations et les techniques permettant d’ajouter des attributs descriptifs pour décrire l’État null des arguments et les valeurs de retour des API
ms.date: 07/31/2019
ms.openlocfilehash: eebd3d190b8c93833de6e1c1f1594c1c1f56e14e
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "70234668"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Mettre à jour les bibliothèques pour utiliser des types référence Nullable et communiquer des règles Nullable aux appelants.

L’ajout de [types de référence Nullable](nullable-references.md) signifie que vous pouvez déclarer si une `null` valeur est autorisée ou non pour chaque variable. Cela offre une excellente expérience lorsque vous écrivez du code. Vous recevez des avertissements si une variable qui `null`n’accepte pas les valeurs NULL peut avoir la valeur. Vous recevez des avertissements si une variable Nullable n’est pas vérifiée par null avant d’être déréférencée. La mise à jour de vos bibliothèques peut prendre du temps, mais les avantages le justifient. Plus d’informations que vous fournissez au compilateur sur les `null` *cas où* une valeur est autorisée ou interdite, les meilleurs avertissements que les utilisateurs de votre API obtiendront. Commençons par un exemple familier. Imaginez que votre bibliothèque possède l’API suivante pour récupérer une chaîne de ressource:

```csharp
bool TryGetMessage(string key, out string message)
```

L’exemple précédent suit le modèle `Try*` familier dans .net. Il existe deux arguments de référence pour cette API: `key` et le `message` paramètre. Cette API comporte les règles suivantes relatives à la valeur null de ces arguments:

- Les appelants ne `null` doivent pas passer comme `key`argument pour.
- Les appelants peuvent passer une variable dont la `null` valeur est l’argument `message`pour.
- Si la `TryGetMessage` méthode retourne `true`, la valeur de `message` n’est pas null. Si la valeur de retour `false,` est la valeur `message` de (et son état null) est null.

La règle pour `key` peut être entièrement exprimée par le type de variable `key` : doit être un type de référence non Nullable. Le `message` paramètre est plus complexe. Elle autorise `null` comme argument, mais garantit que, en cas de réussite, `out` cet argument n’est pas null. Pour ces scénarios, vous avez besoin d’un vocabulaire plus riche pour décrire les attentes.

La mise à jour de votre bibliothèque pour les références Nullable nécessite `?` plus que l’extinction sur certaines variables et certains noms de types. L’exemple précédent montre que vous devez examiner vos API et prendre en compte vos attentes pour chaque argument d’entrée. Considérez les garanties pour la valeur de retour et `out` les `ref` arguments ou sur le retour de la méthode. Ensuite, communiquez ces règles au compilateur et le compilateur fournira des avertissements quand les appelants ne respectent pas ces règles.

Ce travail prend du temps. Commençons par des stratégies pour rendre votre bibliothèque ou votre application prenant en charge les valeurs NULL, tout en équilibrant d’autres exigences et livrables. Vous verrez comment équilibrer le développement en cours et activer les types de référence Nullable. Vous découvrirez les défis liés aux définitions de type générique. Vous apprendrez à appliquer des attributs pour décrire des conditions préalables et postérieures à des API individuelles.

## <a name="choose-a-nullable-strategy"></a>Choisir une stratégie Nullable

Le premier choix est si les types de référence Nullable doivent être activés ou désactivés par défaut. Vous avez deux stratégies:

- Activez les types de référence Nullable pour l’ensemble du projet et désactivez-le dans le code qui n’est pas prêt.
- Activez uniquement les types référence Nullable pour le code qui a été annoté pour les types référence Nullable.

La première stratégie fonctionne mieux lorsque vous ajoutez d’autres fonctionnalités à la bibliothèque lors de sa mise à jour pour les types de référence Nullable. Tout nouveau développement prend en charge les valeurs NULL. Lorsque vous mettez à jour le code existant, vous activez les types de référence Nullable dans ces classes.

Après cette première stratégie, vous procédez comme suit:

1. Activez les types Nullable pour l’ensemble du projet en `<Nullable>enable</Nullable>` ajoutant l’élément à vos fichiers *csproj* . 
1. Ajoutez le `#nullable disable` pragma à chaque fichier source de votre projet. 
1. Lorsque vous travaillez sur chaque fichier, supprimez le pragma et résolvez tous les avertissements.

Cette première stratégie a plus de travail initial pour ajouter le pragma à chaque fichier. L’avantage est que chaque nouveau fichier de code ajouté au projet sera activé pour la valeur null. Tout nouveau travail prend en charge les valeurs null; seul le code existant doit être mis à jour.

La deuxième stratégie fonctionne mieux si la bibliothèque est généralement stable, et l’objectif principal du développement est d’adopter des types de référence Nullable. Vous activez les types de référence Nullable quand vous annotez des API. Lorsque vous avez terminé, vous activez les types de référence Nullable pour l’ensemble du projet.

Après cette seconde stratégie, vous effectuez les opérations suivantes:

1. Ajoutez le `#nullable enable` pragma au fichier que vous souhaitez rendre compatible avec la valeur null.
1. Résolvez tous les avertissements.
1. Poursuivez ces deux premières étapes jusqu’à ce que vous ayez pris en charge la valeur null de la bibliothèque entière.
1. Activez les types Nullable pour l’ensemble du projet en `<Nullable>enable</Nullable>` ajoutant l’élément à vos fichiers *csproj* . 
1. Supprimez `#nullable enable` les pragmas, car ils ne sont plus nécessaires.

Cette deuxième stratégie a moins de travail avant. Le compromis est que la première tâche lorsque vous créez un nouveau fichier consiste à ajouter le pragma et à le rendre compatible avec la valeur null. Si des développeurs de votre équipe oublient, ce nouveau code est désormais dans le backlog de travail pour rendre tout le code prenant en charge la valeur null.

Les stratégies que vous choisissez dépendent de la quantité de développement actif dans votre projet. Plus votre projet est mature et stable, plus la seconde stratégie est performante. Plus vous développez de fonctionnalités, mieux la première stratégie.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Les avertissements de type Nullable introduisent-ils des modifications avec rupture?

Avant d’activer les types de référence Nullable, les variables sont considérées comme *Nullable oublie*. Une fois que vous activez les types de référence Nullable, toutes ces variables ne peuvent pas avoir la valeur *null*. Le compilateur émet des avertissements si ces variables ne sont pas initialisées à des valeurs non null.

Une autre source probable d’avertissements est celle des valeurs de retour lorsque la valeur n’a pas été initialisée.

La première étape de la résolution des avertissements du compilateur consiste `?` à utiliser des annotations sur les types de paramètres et de retour pour indiquer quand les arguments ou les valeurs de retour peuvent être null. Lorsque les variables de référence ne doivent pas avoir la valeur null, la déclaration d’origine est correcte. Dans ce cas, votre objectif n’est pas simplement de corriger les avertissements. L’objectif le plus important est de faire en sorte que le compilateur comprenne votre intention pour les valeurs NULL potentielles. Lorsque vous examinez les avertissements, vous atteignez votre prochaine décision majeure pour votre bibliothèque. Voulez-vous envisager de modifier les signatures d’API pour communiquer plus clairement votre intention de conception? Une meilleure signature d’API pour `TryGetMessage` la méthode examinée précédemment peut être:

```csharp
string? TryGetMessage(string key);
```

La valeur de retour indique la réussite ou l’échec et transporte la valeur si la valeur a été trouvée. Dans de nombreux cas, la modification des signatures d’API peut améliorer la façon dont elles communiquent les valeurs NULL.

Toutefois, pour les bibliothèques publiques ou les bibliothèques avec des bases d’utilisateurs volumineuses, vous préférerez peut-être ne pas introduire de modifications de signature d’API. Dans ces cas-là, et d’autres modèles courants, vous pouvez appliquer des attributs pour définir plus clairement quand un argument ou `null`une valeur de retour peut être. Si vous envisagez de modifier la surface de votre API, vous constaterez sans doute que les annotations de type `null` ne suffisent pas pour décrire les valeurs des arguments ou des valeurs de retour. Dans ces instances, vous pouvez appliquer des attributs pour décrire plus clairement une API. 

## <a name="attributes-extend-type-annotations"></a>Les attributs étendent les annotations de type

Plusieurs attributs ont été ajoutés pour exprimer des informations supplémentaires sur l’État null des variables. Tout le code que vous C# avez écrit avant 8 introduit les types de référence Nullable était *null oublie*. Cela signifie que toute variable de type référence peut avoir la valeur null, mais que les vérifications de valeur NULL ne sont pas requises. Une fois que votre code prend en *charge les valeurs NULL*, ces règles changent. Les types référence ne doivent jamais `null` être la valeur, et les types référence Nullable doivent `null` être vérifiés avant d’être déréférencés.

Les règles de vos API sont probablement plus compliquées, comme vous l’avez `TryGetValue` vu dans le scénario d’API. La plupart de vos API ont des règles plus complexes pour le moment où les `null`variables peuvent ou ne peuvent pas être. Dans ce cas, vous allez utiliser l’un des attributs suivants pour exprimer ces règles:

- [AllowNull a](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Un argument d’entrée n’acceptant pas les valeurs NULL peut avoir la valeur null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Un argument d’entrée Nullable ne doit jamais avoir la valeur null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Une valeur de retour qui n’accepte pas les valeurs NULL peut être null.
- [NOTNULL](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Une valeur de retour Nullable ne sera jamais null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Un argument non Nullable `out` ou `ref` peut avoir la valeur NULL lorsque la valeur de retour remplit une condition.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Un argument `out` Nullable `ref` ou ne peut pas être NULL lorsque la valeur de retour remplit une condition.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Une valeur de retour n’est pas null si l’argument d’entrée pour le paramètre spécifié n’est pas null.

Les descriptions précédentes sont une référence rapide à ce que fait chaque attribut. Chaque section suivante décrit le comportement et la signification de manière plus approfondie.

L’ajout de ces attributs donne au compilateur plus d’informations sur les règles de votre API. Quand le code appelant est compilé dans un contexte compatible avec la valeur null, le compilateur avertit les appelants lorsqu’ils enfreignent ces règles. Ces attributs n’autorisent pas de vérifications supplémentaires sur votre implémentation.

## <a name="specify-preconditions-allownull-and-disallownull"></a>Spécifier les conditions préalables: `AllowNull` et`DisallowNull`

Prenons l’exemple d’une propriété en lecture/ `null` écriture qui n’est jamais retournée, car elle a une valeur par défaut raisonnable. Les appelants `null` passent à l’accesseur Set lors de la définition de cette valeur par défaut. Par exemple, imaginez un système de messagerie qui demande un nom d’écran dans une salle de conversation. Si aucune valeur n’est fournie, le système génère un nom aléatoire:

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

Quand vous compilez le code précédent dans un contexte oublie Nullable, tout est parfait. Une fois que vous activez les types référence `ScreenName` Nullable, la propriété devient une référence qui n’accepte pas les valeurs NULL. C’est correct pour l' `get` accesseur: il ne `null`retourne jamais. Les appelants n’ont pas besoin de vérifier la `null`propriété retournée pour. Mais maintenant, le paramétrage `null` de la propriété pour générer un avertissement. Pour continuer à prendre en charge ce type de code, vous ajoutez l' <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> attribut à la propriété, comme illustré dans le code suivant: 

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

Vous devrez peut-être ajouter `using` une directive <xref:System.Diagnostics.CodeAnalysis> pour utiliser ce et d’autres attributs abordés dans cet article. L’attribut est appliqué à la propriété, et non `set` à l’accesseur. L' `AllowNull` attribut spécifie des *conditions préalables*et s’applique uniquement aux entrées. L' `get` accesseur a une valeur de retour, mais aucun argument d’entrée. Par conséquent, `AllowNull` l’attribut s’applique uniquement `set` à l’accesseur.

L’exemple précédent montre ce qu’il faut rechercher lors de `AllowNull` l’ajout de l’attribut à un argument:

1. Le contrat général pour cette variable est qu’elle ne doit `null`pas l’être, donc vous souhaitez un type de référence non Nullable.
1. Il existe des scénarios pour la variable `null`d’entrée, bien qu’il ne s’agisse pas de l’utilisation la plus courante.

La plupart du temps, vous aurez besoin de cet attribut `in`pour `out`les propriétés `ref` , ou, et les arguments. L' `AllowNull` attribut est le meilleur choix lorsqu’une variable est généralement non null, mais que vous devez autoriser `null` comme condition préalable.

À l’inverse, les scénarios `DisallowNull`d’utilisation de sont les suivants: Vous utilisez cet attribut pour spécifier qu’une variable d’entrée d’un type Nullable ne `null`doit pas être. Considérez une propriété `null` où est la valeur par défaut, mais les clients peuvent uniquement la définir sur une valeur non null. Examinons le code ci-dessous.

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

Le code précédent est la meilleure façon d’exprimer votre conception `ReviewComment` `null`de, `null`mais ne peut pas avoir la valeur. Une fois que ce code prend en charge les valeurs NULL, vous pouvez exprimer ce concept plus clairement <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>aux appelants à l’aide du:

```csharp
[DisallowNull] 
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

Dans un contexte Nullable, l' `ReviewComment` `get` accesseur peut retourner la valeur par `null`défaut de. Le compilateur vous avertit qu’il doit être vérifié avant l’accès. En outre, il avertit les appelants que, même s’ils `null`peuvent l’être, les appelants ne `null`doivent pas lui affecter explicitement la valeur. L' `DisallowNull` attribut spécifie également une *condition préalable*, il n’affecte pas l' `get` accesseur. Vous devez choisir d’utiliser l' `DisallowNull` attribut lorsque vous observez les caractéristiques suivantes:

1. La variable peut être `null` dans des scénarios de base, souvent lors de la première instanciation.
1. La variable ne doit pas avoir explicitement `null`la valeur.

Ces situations sont courantes dans le code qui a été initialement *null oublie*. Les propriétés de l’objet sont peut-être définies dans deux opérations d’initialisation distinctes. Il se peut que certaines propriétés soient définies uniquement après la fin d’un travail asynchrone.

Les `AllowNull` attributs `DisallowNull` et vous permettent de spécifier que les conditions préalables sur les variables peuvent ne pas correspondre aux annotations Nullable sur ces variables. Celles-ci fournissent des informations plus détaillées sur les caractéristiques de votre API. Ces informations supplémentaires permettent aux appelants d’utiliser correctement votre API. N’oubliez pas de spécifier des conditions préalables à l’aide des attributs suivants:

- [AllowNull a](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Un argument d’entrée n’acceptant pas les valeurs NULL peut avoir la valeur null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Un argument d’entrée Nullable ne doit jamais avoir la valeur null.

## <a name="specify-post-conditions-maybenull-and-notnull"></a>Spécifier les conditions postérieures `MaybeNull` : et`NotNull`

Supposons que vous avez une méthode avec la signature suivante:

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

Vous avez probablement écrit une méthode comme celle-ci `null` pour retourner lorsque le nom recherché n’a pas été trouvé. Indique `null` clairement que l’enregistrement n’a pas été trouvé. Dans cet exemple, vous allez probablement modifier le type de retour `Customer` de `Customer?`en. La déclaration de la valeur de retour en tant que type référence Nullable spécifie clairement l’objectif de cette API. 

Pour les raisons couvertes par les [définitions génériques et la possibilité de valeur null](#generic-definitions-and-nullability) , cette technique ne fonctionne pas avec les méthodes génériques. Vous pouvez avoir une méthode générique qui suit un modèle similaire:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Vous ne pouvez pas spécifier que la valeur `T?`de retour est. La méthode retourne `null` lorsque l’élément recherché est introuvable. Étant donné que vous ne `T?` pouvez pas déclarer un type de `MaybeNull` retour, vous ajoutez l’annotation à la méthode Return:

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Le code précédent informe les appelants que le contrat implique un type non Nullable, mais la valeur de retour *peut* en fait être null.  Utilisez l' `MaybeNull` attribut lorsque votre API doit être un type non Nullable, en général un paramètre de type générique, mais il peut y avoir `null` des instances où serait retourné.

Vous pouvez également spécifier qu’une valeur de retour ou `out` un `ref` argument ou n’est pas NULL même si le type est un type Nullable. Prenons l’exemple d’une méthode qui garantit qu’un tableau est suffisamment grand pour contenir un certain nombre d’éléments. Si l’argument d’entrée n’a pas de capacité, la routine alloue un nouveau tableau et copie tous les éléments existants dans celui-ci. Si l’argument d’entrée `null`est, la routine allouera un nouveau stockage. Si la capacité est suffisante, la routine ne fait rien:

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

Vous pouvez appeler cette routine comme suit:

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

Après avoir activé les types référence null, vous souhaitez vous assurer que le code précédent se compile sans avertissements. Lorsque la méthode retourne, l' `storage` argument est garanti comme non null. Toutefois, il est acceptable d’appeler `EnsureCapacity` avec une référence null. Vous pouvez créer `storage` un type référence Nullable et ajouter la `NotNull` condition postérieure à la déclaration du paramètre:

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

Le code précédent exprime très clairement le contrat existant: Les appelants peuvent passer une variable avec `null` la valeur, mais la valeur de retour est garantie pour ne jamais avoir la valeur null. L' `NotNull` attribut est particulièrement utile pour `ref` les `out` arguments et `null` , où peut être passé comme argument, mais que cet argument est garanti comme non NULL lorsque la méthode est retournée.

Vous spécifiez des post-conditions inconditionnelles à l’aide des attributs suivants:

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Une valeur de retour qui n’accepte pas les valeurs NULL peut être null.
- [NOTNULL](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Une valeur de retour Nullable ne sera jamais null.

## <a name="specify-conditional-post-conditions-notnullwhen-and-maybenullwhen"></a>Spécifier les conditions de publication conditionnelles: `NotNullWhen` et`MaybeNullWhen`

Vous êtes probablement familiarisé avec la `string` méthode <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>. Cette méthode retourne `true` lorsque l’argument n’a pas la valeur null, et non la chaîne vide. Il s’agit d’une forme de vérification NULL: Les appelants n’ont pas besoin de vérifier la valeur null si la `false`méthode retourne. Pour rendre une méthode comme cette prise en charge de Nullable, vous devez définir l’argument sur un type Nullable et `NotNullWhen` ajouter l’attribut:

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

Cela indique au compilateur que tout code dont la valeur de retour est n' `false` a pas besoin d’être vérifié par null. L’ajout de l’attribut informe l’analyse statique du compilateur qui `IsNullOrEmpty` effectue la vérification de la valeur null nécessaire: lorsqu’il retourne `false`, l’argument d’entrée `null`n’est pas.

```csharp
string? userInput = GetUserInput();
if (!(string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

La <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> méthode sera annotée comme indiqué ci-dessus pour .net Core 3,0. Vous pouvez avoir des méthodes similaires dans votre code base, qui vérifient l’état des objets pour les valeurs NULL. Le compilateur ne reconnaîtra pas les méthodes de vérification null personnalisées, et vous devrez ajouter vous-même les annotations. Lorsque vous ajoutez l’attribut, l’analyse statique du compilateur sait quand la variable testée a été vérifiée avec la valeur null.

Une autre utilisation de ces attributs est `Try*` le modèle. Les post- `ref` conditions `out` pour les variables et sont communiquées par le biais de la valeur de retour. Prenons l’exemple de cette méthode ci-dessus:

```csharp
bool TryGetMessage(string key, out string message)
```

La méthode précédente suit un idiome .net typique: la valeur de retour indique `message` si a été défini sur la valeur trouvée ou, si aucun message n’est trouvé, à la valeur par défaut. Si la méthode retourne `true`, la valeur de `message` n’est pas NULL; sinon, la `message` méthode affecte la valeur null.

Vous pouvez communiquer cet idiome à l' `NotNullWhen` aide de l’attribut. Quand vous mettez à jour la signature pour les types de `message` référence `string?` Nullable, créez un et ajoutez un attribut:

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

Dans l’exemple précédent, la valeur de `message` est dite NOT NULL lorsque `TryGetMessage` retourne `true`. Vous devez annoter des méthodes similaires dans votre code base de la même façon: les arguments peuvent `null`être, et sont connus pour ne pas avoir la valeur null `true`lorsque la méthode est retournée.

Vous pouvez également avoir un attribut final. Parfois, l’État null d’une valeur de retour dépend de l’État null d’un ou plusieurs arguments d’entrée. Ces méthodes retournent une valeur non null chaque fois que certains arguments `null`d’entrée ne sont pas. Pour annoter correctement ces méthodes, vous utilisez `NotNullIfNotNull` l’attribut. Considérez la méthode suivante:

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

Si l' `url` argument n’est pas null, la `null`sortie n’est pas. Une fois que les références Nullable sont activées, cette signature fonctionne correctement, à condition que votre API n’accepte jamais une entrée null. Toutefois, si l’entrée peut être null, la valeur de retour peut également être null. Par conséquent, vous pouvez remplacer la signature par le code suivant:

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

Cela fonctionne également, mais obligent souvent les appelants à implémenter des vérifications supplémentaires `null` . Le contrat est que la valeur de retour serait `null` uniquement lorsque l’argument `url` d’entrée `null`est. Pour exprimer ce contrat, vous devez annoter cette méthode comme indiqué dans le code suivant:

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

La valeur de retour et l’argument ont tous deux été annotés avec le `?` qui indique que peut être. `null` L’attribut clarifie davantage que la valeur de retour n’est pas null `url` lorsque l' `null`argument n’est pas.

Vous spécifiez des post-conditions conditionnelles à l’aide des attributs suivants:

- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Un argument non Nullable `out` ou `ref` peut avoir la valeur NULL lorsque la valeur de retour remplit une condition.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Un argument `out` Nullable `ref` ou ne peut pas être NULL lorsque la valeur de retour remplit une condition.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Une valeur de retour n’est pas null si l’argument d’entrée pour le paramètre spécifié n’est pas null.

## <a name="generic-definitions-and-nullability"></a>Définitions génériques et possibilité de valeur null

La communication correcte de l’État null des types génériques et des méthodes génériques requiert une attention particulière. Cela découle du fait qu’un type valeur Nullable et un type référence Nullable sont fondamentalement différents. Un `int?` est un synonyme de `Nullable<int>`, tandis `string` que `string?` est associé à un attribut ajouté par le compilateur. Le résultat est que le compilateur ne peut pas générer de `T?` code correct pour `T` sans savoir `class` si est `struct`un ou un. 

Cela ne signifie pas que vous ne pouvez pas utiliser un type Nullable (type valeur ou type référence) comme argument de type pour un type générique fermé. Et sont des instanciations valides de `List<T>`. `List<string?>` `List<int?>` 

Cela signifie que vous ne pouvez pas utiliser `T?` dans une déclaration de classe ou de méthode générique sans contraintes. Par exemple, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> ne peut pas être modifié `T?`pour retourner. Vous pouvez contourner cette limitation en ajoutant la `struct` contrainte `class` ou. Avec l’une de ces contraintes, le compilateur sait comment générer du code pour `T` et `T?`.

Vous pouvez restreindre les types utilisés pour un argument de type générique à des types non nullables. Pour ce faire, vous pouvez ajouter `notnull` la contrainte sur cet argument de type. Quand cette contrainte est appliquée, l’argument de type ne doit pas être un type Nullable.

## <a name="conclusions"></a>Conclusions

L’ajout de types de référence Nullable fournit un vocabulaire initial pour décrire les attentes des API pour `null`les variables qui pourraient être. Les attributs supplémentaires fournissent un vocabulaire plus riche pour décrire l’État null des variables en tant que conditions préalables et post-conditions. Ces attributs décrivent plus clairement vos attentes et offrent une meilleure expérience aux développeurs qui utilisent vos API.

Lorsque vous mettez à jour des bibliothèques pour un contexte Nullable, ajoutez ces attributs pour guider les utilisateurs de vos API vers l’utilisation correcte. Ces attributs vous aident à décrire complètement l’État null des arguments d’entrée et les valeurs de retour:

- [AllowNull a](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Un argument d’entrée n’acceptant pas les valeurs NULL peut avoir la valeur null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Un argument d’entrée Nullable ne doit jamais avoir la valeur null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Une valeur de retour qui n’accepte pas les valeurs NULL peut être null.
- [NOTNULL](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Une valeur de retour Nullable ne sera jamais null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Un argument non Nullable `out` ou `ref` peut avoir la valeur NULL lorsque la valeur de retour remplit une condition.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Un argument `out` Nullable `ref` ou ne peut pas être NULL lorsque la valeur de retour remplit une condition.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Une valeur de retour n’est pas null si l’argument d’entrée pour le paramètre spécifié n’est pas null.
