---
title: 'Attributs réservés C# : analyse statique Nullable'
ms.date: 04/14/2020
description: Ces attributs sont interprétés par le compilateur pour fournir une meilleure analyse statique pour les types de référence Nullable et non Nullable.
ms.openlocfilehash: 6678cd21de23d4ed391eff089e33939b5adff0fa
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955601"
---
# <a name="reserved-attributes-contribute-to-the-compilers-null-state-static-analysis"></a>Les attributs réservés contribuent à l’analyse statique d’État null du compilateur

Dans un contexte Nullable, le compilateur effectue une analyse statique du code pour déterminer l’État null de toutes les variables de type référence :

- *not null*: l’analyse statique détermine qu’une valeur non null est assignée à une variable.
- *peut-être null*: l’analyse statique ne peut pas déterminer qu’une valeur non null est assignée à une variable.

Vous pouvez appliquer un certain nombre d’attributs qui fournissent des informations au compilateur sur la sémantique de vos API. Ces informations permettent au compilateur d’effectuer une analyse statique et de déterminer quand une variable n’a pas la valeur null. Cet article fournit une brève description de chacun de ces attributs et explique comment les utiliser. Tous les exemples supposent C# 8,0 ou une version plus récente et le code se trouve dans un contexte Nullable.

Commençons par un exemple familier. Imaginez que votre bibliothèque possède l’API suivante pour récupérer une chaîne de ressource :

```csharp
bool TryGetMessage(string key, out string message)
```

L’exemple précédent suit le `Try*` modèle familier dans .net. Il existe deux arguments de référence pour cette API : `key` et le `message` paramètre. Cette API comporte les règles suivantes relatives à la valeur null de ces arguments :

- Les appelants ne doivent pas passer `null` comme argument pour `key` .
- Les appelants peuvent passer une variable dont la valeur est `null` l’argument pour `message` .
- Si la `TryGetMessage` méthode retourne `true` , la valeur de `message` n’est pas null. Si la valeur de retour est `false,` la valeur de `message` (et son état null) est null.

La règle pour `key` peut être exprimée par le type de variable : `key` doit être un type référence qui n’accepte pas les valeurs NULL. Le `message` paramètre est plus complexe. Elle autorise `null` comme argument, mais garantit que, en cas de réussite, cet `out` argument n’est pas null. Pour ces scénarios, vous avez besoin d’un vocabulaire plus riche pour décrire les attentes.

Plusieurs attributs ont été ajoutés pour exprimer des informations supplémentaires sur l’État null des variables. Tout le code que vous avez écrit avant C# 8 a introduit des types de référence Nullable était *null oublie*. Cela signifie que toute variable de type référence peut avoir la valeur null, mais que les vérifications de valeur NULL ne sont pas requises. Une fois que votre code prend en *charge les valeurs NULL*, ces règles changent. Les types référence ne doivent jamais être la `null` valeur, et les types référence Nullable doivent être vérifiés `null` avant d’être déréférencés.

Les règles de vos API sont probablement plus compliquées, comme vous l’avez vu dans le `TryGetValue` scénario d’API. La plupart de vos API ont des règles plus complexes pour le moment où les variables peuvent ou ne peuvent pas être `null` . Dans ce cas, vous allez utiliser l’un des attributs suivants pour exprimer ces règles :

- [AllowNull a](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): un argument d’entrée qui n’accepte pas les valeurs NULL peut être null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): un argument d’entrée Nullable ne doit jamais avoir la valeur null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): une valeur de retour qui n’accepte pas les valeurs NULL peut être null.
- [NOTNULL](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): une valeur de retour Nullable ne sera jamais null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): un argument d’entrée qui n’accepte pas les valeurs NULL peut être NULL lorsque la méthode retourne la `bool` valeur spécifiée.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): un argument d’entrée Nullable ne sera pas NULL lorsque la méthode retourne la `bool` valeur spécifiée.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): une valeur de retour n’est pas null si l’argument pour le paramètre spécifié n’est pas null.
- [DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): une méthode ne retourne jamais. En d’autres termes, elle lève toujours une exception.
- [DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): cette méthode ne retourne jamais si le `bool` paramètre associé a la valeur spécifiée.

Les descriptions précédentes sont une référence rapide à ce que fait chaque attribut. Chaque section suivante décrit le comportement et la signification de manière plus approfondie.

L’ajout de ces attributs donne au compilateur plus d’informations sur les règles de votre API. Quand le code appelant est compilé dans un contexte compatible avec la valeur null, le compilateur avertit les appelants lorsqu’ils enfreignent ces règles. Ces attributs n’autorisent pas de vérifications supplémentaires sur votre implémentation.

## <a name="specify-preconditions-allownull-and-disallownull"></a>Spécifier les conditions préalables : `AllowNull` et `DisallowNull`

Prenons l’exemple d’une propriété en lecture/écriture qui n’est jamais retournée `null` , car elle a une valeur par défaut raisonnable. Les appelants passent `null` à l’accesseur Set lors de la définition de cette valeur par défaut. Par exemple, imaginez un système de messagerie qui demande un nom d’écran dans une salle de conversation. Si aucune valeur n’est fournie, le système génère un nom aléatoire :

```csharp
public string ScreenName
{
   get => _screenName;
   set => _screenName = value ?? GenerateRandomScreenName();
}
private string _screenName;
```

Quand vous compilez le code précédent dans un contexte oublie Nullable, tout est parfait. Une fois que vous activez les types référence Nullable, la `ScreenName` propriété devient une référence qui n’accepte pas les valeurs NULL. C’est correct pour l' `get` accesseur : il ne retourne jamais `null` . Les appelants n’ont pas besoin de vérifier la propriété retournée pour `null` . Mais maintenant, le paramétrage de la propriété pour `null` générer un avertissement. Pour continuer à prendre en charge ce type de code, vous ajoutez l' <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> attribut à la propriété, comme illustré dans le code suivant :

```csharp
[AllowNull]
public string ScreenName
{
   get => _screenName;
   set => _screenName = value ?? GenerateRandomScreenName();
}
private string _screenName = GenerateRandomScreenName();
```

Vous devrez peut-être ajouter une `using` directive pour <xref:System.Diagnostics.CodeAnalysis> utiliser ce et d’autres attributs abordés dans cet article. L’attribut est appliqué à la propriété, et non à l' `set` accesseur. L' `AllowNull` attribut spécifie des *conditions préalables*et s’applique uniquement aux entrées. L' `get` accesseur a une valeur de retour, mais aucun argument d’entrée. Par conséquent, l' `AllowNull` attribut s’applique uniquement à l' `set` accesseur.

L’exemple précédent montre ce qu’il faut rechercher lors de l’ajout `AllowNull` de l’attribut à un argument :

1. Le contrat général pour cette variable est qu’elle ne doit pas l’être `null` , donc vous souhaitez un type de référence non Nullable.
1. Il existe des scénarios pour la variable d’entrée `null` , bien qu’il ne s’agisse pas de l’utilisation la plus courante.

La plupart du temps, vous aurez besoin de cet attribut pour les propriétés, ou `in` , `out` et les `ref` arguments. L' `AllowNull` attribut est le meilleur choix lorsqu’une variable est généralement non null, mais que vous devez autoriser `null` comme condition préalable.

À l’inverse, avec les scénarios d’utilisation de `DisallowNull` :, vous utilisez cet attribut pour spécifier qu’une variable d’entrée d’un type de référence Nullable ne doit pas être `null` . Considérez une propriété où `null` est la valeur par défaut, mais les clients peuvent uniquement la définir sur une valeur non null. Considérez le code suivant :

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

Le code précédent est la meilleure façon d’exprimer votre conception de `ReviewComment` `null` , mais ne peut pas avoir la valeur `null` . Une fois que ce code prend en charge les valeurs NULL, vous pouvez exprimer ce concept plus clairement aux appelants à l’aide du <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType> :

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

Dans un contexte Nullable, l' `ReviewComment` `get` accesseur peut retourner la valeur par défaut de `null` . Le compilateur vous avertit qu’il doit être vérifié avant l’accès. En outre, il avertit les appelants que, même s’ils peuvent l’être `null` , les appelants ne doivent pas lui affecter explicitement la valeur `null` . L' `DisallowNull` attribut spécifie également une *condition préalable*, il n’affecte pas l' `get` accesseur. Vous utilisez l' `DisallowNull` attribut lorsque vous observez les caractéristiques suivantes :

1. La variable peut être `null` dans des scénarios de base, souvent lors de la première instanciation.
1. La variable ne doit pas avoir explicitement la valeur `null` .

Ces situations sont courantes dans le code qui a été initialement *null oublie*. Les propriétés de l’objet sont peut-être définies dans deux opérations d’initialisation distinctes. Il se peut que certaines propriétés soient définies uniquement après la fin d’un travail asynchrone.

Les `AllowNull` `DisallowNull` attributs et vous permettent de spécifier que les conditions préalables sur les variables peuvent ne pas correspondre aux annotations Nullable sur ces variables. Celles-ci fournissent des informations plus détaillées sur les caractéristiques de votre API. Ces informations supplémentaires permettent aux appelants d’utiliser correctement votre API. N’oubliez pas de spécifier des conditions préalables à l’aide des attributs suivants :

- [AllowNull a](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): un argument d’entrée qui n’accepte pas les valeurs NULL peut être null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): un argument d’entrée Nullable ne doit jamais avoir la valeur null.

## <a name="specify-post-conditions-maybenull-and-notnull"></a>Spécifier les conditions postérieures : `MaybeNull` et `NotNull`

Supposons que vous avez une méthode avec la signature suivante :

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

Vous avez probablement écrit une méthode comme celle-ci pour retourner `null` lorsque le nom recherché n’a pas été trouvé. `null`Indique clairement que l’enregistrement n’a pas été trouvé. Dans cet exemple, vous allez probablement modifier le type de retour de `Customer` en `Customer?` . La déclaration de la valeur de retour en tant que type référence Nullable spécifie clairement l’objectif de cette API.

Pour les raisons couvertes par les [définitions génériques et la possibilité de valeur null](../../nullable-migration-strategies.md#generic-definitions-and-nullability) , cette technique ne fonctionne pas avec les méthodes génériques. Vous pouvez avoir une méthode générique qui suit un modèle similaire :

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> predicate)
```

Vous ne pouvez pas spécifier que la valeur de retour est `T?` . La méthode retourne `null` lorsque l’élément recherché est introuvable. Étant donné que vous ne pouvez pas déclarer un `T?` type de retour, vous ajoutez l' `MaybeNull` annotation à la méthode Return :

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> predicate)
```

Le code précédent informe les appelants que le contrat implique un type non Nullable, mais la valeur de retour *peut* en fait être null.  Utilisez l' `MaybeNull` attribut lorsque votre API doit être un type non Nullable, en général un paramètre de type générique, mais il peut y avoir des instances où `null` serait retourné.

Vous pouvez également spécifier qu’une valeur de retour ou `out` un `ref` argument ou n’est pas null bien que le type soit un type référence Nullable. Prenons l’exemple d’une méthode qui garantit qu’un tableau est suffisamment grand pour contenir un certain nombre d’éléments. Si l’argument d’entrée n’a pas de capacité, la routine alloue un nouveau tableau et copie tous les éléments existants dans celui-ci. Si l’argument d’entrée est `null` , la routine allouera un nouveau stockage. Si la capacité est suffisante, la routine ne fait rien :

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

Vous pouvez appeler cette routine comme suit :

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

Après avoir activé les types référence null, vous souhaitez vous assurer que le code précédent se compile sans avertissements. Lorsque la méthode retourne, l' `storage` argument est garanti comme non null. Toutefois, il est acceptable d’appeler `EnsureCapacity` avec une référence null. Vous pouvez créer `storage` un type référence Nullable et ajouter la `NotNull` condition postérieure à la déclaration du paramètre :

```csharp
public void EnsureCapacity<T>([NotNull] ref T[]? storage, int size)
```

Le code précédent exprime clairement le contrat existant : les appelants peuvent passer une variable avec la `null` valeur, mais la valeur de retour est garantie pour ne jamais avoir la valeur null. L' `NotNull` attribut est particulièrement utile pour `ref` les `out` arguments et `null` , où peut être passé comme argument, mais que cet argument est garanti comme non NULL lorsque la méthode est retournée.

Vous spécifiez des post-conditions inconditionnelles à l’aide des attributs suivants :

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): une valeur de retour qui n’accepte pas les valeurs NULL peut être null.
- [NOTNULL](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): une valeur de retour Nullable ne sera jamais null.

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a>Spécifier les conditions de publication conditionnelles : `NotNullWhen` , `MaybeNullWhen` et `NotNullIfNotNull`

Vous êtes probablement familiarisé avec la `string` méthode <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> . Cette méthode retourne `true` lorsque l’argument a la valeur null ou est une chaîne vide. Il s’agit d’une forme de contrôle de valeur NULL : les appelants n’ont pas besoin de vérifier la valeur null si la méthode retourne `false` . Pour rendre une méthode comme cette prise en charge de Nullable, vous devez définir l’argument sur un type de référence Nullable et ajouter l' `NotNullWhen` attribut :

```csharp
bool IsNullOrEmpty([NotNullWhen(false)] string? value);
```

Cela indique au compilateur que tout code dont la valeur de retour est n’a `false` pas besoin d’être vérifié par null. L’ajout de l’attribut informe l’analyse statique du compilateur qui `IsNullOrEmpty` effectue la vérification de la valeur null nécessaire : lorsqu’il retourne `false` , l’argument d’entrée n’est pas `null` .

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

La <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> méthode sera annotée comme indiqué ci-dessus pour .net Core 3,0. Vous pouvez avoir des méthodes similaires dans votre code base, qui vérifient l’état des objets pour les valeurs NULL. Le compilateur ne reconnaîtra pas les méthodes de vérification null personnalisées, et vous devrez ajouter vous-même les annotations. Lorsque vous ajoutez l’attribut, l’analyse statique du compilateur sait quand la variable testée a été vérifiée avec la valeur null.

Une autre utilisation de ces attributs est le `Try*` modèle. Les post-conditions pour les `ref` `out` variables et sont communiquées par le biais de la valeur de retour. Prenons l’exemple de cette méthode ci-dessus :

```csharp
bool TryGetMessage(string key, out string message)
```

La méthode précédente suit un idiome .NET typique : la valeur de retour indique si `message` a été défini sur la valeur trouvée ou, si aucun message n’est trouvé, à la valeur par défaut. Si la méthode retourne `true` , la valeur de `message` n’est pas NULL ; sinon, la méthode affecte la valeur `message` null.

Vous pouvez communiquer cet idiome à l’aide de l' `NotNullWhen` attribut. Quand vous mettez à jour la signature pour les types de référence Nullable, créez `message` un `string?` et ajoutez un attribut :

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

Dans l’exemple précédent, la valeur de `message` est dite NOT NULL lorsque `TryGetMessage` retourne `true` . Vous devez annoter des méthodes similaires dans votre code base de la même façon : les arguments peuvent être `null` , et sont connus pour ne pas avoir la valeur NULL lorsque la méthode est retournée `true` .

Vous pouvez également avoir un attribut final. Parfois, l’État null d’une valeur de retour dépend de l’État null d’un ou plusieurs arguments d’entrée. Ces méthodes retournent une valeur non null chaque fois que certains arguments d’entrée ne sont pas `null` . Pour annoter correctement ces méthodes, vous utilisez l' `NotNullIfNotNull` attribut. Considérez la méthode suivante :

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

Si l' `url` argument n’est pas null, la sortie n’est pas `null` . Une fois que les références Nullable sont activées, cette signature fonctionne correctement, à condition que votre API n’accepte jamais une entrée null. Toutefois, si l’entrée peut être null, la valeur de retour peut également être null. Par conséquent, vous pouvez remplacer la signature par le code suivant :

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

Cela fonctionne également, mais obligent souvent les appelants à implémenter des `null` vérifications supplémentaires. Le contrat est que la valeur de retour serait `null` uniquement lorsque l’argument d’entrée `url` est `null` . Pour exprimer ce contrat, vous devez annoter cette méthode comme indiqué dans le code suivant :

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

La valeur de retour et l’argument ont tous deux été annotés avec le `?` qui indique que peut être `null` . L’attribut clarifie davantage que la valeur de retour n’est pas NULL lorsque l' `url` argument n’est pas `null` .

Vous spécifiez des post-conditions conditionnelles à l’aide des attributs suivants :

- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): un argument d’entrée qui n’accepte pas les valeurs NULL peut être NULL lorsque la méthode retourne la `bool` valeur spécifiée.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): un argument d’entrée Nullable ne sera pas NULL lorsque la méthode retourne la `bool` valeur spécifiée.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): une valeur de retour n’est pas null si l’argument d’entrée pour le paramètre spécifié n’est pas null.

## <a name="verify-unreachable-code"></a>Vérifier le code inaccessible

Certaines méthodes, généralement des applications d’assistance d’exception ou d’autres méthodes utilitaires, se ferment toujours en levant une exception. Ou bien, une application d’assistance peut lever une exception en fonction de la valeur d’un argument booléen.

Dans le premier cas, vous pouvez ajouter l' `DoesNotReturn` attribut à la déclaration de méthode. Le compilateur vous aide de trois façons. Tout d’abord, le compilateur émet un avertissement s’il existe un chemin d’accès où la méthode peut se fermer sans lever d’exception. Deuxièmement, le compilateur marque tout code après un appel à cette méthode comme étant *inaccessible*, jusqu’à ce qu’une `catch` clause appropriée soit rencontrée. Troisièmement, le code inaccessible n’affecte pas les États null. Prenons la méthode suivante :

```csharp
[DoesNotReturn]
private void FailFast()
{
    throw new InvalidOperationException();
}

public void SetState(object containedField)
{
    if (!isInitialized)
    {
        FailFast();
    }

    // unreachable code:
    _field = containedField;
}
```

Dans le deuxième cas, vous ajoutez l' `DoesNotReturnIf` attribut à un paramètre booléen de la méthode. Vous pouvez modifier l’exemple précédent comme suit :

```csharp
private void FailFast([DoesNotReturnIf(false)] bool isValid)
{
    if (!isValid)
    {
        throw new InvalidOperationException();
    }
}

public void SetState(object containedField)
{
    FailFast(isInitialized);

    // unreachable code when "isInitialized" is false:
    _field = containedField;
}
```

## <a name="summary"></a>Résumé

[!INCLUDE [C# version alert](../../includes/csharp-version-alert.md)]

L’ajout de types de référence Nullable fournit un vocabulaire initial pour décrire les attentes des API pour les variables qui pourraient être `null` . Les attributs supplémentaires fournissent un vocabulaire plus riche pour décrire l’État null des variables en tant que conditions préalables et post-conditions. Ces attributs décrivent plus clairement vos attentes et offrent une meilleure expérience aux développeurs qui utilisent vos API.

Lorsque vous mettez à jour des bibliothèques pour un contexte Nullable, ajoutez ces attributs pour guider les utilisateurs de vos API vers l’utilisation correcte. Ces attributs vous aident à décrire complètement l’État null des arguments d’entrée et les valeurs de retour :

- [AllowNull a](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): un argument d’entrée qui n’accepte pas les valeurs NULL peut être null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): un argument d’entrée Nullable ne doit jamais avoir la valeur null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): une valeur de retour qui n’accepte pas les valeurs NULL peut être null.
- [NOTNULL](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): une valeur de retour Nullable ne sera jamais null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): un argument d’entrée qui n’accepte pas les valeurs NULL peut être NULL lorsque la méthode retourne la `bool` valeur spécifiée.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): un argument d’entrée Nullable ne sera pas NULL lorsque la méthode retourne la `bool` valeur spécifiée.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): une valeur de retour n’est pas null si l’argument d’entrée pour le paramètre spécifié n’est pas null.
- [DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): une méthode ne retourne jamais. En d’autres termes, elle lève toujours une exception.
- [DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): cette méthode ne retourne jamais si le `bool` paramètre associé a la valeur spécifiée.
