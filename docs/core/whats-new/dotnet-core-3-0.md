---
title: Nouveautés de .NET Core 3.0
description: Découvrez les nouvelles fonctionnalités de .NET Core 3.0.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 01/27/2020
ms.openlocfilehash: be5c26c81480dc2854b849dd7f2b1c46ee3e526a
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989166"
---
# <a name="whats-new-in-net-core-30"></a>Nouveautés de .NET Core 3.0

Cet article décrit ce qui est nouveau dans .NET Core 3.0. Une des principales améliorations est la prise en charge des applications de bureau Windows (Windows uniquement). En utilisant le composant du SDK .NET Core 3.0 Windows Desktop, vous pouvez porter vos applications Windows Forms et Windows Presentation Foundation (WPF). Pour être clair, le composant Windows Desktop est pris en charge et inclus seulement sur Windows. Pour plus d’informations, consultez la section [Bureau Windows](#windows-desktop) plus loin dans cet article.

.NET Core 3.0 prend en charge C# 8.0. Il est fortement recommandé d’utiliser [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou plus récent, [Visual Studio pour Mac 8.3](/visualstudio/mac/install-preview) ou plus récent, ou [Visual Studio Code](https://code.visualstudio.com/) avec la dernière **extension C**.

[Téléchargez et démarez avec .NET Core 3.0](https://aka.ms/netcore3download) dès maintenant sur Windows, macOS ou Linux.

Pour plus d’informations sur la version, voir [l’annonce .NET Core 3.0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).

.NET Core RC1 a été considéré comme la production prête par Microsoft et a été entièrement pris en charge. Si vous utilisez une version de prévisualisation, vous devez passer à la version RTM pour un support continu.

## <a name="language-improvements-c-80"></a>Améliorations linguistiques C 8.0

C 8.0 fait également partie de cette version, qui comprend la fonction [de type de référence annulée,](../../csharp/tutorials/nullable-reference-types.md) les flux [async](../../csharp/tutorials/generate-consume-asynchronous-stream.md), et [plus de modèles](../../csharp/tutorials/pattern-matching.md). Pour plus d’informations sur les fonctionnalités de C# 8.0, consultez [Nouveautés de C# 8.0](../../csharp/whats-new/csharp-8.md).

Des améliorations linguistiques ont été ajoutées pour prendre en charge les caractéristiques suivantes de l’API détaillées ci-dessous :

- [Plages et index](#ranges-and-indices)
- [Flux Async](#async-streams)

## <a name="net-standard-21"></a>.NET Standard 2.1

.NET Core 3.0 implémente **.NET Standard 2.1**. Cependant, le `dotnet new classlib` modèle par défaut génère un projet qui cible toujours **.NET Standard 2.0**. Pour cibler **.NET Standard 2.1**, modifiez votre fichier projet et définissez la propriété `TargetFramework` sur `netstandard2.1` :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

Si vous utilisez Visual Studio, vous avez besoin de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), car Visual Studio 2017 ne prend pas en charge **.NET Standard 2.1** ou **.NET Core 3.0**.

## <a name="compiledeploy"></a>Compile/Déploiement

### <a name="default-executables"></a>Exécutables par défaut

.NET Core construit maintenant [des exécutions dépendantes du temps d’exécution](../deploying/index.md#publish-runtime-dependent) par défaut. Ce comportement est nouveau pour les applications qui utilisent une version .NET Core installée de façon globale. Auparavant, seuls les [déploiements autonomes](../deploying/index.md#publish-self-contained) produisaient un exécutable.

Pendant `dotnet build` `dotnet publish`ou , un exécutable (connu sous le nom **d’appHost**) est créé qui correspond à l’environnement et la plate-forme du SDK que vous utilisez. Vous pouvez obtenir le même résultat avec ces exécutables, comme vous le feriez avec d’autres exécutables natifs comme :

- Vous pouvez double-cliquer sur l’exécutable.
- Vous pouvez lancer l’application directement à partir d’une invite de commandes, par exemple `myapp.exe` sous Windows, et `./myapp` sous Linux et macOS.

### <a name="macos-apphost-and-notarization"></a>macOS appHost et notarisation

*macOS seulement*

En commençant par le .NET Core SDK 3.0 notarié pour macOS, le paramètre pour produire un exécutable par défaut (connu sous le nom d’appHost) est désactivé par défaut. Pour plus d’informations, voir [macOS Catalina Notarization et l’impact sur les téléchargements et les projets .NET Core](../install/macos-notarization-issues.md).

Lorsque le paramètre appHost est activé, .NET Core génère un Mach-O natif exécutable lorsque vous construisez ou publiez. Votre application s’exécute dans le cadre de l’appHost lorsqu’elle est exécutée à partir du code source avec la `dotnet run` commande, ou en commençant le Mach-O exécutable directement.

Sans l’appHost, la seule façon pour un utilisateur de `dotnet <filename.dll>` démarrer une application dépendante du temps [d’exécution](../deploying/index.md#publish-runtime-dependent) est la commande. Un appHost est toujours créé lorsque vous publiez votre application [autonome](../deploying/index.md#publish-self-contained).

Vous pouvez configurer l’appHost au niveau du projet, soit `dotnet` basculer `-p:UseAppHost` l’appHost pour une commande spécifique avec le paramètre :

- Fichier projet

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- Paramètre de ligne de commande

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

Pour plus d’informations sur le `UseAppHost` paramètre, voir [propriétés MSBuild pour Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).

### <a name="single-file-executables"></a>Exécutable monofichier

La commande `dotnet publish` prend en charge l’empaquetage de votre application dans un exécutable monofichier spécifique de la plateforme. L’exécutable est auto-extractible et contient toutes les dépendances (y compris natives) nécessaires à l’exécution de votre application. Lors de la première exécution de l’application, celle-ci est extraite d’un répertoire basé sur le nom de l’application et l’identificateur de la build. Le démarrage est plus rapide quand l’application est réexécutée. L’application n’a pas besoin de s’extraire elle-même une deuxième fois, sauf si une nouvelle version a été utilisée.

Pour publier un exécutable monofichier, définissez `PublishSingleFile` dans votre projet ou sur la ligne de commande avec la commande `dotnet publish` :

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

-ou-

```dotnetcli
dotnet publish -r win10-x64 -p:PublishSingleFile=true
```

Pour plus d’informations sur la publication monofichier, consultez le [document conceptuel sur l’outil de regroupement monofichier](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).

### <a name="assembly-linking"></a>Liaison d’assemblys

Le SDK .NET Core 3.0 est fourni avec un outil qui peut réduire la taille des applications en analysant le langage intermédiaire et en supprimant les assemblys inutilisés.

Les applications autonomes incluent tous les éléments nécessaires pour exécuter votre code, sans nécessiter que .NET soit installé sur la machine hôte. Toutefois, il arrive souvent que l’application nécessite seulement un petit sous-ensemble de l’infrastructure pour fonctionner, et que les autres bibliothèques inutilisées puissent être supprimées.

.NET Core inclut désormais un paramètre qui utilisera l’outil [Éditeur de liens de langage intermédiaire](https://github.com/mono/linker) analyser le langage intermédiaire de votre application. Cet outil détecte le code requis, puis coupe les bibliothèques inutilisées. Cet outil peut réduire considérablement la taille de déploiement de certaines applications.

Pour activer cet outil, ajoutez le paramètre `<PublishTrimmed>` dans votre projet et publiez une application autonome :

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

Par exemple, le nouveau modèle de projet de console de base « hello world » inclus, lors de sa publication, atteint la taille d’environ 70 Mo. Avec `<PublishTrimmed>`, sa taille est réduite à environ 30 Mo.

Il est important de prendre en compte le fait que les applications ou infrastructures (dont ASP.NET Core et WPF) qui utilisent la réflexion ou des fonctionnalités dynamiques associées cesseront souvent de fonctionner après cette troncature. Cette rupture se produit car l’éditeur de liens ne connaît pas ce comportement dynamique et ne peut pas déterminer les types de framework nécessaires pour la réflexion. L’outil d’éditeur de liens de langage intermédiaire peut être configuré pour être conscient de ce scénario.

Avant toute chose, veillez à tester votre application après réduction.

Pour plus d’informations sur l’outil d’éditeur de liens de langage intermédiaire, consultez la [documentation](https://aka.ms/dotnet-illink) ou visitez le référentiel [mono/linker]( https://github.com/mono/linker).

### <a name="tiered-compilation"></a>Compilation hiérarchisée

La [compilation hiérarchisée](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md) est activée par défaut avec .NET Core 3.0. Cette fonctionnalité permet au temps d’exécution d’utiliser plus adaptativement le compilateur juste-à-temps (JIT) pour obtenir de meilleures performances.

Le principal avantage de la compilation à plusieurs niveaux est de fournir deux façons de jitting méthodes: dans un niveau de qualité inférieure, mais plus rapide ou un niveau de meilleure qualité, mais plus lent. La qualité se réfère à la façon dont la méthode est optimisée. TC contribue à améliorer les performances d’une application au fur et à mesure qu’elle passe par différentes étapes d’exécution, du démarrage à l’état stable. Lorsque la compilation à plusieurs niveaux est désactivée, chaque méthode est compilée d’une manière unique qui est biaisée à des performances à l’état stable sur les performances de démarrage.

Lorsque TC est activé, le comportement suivant s’applique pour la compilation de la méthode lorsqu’une application démarre :

- Si la méthode a un code compilé à l’avance, ou [ReadyToRun](#readytorun-images), le code prégénéré est utilisé.
- Sinon, la méthode est jitted. Typiquement, ces méthodes sont génériques sur les types de valeur.
  - *Quick JIT* produit plus rapidement du code de qualité inférieure (ou moins optimisé). Dans .NET Core 3.0, Quick JIT est activé par défaut pour des méthodes qui ne contiennent pas de boucles et est préférée pendant le démarrage.
  - Le JIT entièrement optimisé produit plus lentement du code de meilleure qualité (ou plus optimisé). Pour les méthodes où quick JIT ne serait pas <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>utilisé (par exemple, si la méthode est attribuée avec ), le JIT entièrement optimisé est utilisé.

Pour les méthodes fréquemment appelées, le compilateur juste-à-temps crée finalement le code entièrement optimisé en arrière-plan. Le code optimisé remplace ensuite le code pré-compilé pour cette méthode.

Le code généré par Quick JIT peut fonctionner plus lentement, allouer plus de mémoire ou utiliser plus d’espace de pile. S’il y a des problèmes, vous pouvez désactivé Quick JIT en utilisant cette propriété MSBuild dans le fichier du projet :

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

Pour désactiver complètement TC, utilisez cette propriété MSBuild dans votre dossier de projet :

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

> [!TIP]
> Si vous modifiez ces paramètres dans le fichier de projet, vous devrez peut-être `obj` `bin` effectuer une version propre pour que les nouveaux paramètres soient réfléchis (supprimer les répertoires et reconstruire).

Pour plus d’informations sur la compilation configurante à l’heure de l’exécution, voir [options de configuration Run-time pour la compilation](../run-time-config/compilation.md).

### <a name="readytorun-images"></a>Images ReadyToRun

Vous pouvez améliorer le temps de démarrage de votre application .NET Core en compilant les assemblys de votre application au format ReadyToRun (R2R). R2R est une forme de compilation ahead-of-time (AOT).

Les fichiers binaires R2R améliorent les performances de démarrage en réduisant la quantité de travail que le compilateur juste-à-temps (JIT) doit faire lorsque votre application est chargée. Les fichiers binaires contiennent du code natif similaire à ce que la compilation JIT produirait. Cependant, les fichiers binaires R2R sont plus grands, car ils contiennent à la fois le code du langage intermédiaire (IL), qui est toujours nécessaire pour certains scénarios, et la version native du même code. R2R est disponible seulement quand vous publiez une application autonome qui cible des environnements d’exécution spécifiques (RID), comme Linux x64 ou Windows x64.

Pour compiler votre projet en ReadyToRun, procédez comme suit :

01. Ajoutez `<PublishReadyToRun>` le paramètre à votre projet :

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. Publiez une application autonome. Par exemple, cette commande crée une application autonome pour la version 64 bits de Windows :

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a>Restrictions d’architecture/de multiplateforme

Le compilateur ReadyToRun ne prend actuellement pas en charge le ciblage croisé. Vous devez compiler sur une cible donnée. Par exemple, si vous souhaitez avoir des images R2R Windows x64, vous devez exécuter la commande de publication sur cet environnement.

Exceptions au ciblage croisé :

- Windows x64 peut être utilisé pour compiler des images Windows ARM32, ARM64 et x86.
- Windows x86 peut être utilisé pour compiler des images Windows ARM32.
- Linux x64 peut être utilisé pour compiler des images Linux ARM32 et ARM64.

## <a name="runtimesdk"></a>Runtime/SDK

### <a name="major-version-runtime-roll-forward"></a>Rouleau de temps d’exécution de version majeure vers l’avant

.NET Core 3.0 introduit une fonctionnalité que vous pouvez choisir d’utiliser et qui permet de restaurer par progression votre application vers la dernière version majeure de .NET Core. En outre, un nouveau paramètre a été ajouté pour contrôler la façon dont la restauration par progression est appliquée à votre application. Ce paramètre peut être configuré des façons suivantes :

- Propriété du fichier projet : `RollForward`
- Propriété de fichier de configuration de temps d’exécution :`rollForward`
- Variable d’environnement : `DOTNET_ROLL_FORWARD`
- Argument de ligne de commande : `--roll-forward`

L’une des valeurs suivantes doit être spécifiée. Si le paramètre est omis, **Minor** est la valeur par défaut.

- **DernièrePatch**\
Restauration par progression vers la version de correctif la plus élevée. Cette valeur désactive la restauration par progression d’une version mineure.
- **Mineur**\
Restauration par progression vers la version mineure supérieure la plus basse, si la version mineure demandée est manquante. Si la version mineure demandée est présente, la stratégie **LatestPatch** est utilisée.
- **Majeur**\
Restauration par progression vers la version majeure supérieure la plus basse, et la version mineure la plus basse, si la version majeure demandée est manquante. Si la version majeure demandée est présente, la stratégie **Minor** est utilisée.
- **DernièresMinor**\
Restauration par progression vers la version mineure la plus élevée, si la version mineure demandée est présente. Conçu pour les scénarios d’hébergement de composant.
- **DernièresMajor**\
Restauration par progression vers la version majeure la plus élevée et la version mineure la plus élevée, si la version majeure demandée est présente. Conçu pour les scénarios d’hébergement de composant.
- **Désactiver**\
Ne pas effectuer de restauration par progression. Lier uniquement à la version spécifiée. Cette stratégie n’est pas recommandée pour une utilisation générale, car elle désactive la possibilité d’effectuer une restauration par progression vers les derniers correctifs. Cette valeur est recommandée uniquement à des fins de test.

Outre le paramètre **Disable**, tous les paramètres utilisent la version de correctif disponible la plus élevée.

### <a name="build-copies-dependencies"></a>Dépendances de copies de build

La commande `dotnet build` copie maintenant les dépendances NuGet pour votre application à partir du cache NuGet vers le dossier de sortie de build. Auparavant, les dépendances étaient copiées uniquement dans le cadre de `dotnet publish`.

Certaines opérations, par exemple la liaison et la publication d’une page de type Razor, nécessiteront toujours une publication.

### <a name="local-tools"></a>Outils locaux

.NET Core 3.0 introduit des outils locaux. Les outils locaux sont similaires aux [outils globaux,](../tools/global-tools.md) mais sont associés à un emplacement particulier sur le disque. Les outils locaux ne sont pas disponibles globalement et sont distribués en tant que packages NuGet.

> [!WARNING]
> Si vous avez essayé des outils locaux dans .NET Core 3.0 Preview 1, par exemple pour exécuter `dotnet tool restore` ou `dotnet tool install`, supprimez le dossier de cache des outils locaux. Sinon, les outils locaux ne fonctionneront sur aucune nouvelle version. Ce dossier se trouve à ces emplacements :
>
> Sur macOS, Linux : `rm -r $HOME/.dotnet/toolResolverCache`
>
> Sur Windows : `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`

Les outils locaux s’appuient sur un nom de fichier manifeste `dotnet-tools.json` dans votre répertoire actuel. Ce fichier manifeste définit les outils qui doivent être disponibles dans ce dossier et sous-celui-ci. Vous pouvez distribuer le fichier manifeste avec votre code pour que toute personne qui utilise votre code puisse restaurer et utiliser les mêmes outils.

Pour les outils locaux et globaux, une version compatible du runtime est requise. De nombreux outils actuellement sur NuGet.org ciblent le runtime .NET Core 2.1. Pour installer ces outils de façon locale ou globale, vous devez toujours installer le [runtime NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

### <a name="new-globaljson-options"></a>Nouvelles options global.json

Le fichier *global.json* a de nouvelles options qui offrent plus de flexibilité lorsque vous essayez de définir quelle version de la SDK Core .NET est utilisé. Les nouvelles options sont les suivantes :

- `allowPrerelease`: Indique si le résolveur SDK doit tenir compte des versions préreléase lors de la sélection de la version SDK à utiliser.
- `rollForward`: Indique la stratégie de déploiement à utiliser lors de la sélection d’une version SDK, soit comme un repli lorsqu’une version spécifique SDK est manquante ou comme une directive pour utiliser une version supérieure.

Pour plus d’informations sur les changements, y compris les valeurs par défaut, les valeurs prises en charge, et de nouvelles règles de correspondance, voir [global.json aperçu](../tools/global-json.md).

### <a name="smaller-garbage-collection-heap-sizes"></a>Tailles de tas de garbage collection plus petites

La taille de tas par défaut du récupérateur de mémoire a été réduite, aboutissant à une diminution de la quantité de mémoire utilisée par .NET Core. Ce changement est plus conforme au budget d’allocation de génération 0 avec les tailles des caches des processeurs modernes.

### <a name="garbage-collection-large-page-support"></a>Prise en charge de grandes pages du garbage collection

Les grandes pages (également appelées HugePages sur Linux) sont une fonctionnalité qui permet au système d’exploitation d’établir des régions de mémoire plus grandes que la taille de page native (souvent 4 Ko) pour améliorer les performances de l’application qui demande ces grandes pages.

Vous pouvez maintenant configurer le récupérateur de mémoire avec la définition **GCLargePages** en tant que fonctionnalité que vous pouvez choisir d’utiliser et qui permet d’allouer de grandes pages sur Windows.

## <a name="windows-desktop--com"></a>Windows Desktop & COM

### <a name="net-core-sdk-windows-installer"></a>Windows Installer pour le kit SDK .NET Core

Le programme d’installation MSI pour Windows a changé à compter de .NET Core 3.0. Les programmes d’installation du SDK mettent désormais à niveau les versions des plages de fonctionnalités du SDK. Les plages de fonctionnalités sont définies dans les groupes *hundreds* de la section *patch* du numéro de version. Par exemple, **3.0._101_** et **3.0._201_** sont des versions dans deux plages de fonctionnalités différentes, tandis que **3.0._101_** et **3.0._199_** se trouvent dans la même plages de fonctionnalités. En outre, quand le SDK .NET Core **3.0._101_** est installé, le SDK .NET Core **3.0._100_** est supprimé de la machine s’il existe. Quand le SDK .NET Core **3.0._200_** est installé sur la même machine, le SDK .NET Core **3.0._101_** n’est pas supprimé.

Pour plus d’informations sur la gestion des versions, consultez [Vue d’ensemble de la gestion des versions .NET Core](../versions/index.md).

### <a name="windows-desktop"></a>Ordinateurs Windows

.NET Core 3.0 prend en charge les applications de bureau Windows utilisant Windows Presentation Foundation (WPF) et Windows Forms. Ces infrastructures prennent également en charge l’utilisation de contrôles modernes et le style Fluent à partir de la bibliothèque XAML de l’interface utilisateur Windows (WinUI) via des [îles XAML](/windows/uwp/xaml-platform/xaml-host-controls).

Le composant Bureau Windows fait partie du SDK .NET Core 3.0 Windows.

Vous pouvez créer une nouvelle application WPF ou Windows Forms à l’aide des commandes `dotnet` suivantes :

```dotnetcli
dotnet new wpf
dotnet new winforms
```

Visual Studio 2019 ajoute des modèles **Nouveau projet** pour Windows Forms et WPF .NET Core 3.0.

Pour plus d’informations sur la façon de porter une application .NET Framework existante, consultez [Porter des projets WPF](../../desktop-wpf/migration/convert-project-from-net-framework.md) et [Porter des projets Windows Forms](../porting/winforms.md).

#### <a name="winforms-high-dpi"></a>Haute résolution WinForms

Les applications Windows Forms .NET Core peuvent définir le mode de haute résolution avec <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>. La méthode `SetHighDpiMode` définit le mode de haute résolution correspondant, sauf si le paramètre a été défini par d’autres moyens, comme `App.Manifest` ou P/Invoke avant `Application.Run`.

Les valeurs `highDpiMode` possibles, telles qu’exprimées par l’enum <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType>, sont les suivantes :

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

Pour plus d’informations sur les modes de haute résolution, consultez [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) (Développement d’applications de bureau haute résolution sur Windows).

### <a name="create-com-components"></a>Créer des composants COM

Sur Windows, vous pouvez maintenant créer des composants gérés appelables par COM. Cette fonctionnalité est essentielle pour utiliser .NET Core avec les modèles de compléments COM et également pour assurer la parité avec .NET Framework.

Contrairement à .NET Framework, où *mscoree.dll* était utilisé comme serveur COM, .NET Core ajoute une dll de lanceur natif au répertoire *bin* quand vous générez votre composant COM.

Pour obtenir un exemple montrant comment créer un composant COM et le consommer, consultez la [démonstration COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).

### <a name="windows-native-interop"></a>Interopérabilité native Windows

Windows offre une API native riche sous la forme d’API C plates, de COM et de WinRT. Tandis que .NET Core prend en charge **P/Invoke**, .NET Core 3.0 ajoute la possibilité de **cocréer des API COM** et d’**activer des API WinRT**. Pour obtenir un exemple de code, consultez la [démonstration Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).

### <a name="msix-deployment"></a>Déploiement MSIX

[MSIX](https://docs.microsoft.com/windows/msix/) est un nouveau format de package d’application Windows. Il peut être utilisé pour déployer des applications de poste de travail .NET Core 3.0 pour Windows 10.

Le [projet de package d’application Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), disponible dans Visual Studio 2019, vous permet de créer des packages MSIX avec des applications .NET Core [autonomes](../deploying/index.md#publish-self-contained).

Le fichier projet .NET Core doit spécifier les runtimes pris en charge dans la propriété `<RuntimeIdentifiers>` :

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a>Améliorations Linux

### <a name="serialport-for-linux"></a>SerialPort pour Linux

.NET Core 3.0 offre une prise en charge de base de <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> sur Linux.

Auparavant, .NET Core était uniquement pris en charge au moyen de `SerialPort` sur Windows.

Pour plus d’informations sur la prise en charge limitée du port série sur Linux, consultez [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).

### <a name="docker-and-cgroup-memory-limits"></a>Docker et limites de mémoire cgroup

Exécution .NET Core 3.0 sur Linux avec Docker fonctionne mieux avec des limites de mémoire de groupe. L’exécution d’un conteneur Docker avec des limites de mémoire, par exemple avec `docker run -m`, change le comportement de .NET Core.

- Taille de tas par défaut du récupérateur de mémoire (GC) : au maximum 20 Mo ou 75 % de la limite de mémoire sur le conteneur.
- Une taille explicite peut être définie sous forme de nombre absolu ou de pourcentage de la limite cgroup.
- La taille de segment réservée minimale par tas GC est de 16 Mo. Cette taille réduit le nombre de segments de mémoire qui sont créés sur les machines.

### <a name="gpio-support-for-raspberry-pi"></a>Prise en charge de GPIO pour Raspberry Pi

Deux packages ont été publiés sur NuGet, que vous pouvez utiliser pour la programmation de GPIO :

- [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio)
- [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings)

Les packages GPIO incluent des API pour les appareils *GPIO*, *SPI*, *I2C* et *PWM*. Le package de liaisons IoT comprend des liaisons d’appareil. Pour plus d’informations, consultez le [dépôt GitHub devices](https://github.com/dotnet/iot/blob/master/src/devices/).

### <a name="arm64-linux-support"></a>Support ARM64 Linux

.NET Core 3.0 prend en charge ARM64 pour Linux. Actuellement, ARM64 est principallement utilisé dans des scénarios IoT. Pour plus d’informations, consultez [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).

Des [images Docker pour .NET Core sur ARM64](https://hub.docker.com/r/microsoft/dotnet/) sont disponibles pour Alpine, Debian et Ubuntu.

> [!NOTE]
> La prise en charge d’**ARM64** sous Windows n’est pas encore disponible.

## <a name="security"></a>Sécurité

### <a name="tls-13--openssl-111-on-linux"></a>TLS 1.3 et OpenSSL 1.1.1 sous Linux

.NET Core tire désormais parti de la [prise en charge de TLS 1.3 dans OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), si disponible dans un environnement donné. Avec TLS 1.3 :

- Les délais de connexion sont améliorés grâce à une réduction des allers-retours requis entre le client et le serveur.
- La sécurité est améliorée en raison de la suppression de différents algorithmes de chiffrement obsolètes et non sécurisés.

.NET Core 3.0 utilise **OpenSSL 1.1.1**, **OpenSSL 1.1.0** ou **OpenSSL 1.0.2** sur un système Linux s’ils sont disponibles. Quand **OpenSSL 1.1.1** est disponible, les types <xref:System.Net.Security.SslStream?displayProperty=nameWithType> et <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> utilisent **TLS 1.3** (sous réserve que le client et le serveur prennent en charge **TLS 1.3**).

> [!IMPORTANT]
> Windows et macOS ne prennent pas encore en charge **TLS 1.3**. .NET Core 3.0 prendra en charge **TLS 1.3** sur ces systèmes d’exploitation dès que de la prise en charge sera disponible.

L’exemple C# 8.0 suivant montre comment .NET Core 3.0 sur Ubuntu 18.10 se connecte à <https://www.cloudflare.com> :

[!code-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a>Chiffrements

.NET 3.0 prend en charge les chiffrements **AES-GCM** et **AES-CCM**, implémentés avec <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> et <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectivement. Ces algorithmes sont tous deux des [algorithmes AEAD (Authenticated Encryption with Association Data)](https://en.wikipedia.org/wiki/Authenticated_encryption).

Le code suivant montre l’utilisation du chiffrement `AesGcm` pour chiffrer et déchiffrer des données aléatoires.

[!code-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a>Importation/exportation d’une clé de chiffrement

.NET Core 3.0 prend en charge l’importation et l’exportation de clés publiques et privées asymétriques aux formats standard. Vous n’avez pas besoin d’utiliser un certificat X.509.

Tous les types de clés, tels que *RSA*, *DSA*, *ECDsa* et *ECDiffieHellman*, prennent en charge les formats suivants :

- **Clé publique**
  - X.509 SubjectPublicKeyInfo

- **Private key**
  - PKCS#8 PrivateKeyInfo
  - PKCS#8 EncryptedPrivateKeyInfo

Les clés RSA prennent également en charge :

- **Clé publique**
  - PKCS#1 RSAPublicKey

- **Private key**
  - PKCS#1 RSAPrivateKey

Les méthodes d’exportation produisent des données binaires encodées au format DER, tout comme les méthodes d’importation. Si une clé est stockée au format PEM compatible avec le texte, l’appelant devra décoder le contenu au format base64 avant d’appeler une méthode d’importation.

[!code-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

Les fichiers **PKCS#8** peuvent être inspectés avec <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType>, tandis que les fichiers **PFX/PKCS#12** peuvent être inspectés avec <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>. Les fichiers **PFX/PKCS#12** peuvent être manipulés avec <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.

## <a name="net-core-30-api-changes"></a>.NET Core 3.0 Modifications de l’API

### <a name="ranges-and-indices"></a>Plages et index

Le nouveau type <xref:System.Index?displayProperty=nameWithType> peut être utilisé pour l’indexation. Vous pouvez en créer un à partir d’un `int` qui compte à partir du début, ou avec un opérateur (C#) `^` préfixé qui compte à partir de la fin :

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Il existe également le type <xref:System.Range?displayProperty=nameWithType>, composé de deux valeurs `Index`, une pour le début et une pour la fin, et qui peut être écrit avec une expression de plage (C#) `x..y`. Vous pouvez indexer ensuite avec un `Range`, ce qui génère une tranche :

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

Pour plus d’informations, consultez le [tutoriel sur les plages et les index](../../csharp/tutorials/ranges-indexes.md).

### <a name="async-streams"></a>Flux asynchrones

Le type <xref:System.Collections.Generic.IAsyncEnumerable%601> est une nouvelle version asynchrone de <xref:System.Collections.Generic.IEnumerable%601>. Le langage vous permet d’utiliser `await foreach` sur `IAsyncEnumerable<T>` pour consommer ses éléments, et `yield return` sur ceux-ci pour produire des éléments.

L’exemple suivant montre la production et la consommation de flux de données asynchrones. L’instruction `foreach` est asynchrone et utilise elle-même `yield return` afin de produire un flux asynchrone pour les appelants. Ce modèle (qui utilise `yield return`) est le modèle recommandé pour produire des flux de données asynchrones.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

Outre la possibilité d’effectuer une opération `await foreach`, vous pouvez également créer des itérateurs asynchrones, par exemple un itérateur qui retourne un objet `IAsyncEnumerable/IAsyncEnumerator` auquel vous pouvez à la fois appliquer des opérations `await` et `yield`. Pour les objets qui doivent être supprimés, vous pouvez utiliser `IAsyncDisposable`, qui implémentent différents types BCL, notamment `Stream` et `Timer`.

Pour plus d’informations, consultez le [tutoriel sur les flux asynchrones](../../csharp/tutorials/generate-consume-asynchronous-stream.md).

### <a name="ieee-floating-point"></a>IEEE Point flottant

Les API de virgule flottante sont en cours de mise à jour pour devenir conformes à la [révision 754-2008 d’IEEE](https://en.wikipedia.org/wiki/IEEE_754-2008_revision). L’objectif de ces changements est d’exposer toutes les opérations **requises** et de s’assurer qu’ils sont conformes au comportement avec les spécifications de l’IEEE. Pour plus d’informations sur les améliorations des points flottants, voir les améliorations de parsing et de formatage de point flottant dans le billet de blog [.NET Core 3.0.](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)

Les correctifs de l’analyse et de la mise en forme comprennent :

- Analyse et arrondi corrects des entrées, quelle que soit leur longueur.
- Analyse et mise en forme correctes des zéros négatifs.
- Analyse correcte de `Infinity` et `NaN` en effectuant une vérification sans tenir compte de la casse et en autorisant un signe `+` facultatif de début là où c’est applicable.

Les nouvelles API <xref:System.Math?displayProperty=nameWithType> incluent :

- <xref:System.Math.BitIncrement(System.Double)> et <xref:System.Math.BitDecrement(System.Double)>\
Correspond aux opérations IEEE `nextUp` et `nextDown`. Elles retournent le plus petit nombre à virgule flottante dont la valeur est supérieure ou inférieure à l’entrée (respectivement). Par exemple, `Math.BitIncrement(0.0)` retourne `double.Epsilon`.

- <xref:System.Math.MaxMagnitude(System.Double,System.Double)> et <xref:System.Math.MinMagnitude(System.Double,System.Double)>\
Correspond aux opérations IEEE `maxNumMag` et `minNumMag`. Elles retournent la valeur la plus grande ou la plus petite des deux entrées (respectivement). Par exemple, `Math.MaxMagnitude(2.0, -3.0)` retourne `-3.0`.

- <xref:System.Math.ILogB(System.Double)>\
Correspond à l’opération IEEE `logB` qui retourne une valeur intégrale ; elle retourne le logarithme de base 2 intégral du paramètre d’entrée. Cette méthode est identique à `floor(log2(x))`, mais effectuée avec une erreur d’arrondi minimale.

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
Correspond à l’opération IEEE `scaleB` qui prend une valeur intégrale ; elle retourne `x * pow(2, n)`, mais est effectuée avec une erreur d’arrondi minimale.

- <xref:System.Math.Log2(System.Double)>\
Correspond à l’opération IEEE `log2` ; elle retourne le logarithme de base 2. Son erreur d’arrondi est minimale.

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
Correspond à l’opération IEEE `fma` ; elle effectue une multiplication-addition fusionnée. Elle effectue `(x * y) + z` comme une seule opération, avec une erreur d’arrondi minimale. Un exemple `FusedMultiplyAdd(1e308, 2.0, -1e308)`est `1e308`, qui revient . L’opération régulière `(1e308 * 2.0) - 1e308` retourne `double.PositiveInfinity`.

- <xref:System.Math.CopySign(System.Double,System.Double)>\
Correspond à l’opération IEEE `copySign` ; elle retourne la valeur de `x`, mais avec le signe de `y`.

### <a name="net-platform-dependent-intrinsics"></a>Intrinsèques dépendant de la plateforme .NET

Des API ont été ajoutées, qui permettent d’accéder à certaines instructions de l’UC orientées performances, comme les ensembles **SIMD** ou les ensembles d’**instructions de manipulation de bits**. Ces instructions peuvent améliorer les performances dans certains scénarios de matière significative, comme le traitement efficace de données en parallèle.

Le cas échéant, les bibliothèques .NET ont commencé à utiliser ces instructions pour améliorer les performances.

Pour plus d’informations, voir [.NET Plateforme-Dépendant Intrinsèques](https://github.com/dotnet/designs/blob/master/accepted/2018/platform-intrinsics.md).

### <a name="improved-net-core-version-apis"></a>API de version de .NET Core améliorées

À compter de .NET Core 3.0, les API de version fournies avec .NET Core retournent les informations souhaitées. Par exemple :

```csharp
System.Console.WriteLine($"Environment.Version: {System.Environment.Version}");

// Old result
//   Environment.Version: 4.0.30319.42000
//
// New result
//   Environment.Version: 3.0.0
```

```csharp
System.Console.WriteLine($"RuntimeInformation.FrameworkDescription: {System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription}");

// Old result
//   RuntimeInformation.FrameworkDescription: .NET Core 4.6.27415.71
//
// New result (notice the value includes any preview release information)
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> Modification avec rupture. Il s’agit techniquement d’une modification avec rupture, car le schéma de gestion de version a changé.

### <a name="fast-built-in-json-support"></a>Prise en charge JSON intégrée rapide

.NET utilisateurs ont largement compté sur [Newtonsoft.Json](https://www.newtonsoft.com/json) et d’autres bibliothèques JSON populaires, qui continuent d’être de bons choix. `Newtonsoft.Json`utilise des chaînes .NET comme son datatype de base, qui est UTF-16 sous le capot.

Le nouveau support JSON intégré est haute performance, faible allocation, et fonctionne avec UTF-8 encodé texte JSON. Pour plus d’informations sur l’espace nom et les <xref:System.Text.Json> types, voir les articles suivants:

* [JSON sérialisation en .NET - aperçu](../../standard/serialization/system-text-json-overview.md)
* [Comment sérialiser et déséialiser JSON en .NET](../../standard/serialization/system-text-json-how-to.md).
* [Comment migrer de Newtonsoft.Json à System.Text.Json](../../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md)

### <a name="http2-support"></a>Assistance HTTP/2

Le type <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> prend en charge le protocole HTTP/2. Si HTTP/2 est activé, la version du protocole HTTP est négociée par le biais de TLS/ALPN, et HTTP/2 n’est utilisée que si le serveur le choisit.

Le protocole par défaut reste HTTP/1.1, mais HTTP/2 peut être activé de deux manières différentes. Tout d’abord, vous pouvez définir le message de requête HTTP de sorte à utiliser HTTP/2 :

[!code-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

Ensuite, vous pouvez modifier <xref:System.Net.Http.HttpClient> pour utiliser HTTP/2 par défaut :

[!code-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

Souvent, lorsque vous développez une application, vous souhaiterez utiliser une connexion non chiffrée. Si vous savez que le point de terminaison cible utilisera HTTP/2, vous pouvez activer les connexions non chiffrées pour HTTP/2. Vous pouvez activer cela en définissant la variable d’environnement `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` sur `1` ou en l’activant dans le contexte de l’application :

[!code-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="next-steps"></a>Étapes suivantes

- [Passez en revue les changements de rupture entre .NET Core 2.2 et 3.0.](../compatibility/2.2-3.0.md)
- [Passez en revue les changements de rupture dans .NET Core 3.0 pour les applications Windows Forms.](../compatibility/winforms.md#net-core-30)
