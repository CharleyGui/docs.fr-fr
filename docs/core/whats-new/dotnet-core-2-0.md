---
title: Nouveautés de .NET Core 2.0
description: Découvrez les nouvelles fonctionnalités de .NET Core.
ms.date: 08/13/2017
ms.openlocfilehash: 115b3adc72b6798c6a7bac9cc18044a8822808a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398831"
---
# <a name="whats-new-in-net-core-20"></a>Nouveautés de .NET Core 2.0

.NET core 2.0 inclut les nouvelles fonctionnalités et améliorations dans les domaines suivants :

- [Outils](#tooling)
- [Support multilingue](#language-support)
- [Améliorations de plate-forme](#platform-improvements)
- [Modifications d'API](#api-changes-and-library-support)
- [Intégration Visual Studio](#visual-studio-integration)
- [Améliorations de la documentation](#documentation-improvements)

## <a name="tooling"></a>Outils

### <a name="dotnet-restore-runs-implicitly"></a>la restauration de dotnet s’exécute implicitement

Dans les versions précédentes de .NET Core, vous deviez exécuter la commande [restauration de dotnet ](../tools/dotnet-restore.md) pour télécharger les dépendances immédiatement après la création d’un nouveau projet avec la commande [nouveauté de dotnet](../tools/dotnet-new.md), ainsi que dès que vous ajoutiez une nouvelle dépendance à votre projet.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Vous pouvez également désactiver l’appel automatique de `dotnet restore` en passant le commutateur `--no-restore` sur les commandes `new`, `run`, `build`, `publish`, `pack` et `test`.

### <a name="retargeting-to-net-core-20"></a>Reciblage vers .NET Core 2.0

Si le Kit SDK .NET Core 2.0 est installé, les projets qui ciblent .NET Core 1.x peuvent être reciblés vers .NET Core 2.0.

Pour recibler vers .NET Core 2.0, modifiez votre fichier projet en modifiant la valeur de l’élément `<TargetFramework>` (ou l’élément `<TargetFrameworks>` si vous avez plus d’une cibles dans votre fichier projet) de 1.x à 2.0 :

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

Vous pouvez également recibler les bibliothèques .NET Standard vers .NET Standard 2.0 de la même façon :

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

Pour plus d’informations sur la migration de votre projet vers .NET Core 2.0, consultez [Migration depuis ASP.NET Core 1.x vers ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).

## <a name="language-support"></a>Support multilingue

En plus de la prise en charge de c# et F#, .NET Core 2.0 prend également en charge Visual Basic.

### <a name="visual-basic"></a>Visual Basic

Avec la version 2.0, .NET Core prend désormais en charge Visual Basic 2017. Vous pouvez utiliser Visual Basic pour créer des types de projets suivants :

- Applications de consoles .NET Core
- Bibliothèques de classes .NET Core
- Bibliothèques de classes .NET Standard
- Projets de test unitaire .NET Core
- Projet de test xUnit .NET Core

Par exemple, pour créer une application Visual Basic « Hello World », procédez comme suit à partir de la ligne de commande :

1. Ouvrez la fenêtre de la console, créez un répertoire pour votre projet et définissez-le comme répertoire actif.

1. Entrez la commande `dotnet new console -lang vb`.

   La commande crée un fichier projet avec une extension de fichier `.vbproj` ainsi qu’un fichier de code source Visual Basic nommé *Program.vb*. Ce fichier contient le code source pour écrire la chaîne « Hello World ! » sur la fenêtre de console.

1. Entrez la commande `dotnet run`. [CLI .NET Core](../tools/index.md) compile et exécute automatiquement l’application, qui affiche le message « Hello World ! » dans la fenêtre de console.

### <a name="support-for-c-71"></a>Prise en charge de C#, 7.1

.NET core 2.0 prend en charge C# 7.1, qui ajoute un nombre de nouvelles fonctionnalités, notamment :

- La méthode `Main`, le point d’entrée de l’application, peut être marquée avec le mot clé [asynchrone](../../csharp/language-reference/keywords/async.md).
- Déduire les noms de tuple.
- Expressions par défaut.

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a>Améliorations de plate-forme

.NET core 2.0 inclut plusieurs fonctionnalités qui facilitent l’installation de .NET Core et pour l’utiliser sur les systèmes d’exploitation pris en charge.

### <a name="net-core-for-linux-is-a-single-implementation"></a>.NET core pour Linux est une mise en œuvre unique

.NET core 2.0 offre une mise en œuvre unique de Linux qui fonctionne sur plusieurs distributions de Linux. .NET core 1.x exige que vous téléchargiez une mise en œuvre de Linux spécifique à la distribution.

Vous pouvez également développer des applications qui ciblent Linux en tant que système d’exploitation unique. .NET core 1.x exige que vous cibliez séparément chaque distribution Linux.

### <a name="support-for-the-apple-cryptographic-libraries"></a>Prise en charge des bibliothèques de chiffrement Apple

.NET core 1.x sur macOS exige la bibliothèque de chiffrements du kit de ressources OpenSSL. .NET core 2.0 utilise les bibliothèques de chiffrement Apple et ne nécessite pas OpenSSL, vous n’en avez donc pas besoin pour l’installer.

## <a name="api-changes-and-library-support"></a>Prise en charge de la bibliothèque et des modifications de l’API

### <a name="support-for-net-standard-20"></a>Prise en charge de .NET 2.0 Standard

.NET Standard définit un ensemble par version de l’API qui doit être disponible sur des mises en œuvre .NET conformes à cette version de la norme. .NET Standard est destiné aux développeurs de bibliothèques. Il vise à garantir la fonctionnalité disponible dans une bibliothèque qui cible une version de .NET Standard sur chaque mise en œuvre .NET. .NET core 1.x prend en charge la .NET Standard version 1.6 ; .NET Core 2.0 prend en charge la dernière version, .NET Standard 2.0. Pour plus d'informations, consultez [.NET Standard](../../standard/net-standard.md).

.NET Standard 2.0 inclut plus de 20 000 API de plus que dans la version .NET Standard 1.6. Une grande partie de cette surface d’exposition étendue résulte de l’incorporation des API communs à .NET Framework et Xamarin dans .NET Standard.

Les bibliothèques de classes .NET Standard 2.0 peuvent également faire référence à des bibliothèques de classes .NET Framework, à condition qu’elles appellent des API présents dans .NET Standard 2.0. Aucune recompilation des bibliothèques .NET Framework n’est requise.

Pour une liste des API qui ont été ajoutées à la norme .NET depuis sa dernière version, le .NET Standard 1.6, voir [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

### <a name="expanded-surface-area"></a>Surface d’exposition étendue

Le nombre total d’API disponible sur .NET Core 2.0 a plus que doublé par rapport à .NET Core 1.1.

Et grâce au [pack de compatibilité Windows](../porting/windows-compat-pack.md), le portage à partir du .NET Framework est beaucoup plus simple.

### <a name="support-for-net-framework-libraries"></a>Prise en charge des bibliothèques .NET Framework

Le code .NET Core peut faire référence aux bibliothèques .NET Framework existantes, y compris les packages NuGet existants. Notez que les bibliothèques doivent utiliser des API qui se trouvent dans .NET Standard.

## <a name="visual-studio-integration"></a>Intégration de Visual Studio

Visual Studio 2017 version 15,3 et dans certains cas, Visual Studio pour Mac proposent un nombre d’améliorations importantes pour les développeurs de .NET Core.

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a>Reciblage des applications .NET Core et des bibliothèques .NET Standard

Si le Kit SDK .NET Core 2.0 est installé, vous pouvez recibler les projets .NET Core 1.x vers .NET Core 2.0 et les bibliothèques .NET Standard 1.x vers .NET Standard 2.0.

Pour recibler votre projet dans Visual Studio, ouvrez l’onglet **Application** de la boîte de dialogue des propriétés du projet et modifiez la valeur**Infrastructure cible** sur **.NET Core 2.0** ou **.NET Standard 2.0**. Vous pouvez également le modifier en cliquant sur le projet avec le bouton droit et en sélectionnant l’option **Modifier le fichier\*.csproj**. Pour plus d'informations, consultez la section [Outillage](#tooling) plus haut dans cette rubrique.

### <a name="live-unit-testing-support-for-net-core"></a>Prise en charge de Live Unit Testing pour .NET Core

Lorsque vous modifiez votre code, Live Unit Testing exécute automatiquement tous les tests unitaires affectés en arrière-plan et présente les résultats et la couverture du code dans l’environnement Visual Studio. .NET Core 2.0 prend désormais en charge Live Unit Testing. Live Unit Testing était auparavant disponible uniquement pour les applications .NET Framework.

Pour plus d’informations, voir [Live Unit Testing with Visual Studio](/visualstudio/test/live-unit-testing) et live Unit Testing [FAQ](/visualstudio/test/live-unit-testing-faq).

### <a name="better-support-for-multiple-target-frameworks"></a>Meilleure prise en charge pour plusieurs infrastructures cibles

Si vous créez un projet pour plusieurs infrastructures cibles, vous pouvez maintenant sélectionner la plateforme cible dans le menu de niveau supérieur. Dans l’illustration suivante, un projet nommé SCD1 cible macOS X 10.11 64 bits (`osx.10.11-x64`) et Windows 10/Windows Server 2016 64 bits (`win10-x64`). Vous pouvez sélectionner l’infrastructure cible avant de sélectionner le bouton du projet, dans ce cas pour exécuter une version de débogage.

![Capture d’écran montrant la sélection du framework cible lors de la génération d’un projet.](./media/dotnet-core-2-0/target-framework-selection.png)

### <a name="side-by-side-support-for-net-core-sdks"></a>Prise en charge côte à côte pour les kits SDK .NET Core

Vous pouvez maintenant installer le Kit SDK .NET Core indépendamment de Visual Studio. Cela rend possible pour une seule version de Visual Studio pour générer des projets qui ciblent des versions différentes du .NET Core. Auparavant, Visual Studio et le Kit SDK .NET Core ont été étroitement couplés ; une version particulière du kit SDK accompagnée d’une version particulière de Visual Studio.

## <a name="documentation-improvements"></a>Améliorations de la documentation

### <a name="net-application-architecture"></a>Architecture de l’application .NET

[L’architecture de l’application .NET](https://dotnet.microsoft.com/learn/dotnet/architecture-guides) vous donne accès à un ensemble de livres électroniques qui fournissent des instructions, des bonnes pratiques et des exemples d’applications lors de l’utilisation de .NET pour générer :

- [Microservices et conteneurs Docker](../../architecture/microservices/index.md)
- [Applications Web avec ASP.NET](../../architecture/modern-web-apps-azure/index.md)
- [Applications mobiles avec Xamarin](/xamarin/xamarin-forms/enterprise-application-patterns/index)
- [Applications déployées dans le Cloud avec Azure](/azure/architecture/reference-architectures/index)

## <a name="see-also"></a>Voir aussi

- [Nouveautés de ASP.NET Core 2.0](/aspnet/core/aspnetcore-2.0)
