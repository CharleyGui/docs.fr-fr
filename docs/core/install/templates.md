---
title: Installer et gérer des modèles de kit de développement logiciel (SDK) .NET Core
description: Découvrez comment installer des modèles .NET Core sur Windows, Linux et macOS.
author: adegeo
ms.author: adegeo
ms.date: 04/24/2020
zone_pivot_groups: operating-systems-set-one
no-loc:
- dotnet new
- dotnet nuget add source
ms.openlocfilehash: 09acae1409eb0492be10bd3a61b14da5be57c6c7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324494"
---
# <a name="manage-net-project-and-item-templates"></a>Gérer les modèles de projet et d’élément .NET

.NET Core fournit un système de modèles qui permet aux utilisateurs d’installer ou de désinstaller des modèles à partir de NuGet, d’un fichier de package NuGet ou d’un répertoire de système de fichiers. Cet article explique comment gérer les modèles .NET Core par le biais de l’interface de commande kit SDK .NET Core.

Pour plus d’informations sur la création de modèles, consultez [Didacticiel : créer des modèles](../tutorials/cli-templates-create-item-template.md).

## <a name="install-template"></a>Installer le modèle

Les modèles sont installés à l’aide de la [dotnet new](../tools/dotnet-new.md) commande SDK avec le `-i` paramètre. Vous pouvez soit fournir l’identificateur de package NuGet d’un modèle, soit un dossier qui contient les fichiers modèles.

### <a name="nuget-hosted-package"></a>Package hébergé par NuGet

Les modèles CLI .NET sont téléchargés vers [NuGet](https://www.nuget.org/) pour une distribution étendue. Les modèles peuvent également être installés à partir d’un flux privé. Au lieu de télécharger un modèle dans un flux NuGet, les fichiers de modèle *nupkg* peuvent être distribués et installés manuellement, comme décrit dans la section [package NuGet local](#local-nuget-package) .

Pour plus d’informations sur la configuration des flux NuGet, consultez [dotnet nuget add source](../tools/dotnet-nuget-add-source.md) .

Pour installer un package de modèles à partir du flux NuGet par défaut, utilisez la `dotnet new -i {package-id}` commande suivante :

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates
```

Pour installer un package de modèles à partir du flux NuGet par défaut avec une version spécifique, utilisez la `dotnet new -i {package-id}::{version}` commande :

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.2.6
```

### <a name="local-nuget-package"></a>Package NuGet local

Quand un pack de modèles est créé, un fichier *nupkg* est généré. Si vous avez un fichier *nupkg* contenant des modèles, vous pouvez l’installer à l’aide de la `dotnet new -i {path-to-package}` commande :

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\Some.Templates.1.0.0.nupkg
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/Some.Templates.1.0.0.nupkg
```

::: zone-end

### <a name="folder"></a>Dossier

Au lieu d’installer le modèle à partir d’un fichier *nupkg* , vous pouvez également installer des modèles à partir d’un dossier directement avec la `dotnet new -i {folder-path}` commande. Le dossier spécifié est considéré comme l’identificateur de package de modèle pour tout modèle trouvé. Tout modèle trouvé dans la hiérarchie du dossier spécifié est installé.

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\some-folder\
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/some-folder/
```

::: zone-end

Le `{folder-path}` spécifié sur la commande devient l’identificateur de modèle de package pour tous les modèles trouvés. Comme indiqué dans la section [modèles de liste](#list-templates) , vous pouvez obtenir la liste des modèles installés à l’aide de la `dotnet new -u` commande. Dans cet exemple, l’identificateur template Pack est indiqué comme dossier utilisé pour l’installation :

::: zone pivot="os-windows"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  /home/username/code/templates
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="uninstall-template"></a>Désinstaller le modèle

Les modèles sont désinstallés via la [dotnet new](../tools/dotnet-new.md) commande du kit de développement logiciel (SDK) avec le `-u` paramètre. Vous pouvez soit fournir l’identificateur de package NuGet d’un modèle, soit un dossier qui contient les fichiers modèles.

### <a name="nuget-package"></a>Package NuGet

Après l’installation d’un pack de modèles NuGet à partir d’un flux NuGet ou d’un fichier *nupkg* , vous pouvez le désinstaller en référençant l’identificateur de package NuGet.

Pour désinstaller un pack de modèles, utilisez la `dotnet new -u {package-id}` commande suivante :

```dotnetcli
dotnet new -u Microsoft.DotNet.Web.Spa.ProjectTemplates
```

### <a name="folder"></a>Dossier

Lorsque des modèles sont installés par le biais [d’un chemin d’accès au dossier](#folder), le chemin d’accès au dossier devient l’identificateur du Pack de modèles.

Pour désinstaller un pack de modèles, utilisez la `dotnet new -u {package-folder-path}` commande suivante :

::: zone pivot="os-windows"

```dotnetcli
dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="list-templates"></a>Liste des modèles

En utilisant la commande de désinstallation standard sans identificateur de package, vous pouvez voir la liste des modèles installés avec la commande qui désinstalle chaque modèle.

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

## <a name="install-templates-from-other-sdks"></a>Installer des modèles à partir d’autres SDK

Si vous avez installé chaque version du kit de développement logiciel (SDK) de manière séquentielle, par exemple si vous avez installé le kit de développement logiciel 2,0, le kit de développement logiciel (SDK) 2,1, etc., tous les modèles du SDK sont installés. Toutefois, si vous démarrez avec une version ultérieure du kit de développement logiciel (SDK), comme 3,1, seuls les modèles pour [LTS (support à long terme)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sont inclus, qui au moment de la publication du kit de développement logiciel (sdk) 3,1 est SDK 2,1 et SDK 3,1. Les modèles pour toute autre version ne sont pas inclus.

Les modèles .NET Core sont disponibles sur NuGet et vous pouvez les installer comme n’importe quel autre modèle. Pour plus d’informations, consultez [install NuGet Hosted package](#nuget-hosted-package).

| Kit SDK              | Identificateur du package NuGet                                                                                                      |
|------------------|-------------------------------------------------------------------------------------------------------------------------------|
| .NET Core 2.1    | [`Microsoft.DotNet.Common.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.1) |
| .NET Core 2.2    | [`Microsoft.DotNet.Common.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.2) |
| .NET Core 3.0    | [`Microsoft.DotNet.Common.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.0) |
| .NET Core 3.1    | [`Microsoft.DotNet.Common.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.1) |
| ASP.NET Core 2.1 | [`Microsoft.DotNet.Web.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.1)       |
| ASP.NET Core 2.2 | [`Microsoft.DotNet.Web.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.2)       |
| ASP.NET Core 3,0 | [`Microsoft.DotNet.Web.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.0)       |
| ASP.NET Core 3,1 | [`Microsoft.DotNet.Web.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.1)       |

Par exemple, le kit SDK .NET Core contient des modèles pour une application console ciblant .NET Core 2,1 et .NET Core 3,1. Si vous souhaitez cibler .NET Core 3,0, vous devez installer les modèles 3,0.

01. Essayez de créer une application qui cible .NET Core 3,0.

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    Si un message d’erreur s’affiche, vous devez installer les modèles.

    > Impossible de trouver un modèle installé qui correspond à l’entrée, recherche en ligne d’un modèle qui fait...

01. Installez les modèles de projet .NET Core 3,0.

    ```dotnetcli
    dotnet new -i Microsoft.DotNet.Common.ProjectTemplates.3.0
    ```

01. Essayez de créer l’application une deuxième fois.

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    Et un message indiquant que le projet a été créé doit s’afficher.

    > Le modèle « application console » a été créé avec succès.
    >
    > Traitement des actions après création... Exécution de « dotnet restore » sur Path-to-Project-file. csproj... Détermination des projets à restaurer... Restauration terminée dans 1,05 s pour Path-to-Project-file. csproj.
    >
    > Restauration réussie.

## <a name="see-also"></a>Voir aussi

- [Didacticiel : créer un modèle d’élément](../tutorials/cli-templates-create-item-template.md)
- [dotnet new](../tools/dotnet-new.md)
- [dotnet nuget add source](../tools/dotnet-nuget-add-source.md)
