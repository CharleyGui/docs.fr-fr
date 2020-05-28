---
title: Outil de désinstallation
description: Vue d’ensemble de l’outil de désinstallation de .NET Core, outil guidé qui permet le nettoyage contrôlé des kits de développement logiciel (SDK) .NET Core et des runtimes.
author: sfoslund
ms.date: 05/27/2020
ms.openlocfilehash: 1ad31cd42d8f8f87e3501b422fc4298c643e2067
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144511"
---
# <a name="net-core-uninstall-tool"></a>Outil de désinstallation de .NET Core

L' [outil de désinstallation de .net Core](https://aka.ms/dotnet-core-uninstall-tool) ( `dotnet-core-uninstall` ) vous permet de supprimer des kits de développement logiciel (SDK) .net Core et des runtimes d’un système. Une collection d’options est disponible pour spécifier les versions que vous souhaitez désinstaller.

L’outil prend en charge Windows et macOS. Pour le moment, Linux n’est pas pris en charge.

Sur Windows, l’outil ne peut désinstaller que les kits de développement logiciel (SDK) et les runtimes qui ont été installés à l’aide de l’un des programmes d’installation suivants :

- Kit SDK .NET Core et le programme d’installation du Runtime.
- Le programme d’installation de Visual Studio dans les versions antérieures à Visual Studio 2019 version 16,3.

Sur macOS, l’outil ne peut désinstaller que les kits de développement logiciel (SDK) et les runtimes situés dans le dossier */usr/local/share/dotnet* .

En raison de ces limitations, l’outil peut ne pas être en mesure de désinstaller tous les kits de développement logiciel (SDK) .NET Core et les runtimes sur votre ordinateur. Vous pouvez utiliser la `dotnet --info` commande pour rechercher tous les kits de développement logiciel (SDK) .net Core et les runtimes installés, y compris les kits de développement logiciel (SDK) et runtimes que cet outil ne peut pas supprimer. La `dotnet-core-uninstall list` commande affiche les kits de développement logiciel (SDK) qui peuvent être désinstallés avec l’outil.

## <a name="install-the-tool"></a>Installer l’outil

Vous pouvez télécharger l’outil de désinstallation de .NET Core à partir d' [ici](https://aka.ms/dotnet-core-uninstall-tool) et rechercher le code source dans le référentiel GitHub [dotnet/CLI-Lab](https://github.com/dotnet/cli-lab) .

> [!NOTE]
> L’outil nécessite une élévation pour désinstaller les kits de développement logiciel (SDK) .NET Core et les runtimes. Par conséquent, il doit être installé dans un répertoire protégé en écriture, tel que *C:\Program Files* sur Windows ou */usr/local/bin* sur MacOS. Consultez également [l’accès avec élévation de privilèges pour les commandes dotnet](../tools/elevated-access.md). Pour plus d’informations, consultez les [instructions d’installation détaillées](https://aka.ms/dotnet-core-uninstall-tool).

## <a name="run-the-tool"></a>Exécution de l'outil

Les étapes suivantes illustrent l’approche recommandée pour l’exécution de l’outil de désinstallation :

- [Étape 1 : afficher les kits de développement logiciel (SDK) .NET Core installés et les runtimes](#step-1---display-installed-net-core-sdks-and-runtimes)
- [Étape 2 : effectuer une exécution à sec](#step-2---do-a-dry-run)
- [Étape 3 : désinstaller les kits de développement logiciel (SDK) et runtimes .NET Core](#step-3---uninstall-net-core-sdks-and-runtimes)
- [Étape 4 : supprimer le dossier NuGet Fallback (facultatif)](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a>Étape 1 : afficher les kits de développement logiciel (SDK) .NET Core installés et les runtimes

La `dotnet-core-uninstall list` commande répertorie les kits de développement logiciel (SDK) .net Core installés et les runtimes qui peuvent être supprimés avec cet outil. Certains kits de développement logiciel (SDK) et runtimes peuvent être requis par Visual Studio et ils s’affichent avec la raison pour laquelle il n’est pas recommandé de les désinstaller.

> [!NOTE]
> La sortie de la `dotnet-core-uninstall list` commande ne correspond pas à la liste des versions installées dans la sortie de `dotnet --info` dans la plupart des cas. Plus précisément, cet outil n’affiche pas les versions installées par les fichiers zip ou gérées par Visual Studio (n’importe quelle version installée avec Visual Studio 2019 16,3 ou version ultérieure). Une façon de vérifier si une version est gérée par Visual Studio est de l’afficher dans `Add or Remove Programs` , où les versions gérées de Visual Studio sont marquées comme telles dans leurs noms complets.

**dotnet-Core-liste de désinstallation**

#### <a name="synopsis"></a>Synopsis

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a>Options

## <a name="windows"></a>[Windows](#tab/windows)

* **`--aspnet-runtime`**

  Répertorie tous les runtimes ASP.NET Core qui peuvent être désinstallés avec cet outil.

* **`--hosting-bundle`**

  Répertorie toutes les offres d’hébergement .NET Core qui peuvent être désinstallées avec cet outil.

* **`--runtime`**

  Répertorie tous les runtimes .NET Core qui peuvent être désinstallés avec cet outil.

* **`--sdk`**

  Répertorie tous les kits de développement logiciel (SDK) .NET Core qui peuvent être désinstallés avec cet outil.

* **`-v, --verbosity <LEVEL>`**

  Définit le niveau de détail. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `normal`.

* **`--x64`**

  Répertorie tous les kits de développement logiciel (SDK) .NET Core x64 et les runtimes qui peuvent être désinstallés avec cet outil.

* **`--x86`**

  Répertorie tous les kits de développement logiciel (SDK) .NET Core x86 et les runtimes qui peuvent être désinstallés avec cet outil.

## <a name="macos"></a>[MacOS](#tab/macos)

* **`--runtime`**

  Répertorie tous les runtimes .NET Core qui peuvent être désinstallés avec cet outil.

* **`--sdk`**

  Répertorie tous les kits de développement logiciel (SDK) .NET Core qui peuvent être désinstallés avec cet outil.

* **`-v, --verbosity <LEVEL>`**

  Définit le niveau de détail. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `normal`.
  
---

#### <a name="examples"></a>Exemples

* Répertorie tous les kits de développement logiciel (SDK) .NET Core et les runtimes qui peuvent être supprimés à l’aide de cet outil :

  ```console
  dotnet-core-uninstall list
  ```

* Répertoriez tous les kits de développement logiciel (SDK) et runtimes x64 .NET Core :

  ```console
  dotnet-core-uninstall list --x64
  ```

* Répertorier tous les kits de développement logiciel (SDK) .NET Core x86 :

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a>Étape 2 : effectuer une exécution à sec

Les `dotnet-core-uninstall dry-run` `dotnet-core-uninstall whatif` commandes et affichent les kits de développement logiciel (SDK) .net Core et les runtimes qui seront supprimés en fonction des options fournies sans effectuer la désinstallation. Ces commandes sont des synonymes.

**dotnet-Core-désinstaller Dry-Run et DOTNET-Core-Uninstall WhatIf**

#### <a name="synopsis"></a>Synopsis

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a>Arguments

* **`VERSION`**

  Version spécifiée à désinstaller. Vous pouvez répertorier plusieurs versions l’une après l’autre, séparées par des espaces. Les fichiers réponse sont également pris en charge.

  > [!TIP]
  > Les fichiers réponse sont une alternative au placement de toutes les versions sur la ligne de commande.
  > Il s’agit de fichiers texte, généralement avec une \* extension. rsp, et chaque version est indiquée sur une ligne distincte.
  > Pour spécifier un fichier réponse pour l' `VERSION` argument, utilisez le \@ caractère immédiatement suivi du nom du fichier réponse.

#### <a name="options"></a>Options

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes.

* **`--all-below <VERSION>`**

  Supprime uniquement les kits de développement logiciel (SDK) .NET Core et les runtimes dont la version est inférieure à la version spécifiée. La version spécifiée reste installée.

* **`--all-but <VERSIONS>`**

  Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception des versions spécifiées.

* **`--all-but-latest`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception de la version la plus récente.

* **`--all-lower-patches`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes remplacés par des correctifs plus élevés. Cette option protège global. JSON.

* **`--all-previews`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes marqués en tant qu’aperçus.

* **`--all-previews-but-latest`**

  Supprime les kits de développement logiciel (SDK) et runtimes .NET Core marqués comme préversions, à l’exception de la version préliminaire la plus élevée.

* **`--aspnet-runtime`**

  Supprime ASP.NET Core runtimes uniquement.

* **`--hosting-bundle`**

  Supprime uniquement le Runtime .NET Core et les regroupements d’hébergement.

* **`--major-minor <MAJOR_MINOR>`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes qui correspondent à la `major.minor` version spécifiée.

* **`--runtime`**

  Supprime uniquement les runtimes .NET Core.

* **`--sdk`**

  Supprime uniquement les kits de développement logiciel (SDK) .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Définit le niveau de détail. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `normal`.

* **`--x64`**

  Doit être utilisé avec `--sdk` , `--runtime` et `--aspnet-runtime` pour supprimer les runtimes ou les kits de développement logiciel (SDK) x64.

* **`--x86`**

  Doit être utilisé avec `--sdk` , `--runtime` et `--aspnet-runtime` pour supprimer les kits de développement logiciel (SDK) ou runtimes x86.

* **`--force`** Force la suppression des versions qui peuvent être utilisées par Visual Studio.

Remarques :

1. Exactement l’un des `--sdk` ,, `--runtime` `--aspnet-runtime` et `--hosting-bundle` est obligatoire.
2. `--all`, `--all-below` , `--all-but` , `--all-but-latest` , `--all-lower-patches` , `--all-previews` , `--all-previews-but-latest` , `--major-minor` et `[<VERSION>...]` sont exclusifs.
3. Si `--x64` ou `--x86` n’est pas spécifié, les paramètres x64 et x86 seront supprimés.

## <a name="macos"></a>[MacOS](#tab/macos)

* **`--all`**

  Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes.

* **`--all-below <VERSION>`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes inférieurs à la version spécifiée. La version spécifiée est conservée.

* **`--all-but <VERSIONS>`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception des versions spécifiées.

* **`--all-but-latest`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception de la version la plus récente.

* **`--all-lower-patches`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes remplacés par des correctifs plus élevés. Cette option protège global. JSON.

* **`--all-previews`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes marqués en tant qu’aperçus.

* **`--all-previews-but-latest`**

  Supprime les kits de développement logiciel (SDK) et runtimes .NET Core marqués comme préversions, à l’exception de la version préliminaire la plus élevée.

* **`--major-minor <MAJOR_MINOR>`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes qui correspondent à la `major.minor` version spécifiée.

* **`--runtime`**

  Supprime uniquement les runtimes .NET Core.

* **`--sdk`**

  Supprime uniquement les kits de développement logiciel (SDK) .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Définit le niveau de détail. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `normal`.
  
* **`--force`** Force la suppression des versions qui peuvent être utilisées par Visual Studio ou les kits de développement logiciel (SDK).

Remarques :

1. Une seule `--sdk` et unique `--runtime` est requise.
2. `--all`, `--all-below` , `--all-but` , `--all-but-latest` , `--all-lower-patches` , `--all-previews` , `--all-previews-but-latest` , `--major-minor` et `[<VERSION>...]` sont exclusifs.

---

#### <a name="examples"></a>Exemples

> [!NOTE]
> Par défaut, les kits de développement logiciel (SDK) .NET Core et les runtimes qui peuvent être requis par Visual Studio ou d’autres SDK ne sont pas inclus dans la `dotnet-core-uninstall dry-run` sortie. Dans les exemples suivants, certains des kits de développement logiciel (SDK) et runtimes spécifiés peuvent ne pas être inclus dans la sortie, en fonction de l’état de l’ordinateur. Pour inclure tous les kits de développement logiciel (SDK) et runtimes, répertoriez-les explicitement comme arguments ou utilisez l' `--force` option.

* Exécution à sec de la suppression de tous les runtimes .NET Core qui ont été remplacés par des correctifs plus élevés :

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* Exécution à sec de la suppression de tous les kits de développement logiciel (SDK) .NET Core sous la version `2.2.301` :

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a>Étape 3 : désinstaller les kits de développement logiciel (SDK) et runtimes .NET Core

`dotnet-core-uninstall remove`désinstalle les kits de développement logiciel (SDK) .NET Core et les runtimes spécifiés par une collection d’options. L’outil ne peut pas être utilisé pour désinstaller des kits de développement logiciel (SDK) et des runtimes avec la version 5,0 ou ultérieure.

Étant donné que cet outil a un comportement destructif, il est **fortement** recommandé d’effectuer une exécution à sec avant d’exécuter la commande Remove. La série à sec vous montrera les kits de développement logiciel (SDK) .NET Core et les runtimes qui seront supprimés lorsque vous utiliserez la `remove` commande. Reportez-vous à [la rubrique dois-je supprimer une version ?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) pour savoir quels SDK et runtimes peuvent être supprimés en toute sécurité.

> [!CAUTION]
> Rappelez-vous des avertissements suivants :
>
>- Cet outil peut désinstaller les versions des kit SDK .NET Core requises par les `global.json` fichiers sur votre ordinateur. Vous pouvez réinstaller les kits de développement logiciel (SDK) .NET Core à partir de la page [Télécharger .net Core](https://dotnet.microsoft.com/download/dotnet-core) .
>- Cet outil peut désinstaller des versions du Runtime .NET Core qui sont requises par les applications dépendantes du Framework sur votre ordinateur. Vous pouvez réinstaller les runtimes .NET Core à partir de la page [Télécharger .net Core](https://dotnet.microsoft.com/download/dotnet-core) .
>- Cet outil peut désinstaller des versions du kit SDK .NET Core et du Runtime sur lesquelles s’appuie Visual Studio. Si vous interrompez votre installation de Visual Studio, exécutez « réparer » dans le programme d’installation de Visual Studio pour revenir à un état de travail.

Par défaut, toutes les commandes conservent les kits de développement logiciel (SDK) .NET Core et les runtimes qui peuvent être requis par Visual Studio ou d’autres kits de développement logiciel (SDK). Ces kits de développement logiciel (SDK) et runtimes peuvent être désinstallés en les répertoriant explicitement comme arguments ou à l’aide de l' `--force` option.

L’outil nécessite une élévation pour désinstaller les kits de développement logiciel (SDK) .NET Core et les runtimes. Exécutez l’outil dans une invite de commandes d’administrateur sur Windows et avec `sudo` sur MacOS. Les `dry-run` `whatif` commandes et ne nécessitent pas d’élévation.

**dotnet-Core-désinstaller supprimer**

#### <a name="synopsis"></a>Synopsis

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a>Arguments

* **`VERSION`**

  Version spécifiée à désinstaller. Vous pouvez répertorier plusieurs versions l’une après l’autre, séparées par des espaces. Les fichiers réponse sont également pris en charge.

  > [!TIP]
  > Les fichiers réponse sont une alternative au placement de toutes les versions sur la ligne de commande.
  > Il s’agit de fichiers texte, généralement avec une \* extension. rsp, et chaque version est indiquée sur une ligne distincte.
  > Pour spécifier un fichier réponse pour l' `VERSION` argument, utilisez le \@ caractère immédiatement suivi du nom du fichier réponse.

#### <a name="options"></a>Options

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes.

* **`--all-below <VERSION>`**

  Supprime uniquement les kits de développement logiciel (SDK) .NET Core et les runtimes dont la version est inférieure à la version spécifiée. La version spécifiée reste installée.

* **`--all-but <VERSIONS>`**

  Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception des versions spécifiées.

* **`--all-but-latest`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception de la version la plus récente.

* **`--all-lower-patches`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes remplacés par des correctifs plus élevés. Cette option protège global. JSON.

* **`--all-previews`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes marqués en tant qu’aperçus.

* **`--all-previews-but-latest`**

  Supprime les kits de développement logiciel (SDK) et runtimes .NET Core marqués comme préversions, à l’exception de la version préliminaire la plus élevée.

* **`--aspnet-runtime`**

  Supprime ASP.NET Core runtimes uniquement.

* **`--hosting-bundle`**

  Supprime uniquement le Runtime .NET Core et les regroupements d’hébergement.

* **`--major-minor <MAJOR_MINOR>`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes qui correspondent à la `major.minor` version spécifiée.

* **`--runtime`**

  Supprime uniquement les runtimes .NET Core.

* **`--sdk`**

  Supprime uniquement les kits de développement logiciel (SDK) .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Définit le niveau de détail. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `normal`.

* **`--x64`**

  Doit être utilisé avec `--sdk` , `--runtime` et `--aspnet-runtime` pour supprimer les runtimes ou les kits de développement logiciel (SDK) x64.

* **`--x86`**

  Doit être utilisé avec `--sdk` , `--runtime` et `--aspnet-runtime` pour supprimer les kits de développement logiciel (SDK) ou runtimes x86.

* **`-y, --yes`** Exécute la commande sans demander de confirmation oui ou non.

* **`--force`** Force la suppression des versions qui peuvent être utilisées par Visual Studio.

Remarques :

1. Exactement l’un des `--sdk` ,, `--runtime` `--aspnet-runtime` et `--hosting-bundle` est obligatoire.
2. `--all`, `--all-below` , `--all-but` , `--all-but-latest` , `--all-lower-patches` , `--all-previews` , `--all-previews-but-latest` , `--major-minor` et `[<VERSION>...]` sont exclusifs.
3. Si `--x64` ou `--x86` n’est pas spécifié, les paramètres x64 et x86 seront supprimés.

## <a name="macos"></a>[MacOS](#tab/macos)

* **`--all`**

  Supprime tous les kits de développement logiciel (SDK) .NET Core et les runtimes.

* **`--all-below <VERSION>`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes inférieurs à la version spécifiée. La version spécifiée est conservée.

* **`--all-but <VERSIONS>`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception des versions spécifiées.

* **`--all-but-latest`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes, à l’exception de la version la plus récente.

* **`--all-lower-patches`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes remplacés par des correctifs plus élevés. Cette option protège global. JSON.

* **`--all-previews`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes marqués en tant qu’aperçus.

* **`--all-previews-but-latest`**

  Supprime les kits de développement logiciel (SDK) et runtimes .NET Core marqués comme préversions, à l’exception de la version préliminaire la plus élevée.

* **`--major-minor <MAJOR_MINOR>`**

  Supprime les kits de développement logiciel (SDK) .NET Core et les runtimes qui correspondent à la `major.minor` version spécifiée.

* **`--runtime`**

  Supprime uniquement les runtimes .NET Core.

* **`--sdk`**

  Supprime uniquement les kits de développement logiciel (SDK) .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Définit le niveau de détail. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `normal`.

* **`-y, --yes`** Exécute la commande sans demander de confirmation Y/N.
  
* **`--force`** Force la suppression des versions qui peuvent être utilisées par Visual Studio ou les kits de développement logiciel (SDK).

Remarques :

1. Une seule `--sdk` et unique `--runtime` est requise.
2. `--all`, `--all-below` , `--all-but` , `--all-but-latest` , `--all-lower-patches` , `--all-previews` , `--all-previews-but-latest` , `--major-minor` et `[<VERSION>...]` sont exclusifs.

---

#### <a name="examples"></a>Exemples

> [!NOTE]
> Par défaut, les kits de développement logiciel (SDK) .NET Core et les runtimes qui peuvent être requis par Visual Studio ou d’autres kits de développement logiciel (SDK) sont conservés. Dans les exemples suivants, certains des kits de développement logiciel (SDK) et runtimes spécifiés peuvent être conservés, en fonction de l’état de l’ordinateur. Pour supprimer tous les kits de développement logiciel (SDK) et runtimes, répertoriez-les explicitement comme arguments ou utilisez l' `--force` option.

* Supprimez tous les runtimes .NET Core à l’exception de la version `3.0.0-preview6-27804-01` sans demander de confirmation Y/N :

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* Supprimer tous les kits de développement logiciel (SDK) .NET Core 1,1 sans demander de confirmation Y/n :

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* Supprimez le kit de développement logiciel (SDK) .NET Core 1.1.11 au minimum sans sortie de la console :

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* Supprimez tous les kits de développement logiciel (SDK) .NET Core pouvant être supprimés en toute sécurité par cet outil :

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* Supprimer tous les kits de développement logiciel (SDK) .NET Core qui peuvent être supprimés par cet outil, y compris les kits de développement logiciel (SDK) qui peuvent être requis par Visual Studio (non recommandé) :

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* Supprimer tous les kits de développement logiciel (SDK) .NET Core spécifiés dans le fichier réponse`versions.rsp`

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  Le contenu de *versions. rsp* est le suivant :
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a>Étape 4 : supprimer le dossier NuGet Fallback (facultatif)

Dans certains cas, vous n’avez plus besoin de la et vous souhaiterez `NuGetFallbackFolder` peut-être la supprimer. Pour plus d’informations sur la suppression de ce dossier, consultez [Remove the NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).

## <a name="uninstall-the-tool"></a>Désinstaller l’outil

## <a name="windows"></a>[Windows](#tab/windows)

1. Ouvrez la boîte de dialogue **Ajout/Suppression de programmes**.
2. Recherchez `Microsoft .NET Core SDK Uninstall Tool`.
3. Sélectionner **Désinstaller**.

## <a name="macos"></a>[MacOS](#tab/macos)

Supprimez le fichier *dotnet-Core-Uninstall. tar. gz* téléchargé à partir du répertoire où il a été installé. Si vous dézippéz le contenu de ce fichier dans un autre répertoire, veillez à supprimer également ce contenu.

---
