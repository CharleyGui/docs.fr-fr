---
title: Générer .NET Core à partir de la source
description: Découvrez comment générer .NET Core et le .NET Core CLI à partir du code source.
author: bleroy
ms.date: 06/28/2017
ms.custom: seodec18
ms.openlocfilehash: dcd7c909325eec5a79db74098d7ac880000eafa1
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105385"
---
# <a name="build-net-core-from-source"></a>Générer .NET Core à partir de la source

La capacité de générer .NET Core à partir de son code source est importante à plusieurs titres : elle facilite le portage de .NET Core vers de nouvelles plateformes, elle permet les contributions et les correctifs pour le produit, et elle permet la création de versions personnalisées de .NET.
Cet article fournit de l’aide aux développeurs qui veulent créer et distribuer leurs propres versions de .NET Core.

## <a name="build-the-clr-from-source"></a>Générer le CLR à partir de la source

Vous trouverez le code source de .NET CoreCLR dans le référentiel [dotnet/coreclr](https://github.com/dotnet/coreclr/) sur GitHub.

La génération dépend actuellement des prérequis suivants :

- [Git](https://git-scm.com/)
- [CMake](https://cmake.org/)
- [Python](https://www.python.org/)
- Un compilateur C++.

Une fois ces composants requis installés, vous pouvez générer le CLR en appelant le script de génération (`build.cmd` sur Windows ou `build.sh` sur Linux et macOS) à la base du dépôt [dotnet/coreclr](https://github.com/dotnet/coreclr/).

L’installation des composants diffère selon le système d’exploitation. Consultez les instructions de génération pour votre système d’exploitation spécifique :

- [Fenêtres](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
- [Linux](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
- [macOS](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
- [FreeBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
- [NetBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

La génération croisée entre systèmes d’exploitation n’est pas possible (sauf pour ARM, qui est basé sur X64).  
Vous devez être sur la plateforme spécifique pour générer cette plateforme.  

La build a deux `buildTypes` principaux :

- Debug (par défaut) : compile le runtime avec des optimisations minimales et des vérifications (assertions) supplémentaires à l’exécution. Cette réduction du niveau d’optimisation et les vérifications supplémentaires ralentissent l’exécution du runtime, mais sont utiles pour le débogage. Il s’agit du paramètre recommandé pour les environnements de développement et de test.
- Release : compile le runtime avec des optimisations complètes et sans les vérifications supplémentaires à l’exécution. Vous obtenez des performances d’exécution plus rapides, mais la génération peut prendre plus de temps et être difficile à déboguer. Passez `release` au script de compilation pour sélectionner ce type de build.

Par défaut, la génération crée non seulement les exécutables du runtime, mais elle produit également tous les tests.
Il existe un bon nombre de tests qui prennent un temps considérable alors qu’ils ne sont pas nécessaires si vous voulez faire des essais avec des modifications.
Vous pouvez ignorer les builds de tests en ajoutant l’argument `skiptests` au script de génération, comme dans l’exemple suivant (remplacez `.\build` par `./build.sh` sur les machines Unix) :

```bat
    .\build skiptests
```

L’exemple précédent a montré comment générer la version `Debug`, avec les vérifications (assertions) au moment du développement activées et les optimisations désactivées. Pour générer la version Release (celle qui s’exécute à pleine vitesse), procédez comme suit :

```bat
    .\build release skiptests
```

Vous trouverez plus d’options de génération de la build en utilisant le qualificateur -? ou - help.

### <a name="using-your-build"></a>Utilisation de votre build

La build place tous les fichiers générés sous le répertoire `bin` à la base du dépôt.
Il existe un répertoire *bin\Log* qui contient les fichiers journaux générés pendant la génération (utiles principalement en cas d’échec de la build).
Le résultat est placé dans un répertoire *bin\Product\[plateforme].[Architecture d’UC].[type de build]* , comme *bin\Product\Windows_NT.x64.Release*.

Si la sortie « brute » de la build est parfois utile, vous n’êtes normalement intéressé que par les packages NuGet, qui sont placés dans le sous-répertoire `.nuget\pkg` du répertoire de sortie précédent.

Vous pouvez utiliser votre nouveau runtime selon deux techniques de base :

 1. **Utiliser dotnet.exe et NuGet pour composer une application**.
    Consultez [Utilisation de votre build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) pour obtenir des instructions sur la création d’un programme qui utilise votre nouveau runtime avec les packages NuGet que vous venez de créer et l’interface de ligne de commande (CLI) « dotnet ». Cette technique est celle que les développeurs « non-runtime » vont probablement utiliser pour consommer votre nouveau runtime.

 2. **Utiliser corerun.exe pour exécuter une application avec des DLL non packagées**.
    Ce dépôt définit également un hôte simple appelé corerun.exe, qui n’accepte AUCUNE dépendance de NuGet.
    Vous devez indiquer à l’hôte où obtenir les DLL nécessaires que vous utilisez, puis vous devez les rassembler manuellement.
    Cette technique, utilisée par tous les tests du référentiel [dotnet/coreclr](https://github.com/dotnet/coreclr), est utile pour la boucle locale rapide « Édition-Compilation-Débogage », comme les tests unitaires préliminaires.
    Pour plus d’informations sur l’utilisation de cette technique, consultez [Exécution d’applications .NET Core avec CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md).

## <a name="build-the-cli-from-source"></a>Générer l’interface CLI à partir de la source

Vous trouverez le code source de l’interface CLI .NET Core dans le référentiel [dotnet/cli](https://github.com/dotnet/cli/) sur GitHub.

Pour générer l’interface CLI de .NET Core, les éléments suivants doivent être installés sur votre ordinateur.

- Windows et Linux :
  - git sur la variable PATH
- macOS :
  - git sur la variable PATH
  - Xcode
  - Openssl

Pour générer, exécutez `build.cmd` sur Windows, ou `build.sh` sur Linux et macOS à partir de la racine. Si vous ne voulez pas exécuter les tests, exécutez `build.cmd -t:Compile` ou `./build.sh -t:Compile`. Pour générer l’interface CLI dans macOS Sierra, vous devez définir la variable d’environnement DOTNET_RUNTIME_ID en exécutant `export DOTNET_RUNTIME_ID=osx.10.11-x64`.

### <a name="using-your-build"></a>Utilisation de votre build

Utilisez l’exécutable `dotnet` à partir de *artifacts/{os}-{arch}/stage2* pour essayer l’interface CLI nouvellement générée. Si vous voulez utiliser la sortie de la génération lors de l’appel de `dotnet` à partir de la console active, vous pouvez également ajouter *artifacts/{os}-{arch}/stage2* à la variable PATH.

## <a name="see-also"></a>Voir aussi

- [Common Language Runtime .NET Core (CoreCLR)](https://github.com/dotnet/coreclr/blob/master/README.md)
- [Guide du développeur de l’interface CLI .NET Core](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
- [Empaquetage de la distribution de .NET Core](./distribution-packaging.md)
