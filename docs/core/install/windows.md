---
title: Installer .NET Core sur Windows
description: Découvrez les versions de Windows sur lesquelles vous pouvez installer .NET Core.
author: adegeo
ms.author: adegeo
ms.date: 06/22/2020
ms.openlocfilehash: e26494de7e9246b241cb965d8d735a781aab5478
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85804494"
---
# <a name="install-net-core-on-windows"></a>Installer .NET Core sur Windows

> [!div class="op_single_selector"]
>
> - [Installer sur Windows](windows.md)
> - [Installer sur macOS](macos.md)
> - [Installer sur Linux](linux.md)

Dans cet article, vous allez apprendre à installer .NET Core sur Windows. .NET Core est constitué du runtime et du kit de développement logiciel (SDK). Le runtime est utilisé pour exécuter une application .NET Core et peut ou ne peut pas être inclus avec l’application. Le kit de développement logiciel (SDK) est utilisé pour créer des applications et des bibliothèques .NET Core. Le Runtime .NET Core est toujours installé avec le kit de développement logiciel (SDK).

La dernière version de .NET Core est 3,1.

[Téléchargez .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a>Versions prises en charge

Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge et les versions de Windows sur lesquelles elles sont prises en charge. Ces versions restent prises en charge jusqu’à la fin de la [prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net Core ou de la version de [Windows](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

Les dates de fin de service des versions de Windows 10 sont segmentées par édition. Seules les éditions **familiales**, **Pro**, **Pro Education**et **Pro for Workstations** sont étudiées dans le tableau suivant. Consultez la [feuille de faits du cycle de vie Windows](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) pour obtenir des détails spécifiques.

- Une ✔️ indique que la version de Windows ou de .NET Core est toujours prise en charge.
- Une ❌ indique que la version de Windows ou de .net Core n’est pas prise en charge sur cette version de Windows.
- Quand une version de Windows et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.

| Système d'exploitation                      | .NET Core 2.1 | .NET Core 3.1 | Version préliminaire de .NET 5 |
|-----------------------------|---------------|---------------|----------------|
| ✔️ Windows 10, version 2004 | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ✔️ Windows 10, version 1909 | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ✔️ Windows 10, version 1903 | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ✔️ Windows 10, version 1809 | ✔️ 2,1        | ✔️ 3,1        | ✔️ version préliminaire 5,0 |
| ❌Windows 10, version 1803 | ✔️ 2,1        | ❌3,1        | ❌version préliminaire 5,0 |
| ❌Windows 10, version 1709 | ❌2,1        | ❌3,1        | ❌version préliminaire 5,0 |
| ❌Windows 10, version 1703 | ❌2,1        | ❌3,1        | ❌version préliminaire 5,0 |
| ❌Windows 10, version 1607 | ❌2,1        | ❌3,1        | ❌version préliminaire 5,0 |
| ❌Windows 10, version 1511 | ❌2,1        | ❌3,1        | ❌version préliminaire 5,0 |
| ❌Windows 10, version 1507 | ❌2,1        | ❌3,1        | ❌version préliminaire 5,0 |

## <a name="unsupported-releases"></a>Mises en production non prises en charge

Les versions suivantes de .NET Core ne sont ❌ plus prises en charge. Les téléchargements sont toujours publiés :

- 3.0
- 2.2
- 2.0

## <a name="runtime-information"></a>Informations d’exécution

Le runtime est utilisé pour exécuter des applications créées avec .NET Core. Quand un auteur d’application publie une application, il peut inclure le Runtime avec son application. Si elles n’incluent pas le runtime, c’est à l’utilisateur d’installer le Runtime.

Il existe trois runtimes différents que vous pouvez installer sur Windows :

*Runtime ASP.NET Core*\
Exécute ASP.NET Core applications. Comprend le Runtime .NET Core.

*Runtime Desktop*\
Exécute les applications de bureau .NET Core WPF et .NET Core Windows Forms pour Windows. Comprend le Runtime .NET Core.

*Runtime .NET Core*\
Ce Runtime est le runtime le plus simple et n’inclut pas d’autre Runtime. Il est fortement recommandé d’installer à la fois *ASP.net Core Runtime* et *Desktop Runtime* pour une meilleure compatibilité avec les applications .net core.

[Téléchargez le Runtime .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a>Informations sur le SDK

Le kit de développement logiciel (SDK) est utilisé pour créer et publier des applications et des bibliothèques .NET Core. L’installation du kit de développement logiciel (SDK) comprend les trois [runtimes](#runtime-information): ASP.net Core, Desktop et .net core.

[Téléchargez kit SDK .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a>Les dépendances

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[.NET Core 3.1](#tab/netcore31)

Les versions de Windows suivantes sont prises en charge avec .NET Core 3,1 :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                            | Version                        | Architectures   |
| ----------------------------- | ------------------------------ | --------------- |
| Client Windows                | 8.1                            | x64, x86        |
| Client Windows 10             | Version 1609 +                  | x64, x86        |
| Windows Server                | 2012 R2 +                       | x64, x86        |
| Nano Server                   | Version 1803 +                  | x64, ARM32      |

Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

*.NET Core 3,0 n’est pas pris en charge pour le moment. Pour plus d’informations, consultez la [stratégie de support .net Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

Les versions de Windows suivantes sont prises en charge avec .NET Core 3,0 :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                            | Version                        | Architectures   |
| ----------------------------- | ------------------------------ | --------------- |
| Client Windows                | 7 SP1 +, 8,1                    | x64, x86        |
| Client Windows 10             | Version 1607 +                  | x64, x86        |
| Windows Server                | 2012 R2 +                       | x64, x86        |
| Nano Server                   | Version 1803 +                  | x64, ARM32      |

Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,0 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

*.NET Core 2,2 n’est pas pris en charge pour le moment. Pour plus d’informations, consultez la [stratégie de support .net Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

Les versions de Windows suivantes sont prises en charge avec .NET Core 2,2 :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                            | Version                        | Architectures   |
| ----------------------------- | ------------------------------ | --------------- |
| Client Windows                | 7 SP1 +, 8,1                    | x64, x86        |
| Client Windows 10             | Version 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64, x86        |
| Nano Server                   | Version 1803 +                   | x64, ARM32      |

Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,2 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

Les versions de Windows suivantes sont prises en charge avec .NET Core 2,1 :

> [!NOTE]
> Un `+` symbole représente la version minimale.

| Système d''exploitation                            | Version                        | Architectures   |
| ----------------------------- | ------------------------------ | --------------- |
| Client Windows                | 7 SP1 +, 8,1                    | x64, x86        |
| Client Windows 10             | Version 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64, x86        |
| Nano Server                   | Version 1803 +                  | 64x            |

Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a>Windows 7/Vista/8,1/Server 2008 R2/Server 2012 R2

Des dépendances supplémentaires sont requises si vous installez le kit de développement logiciel (SDK) .NET ou le runtime sur les versions suivantes de Windows :

- ❌Windows 7 SP1
- ❌Windows Vista SP 2
- ✔️ Windows 8.1
- ✔️ Windows Server 2008 R2
- ✔️ Windows Server 2012 R2

Installez les éléments suivants :

- [Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

La configuration requise ci-dessus est également requise si vous rencontrez l’une des erreurs suivantes :

> Le programme ne peut pas démarrer, car *api-ms-win-crt-runtime-l1-1-0.dll* n’est pas présent sur votre ordinateur. Essayez de réinstaller le programme pour résoudre ce problème.
>
> \- ou -
>
> Le programme ne peut pas démarrer, car *api-ms-win-cor-timezone-l1-1-0.dll* n’est pas présent sur votre ordinateur. Essayez de réinstaller le programme pour résoudre ce problème.
>
> \- ou -
>
> La bibliothèque *hostfxr.dll* a été trouvée, mais son chargement à partir de *C : \\ \<path_to_app> \\hostfxr.dll* a échoué.

## <a name="install-with-powershell-automation"></a>Installer avec l’automatisation PowerShell

Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation d’intégration continue et les installations non administratives du Runtime. Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).

Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1. Vous pouvez choisir une version spécifique en spécifiant le `Channel` commutateur. Incluez le `Runtime` commutateur pour installer un Runtime. Dans le cas contraire, le script installe le [Kit de développement logiciel (SDK)](sdk.md).

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

Installez le kit de développement logiciel (SDK) en omettant le `-Runtime` commutateur. Le `-Channel` commutateur est défini dans cet exemple sur `Current` , qui installe la version la plus récente prise en charge.

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a>Installer avec Visual Studio

Si vous utilisez Visual Studio pour développer des applications .NET Core, le tableau suivant décrit la version minimale requise de Visual Studio en fonction de la version de kit SDK .NET Core cible.

| Version de kit SDK .NET Core | Version de Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 3.1                   | Visual Studio 2019 version 16,4 ou ultérieure. |
| 3.0                   | Visual Studio 2019 version 16,3 ou ultérieure. |
| 2.2                   | Visual Studio 2017 version 15,9 ou ultérieure. |
| 2.1                   | Visual Studio 2017 version 15,7 ou ultérieure. |

Si vous avez déjà installé Visual Studio, vous pouvez vérifier votre version en procédant comme suit.

01. Ouvrez Visual Studio.
01. Sélectionnez **aide**  >  **sur Microsoft Visual Studio**.
01. Lisez le numéro de version dans la boîte de dialogue **à propos** de.

Visual Studio peut installer les kit SDK .NET Core et Runtime les plus récents.

- [Téléchargez Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).

### <a name="select-a-workload"></a>Sélectionner une charge de travail

Lors de l’installation ou de la modification de Visual Studio, sélectionnez une ou plusieurs des charges de travail suivantes, en fonction du type d’application que vous créez :

- La charge de travail **développement multiplateforme .net Core** dans la section **autres ensembles d’outils** .
- La charge de travail **ASP.net et développement Web** dans la section **Web & Cloud** .
- La charge de travail **développement Azure** dans la section **Web & Cloud** .
- La charge de travail **développement .net Desktop** dans la section **Desktop & mobile** .

[![Windows Visual Studio 2019 avec charge de travail .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

## <a name="install-alongside-visual-studio-code"></a>Installer en même temps que Visual Studio Code

Visual Studio Code est un éditeur de code source puissant et léger qui s’exécute sur votre bureau. Visual Studio Code est disponible pour Windows, macOS et Linux.

Même si Visual Studio Code n’est pas fourni avec un programme d’installation automatisé de .NET Core, comme Visual Studio, l’ajout de la prise en charge de .NET Core est simple.

01. [Téléchargez et installez Visual Studio code](https://code.visualstudio.com/Download).
01. [Téléchargez et installez le kit SDK .net Core](https://dotnet.microsoft.com/download/dotnet-core).
01. [Installez l’extension C# à partir de la place de marché Visual Studio code](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).

## <a name="download-and-manually-install"></a>Télécharger et installer manuellement

Comme alternative aux programmes d’installation Windows pour .NET Core, vous pouvez télécharger et installer manuellement le kit de développement logiciel (SDK) ou le Runtime. L’installation manuelle est généralement effectuée dans le cadre du test d’intégration continue. Pour un développeur ou un utilisateur, il est généralement préférable d’utiliser un [programme d’installation](https://dotnet.microsoft.com/download/dotnet-core).

Les kit SDK .NET Core et le Runtime .NET Core peuvent être installés manuellement après avoir été téléchargés. Si vous installez kit SDK .NET Core, vous n’avez pas besoin d’installer le runtime correspondant. Tout d’abord, téléchargez une version binaire pour le kit de développement logiciel (SDK) ou le runtime à partir de l’un des sites suivants :

- Téléchargements de ✔️ [.net 5,0 Preview](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [téléchargements .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ✔️ [téléchargements .net Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [Tous les téléchargements .NET Core](https://dotnet.microsoft.com/download/dotnet-core)

Créez un répertoire dans lequel extraire .NET, par exemple `%USERPROFILE%\dotnet` . Ensuite, extrayez le fichier zip téléchargé dans ce répertoire.

Par défaut, les commandes et les applications CLI .NET Core n’utilisent pas .NET Core de cette manière et vous devez choisir explicitement de l’utiliser. Pour ce faire, modifiez les variables d’environnement à l’aide desquelles une application est démarrée :

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

Cette approche vous permet d’installer plusieurs versions dans des emplacements distincts, puis de choisir explicitement l’emplacement d’installation qu’une application doit utiliser en exécutant l’application avec des variables d’environnement qui pointent à cet emplacement.

Lorsque `DOTNET_MULTILEVEL_LOOKUP` a la valeur `0` , .net Core ignore toute version installée globalement de .net core. Supprimez ce paramètre d’environnement pour laisser .NET Core prendre en compte l’emplacement d’installation globale par défaut lors de la sélection du meilleur Framework pour l’exécution de l’application. La valeur par défaut est généralement `C:\Program Files\dotnet` , où les programmes d’installation installent .net core.

## <a name="docker"></a>Docker

Les conteneurs offrent un moyen léger d’isoler votre application du reste du système hôte. Les conteneurs sur le même ordinateur partagent simplement le noyau et utilisent les ressources fournies à votre application.

.NET Core peut s’exécuter dans un conteneur d’ancrage. Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/). Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.

Microsoft fournit des images adaptées à des scénarios particuliers. Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.

Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur d’ancrage, consultez [Introduction à .net et à l’ancreur](../docker/introduction.md) et aux [exemples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Étapes suivantes

- [Comment vérifier si .net Core est déjà installé](how-to-detect-installed-versions.md?pivots=os-windows).
- [Didacticiel : Hello World didacticiel](../tutorials/with-visual-studio.md).
- [Didacticiel : créer une application avec Visual Studio code](../tutorials/with-visual-studio-code.md).
- [Didacticiel : conteneur d’une application .net Core](../docker/build-container.md).
