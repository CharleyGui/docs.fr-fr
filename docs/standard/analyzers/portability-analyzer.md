---
title: Analyseur de portabilité .NET – .NET
description: Découvrez comment utiliser l’outil Analyseur de portabilité .NET pour évaluer la portabilité de votre code sur les différentes implémentations de .NET, notamment .NET Core, .NET Standard, UWP et Xamarin.
ms.date: 09/13/2019
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: 048ff916d309f4159fe78177e093a58d731c2e11
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734281"
---
# <a name="the-net-portability-analyzer"></a>Analyseur de portabilité .NET

Vous voulez que vos bibliothèques prennent en charge plusieurs plateformes ? Vous voulez savoir quelle quantité de travail est nécessaire pour que votre application .NET Framework s’exécute sur .NET Core ? L' [Analyseur de portabilité .net](https://github.com/microsoft/dotnet-apiport) est un outil qui analyse les assemblys et fournit un rapport détaillé sur les API .net qui manquent pour que les applications ou les bibliothèques soient portables sur les plateformes .net ciblées spécifiées. L’analyseur de portabilité est proposé sous la forme d’une [extension Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), qui analyse un assembly par projet, et en tant qu' [application console ApiPort](https://aka.ms/apiportdownload), qui analyse les assemblys par fichiers ou répertoires spécifiés.

Une fois que vous avez converti votre projet pour cibler la nouvelle plateforme, comme .NET Core, vous pouvez utiliser l' [outil Analyseur d’API](api-analyzer.md) basé sur Roslyn pour identifier les API levant <xref:System.PlatformNotSupportedException> des exceptions et d’autres problèmes de compatibilité.

## <a name="common-targets"></a>Cibles courantes

- [.Net Core](../../core/introduction.md): possède une conception modulaire, prend en charge l’installation côte à côte et cible des scénarios multiplateformes. L’installation côte à côte vous permet d’adopter de nouvelles versions de .NET Core sans interrompre les autres applications. Si votre objectif est de porter votre application sur .NET Core et de prendre en charge plusieurs plateformes, il s’agit de la cible recommandée.
- . [NET standard](../net-standard.md): comprend les API .NET standard disponibles sur toutes les implémentations .net. Si votre objectif est de faire en sorte que votre bibliothèque s’exécute sur toutes les plates-formes prises en charge par .NET, il s’agit de la cible recommandée.
- [ASP.net Core](/aspnet/core): une infrastructure Web moderne reposant sur .net core. Si votre objectif est de porter votre application web vers .NET Core pour prendre en charge plusieurs plateformes, c’est la cible recommandée.
- .NET Core + [extensions de plateforme](../../core/porting/windows-compat-pack.md): inclut les API .net core en plus du Pack de compatibilité Windows, qui fournit un grand nombre des .NET Framework technologies disponibles. Il s’agit d’une cible recommandée pour le portage de votre application depuis le .NET Framework vers .NET Core sur Windows.
- .NET Standard + [extensions de plateforme](../../core/porting/windows-compat-pack.md): inclut les API .NET standard en plus du Pack de compatibilité Windows, qui fournit une grande partie des .NET Framework technologies disponibles. Il s’agit d’une cible recommandée pour le portage de votre bibliothèque depuis le .NET Framework vers .NET Core sur Windows.

## <a name="how-to-use-the-net-portability-analyzer"></a>Comment utiliser l’Analyseur de portabilité .NET

Pour commencer à utiliser l’Analyseur de portabilité .NET dans Visual Studio, vous devez d’abord télécharger l’extension à partir du [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) et l’installer. Elle fonctionne sur Visual Studio 2017 et les versions ultérieures. Configurez-le dans Visual Studio via **analyser** les  >  paramètres de l'**Analyseur de portabilité** et sélectionnez vos plateformes cibles, qui correspondent aux plateformes/versions .net dont vous souhaitez évaluer les écarts de portabilité comparés à la plateforme/version avec laquelle votre assembly actuel est généré.

![Capture d’écran de l’analyseur de portabilité.](./media/portability-analyzer/portability-screenshot.png)

Vous pouvez aussi utiliser l’application console ApiPort et la télécharger à partir du [référentiel ApiPort](https://aka.ms/apiportdownload). Vous pouvez utiliser l’option de commande `listTargets` pour afficher la liste des cibles disponibles, puis sélectionner les plateformes cibles en spécifiant l’option de commande `-t` ou `--target`.

### <a name="solution-wide-view"></a>Vue étendue de la solution

Une étape utile pour analyser une solution avec de nombreux projets consiste à visualiser les dépendances pour comprendre quel sous-ensemble d’assemblys dépend de quoi. La recommandation générale consiste à appliquer les résultats de l’analyse dans une approche ascendante, en commençant par les nœuds terminaux dans un graphique de dépendance.

Pour récupérer ce code, vous pouvez exécuter la commande suivante :

```console
ApiPort.exe analyze -r DGML -f [directory or file]
```

Un résultat de ce type ressemble à ce qui suit quand il est ouvert dans Visual Studio :

![Capture d’écran de l’analyse DGML.](./media/portability-analyzer/dgml-example.png)

### <a name="analyze-portability"></a>Analyser la portabilité

Pour analyser l’ensemble de votre projet dans Visual Studio, cliquez avec le bouton droit sur votre projet dans l’**Explorateur de solutions** et sélectionnez **Analyser la portabilité des assemblys**. Sinon, accédez au menu **Analyser** et sélectionnez **Analyser la portabilité des assemblys**. À partir de là, sélectionnez l’exécutable ou la DLL de votre projet.

![Capture d’écran de l’analyseur de portabilité de Explorateur de solutions.](./media/portability-analyzer/portability-solution-explorer.png)

Vous pouvez également utiliser l’[application console ApiPort](https://aka.ms/apiportdownload).

- Tapez la commande suivante pour analyser le répertoire actif : `ApiPort.exe analyze -f .`
- Pour analyser une liste spécifique de fichiers .dll, tapez la commande suivante : `ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`
- Exécuter `ApiPort.exe -?` pour obtenir plus d’aide

Il est recommandé d’inclure tous les fichiers exe et dll associés dont vous êtes propriétaire et que vous souhaitez porter, et d’exclure les fichiers dont dépend votre application, mais dont vous n’êtes pas propriétaire et que vous ne pouvez pas porter. Vous obtiendrez ainsi le rapport de portabilité le plus pertinent possible.

### <a name="view-and-interpret-portability-result"></a>Consulter et interpréter les résultats de portabilité

Seules les API qui ne sont pas prises en charge par une plateforme cible apparaissent dans le rapport.
Après avoir exécuté l’analyse dans Visual Studio, vous verrez s’afficher un lien vers le fichier du rapport de portabilité .NET. Si vous avez utilisé l’[application console ApiPort](https://aka.ms/apiportdownload), votre rapport de portabilité de .NET est enregistré en tant que fichier dans le format que vous avez spécifié. Le format par défaut est un fichier Excel (*.xlsx*) dans votre répertoire actuel.

#### <a name="portability-summary"></a>Synthèse de la portabilité

![Capture d’écran de la synthèse de la portabilité.](./media/portability-analyzer/api-catalog-portablility-summary.png)

La section sur la synthèse de la portabilité du rapport montre le pourcentage de portabilité de chaque assembly inclus lors de l’exécution. Dans l’exemple précédent, 71,24 % des API .NET Framework utilisées dans l’application `svcutil` sont disponibles dans .NET Core + Extensions de plateforme. Si vous exécutez l’outil Analyseur de portabilité .NET sur plusieurs assemblys, chaque assembly doit avoir une ligne dans le rapport de synthèse de la portabilité.

#### <a name="details"></a>Détails

![Capture d’écran des détails de la portabilité.](./media/portability-analyzer/api-catalog-portablility-details.png)

La section **Détails** du rapport répertorie les API manquantes dans les **plateformes ciblées** sélectionnées.

- Type cible : le type a une API manquante dans une plateforme cible
- Membre cible : la méthode est manquante dans une plateforme cible
- Nom de l’assembly : assembly .NET Framework dans lequel réside l’API manquante.
- Chacune des plateformes cibles sélectionnées est une colonne, par exemple « .NET Core » : la valeur « non pris en charge » signifie que l’API n’est pas prise en charge sur cette plateforme cible.
- Modifications recommandées : l’API ou la technologie recommandée pour passer à. Actuellement, ce champ est vide ou obsolète pour de nombreuses API. En raison du grand nombre d’API, nous avons un défi important à rester à jour. Nous examinons d’autres solutions pour fournir des informations utiles aux clients.

#### <a name="missing-assemblies"></a>Assemblys manquants

![Capture d’écran des assemblys manquants.](./media/portability-analyzer/api-catalog-missing-assemblies.png)

Vous trouverez peut-être une section sur les assemblys manquants dans votre rapport. Cette section contient la liste des assemblys qui sont référencés par vos assemblys analysés et qui n’ont pas été analysés. S’il s’agit d’un assembly dont vous êtes propriétaire, incluez-le dans l’exécution de l’analyseur de portabilité des API pour obtenir un rapport de portabilité détaillé au niveau de l’API. S’il s’agit d’une bibliothèque tierce, vérifiez s’il existe une version plus récente qui prend en charge votre plateforme cible et passez à la version plus récente. Finalement, la liste doit inclure tous les assemblys tiers dont dépend votre application et qui ont une version prenant en charge votre plateforme cible.

Pour plus d’informations sur l’Analyseur de portabilité .NET, consultez la [documentation GitHub](https://github.com/Microsoft/dotnet-apiport#documentation) et la vidéo Channel 9 [A brief look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) (Aperçu rapide de l’Analyseur de portabilité .NET).
