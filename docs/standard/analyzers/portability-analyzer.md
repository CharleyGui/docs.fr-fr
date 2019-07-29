---
title: Analyseur de portabilité .NET – .NET
description: Découvrez comment utiliser l’outil Analyseur de portabilité .NET pour évaluer la portabilité de votre code sur les différentes implémentations de .NET, notamment .NET Core, .NET Standard, UWP et Xamarin.
ms.date: 07/18/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: 32b4f980061b0975c413a8cde436074f76cfabc9
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433953"
---
# <a name="the-net-portability-analyzer"></a>Analyseur de portabilité .NET

Vous voulez que vos bibliothèques prennent en charge plusieurs plateformes ? Vous souhaitez savoir quelle quantité de travail est nécessaire pour rendre votre application compatible avec d’autres profils et implémentations .NET, notamment .NET Core, .NET Standard, UWP et Xamarin pour iOS, Android et Mac ? L’[Analyseur de portabilité .NET](https://github.com/microsoft/dotnet-apiport) est un outil qui vous donne un rapport détaillé sur la flexibilité de votre programme sur les implémentations de .NET en analysant des assemblys. L’Analyseur de portabilité est proposé comme [Extension Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), qui analyse les assemblys par projet, et comme [application console ApiPort](https://aka.ms/apiportdownload), qui analyse les assemblys par fichier ou répertoire spécifié.

## <a name="common-targets"></a>Cibles courantes

* [.NET Core](../../core/index.md) : possède une conception modulaire, emploie le mode côte à côte et cible les scénarios multiplateformes. Le mode côte-à-côte vous permet d’adopter de nouvelles versions de .NET Core sans interrompre les autres applications. Si votre objectif est de porter votre application vers plusieurs plateformes prises en charge par .NET Core, c’est la cible recommandée. 
* .[NET Standard](../../standard/net-standard.md) : Inclut les API .NET Standard disponibles sur toutes les implémentations de .NET. Si votre objectif consiste à faire en sorte que votre bibliothèque s’exécute sur toutes les plateformes prises en charge par .NET, c’est la cible recommandée.  
* [ASP.NET Core](/aspnet/core) : Framework web moderne reposant sur .NET Core. Si votre objectif est de porter votre application web vers .NET Core pour prendre en charge plusieurs plateformes, c’est la cible recommandée.
* .NET Core + [extensions de plateforme](../../core/porting/windows-compat-pack.md) : Inclut les API .NET Core en plus du Pack de compatibilité Windows, qui fournit un grand nombre de technologies .NET Framework disponibles. Il s’agit d’une cible recommandée pour le portage de votre application depuis le .NET Framework vers .NET Core sur Windows.
* .NET Standard + [extensions de plateforme](../../core/porting/windows-compat-pack.md) : Inclut les API .NET Standard en plus du Pack de compatibilité Windows, qui fournit un grand nombre de technologies .NET Framework disponibles. Il s’agit d’une cible recommandée pour le portage de votre bibliothèque depuis le .NET Framework vers .NET Core sur Windows.

## <a name="how-to-use-the-net-portability-analyzer"></a>Comment utiliser l’Analyseur de portabilité .NET

Pour commencer à utiliser l’Analyseur de portabilité .NET dans Visual Studio, vous devez d’abord télécharger l’extension à partir du [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) et l’installer. Elle fonctionne sur Visual Studio 2017 et les versions ultérieures. Vous pouvez la configurer dans Visual Studio via **Analyser** > **Paramètres de l’Analyseur de portabilité** et choisir vos plateformes cibles, c'est-à-dire les plateformes/versions .NET dont vous souhaitez évaluer les écarts de portabilité en les comparant à la plateforme/version avec laquelle votre assembly actuel est créé.

![Capture d’écran de portabilité](./media/portability-analyzer/portability-screenshot.png)

Vous pouvez aussi utiliser l’application console ApiPort et la télécharger à partir du [référentiel ApiPort](https://aka.ms/apiportdownload). Vous pouvez utiliser l’option de commande `listTargets` pour afficher la liste des cibles disponibles, puis sélectionner les plateformes cibles en spécifiant l’option de commande `-t` ou `--target`. 

### <a name="analyze-portability"></a>Analyser la portabilité
Pour analyser l’ensemble de votre projet dans Visual Studio, cliquez avec le bouton droit sur votre projet dans l’**Explorateur de solutions** et sélectionnez **Analyser la portabilité des assemblys**. Sinon, accédez au menu **Analyser** et sélectionnez **Analyser la portabilité des assemblys**. À partir de là, sélectionnez l’exécutable ou la DLL de votre projet.

![Analyseur de portabilité dans l’Explorateur de solutions](./media/portability-analyzer/portability-solution-explorer.png)

Vous pouvez également utiliser l’[application console ApiPort](https://aka.ms/apiportdownload). 

* Tapez la commande suivante pour analyser le répertoire actif : `ApiPort.exe analyze -f .`
* Pour analyser une liste spécifique de fichiers .dll, tapez la commande suivante : `ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`
* Exécuter `ApiPort.exe -?` pour obtenir plus d’aide

Il est recommandé d’inclure tous les fichiers exe et dll associés dont vous êtes propriétaire et que vous souhaitez porter, et d’exclure les fichiers dont dépend votre application, mais dont vous n’êtes pas propriétaire et que vous ne pouvez pas porter. Vous obtiendrez ainsi le rapport de portabilité le plus pertinent possible.  

### <a name="view-and-interpret-portability-result"></a>Consulter et interpréter les résultats de portabilité

Seules les API qui ne sont pas prises en charge par une plateforme cible apparaissent dans le rapport. Après avoir exécuté l’analyse dans Visual Studio, vous verrez s’afficher un lien vers le fichier du rapport de portabilité .NET. Si vous avez utilisé l’[application console ApiPort](https://aka.ms/apiportdownload), votre rapport de portabilité de .NET est enregistré en tant que fichier dans le format que vous avez spécifié. Le format par défaut est un fichier Excel ( *.xlsx*) dans votre répertoire actuel.

#### <a name="portability-summary"></a>Synthèse de la portabilité 

![Synthèse de la portabilité](./media/portability-analyzer/portabilitysummary.png)

La section sur la synthèse de la portabilité du rapport montre le pourcentage de portabilité de chaque assembly inclus lors de l’exécution. Dans l’exemple précédent, 71,24 % des API .NET Framework utilisées dans l’application `svcutil` sont disponibles dans .NET Core + Extensions de plateforme. Si vous exécutez l’outil Analyseur de portabilité .NET sur plusieurs assemblys, chaque assembly doit avoir une ligne dans le rapport de synthèse de la portabilité.

#### <a name="details"></a>Détails

![Détails de la portabilité](./media/portability-analyzer/portabilitydetails.png)

La section des détails du rapport liste les API manquantes de l’une des plateformes cibles. 

- Type cible : le type a une API manquante dans une plateforme cible 
- Membre cible : la méthode est manquante dans une plateforme cible 
- Nom de l’assembly : assembly .NET Framework dans lequel réside l’API manquante. 
- Chacune des plateformes cibles sélectionnées est une colonne, comme « .NET Core » : La valeur « Non pris en charge » signifie que l’API n’est pas prise en charge sur cette plateforme cible. 
- Changements recommandés : API ou technologie de remplacement recommandée. Actuellement, ce champ est vide ou obsolète pour un grand nombre d’API. En raison du grand nombre d’API, il est très difficile de le maintenir à jour. Nous étudions d’autres solutions pour fournir des informations utiles aux clients.

#### <a name="missing-assemblies"></a>Assemblys manquants

![Détails de la portabilité](./media/portability-analyzer/missingassemblies.png)

Vous trouverez peut-être une section sur les assemblys manquants dans votre rapport. Elle vous indique que cette liste d’assemblys est référencée par vos assemblys analysés et qu’ils n’ont pas été analysés. Si c’est un assembly qui vous appartient, incluez-le dans l’exécution de l’Analyseur de portabilité d’Api afin d’obtenir un rapport de portabilité détaillé au niveau de l’API. S’il s’agit d’une bibliothèque tierce, regardez si elle a une version plus récente prenant en charge votre plateforme cible. Si oui, passez à la version plus récente. Au final, vous devriez obtenir une liste qui inclut tous les assemblys tiers dont dépend votre application et qui confirme qu’ils ont une version prenant en charge votre plateforme cible.  

Pour plus d’informations sur l’Analyseur de portabilité .NET, consultez la [documentation GitHub](https://github.com/Microsoft/dotnet-apiport#documentation) et la vidéo Channel 9 [A brief look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) (Aperçu rapide de l’Analyseur de portabilité .NET).
