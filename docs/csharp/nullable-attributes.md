---
title: Améliorer les API pour les types de référence nuls avec des attributs qui définissent les attentes pour les valeurs nulles
description: Apprenez à utiliser les attributs descriptifs AllowNull, DisallowNull, MaybeNull, NotNull et plus encore pour décrire pleinement l’état nul de vos API.
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: ca04db800271b9b01b5b9f1482dd5a0db2cc1c35
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249243"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Mettre à jour les bibliothèques pour qu’elles utilisent des types de référence nuls et communiquent des règles in annulables aux appelants

L’ajout de types de [référence in annulables](nullable-references.md) signifie que vous pouvez déclarer si une `null` valeur est autorisée ou attendue pour chaque variable. En outre, vous pouvez appliquer un `AllowNull` `DisallowNull`certain `MaybeNull` `NotNull`nombre `NotNullWhen` `MaybeNullWhen`d’attributs: , , , , , et `NotNullWhenNotNull` de décrire complètement les états nuls de l’argumentation et les valeurs de retour. Cela offre une grande expérience que vous écrivez du code. Vous obtenez des avertissements si une variable `null`non-nullable pourrait être définie à . Vous obtenez des avertissements si une variable nulle n’est pas vérifiée non vérifiée avant de la déreférencer. La mise à jour de vos bibliothèques peut prendre du temps, mais les retombées en valent la peine. Plus vous fournissez d’informations au `null` compilateur sur le *moment où* une valeur est autorisée ou interdite, les meilleurs avertissements que les utilisateurs de votre API obtiendront. Commençons par un exemple familier. Imaginez que votre bibliothèque dispose de l’API suivante pour récupérer une chaîne de ressources :

```csharp
bool TryGetMessage(string key, out string message)
```

L’exemple précédent `Try*` suit le modèle familier en .NET. Il existe deux arguments de référence `key` pour `message` cette API : le et le paramètre. Cette API a les règles suivantes relatives à l’annulation de ces arguments :

- Les appelants `null` ne devraient pas `key`passer comme l’argument pour .
- Les appelants peuvent passer une `null` variable dont `message`la valeur est comme l’argument pour .
- Si `TryGetMessage` la `true`méthode revient, la valeur de `message` n’est pas nulle. Si la valeur `false,` de `message` rendement est la valeur de (et son état nul) est nulle.

La règle `key` pour peut être entièrement `key` exprimée par le type variable: devrait être un type de référence non-nullable. Le `message` paramètre est plus complexe. Il `null` permet comme argument, mais garantit que, sur le succès, cet `out` argument n’est pas nul. Pour ces scénarios, vous avez besoin d’un vocabulaire plus riche pour décrire les attentes.

La mise à jour de votre bibliothèque `?` pour les références annulées nécessite plus que saupoudrer sur certaines des variables et des noms de type. L’exemple précédent montre que vous devez examiner vos API et tenir compte de vos attentes pour chaque argument d’entrée. Tenez compte des garanties pour `out` la `ref` valeur de retour, et tout ou argumentation lors du retour de la méthode. Communiquez ensuite ces règles au compilateur, et le compilateur fournira des avertissements lorsque les appelants ne respectent pas ces règles.

Ce travail prend du temps. Commençons par des stratégies pour rendre votre bibliothèque ou votre application in annulable, tout en équilibrant d’autres exigences et livrables. Vous verrez comment équilibrer le développement en cours permettant des types de référence nuls. Vous apprendrez des défis pour les définitions de type générique. Vous apprendrez à appliquer des attributs pour décrire les conditions préalables et post-conditions sur les API individuelles.

## <a name="choose-a-strategy-for-nullable-reference-types"></a>Choisissez une stratégie pour les types de référence nuls

Le premier choix est de savoir si les types de référence nuls doivent être allumés ou annulés par défaut. Vous avez deux stratégies :

- Activez les types de référence nuls pour l’ensemble du projet et désactivez-le dans un code qui n’est pas prêt.
- N’activez que les types de référence inquérables pour le code qui a été annoté pour les types de référence annulés.

La première stratégie fonctionne mieux lorsque vous ajoutez d’autres fonctionnalités à la bibliothèque lorsque vous la mettez à jour pour les types de référence nuls. Tout nouveau développement est invenu conscient. Lorsque vous mettez à jour le code existant, vous activez des types de référence nuls dans ces classes.

Suite à cette première stratégie, vous faites ce qui suit :

1. Activez les types de référence nuls pour l’ensemble du projet en ajoutant l’élément `<Nullable>enable</Nullable>` à vos fichiers *csproj.*
1. Ajoutez `#nullable disable` le pragma à chaque fichier source de votre projet.
1. Lorsque vous travaillez sur chaque fichier, retirez le pragma et adressez les avertissements.

Cette première stratégie a plus de travail à l’avance pour ajouter le pragma à chaque fichier. L’avantage est que chaque nouveau fichier de code ajouté au projet sera annulé activé. Tout nouveau travail sera in nullable au courant; seul le code existant doit être mis à jour.

La deuxième stratégie fonctionne mieux si la bibliothèque est généralement stable, et l’objectif principal de l’élaboration est d’adopter des types de référence nuls. Vous activez les types de référence incontables au fur et à mesure que vous annotez les API. Lorsque vous avez terminé, vous activez des types de référence nuls pour l’ensemble du projet.

Suite à cette deuxième stratégie, vous faites ce qui suit :

1. Ajoutez `#nullable enable` le pragma au fichier que vous souhaitez rendre nul possible.
1. Adressez tous les avertissements.
1. Poursuivez ces deux premières étapes jusqu’à ce que vous ayez rendu la bibliothèque nulle au courant.
1. Activez les types nuls pour `<Nullable>enable</Nullable>` l’ensemble du projet en ajoutant l’élément à vos fichiers *csproj.*
1. Retirez `#nullable enable` les pragmas, car ils ne sont plus nécessaires.

Cette deuxième stratégie a moins de travail à l’avance. Le compromis est que la première tâche lorsque vous créez un nouveau fichier est d’ajouter le pragma et le rendre invenu possible. Si des développeurs de votre équipe oublient, ce nouveau code est maintenant dans l’arriéré de travail pour rendre tout le code infirament.

Les stratégies que vous choisissez dépendent de l’ampleur du développement actif de votre projet. Plus votre projet est mature et stable, meilleure est la deuxième stratégie. Plus il y a de fonctionnalités développées, meilleure est la première stratégie.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Les avertissements annulés devraient-ils introduire des changements de rupture?

Avant d’activer les types de référence annulables, les variables sont considérées comme *nulles inconscientes.* Une fois que vous activez les types de référence annulés, toutes ces variables ne sont *pas annulables.* Le compilateur émettra des avertissements si ces variables ne sont pas parasitées à des valeurs non nulles.

Une autre source probable d’avertissements est les valeurs de rendement lorsque la valeur n’a pas été parasécée.

La première étape pour traiter les avertissements `?` de compilateur est d’utiliser des annotations sur les types de paramètres et de retour pour indiquer quand les arguments ou les valeurs de retour peuvent être nuls. Lorsque les variables de référence ne doivent pas être nulles, la déclaration initiale est correcte. Comme vous le faites, votre objectif n’est pas seulement de fixer les avertissements. L’objectif le plus important est de faire comprendre au compilateur votre intention de valeurs nulles potentielles. Lorsque vous examinez les avertissements, vous arrivez à votre prochaine décision majeure pour votre bibliothèque. Voulez-vous envisager de modifier les signatures API pour communiquer plus clairement votre intention de conception? Une meilleure signature API pour la `TryGetMessage` méthode examinée plus tôt pourrait être :

```csharp
string? TryGetMessage(string key);
```

La valeur de rendement indique le succès ou l’échec, et porte la valeur si la valeur a été trouvée. Dans de nombreux cas, la modification des signatures API peut améliorer la façon dont elles communiquent des valeurs nulles.

Toutefois, pour les bibliothèques publiques ou les bibliothèques dotées de grandes bases d’utilisateurs, vous préférerez peut-être ne pas introduire de modifications de signatures de l’API. Pour ces cas, et d’autres modèles communs, vous pouvez appliquer des `null`attributs pour définir plus clairement quand un argument ou une valeur de retour peut être . Que vous envisagez ou non de changer la surface de votre API, vous constaterez `null` probablement que les annotations de type à elles seules ne sont pas suffisantes pour décrire les valeurs pour les arguments ou les valeurs de retour. Dans ces cas, vous pouvez appliquer des attributs pour décrire plus clairement une API.

## <a name="attributes-extend-type-annotations"></a>Les attributs prolongent les annotations de type

Plusieurs attributs ont été ajoutés pour exprimer des informations supplémentaires sur l’état nul des variables. Tout le code que vous avez écrit avant que le C 8 n’introduise des types de référence nuls *était nul inconscient.* Cela signifie que toute variable de type de référence peut être nulle, mais les contrôles nuls ne sont pas nécessaires. Une fois que votre code est *infirampable au courant,* ces règles changent. Les types de `null` référence ne doivent jamais être la `null` valeur, et les types de référence nuls doivent être vérifiés avant d’être déreférés.

Les règles de vos API sont probablement plus `TryGetValue` compliquées, comme vous l’avez vu avec le scénario API. Beaucoup de vos API ont des règles plus complexes pour quand les variables peuvent ou ne peuvent pas être `null`. Dans ces cas, vous utiliserez l’un des attributs suivants pour exprimer ces règles :

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Un argument d’entrée non annulable peut être nul.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Un argument d’entrée nul ne devrait jamais être nul.
- [Peut-êtreNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Une valeur de retour non annulable peut être nulle.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Une valeur de retour annulée ne sera jamais nulle.
- [Peut-êtreNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Un argument d’entrée non annulable `bool` peut être nul lorsque la méthode renvoie la valeur spécifiée.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Un argument d’entrée nul ne sera `bool` pas nul lorsque la méthode retourne la valeur spécifiée.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Une valeur de retour n’est pas nulle si l’argument du paramètre spécifié n’est pas nul.

Les descriptions précédentes sont une référence rapide à ce que chaque attribut fait. Chaque section suivante décrit le comportement et le sens plus en profondeur.

L’ajout de ces attributs donne au compilateur plus d’informations sur les règles de votre API. Lorsque le code d’appel est compilé dans un contexte activé nul, le compilateur avertit les appelants lorsqu’ils violent ces règles. Ces attributs n’activent pas de contrôles supplémentaires sur votre implémentation.

## <a name="specify-preconditions-allownull-and-disallownull"></a>Spécifier `AllowNull` les conditions préalables: et`DisallowNull`

Considérez une propriété de `null` lecture/écriture qui ne revient jamais parce qu’elle a une valeur raisonnable par défaut. Les appelants `null` passent à l’accesseur de configuration lors de la définition de cette valeur par défaut. Par exemple, considérez un système de messagerie qui demande un nom d’écran dans une salle de chat. Si aucun n’est fourni, le système génère un nom aléatoire :

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

Lorsque vous compilez le code précédent dans un contexte oubliable, tout va bien. Une fois que vous activez les types de référence annulés, la `ScreenName` propriété devient une référence non annulable. C’est correct `get` pour l’accesseur: il ne revient `null`jamais . Les appelants n’ont pas besoin `null`de vérifier la propriété retournée pour . Mais maintenant la `null` mise de la propriété pour génère un avertissement. Afin de continuer à prendre en charge <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> ce type de code, vous ajoutez l’attribut à la propriété, comme indiqué dans le code suivant:

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

Vous devrez peut-être ajouter une `using` directive pour <xref:System.Diagnostics.CodeAnalysis> utiliser ceci et d’autres attributs discutés dans cet article. L’attribut est appliqué à `set` la propriété, et non à l’accesseur. L’attribut `AllowNull` spécifie *les conditions préalables*et ne s’applique qu’aux entrées. L’accesseur `get` a une valeur de retour, mais pas d’arguments d’entrée. Par conséquent, `AllowNull` l’attribut `set` ne s’applique qu’à l’accesseur.

L’exemple précédent montre ce qu’il faut rechercher lors de l’ajout de l’attribut `AllowNull` sur un argument :

1. Le contrat général pour cette variable est `null`qu’il ne devrait pas être , de sorte que vous voulez un type de référence non-nullable.
1. Il existe des scénarios pour `null`la variable d’entrée d’être, mais ils ne sont pas l’utilisation la plus courante.

Le plus souvent, vous aurez besoin `in` `out`de `ref` cet attribut pour les propriétés, ou , et les arguments. L’attribut `AllowNull` est le meilleur choix lorsqu’une variable n’est généralement pas nulle, mais vous devez le permettre `null` comme condition préalable.

Comparez cela avec `DisallowNull`les scénarios pour l’utilisation : Vous utilisez cet attribut pour `null`spécifier qu’une variable d’entrée d’un type de référence nul ne devrait pas être . Considérez une `null` propriété où est la valeur par défaut, mais les clients ne peuvent la définir qu’à une valeur non nulle. Examinons le code ci-dessous.

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

Le code précédent est la meilleure façon `ReviewComment` d’exprimer votre conception que le pourrait être `null`, mais ne peut pas être réglé à `null`. Une fois que ce code est in nullable conscient, <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>vous pouvez exprimer ce concept plus clairement aux appelants en utilisant le :

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

Dans un contexte in `ReviewComment` `get` annulable, l’accesseur peut retourner la valeur par défaut de `null`. Le compilateur prévient qu’il doit être vérifié avant l’accès. En outre, il avertit les appelants que, même si elle pourrait être `null`, les appelants ne devraient pas explicitement le définir à `null`. L’attribut `DisallowNull` spécifie également une condition `get` *préalable,* il n’affecte pas l’accesseur. Vous devez choisir `DisallowNull` d’utiliser l’attribut lorsque vous observez ces caractéristiques au sujet de :

1. La variable `null` peut être dans les scénarios de base, souvent lors de la première instantané.
1. La variable ne devrait pas `null`être explicitement définie à .

Ces situations sont courantes dans le code qui était à l’origine *nulle inconscient*. Il se peut que les propriétés d’objets soient définies dans deux opérations distinctes de initialisation. Il se peut que certaines propriétés ne soient définies qu’après la fin de certains travaux asynchrones.

Les `AllowNull` `DisallowNull` et les attributs vous permettent de spécifier que les conditions préalables sur les variables peuvent ne pas correspondre aux annotations annulables sur ces variables. Ceux-ci fournissent plus de détails sur les caractéristiques de votre API. Ces informations supplémentaires aident les appelants à utiliser correctement votre API. N’oubliez pas que vous spécifiez les conditions préalables à l’aide des attributs suivants :

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Un argument d’entrée non annulable peut être nul.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Un argument d’entrée nul ne devrait jamais être nul.

## <a name="specify-post-conditions-maybenull-and-notnull"></a>Spécifier `MaybeNull` les conditions postérieures et`NotNull`

Supposons que vous avez une méthode avec la signature suivante:

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

Vous avez probablement écrit une méthode `null` comme celle-ci pour revenir lorsque le nom recherché n’a pas été trouvé. Le `null` indique clairement que le dossier n’a pas été trouvé. Dans cet exemple, vous changeriez probablement `Customer` `Customer?`le type de retour de . Déclarer la valeur de déclaration comme un type de référence nul précise clairement l’intention de cette API.

Pour des raisons couvertes par [des définitions génériques et l’annulation,](#generic-definitions-and-nullability) cette technique ne fonctionne pas avec des méthodes génériques. Vous pouvez avoir une méthode générique qui suit un modèle similaire:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Vous ne pouvez pas spécifier que la valeur de retour est `T?`. La méthode `null` revient lorsque l’article recherché n’est pas trouvé. Puisque vous ne pouvez `T?` pas déclarer un `MaybeNull` type de retour, vous ajoutez l’annotation au retour de méthode :

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Le code précédent informe les appelants que le contrat implique un type non annulable, mais la valeur de déclaration *peut* en fait être nulle.  Utilisez `MaybeNull` l’attribut lorsque votre API devrait être un type non-nullable, généralement `null` un paramètre de type générique, mais il peut y avoir des cas où serait retourné.

Vous pouvez également spécifier `out` `ref` qu’une valeur de retour ou un ou un argument n’est pas nul, même si le type est un type de référence nul. Considérez une méthode qui garantit qu’un tableau est assez grand pour contenir un certain nombre d’éléments. Si l’argument de l’entrée n’a pas de capacité, la routine allouerait un nouveau tableau et copierait tous les éléments existants. Si l’argument `null`de l’entrée est, la routine allouerait un nouveau stockage. S’il y a une capacité suffisante, la routine ne fait rien :

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

Vous pourriez appeler cette routine comme suit:

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

Après avoir permis des types de référence nuls, vous souhaitez vous assurer que le code précédent se compile sans avertissements. Lorsque la méthode `storage` revient, l’argument est garanti pour ne pas être nul. Cependant, il est acceptable `EnsureCapacity` d’appeler avec une référence nulle. Vous pouvez `storage` faire un type de `NotNull` référence annulé et ajouter la post-condition à la déclaration de paramètres :

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

Le code précédent exprime très clairement le contrat existant : `null` les appelants peuvent passer une variable avec la valeur, mais la valeur de rendement est garantie de ne jamais être nulle. `NotNull` L’attribut est `ref` le `out` plus `null` utile et les arguments où peut être adopté comme un argument, mais cet argument est garanti d’être pas nul lorsque la méthode revient.

Vous spécifiez les conditions post-conditions inconditionnelles à l’aide des attributs suivants :

- [Peut-êtreNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Une valeur de retour non annulable peut être nulle.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Une valeur de retour annulée ne sera jamais nulle.

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a>Spécifier les `NotNullWhen` `MaybeNullWhen`conditions post-conditions conditionnelles: , et`NotNullIfNotNull`

Vous êtes probablement familier `string` <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>avec la méthode . Cette méthode `true` revient lorsque l’argument est nul ou une chaîne vide. C’est une forme de null-check: Les appelants n’ont pas `false`besoin de vérifier l’argument si la méthode revient . Pour faire prendre conscience à une méthode comme celle-ci, vous définissez `NotNullWhen` l’argument à un type de référence nul et ajoutez l’attribut :

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

Cela informe le compilateur que tout `false` code où la valeur de retour est n’a pas besoin d’être vérifié non vérifié. L’ajout de l’attribut informe l’analyse `IsNullOrEmpty` statique du compilateur qui `false`effectue la vérification `null`nulle nécessaire : lorsqu’il revient, l’argument de l’entrée n’est pas .

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

La <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> méthode sera annotée comme indiqué ci-dessus pour .NET Core 3.0. Vous pouvez avoir des méthodes similaires dans votre base de code qui vérifient l’état des objets pour les valeurs nulles. Le compilateur ne reconnaîtra pas les méthodes de vérification nulles personnalisées, et vous devrez ajouter les annotations vous-même. Lorsque vous ajoutez l’attribut, l’analyse statique du compilateur sait quand la variable testée a été vérifiée.

Une autre utilisation pour `Try*` ces attributs est le modèle. Les conditions post-conditions `ref` et `out` les variables sont communiquées par la valeur de retour. Considérez cette méthode indiquée plus tôt :

```csharp
bool TryGetMessage(string key, out string message)
```

La méthode précédente suit un idiome .NET `message` typique : la valeur de rendement indique si elle a été réglée à la valeur trouvée ou, si aucun message n’est trouvé, à la valeur par défaut. Si la `true`méthode revient, la valeur de `message` n’est pas nulle; sinon, la `message` méthode s’établit à annuler.

Vous pouvez communiquer cet idiome en utilisant l’attribut. `NotNullWhen` Lorsque vous mettez à jour la `message` signature `string?` pour les types de référence nuls, faites un attribut et ajoutez un attribut :

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

Dans l’exemple précédent, `message` la valeur de `TryGetMessage` est `true`connu pour ne pas être nul lors des déclarations . Vous devez annoter des méthodes similaires dans votre base `null`de code de la même manière: `true`les arguments pourraient être , et sont connus pour ne pas être nul lorsque la méthode revient .

Il ya un attribut final dont vous pouvez également avoir besoin. Parfois, l’état nul d’une valeur de retour dépend de l’état nul d’un ou plusieurs arguments d’entrée. Ces méthodes retourneront une valeur non nulle chaque `null`fois que certains arguments d’entrée ne sont pas . Pour annoter correctement ces méthodes, vous utilisez l’attribut. `NotNullIfNotNull` Considérez la méthode suivante :

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

Si `url` l’argument n’est pas nul, la sortie n’est pas `null`. Une fois que les références annulées sont activées, cette signature fonctionne correctement, à condition que votre API n’accepte jamais une entrée nulle. Toutefois, si l’entrée pouvait être nulle, la valeur de retour pourrait également être nulle. Par conséquent, vous pouvez modifier la signature au code suivant :

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

Cela fonctionne également, mais forcera souvent `null` les appelants à mettre en œuvre des contrôles supplémentaires. Le contrat est que la `null` valeur de `url` rendement `null`ne serait que lorsque l’argument de l’entrée est . Pour exprimer ce contrat, vous annoteriez cette méthode comme indiqué dans le code suivant :

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

La valeur de rendement et l’argument `?` ont tous deux `null`été annotés avec l’indication que l’un ou l’autre pourrait être . L’attribut précise en outre que la valeur `url` de rendement `null`ne sera pas nulle lorsque l’argument n’est pas .

Vous spécifiez des conditions post-conditions conditionnelles à l’aide de ces attributs :

- [Peut-êtreNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Un argument d’entrée non annulable `bool` peut être nul lorsque la méthode renvoie la valeur spécifiée.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Un argument d’entrée nul ne sera `bool` pas nul lorsque la méthode retourne la valeur spécifiée.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Une valeur de retour n’est pas nulle si l’argument de l’entrée pour le paramètre spécifié n’est pas nul.

## <a name="generic-definitions-and-nullability"></a>Définitions génériques et nullité

Communiquer correctement l’état nul des types génériques et des méthodes génériques nécessite un soin particulier. Cela découle du fait qu’un type de valeur nul et un type de référence nul sont fondamentalement différents. Un `int?` est synonyme `Nullable<int>`de `string?` , `string` alors qu’il est avec un attribut ajouté par le compilateur. Le résultat est que le compilateur ne `T?` peut `T` pas `class` générer `struct`un code correct pour sans savoir si est a ou a .

Cela ne signifie pas que vous ne pouvez pas utiliser un type nul (type de valeur ou de type de référence) comme argument de type pour un type générique fermé. Les `List<string?>` `List<int?>` deux et sont des `List<T>`instantanés valides de .

Ce que cela signifie, c’est que vous ne pouvez pas utiliser `T?` dans une classe générique ou une déclaration de méthode sans contraintes. Par exemple, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> ne sera pas `T?`changé pour revenir . Vous pouvez surmonter cette limitation `struct` `class` en ajoutant soit la contrainte. Avec l’une ou l’autre de ces contraintes, le compilateur sait comment générer du code pour les deux `T` et `T?`.

Vous pouvez restreindre les types utilisés pour un argument de type générique pour être des types non-nullables. Vous pouvez le faire `notnull` en ajoutant la contrainte sur cet argument de type. Lorsque cette contrainte est appliquée, l’argument type ne doit pas être un type nul.

## <a name="conclusions"></a>Conclusions

L’ajout de types de référence in annulables fournit `null`un vocabulaire initial pour décrire vos attentes d’API pour les variables qui pourraient être . Les attributs supplémentaires fournissent un vocabulaire plus riche pour décrire l’état nul des variables comme conditions préalables et conditions post. Ces attributs décrivent plus clairement vos attentes et offrent une meilleure expérience pour les développeurs utilisant vos API.

Lorsque vous mettez à jour les bibliothèques pour un contexte nul, ajoutez ces attributs pour guider les utilisateurs de vos API à l’utilisation correcte. Ces attributs vous aident à décrire pleinement l’état nul des arguments d’entrée et des valeurs de rendement :

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Un argument d’entrée non annulable peut être nul.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Un argument d’entrée nul ne devrait jamais être nul.
- [Peut-êtreNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Une valeur de retour non annulable peut être nulle.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Une valeur de retour annulée ne sera jamais nulle.
- [Peut-êtreNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Un argument d’entrée non annulable `bool` peut être nul lorsque la méthode renvoie la valeur spécifiée.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Un argument d’entrée nul ne sera `bool` pas nul lorsque la méthode retourne la valeur spécifiée.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Une valeur de retour n’est pas nulle si l’argument de l’entrée pour le paramètre spécifié n’est pas nul.
