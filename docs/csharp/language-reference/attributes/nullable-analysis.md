---
title: 'Attributs réservés C : Analyse statique nulle'
ms.date: 04/14/2020
description: Ces attributs sont interprétés par le compilateur pour fournir une meilleure analyse statique pour les types de référence nuls et non annulables.
ms.openlocfilehash: 33521133a6a01196e6e1ab9c3cdc191a24f1ecf3
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102708"
---
# <a name="reserved-attributes-contribute-to-the-compilers-null-state-static-analysis"></a>Les attributs réservés contribuent à l’analyse statique de l’état nul du compilateur

Dans un contexte in annulable, le compilateur effectue une analyse statique du code pour déterminer l’état nul de toutes les variables de type de référence :

- *non nulle*: Analyse statique a permis de déterminer que la variable est attribuée à une valeur non nulle.
- *peut-être nulle*: L’analyse statique ne peut pas déterminer qu’une variable se voit attribuer une valeur non nulle.

Vous pouvez appliquer un certain nombre d’attributs qui fournissent des informations au compilateur sur la sémantique de vos API. Cette information aide le compilateur à effectuer une analyse statique et à déterminer quand une variable n’est pas nulle. Cet article fournit une brève description de chacun de ces attributs et comment les utiliser. Tous les exemples supposent C 8.0 ou plus récent, et le code est dans un contexte nul.

Commençons par un exemple familier. Imaginez que votre bibliothèque dispose de l’API suivante pour récupérer une chaîne de ressources :

```csharp
bool TryGetMessage(string key, out string message)
```

L’exemple précédent `Try*` suit le modèle familier en .NET. Il existe deux arguments de référence `key` pour `message` cette API : le et le paramètre. Cette API a les règles suivantes relatives à l’annulation de ces arguments :

- Les appelants `null` ne devraient pas `key`passer comme l’argument pour .
- Les appelants peuvent passer une `null` variable dont `message`la valeur est comme l’argument pour .
- Si `TryGetMessage` la `true`méthode revient, la valeur de `message` n’est pas nulle. Si la valeur `false,` de `message` rendement est la valeur de (et son état nul) est nulle.

La règle `key` pour peut être exprimée `key` par le type variable: devrait être un type de référence non-nullable. Le `message` paramètre est plus complexe. Il `null` permet comme argument, mais garantit que, sur le succès, cet `out` argument n’est pas nul. Pour ces scénarios, vous avez besoin d’un vocabulaire plus riche pour décrire les attentes.

Plusieurs attributs ont été ajoutés pour exprimer des informations supplémentaires sur l’état nul des variables. Tout le code que vous avez écrit avant que le C 8 n’introduise des types de référence nuls *était nul inconscient.* Cela signifie que toute variable de type de référence peut être nulle, mais les contrôles nuls ne sont pas nécessaires. Une fois que votre code est *infirampable au courant,* ces règles changent. Les types de `null` référence ne doivent jamais être la `null` valeur, et les types de référence nuls doivent être vérifiés avant d’être déreférés.

Les règles de vos API sont probablement plus `TryGetValue` compliquées, comme vous l’avez vu avec le scénario API. Beaucoup de vos API ont des règles plus complexes pour quand les variables peuvent ou ne peuvent pas être `null`. Dans ces cas, vous utiliserez l’un des attributs suivants pour exprimer ces règles :

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Un argument d’entrée non annulable peut être nul.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Un argument d’entrée nul ne devrait jamais être nul.
- [Peut-êtreNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Une valeur de retour non annulable peut être nulle.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Une valeur de retour annulée ne sera jamais nulle.
- [Peut-êtreNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Un argument d’entrée non annulable `bool` peut être nul lorsque la méthode renvoie la valeur spécifiée.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Un argument d’entrée nul ne sera `bool` pas nul lorsque la méthode retourne la valeur spécifiée.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Une valeur de retour n’est pas nulle si l’argument du paramètre spécifié n’est pas nul.
- [DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): Une méthode ne revient jamais. En d’autres termes, il jette toujours une exception.
- [DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): Cette méthode ne `bool` revient jamais si le paramètre associé a la valeur spécifiée.

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

Dans un contexte in `ReviewComment` `get` annulable, l’accesseur peut retourner la valeur par défaut de `null`. Le compilateur prévient qu’il doit être vérifié avant l’accès. En outre, il avertit les appelants que, même si elle pourrait être `null`, les appelants ne devraient pas explicitement le définir à `null`. L’attribut `DisallowNull` spécifie également une condition `get` *préalable,* il n’affecte pas l’accesseur. Vous utilisez `DisallowNull` l’attribut lorsque vous observez ces caractéristiques sur :

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

Pour des raisons couvertes par [des définitions génériques et l’annulation,](../../nullable-migration-strategies.md#generic-definitions-and-nullability) cette technique ne fonctionne pas avec des méthodes génériques. Vous pouvez avoir une méthode générique qui suit un modèle similaire:

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

Le code précédent exprime clairement le contrat existant : `null` les appelants peuvent passer une variable avec la valeur, mais la valeur de rendement est garantie de ne jamais être nulle. `NotNull` L’attribut est `ref` le `out` plus `null` utile et les arguments où peut être adopté comme un argument, mais cet argument est garanti d’être pas nul lorsque la méthode revient.

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

## <a name="verify-unreachable-code"></a>Vérifier le code inaccessible

Certaines méthodes, généralement exception aides ou autres méthodes d’utilité, toujours sortir en jetant une exception. Ou, un aide peut jeter une exception basée sur la valeur d’un argument Boolean.

Dans le premier cas, `DoesNotReturn` vous pouvez ajouter l’attribut à la déclaration de méthode. Le compilateur vous aide de trois façons. Tout d’abord, le compilateur émet un avertissement s’il ya un chemin où la méthode peut sortir sans jeter une exception. Deuxièmement, le compilateur marque n’importe quel code après un `catch` appel à cette méthode comme *inaccessible,* jusqu’à ce qu’une clause appropriée soit rencontrée. Troisièmement, le code inaccessible n’affectera aucun état nul. Prenons la méthode suivante :

```csharp
[DoesNotReturn]
private void FailFast()
{
   throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   if (!isInitialized)
      FailFast();

   // unreachable code:
   this.field = containedField;
}
```

Dans le deuxième cas, `DoesNotReturnIf` vous ajoutez l’attribut à un paramètre Boolean de la méthode. Vous pouvez modifier l’exemple précédent comme suit :

```csharp
private void FailFast([DoesNotReturnIf(false)]bool isValid)
{
   if (!isValid)
       throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   FailFast(isInitialized);

   // unreachable code when "isInitialized" is false:
   this.field = containedField;
}
```

## <a name="summary"></a>Résumé

L’ajout de types de référence in annulables fournit `null`un vocabulaire initial pour décrire vos attentes d’API pour les variables qui pourraient être . Les attributs supplémentaires fournissent un vocabulaire plus riche pour décrire l’état nul des variables comme conditions préalables et conditions post. Ces attributs décrivent plus clairement vos attentes et offrent une meilleure expérience pour les développeurs utilisant vos API.

Lorsque vous mettez à jour les bibliothèques pour un contexte nul, ajoutez ces attributs pour guider les utilisateurs de vos API à l’utilisation correcte. Ces attributs vous aident à décrire pleinement l’état nul des arguments d’entrée et des valeurs de rendement :

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Un argument d’entrée non annulable peut être nul.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Un argument d’entrée nul ne devrait jamais être nul.
- [Peut-êtreNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Une valeur de retour non annulable peut être nulle.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Une valeur de retour annulée ne sera jamais nulle.
- [Peut-êtreNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Un argument d’entrée non annulable `bool` peut être nul lorsque la méthode renvoie la valeur spécifiée.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Un argument d’entrée nul ne sera `bool` pas nul lorsque la méthode retourne la valeur spécifiée.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Une valeur de retour n’est pas nulle si l’argument de l’entrée pour le paramètre spécifié n’est pas nul.
- [DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): Une méthode ne revient jamais. En d’autres termes, il jette toujours une exception.
- [DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): Cette méthode ne `bool` revient jamais si le paramètre associé a la valeur spécifiée.
