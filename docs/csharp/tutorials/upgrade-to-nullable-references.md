---
title: Mettre à niveau vers des types de référence Nullable
description: Ce didacticiel avancé montre comment migrer du code existant avec des types de référence Nullable.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: 38619f9efa5da1f9b3264b3d4240103f0869afea
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240026"
---
# <a name="tutorial-migrate-existing-code-with-nullable-reference-types"></a>Didacticiel : migrer du code existant avec des types de référence Nullable

C# 8 introduit les **types référence Nullable**, qui viennent compléter les types référence de la même façon que les types valeur Nullable complètent les types valeur. Pour déclarer une variable comme étant un **type référence Nullable**, on ajoute `?` au type. Par exemple, `string?` représente une `string` Nullable. Vous pouvez utiliser ces nouveaux types pour exprimer plus clairement votre intention de conception : certaines variables *doivent toujours avoir une valeur*, d’autres *peuvent ne pas en avoir*. Toutes les variables existantes d’un type de référence sont interprétées comme un type de référence non nullable. 

Ce didacticiel vous montre comment effectuer les opérations suivantes :

> [!div class="checklist"]
>
> - Activer les vérifications de référence null lorsque vous travaillez avec du code.
> - Diagnostiquer et corriger les différents avertissements liés aux valeurs null.
> - Gérer l’interface entre les contextes compatibles avec nullable et non compatibles avec nullable.
> - Contrôler les contextes d’annotation nullable.

## <a name="prerequisites"></a>Composants requis

Vous devez configurer votre ordinateur pour exécuter .NET Core, y compris le C# compilateur 8,0. Le C# compilateur 8 est disponible à partir de [Visual Studio 2019 version 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou du [Kit de développement logiciel (SDK) .net Core 3,0](https://dotnet.microsoft.com/download).

Ce tutoriel suppose de connaître C# et .NET, y compris Visual Studio ou l’interface CLI .NET Core.

## <a name="explore-the-sample-application"></a>Explorer l’exemple d’application

L’exemple d’application que vous allez migrer est une application web de lecteur de flux RSS. Il lit à partir d’un flux RSS unique et affiche des résumés des articles les plus récents. Vous pouvez sélectionner n’importe quel article pour visiter le site. L’application est relativement nouvelle, mais a été écrite avant que les types de référence nullable ne soient disponibles. Les décisions de conception de l’application constituent des principes solides, mais ne tirent pas parti de cette fonctionnalité de langage importante.

L’exemple d’application inclut une bibliothèque de tests unitaires qui valide les fonctionnalités principales de l’application. Ce projet facilite la mise à niveau en toute sécurité, si vous modifiez l’implémentation basée sur les avertissements générés. Vous pouvez télécharger l’exemple de démarrage à partir du référentiel GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/start).

Votre objectif de migration d’un projet doit être de tirer parti des nouvelles fonctionnalités de langage afin d’exprimer clairement votre intention sur la possibilité de valeur null des variables et faire cela de manière à ce que le compilateur ne génère d’avertissements lorsque le contexte d’annotation nullable et le contexte d’avertissement nullable sont définis sur `enabled`.

## <a name="upgrade-the-projects-to-c-8"></a>Mettre à niveau les projets vers C# 8

La première étape consiste à déterminer l’étendue de la tâche de migration. Commencez par la mise à niveau du projet vers C# 8.0 (ou version ultérieure). Ajoutez l’élément `LangVersion` au PropertyGroup dans les deux fichiers csproj pour le projet Web et le projet de test unitaire :

```xml
<LangVersion>8.0</LangVersion>
```

La mise à niveau de la version de langage sélectionne C# 8.0, mais n’active pas le contexte d’annotation nullable ou le contexte d’avertissement nullable. Régénérez le projet pour vous assurer qu’il se génère sans avertissement.

Une bonne étape suivante consiste à activer le contexte d’annotation nullable et de voir combien d’avertissements sont générés. Ajoutez l’élément suivant aux fichiers csproj dans la solution, directement sous l’élément `LangVersion` :

```xml
<Nullable>enable</Nullable>
```

Effectuez une build de test et notez la liste d’avertissements. Dans cette petite application, le compilateur génère cinq avertissements, il est donc probable que vous laissiez le contexte d’annotation nullable activé et commenciez à résoudre les avertissements pour l’ensemble du projet.

Cette stratégie fonctionne uniquement pour les projets plus petits. Pour tous les projets plus volumineux, le nombre d’avertissements générés par l’activation du contexte d’annotation nullable pour l’intégralité de la base de code rend plus difficile de résoudre les avertissements de manière systématique. Pour les grands projets d’entreprise, vous aurez souvent besoin de migrer un projet à la fois. Dans chaque projet, migrez une classe ou un fichier à la fois.

## <a name="warnings-help-discover-original-design-intent"></a>Les avertissements contribuent à découvrir l’intention de conception d’origine

Il existe deux classes qui génèrent plusieurs avertissements. Commencez avec la classe `NewsStoryViewModel`. Supprimez l’élément `Nullable` des deux fichiers csproj afin de pouvoir limiter l’étendue des avertissements aux sections de code sur lesquelles vous travaillez. Ouvrez le fichier *NewsStoryViewModel.cs*, puis ajoutez les directives suivantes pour activer le contexte d’annotation nullable pour `NewsStoryViewModel` et restaurez-le en suivant cette définition de classe :

```csharp
#nullable enable
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; }
    public string Uri { get; set; }
}
#nullable restore
```

Ces deux directives vous aident à concentrer vos efforts de migration. Les avertissements nullables sont générés pour la zone de code sur laquelle vous travaillez activement. Vous les laissez activés jusqu’à ce que vous soyez prêt à activer les avertissements pour l’ensemble du projet. Vous devriez utiliser `restore` plutôt que la valeur `disable` afin de ne pas désactiver accidentellement le contexte ultérieurement lorsque de l’activation des annotations nullables pour la totalité du projet. Une fois que vous avez activé le contexte d’annotation nullable pour la totalité du projet, vous pouvez supprimer tous les pragmas `#nullable` à partir de ce projet.

La classe `NewsStoryViewModel` est un objet de transfert de données (DTO) et deux des propriétés sont des chaînes de lecture/écriture :

[!code-csharp[InitialViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#StarterViewModel)]

Ces deux propriétés provoquent `CS8618`, « Propriété non-nullable initialisée ». Cela est suffisamment clair : les deux propriétés `string` ont la valeur par défaut `null` lorsqu’un `NewsStoryViewModel` est construit. Il est important de découvrir comment les objets `NewsStoryViewModel` sont construits. En examinant cette classe, vous ne pouvez pas savoir si la valeur `null` fait partie de la conception, ou si ces objets sont définis sur des valeurs non null lors de leur création. Les articles de presse sont créés dans la méthode `GetNews` de la classe `NewsService` :

[!code-csharp[StarterCreateNewsItem](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#CreateNewsItem)]

Il se passe beaucoup de choses dans le bloc de code précédent. Cette application utilise le package NuGet [AutoMapper](https://automapper.org/) pour construire un élément d’article de presse à partir d’un `ISyndicationItem`. Vous avez découvert que les éléments d’articles de presse sont construits et que les propriétés sont définies dans cette seule instruction. Cela signifie que la conception de `NewsStoryViewModel` indique que ces propriétés ne doivent jamais avoir la valeur `null`. Ces propriétés doivent être des **types de référence non nullable**. C’est ce qui correspond le mieux à l’intention de conception d’origine. En fait, tout `NewsStoryViewModel` *est* correctement instancié avec des valeurs non null. Ce qui fait du code d’initialisation suivant un correctif valide :

```csharp
public class NewsStoryViewModel
{
    public DateTimeOffset Published { get; set; }
    public string Title { get; set; } = default!;
    public string Uri { get; set; } = default!;
}
```

L’attribution de `Title` et `Uri` à `default` qui est `null` pour le type `string` ne change pas le comportement d’exécution du programme. `NewsStoryViewModel` est toujours construit avec des valeurs null, mais maintenant le compilateur ne signale aucun avertissement. **L’opérateur indulgent en null**, le caractère `!` qui suit l’expression `default` indique au compilateur que l’expression précédente n’est pas null. Cette technique peut être utile lorsque d’autres modifications forcent beaucoup plus les modifications apportées à une base de code, mais dans cette application, il existe une solution relativement rapide et plus performante : faire de la `NewsStoryViewModel` un type immuable dans lequel toutes les propriétés sont définies dans le constructeur. Dans `NewsStoryViewModel`, effectuez les changements suivants :

[!code-csharp[FinishedViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/ViewModels/NewsStoryViewModel.cs#FinishedViewModel)]

Une fois cette opération effectuée, vous devez mettre à jour le code qui configure AutoMapper afin qu’il utilise le constructeur, plutôt que de définir des propriétés. Ouvrez `NewsService.cs` et recherchez le code suivant en bas du fichier :

[!code-csharp[StarterAutoMapper](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Ce code mappe les propriétés de l’objet `ISyndicationItem` aux propriétés `NewsStoryViewModel`. Vous souhaitez qu’AutoMapper assure le mappage à l’aide d’un constructeur à la place. Remplacez le code ci-dessus par la configuration Automapper suivante :

[!code-csharp[FinishedViewModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ConfigureAutoMapper)]

Notez qu’étant donné que cette classe est petite, et que vous l’avez examinée avec soin, vous devez activer la directive `#nullable enable` au-dessus de cette déclaration de classe. La modification apportée au constructeur peut avoir rompu quelque chose, il est donc judicieux d’exécuter tous les tests et de tester l’application avant de continuer.

Le premier ensemble de modifications vous a montré comment effectuer la détection lorsque la conception d’origine indiquait que les variables ne devaient pas être définies sur `null`. Cette technique est appelée **correcte par construction**. Vous déclarez qu’un objet et ses propriétés ne peuvent pas être `null` quand il est construit. L’analyse du flux du compilateur fournit la garantie que ces propriétés ne sont pas définies sur `null` après la construction. Notez que ce constructeur est appelé par du code externe, que ce code **oublie la valeur nullable**. La nouvelle syntaxe ne fournit pas la vérification lors de l’exécution. Le code externe peut contourner l’analyse du flux du compilateur. 

Parfois, la structure d’une classe fournit des différents indices sur l’intention. Ouvrez le fichier *Error.cshtml.cs* dans le dossier *Pages*. `ErrorViewModel` contient le code suivant :

[!code-csharp[StarterErrorModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Error.cshtml.cs#StartErrorModel)]

Ajouter la directive `#nullable enable` avant la déclaration de classe et une directive `#nullable restore` après. Vous obtiendrez un avertissement indiquant que `RequestId` n’est pas initialisé. En examinant la classe, vous devez décider que la propriété `RequestId` doit avoir la valeur null dans certains cas. L’existence de la propriété `ShowRequestId` indique que des valeurs manquantes sont possibles. Étant donné que `null` est valide, ajoutez `?` sur le type `string` pour indiquer que la propriété `RequestId` est un *type de référence nullable*. La classe finale se présente comme suit :

[!code-csharp[FinishedErrorModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Error.cshtml.cs#ErrorModel)]

Vérifiez les utilisations de la propriété, et vous voyez que dans la page associée, la présence de la valeur null est vérifiée dans la propriété avant de la restituer dans le balisage. C’est une utilisation sécurisée d’un type de référence nullable, donc vous en avez terminé avec cette classe.

## <a name="fixing-nulls-causes-change"></a>La correction des valeurs null entraîne une modification

Fréquemment, le correctif pour un ensemble d’avertissements crée de nouveaux avertissements dans le code connexe. Nous allons voir les avertissements en action en corrigeant la classe `index.cshtml.cs`. Ouvrez le fichier `index.cshtml.cs` et examinez le code. Ce fichier contient le code sous-jacent à la page d’index :

[!code-csharp[StarterIndexModel](~/samples/snippets/csharp/tutorials/nullable-reference-migration/start/SimpleFeedReader/Pages/Index.cshtml.cs#IndexModelStart)]

Ajoutez la directive `#nullable enable` et vous verrez deux avertissements. Ni la propriété `ErrorText` ni la propriété `NewsItems` ne sont initialisées. Un examen de cette classe vous permettra de croire que les deux propriétés doivent être des types de référence Nullable : les deux ont des méthodes setter privées. Une seule exactement est attribuée dans la méthode `OnGet`. Avant d’apporter des modifications, examinez les consommateurs de ces deux propriétés. Dans la page elle-même, `ErrorText` est comparé à la valeur null avant de générer le balisage d’éventuelles erreurs. La collection `NewsItems` est vérifiée par rapport à `null` et afin de garantir que la collection comporte des éléments. Un correctif rapide serait d’attribuer le type de référence nullable aux deux propriétés. Un meilleur correctif consisterait à attribuer un type de référence non nullable à la collection et d’ajouter des éléments à la collection existante lors de la récupération des articles de presse. Le premier correctif consiste à ajouter `?` au type `string` pour `ErrorText` :

[!code-csharp[UpdateErrorText](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#UpdateErrorText)]

Cette modification ne se propage pas à d’autre code, étant donné que tout accès à la propriété `ErrorText` a été déjà protégé par les contrôles de la valeur null. Ensuite, initialisez la liste `NewsItems` et supprimez la méthode setter de propriété, pour en faire une propriété en lecture seule :

[!code-csharp[InitializeNewsItems](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#InitializeNewsItems)]

Cela a résolu l’avertissement, mais a introduit une erreur. La liste `NewsItems` est désormais **correcte par construction**, mais le code qui définit la liste dans `OnGet` doit changer pour correspondre à la nouvelle API. Au lieu d’une attribution, appelez `AddRange` pour ajouter les éléments d’articles de presse à la liste existante :

[!code-csharp[AddRange](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Pages/Index.cshtml.cs#AddRange)]

Utiliser `AddRange` au lieu d’une attribution signifie que la méthode `GetNews` peut retourner `IEnumerable` au lieu de `List`. Cela permet d’économiser une attribution. Modifiez la signature de la méthode et supprimez l’appel `ToList`, comme indiqué dans l’exemple de code suivant :

[!code-csharp[GetNews](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#GetNewsFinished)]

La modification de la signature rompt aussi l’un des tests. Ouvrez le fichier `NewsServiceTests.cs` dans le dossier `Services` du projet `SimpleFeedReader.Tests`. Accédez au test `Returns_News_Stories_Given_Valid_Uri` et modifiez le type de la variable `result` sur `IEnumerable<NewsItem>`. La modification du type signifie que la propriété `Count` n’est plus disponible, par conséquent, remplacez la propriété `Count` dans `Assert` avec un appel à `Any()` :

[!code-csharp[FixTests](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader.Tests/Services/NewsServiceTests.cs#FixTestSignature)]

Vous devrez ajouter une instruction `using System.Linq` au début du fichier également.

Cet ensemble de modifications met en évidence une attention particulière lors de la mise à jour de code qui inclut des instanciations génériques. La liste et les éléments dans la liste sont de type non nullable. L’un ou les deux peuvent être de type nullable. Toutes les déclarations suivantes sont autorisées :

- `List<NewsStoryViewModel>` : liste non nullable de modèles d’affichage non nullable.
- `List<NewsStoryViewModel?>` : liste non nullable de modèles d’affichage nullable.
- `List<NewsStoryViewModel>?` : liste nullable de modèles d’affichage non nullable.
- `List<NewsStoryViewModel?>?` : liste nullable de modèles d’affichage nullable.

## <a name="interfaces-with-external-code"></a>Interfaces avec du code externe

Vous avez apporté des modifications à la classe `NewsService`, donc activez l’annotation `#nullable enable` pour cette classe. Cela ne génère aucun nouvel avertissements. Toutefois, l’examen attentif de la classe permet d’illustrer certaines des limitations de l’analyse du flux du compilateur. Examinez le constructeur :

[!code-csharp[ServiceConstructor](~/samples/snippets/csharp/tutorials/nullable-reference-migration/finished/SimpleFeedReader/Services/NewsService.cs#ServiceConstructor)]

Le paramètre `IMapper` est typé comme référence non nullable. Il est appelé par le code d’infrastructure ASP.NET Core, donc le compilateur ne sait pas vraiment que `IMapper` ne sera jamais null. Le conteneur d’injection de dépendance (DI) ASP.NET Core par défaut lève une exception s’il ne peut pas résoudre un service nécessaire, afin que le code soit correct. Le compilateur ne peut pas valider tous les appels à vos API publiques, même si votre code est compilé avec des contextes d’annotation nullable activés. En outre, vos bibliothèques peuvent être utilisées par des projets qui n’utilisent pas encore des types de référence nullable. Validez les entrées dans les API publiques même si vous les avez déclarées en tant que types non nullable.

## <a name="get-the-code"></a>Obtenir le code

Vous avez résolu les avertissements que vous avez identifiés dans la compilation du test initial, donc vous pouvez désormais activer le contexte d’annotation nullable pour les deux projets. Régénérez les projets ; le compilateur ne signale aucun avertissement. Vous pouvez obtenir le code pour le projet terminé dans le référentiel GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/nullable-reference-migration/finished).

Les nouvelles fonctionnalités qui prennent en charge les types de référence nullable vous aident à trouver et à corriger les erreurs potentielles dans la façon dont vous gérez les valeurs `null` dans votre code. L’activation du contexte d’annotation nullable vous permet d’exprimer votre intention de conception : certaines variables ne doivent jamais être null, d’autres variables peuvent contenir des valeurs null. Ces fonctionnalités facilitent la déclaration de votre intention de conception. De même, le contexte d’avertissement nullable indique au compilateur d’émettre des avertissements lorsque vous avez enfreint cette intention. Ces avertissements vous guident pour effectuer des mises à jour qui rendent votre code plus robuste et moins susceptible de lever une `NullReferenceException` pendant l’exécution. Vous pouvez contrôler l’étendue de ces contextes afin de vous concentrer sur des zones locales de code à migrer alors que la base de code restante reste intacte. Dans la pratique, vous pouvez intégrer cette tâche de migration dans une maintenance régulière de vos classes. Ce tutoriel a présenté le processus de migration d’une application pour utiliser des types de référence nullable. Vous pouvez explorer un exemple réel plus complet de ce processus en examinant la demande de tirage effectuée par [Jon Skeet](https://github.com/jskeet) pour incorporer les types de référence nullable dans [NodaTime](https://github.com/nodatime/nodatime/pull/1240/commits). En outre, vous pouvez également découvrir des techniques permettant d’utiliser des types de référence Nullable avec Entity Framework Core dans [Entity Framework Core-Working avec des types de référence Nullable](/ef/core/miscellaneous/nullable-reference-types).
