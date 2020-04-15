---
title: Améliorer les API pour les types de référence nuls avec des attributs qui définissent les attentes pour les valeurs nulles
description: Apprenez à utiliser les attributs descriptifs AllowNull, DisallowNull, MaybeNull, NotNull et plus encore pour décrire pleinement l’état nul de vos API.
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: 7f78bd0224f93b4b9dcc2b9d4e3577db06497907
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389595"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Mettre à jour les bibliothèques pour qu’elles utilisent des types de référence nuls et communiquent des règles in annulables aux appelants

L’ajout de types de [référence in annulables](nullable-references.md) signifie que vous pouvez déclarer si une `null` valeur est autorisée ou attendue pour chaque variable. En outre, vous pouvez appliquer un `AllowNull` `DisallowNull`certain `MaybeNull` `NotNull`nombre `NotNullWhen` `MaybeNullWhen`d’attributs: , , , , , et `NotNullIfNotNull` de décrire complètement les états nuls de l’argumentation et les valeurs de retour. Cela offre une grande expérience que vous écrivez du code. Vous obtenez des avertissements si une variable `null`non-nullable pourrait être définie à . Vous obtenez des avertissements si une variable nulle n’est pas vérifiée non vérifiée avant de la déreférencer. La mise à jour de vos bibliothèques peut prendre du temps, mais les retombées en valent la peine. Plus vous fournissez d’informations au `null` compilateur sur le *moment où* une valeur est autorisée ou interdite, les meilleurs avertissements que les utilisateurs de votre API obtiendront. Commençons par un exemple familier. Imaginez que votre bibliothèque dispose de l’API suivante pour récupérer une chaîne de ressources :

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

Les règles de vos API sont probablement plus `TryGetValue` compliquées, comme vous l’avez vu avec le scénario API. Beaucoup de vos API ont des règles plus complexes pour quand les variables peuvent ou ne peuvent pas être `null`. Dans ces cas, vous utiliserez des attributs pour exprimer ces règles. Les attributs qui décrivent la sémantique de votre API se trouvent dans l’article sur [les attributs qui ont un impact d’analyse nulle](./language-reference/attributes/nullable-analysis.md).

## <a name="generic-definitions-and-nullability"></a>Définitions génériques et nullité

Communiquer correctement l’état nul des types génériques et des méthodes génériques nécessite un soin particulier. Cela découle du fait qu’un type de valeur nul et un type de référence nul sont fondamentalement différents. Un `int?` est synonyme `Nullable<int>`de `string?` , `string` alors qu’il est avec un attribut ajouté par le compilateur. Le résultat est que le compilateur ne `T?` peut `T` pas `class` générer `struct`un code correct pour sans savoir si est a ou a .

Cela ne signifie pas que vous ne pouvez pas utiliser un type nul (type de valeur ou de type de référence) comme argument de type pour un type générique fermé. Les `List<string?>` `List<int?>` deux et sont des `List<T>`instantanés valides de .

Ce que cela signifie, c’est que vous ne pouvez pas utiliser `T?` dans une classe générique ou une déclaration de méthode sans contraintes. Par exemple, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> ne sera pas `T?`changé pour revenir . Vous pouvez surmonter cette limitation `struct` `class` en ajoutant soit la contrainte. Avec l’une ou l’autre de ces contraintes, le compilateur sait comment générer du code pour les deux `T` et `T?`.

Vous pouvez restreindre les types utilisés pour un argument de type générique pour être des types non-nullables. Vous pouvez le faire `notnull` en ajoutant la contrainte sur cet argument de type. Lorsque cette contrainte est appliquée, l’argument type ne doit pas être un type nul.
