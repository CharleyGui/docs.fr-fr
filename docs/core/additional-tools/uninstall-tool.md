---
title: Outil désinstaller
description: Un aperçu de l’outil .NET Core Uninstall, un outil guidé qui permet le nettoyage contrôlé des SDKs et des runtimes .NET Core.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 816aef6ab8bc0e51bb8befb14fde60513d4fadfc
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507319"
---
# <a name="net-core-uninstall-tool"></a>Outil de désinstallation de .NET Core

[L’outil .NET Core Uninstall](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) vous permet de supprimer .NET Core SDKs et Runtimes d’un système. Une collection d’options est disponible pour spécifier les versions que vous souhaitez désinstaller.

L’outil prend en charge Windows et macOS. Pour le moment, Linux n’est pas pris en charge.

Sur Windows, l’outil ne peut désinstaller les SDK et les Runtimes qui ont été installés à l’aide d’un des installateurs suivants :

- Le .NET Core SDK et l’installateur de temps d’exécution.
- L’installateur Visual Studio en versions antérieures à la version 16.3 de Visual Studio 2019.

Sur macOS, l’outil ne peut désinstaller les SDK et les temps d’exécution situés dans le dossier */usr/local/share/dotnet.*

En raison de ces limitations, l’outil peut ne pas être en mesure de désinstaller tous les SDKs de base .NET et les temps d’exécution sur votre machine. Vous pouvez `dotnet --info` utiliser la commande pour trouver tous les SDKs de base .NET et les temps d’exécution installés, y compris les SDK et les temps d’exécution que cet outil ne peut pas supprimer. La `dotnet-core-uninstall list` commande affiche quels SDKs peuvent être désinstallés avec l’outil.

## <a name="install-the-tool"></a>Installer l’outil

Vous pouvez télécharger l’outil .NET Core Uninstall à partir [d’ici](https://aka.ms/dotnet-core-uninstall-tool) et trouver le code source au référentiel [GitHub dotnet/cli-lab.](https://github.com/dotnet/cli-lab)

> [!NOTE]
> L’outil nécessite l’élévation pour désinstaller .NET Core SDKs et les temps d’exécution. Par conséquent, il devrait être installé dans un répertoire protégé par l’écriture tels que *les fichiers de programme C: 'program* sur Windows ou */usr/local/bin* sur macOS. Voir aussi [Accès élevé pour les commandes dotnet](../tools/elevated-access.md). Pour plus d’informations, voir les [instructions d’installation détaillées](https://aka.ms/dotnet-core-uninstall-tool).

## <a name="run-the-tool"></a>Exécuter l’outil

Les étapes suivantes montrent l’approche recommandée pour l’exécution de l’outil de désinstallation :

- [Étape 1 - Affichage installé .NET Core SDKs et runtimes](#step-1---display-installed-net-core-sdks-and-runtimes)
- [Étape 2 - Faire une course à sec](#step-2---do-a-dry-run)
- [Étape 3 - Uninstall .NET Core SDKs and Runtimes](#step-3---uninstall-net-core-sdks-and-runtimes)
- [Étape 4 - Supprimer le dossier de repli NuGet (facultatif)](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a>Étape 1 - Affichage installé .NET Core SDKs et runtimes

La `dotnet-core-uninstall list` commande répertorie les SDKs et les temps d’exécution .NET core installés qui peuvent être supprimés avec cet outil. Certains SDK et les durées d’exécution peuvent être nécessaires par Visual Studio et ils sont affichés avec une note de pourquoi il n’est pas recommandé de les désinstaller.

> [!NOTE]
> La sortie `dotnet-core-uninstall list` de la commande ne correspondra pas à `dotnet --info` la liste des versions installées dans la sortie de dans la plupart des cas. Plus précisément, cet outil n’affichera pas les versions installées par des fichiers zip ou gérées par Visual Studio (toute version installée avec Visual Studio 2019 16.3 ou plus tard). Une façon de vérifier si une version est gérée `Add or Remove Programs`par Visual Studio est de la voir dans , où Visual Studio versions gérées sont marqués comme tels dans leurs noms d’affichage.

**liste dotnet-core-uninstall**

#### <a name="synopsis"></a>Synopsis

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a>Options

## <a name="windows"></a>[Windows](#tab/windows)

* **`--aspnet-runtime`**

  Répertorie tous les temps d’exécution ASP.NET Core qui peuvent être désinstallés avec cet outil.

* **`--hosting-bundle`**

  Répertorie tous les forfaits .NET Core et les forfaits d’hébergement qui peuvent être désinstallés avec cet outil.

* **`--runtime`**

  Répertorie tous les temps d’exécution .NET Core qui peuvent être désinstallés avec cet outil.

* **`--sdk`**

  Répertorie tous les SDK core .NET qui peuvent être désinstallés avec cet outil.

* **`-v, --verbosity <LEVEL>`**

  Définit le niveau de verbosité. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `normal`.

* **`--x64`**

  Répertorie tous les SDKs et les runtimes de base x64 .NET qui peuvent être désinstallés avec cet outil.

* **`--x86`**

  Répertorie tous les SDKs et les runtimes de base x86 .NET qui peuvent être désinstallés avec cet outil.

## <a name="macos"></a>[macOS](#tab/macos)

* **`--runtime`**

  Répertorie tous les temps d’exécution .NET Core qui peuvent être désinstallés avec cet outil.

* **`--sdk`**

  Répertorie tous les SDK core .NET qui peuvent être désinstallés avec cet outil.

* **`-v, --verbosity <LEVEL>`**

  Définit le niveau de verbosité. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `normal`.
  
---

#### <a name="examples"></a>Exemples

* Énumérez tous les SDKs de base de .NET et les temps d’exécution qui peuvent être supprimés avec cet outil :

  ```console
  dotnet-core-uninstall list
  ```

* Liste tous les X64 .NET Core SDKs et runtimes:

  ```console
  dotnet-core-uninstall list --x64
  ```

* Liste tous les X86 .NET Core SDKs:

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a>Étape 2 - Faire une course à sec

Les `dotnet-core-uninstall dry-run` `dotnet-core-uninstall whatif` commandes et les commandes affichent les SDKs et les temps d’exécution .NET Core qui seront supprimés en fonction des options fournies sans effectuer le désinstallation. Ces commandes sont synonymes.

**dotnet-core-uninstall dry-run et dotnet-core-uninstall whatif**

#### <a name="synopsis"></a>Synopsis

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a>Arguments

* **`VERSION`**

  La version spécifiée pour désinstaller. Vous pouvez énumérer plusieurs versions l’une après l’autre, séparées par des espaces. Les fichiers de réponse sont également pris en charge.

  > [!TIP]
  > Les fichiers de réponse sont une alternative à la mise en place de toutes les versions sur la ligne de commande.
  > Ce sont des fichiers texte, généralement avec une \*extension .rsp, et chaque version est répertoriée sur une ligne séparée.
  > Pour spécifier `VERSION` un fichier \@ de réponse pour l’argument, utilisez le personnage immédiatement suivi du nom du fichier de réponse.

#### <a name="options"></a>Options

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Supprime tous les SDKs et les temps d’exécution .NET Core.

* **`--all-below <VERSION>`**

  Supprime uniquement les SDKs core .NET et les temps d’exécution avec une version plus petite que la version spécifiée. La version spécifiée reste installée.

* **`--all-but <VERSIONS>`**

  Supprime tous les SDK core .NET et les durées d’exécution, à l’exception de celles spécifiées.

* **`--all-but-latest`**

  Supprime .NET Core SDKs et runtimes, sauf la version la plus élevée.

* **`--all-lower-patches`**

  Supprime les SDK core .NET et les temps d’exécution remplacés par des correctifs plus élevés. Cette option protège global.json.

* **`--all-previews`**

  Supprime les SDK core .NET et les temps d’exécution marqués comme aperçus.

* **`--all-previews-but-latest`**

  Supprime .NET Core SDKs et runtimes marqués comme aperçus, sauf l’aperçu le plus élevé.

* **`--aspnet-runtime`**

  Supprime ASP.NET les temps d’exécution Core seulement.

* **`--hosting-bundle`**

  Supprime le temps d’exécution .NET Core et l’hébergement des faisceaux seulement.

* **`--major-minor <MAJOR_MINOR>`**

  Supprime .NET Core SDKs et runtimes `major.minor` qui correspondent à la version spécifiée.

* **`--runtime`**

  Supprime les temps d’exécution .NET Core seulement.

* **`--sdk`**

  Supprime .NET Core SDKs seulement.

* **`-v, --verbosity <LEVEL>`**

  Définit le niveau de verbosité. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `normal`.

* **`--x64`**

  Doit être `--sdk`utilisé `--runtime`avec `--aspnet-runtime` , , et pour supprimer x64 SDKs ou runtimes.

* **`--x86`**

  Doit être `--sdk`utilisé `--runtime`avec `--aspnet-runtime` , , et pour supprimer x86 SDKs ou runtimes.

* **`--force`** Force le retrait des versions qui pourraient être utilisées par Visual Studio.

Remarques :

1. Exactement un `--sdk` `--runtime`de `--aspnet-runtime`, `--hosting-bundle` , , et est nécessaire.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , et sont exclusifs.
3. Si `--x64` `--x86` ou ne sont pas spécifiés, alors x64 et x86 seront supprimés.

## <a name="macos"></a>[macOS](#tab/macos)

* **`--all`**

  Supprime tous les SDKs et les temps d’exécution .NET Core.

* **`--all-below <VERSION>`**

  Supprime les SDK core .NET et les temps d’exécution en dessous de la version spécifiée. La version spécifiée restera.

* **`--all-but <VERSIONS>`**

  Supprime .NET Core SDKs et runtimes, sauf les versions spécifiées.

* **`--all-but-latest`**

  Supprime .NET Core SDKs et runtimes, sauf la version la plus élevée.

* **`--all-lower-patches`**

  Supprime les SDK core .NET et les temps d’exécution remplacés par des correctifs plus élevés. Cette option protège global.json.

* **`--all-previews`**

  Supprime les SDK core .NET et les temps d’exécution marqués comme aperçus.

* **`--all-previews-but-latest`**

  Supprime .NET Core SDKs et runtimes marqués comme aperçus, sauf l’aperçu le plus élevé.

* **`--major-minor <MAJOR_MINOR>`**

  Supprime .NET Core SDKs et runtimes `major.minor` qui correspondent à la version spécifiée.

* **`--runtime`**

  Supprime les temps d’exécution .NET Core seulement.

* **`--sdk`**

  Supprime .NET Core SDKs seulement.

* **`-v, --verbosity <LEVEL>`**

  Définit le niveau de verbosité. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `normal`.
  
* **`--force`** Force le retrait des versions qui pourraient être utilisées par Visual Studio ou SDKs.

Remarques :

1. Exactement un `--sdk` `--runtime` de et est nécessaire.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , et sont exclusifs.

---

#### <a name="examples"></a>Exemples

> [!NOTE]
> Par défaut, les SDKs de base .NET et les temps d’exécution qui `dotnet-core-uninstall dry-run` peuvent être exigés par Visual Studio ou d’autres SDK ne sont pas inclus dans la sortie. Dans les exemples suivants, certains des SDK spécifiés et les temps d’exécution peuvent ne pas être inclus dans la sortie, selon l’état de la machine. Pour inclure tous les SDK et les temps d’exécution, les énumérer explicitement comme arguments ou utiliser l’option. `--force`

* Course sèche de l’élimination de tous les temps d’exécution .NET Core qui ont été remplacés par des correctifs plus élevés:

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* Course sèche de la suppression de tous les `2.2.301`SDKs .NET Core en dessous de la version :

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a>Étape 3 - Uninstall .NET Core SDKs and Runtimes

`dotnet-core-uninstall remove`désinstaller .NET Core SDKs et Runtimes qui sont spécifiés par une collection d’options. L’outil ne peut pas être utilisé pour désinstaller les SDK et les Runtimes avec la version 5.0 ou plus.

Depuis cet outil a un comportement destructeur, il est **fortement** recommandé que vous faites une course à sec avant d’exécuter la commande de suppression. La course à sec vous montrera ce que les SDKs de `remove` base de .NET et les temps d’exécution seront supprimés lorsque vous utilisez la commande. Se référer à [Dois-je supprimer une version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) pour savoir quels SDKs et runtimes sont sûrs à supprimer.

> [!CAUTION]
> Rappelez-vous des avertissements suivants :
>
>- Cet outil peut désinstaller les versions du SDK `global.json` .NET Core qui sont requis par les fichiers sur votre machine. Vous pouvez réinstaller .NET Core SDKs à partir de la page [Télécharger .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)
>- Cet outil peut désinstaller les versions du temps d’exécution .NET Core qui sont requis par des applications dépendantes du cadre de votre machine. Vous pouvez réinstaller les temps d’exécution .NET Core à partir de la page [Télécharger .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)
>- Cet outil peut désinstaller les versions du .NET Core SDK et le temps d’exécution sur lequel Visual Studio s’appuie. Si vous cassez votre installation Visual Studio, exécutez "Repair" dans l’installateur Visual Studio pour revenir à un état de travail.

Par défaut, toutes les commandes conservent les SDKs et les temps d’exécution .NET Core qui peuvent être requis par Visual Studio ou d’autres SDK. Ces SDK et runtimes peuvent être désinstallés en `--force` les énumérant explicitement comme arguments ou en utilisant l’option.

L’outil nécessite l’élévation pour désinstaller .NET Core SDKs et les temps d’exécution. Exécutez l’outil dans une invite `sudo` de commande d’administrateur sur Windows et avec sur macOS. L’élévation `dry-run` et `whatif` les commandes ne nécessitent pas d’élévation.

**dotnet-core-uninstall supprimer**

#### <a name="synopsis"></a>Synopsis

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a>Arguments

* **`VERSION`**

  La version spécifiée pour désinstaller. Vous pouvez énumérer plusieurs versions l’une après l’autre, séparées par des espaces. Les fichiers de réponse sont également pris en charge.

  > [!TIP]
  > Les fichiers de réponse sont une alternative à la mise en place de toutes les versions sur la ligne de commande.
  > Ce sont des fichiers texte, généralement avec une \*extension .rsp, et chaque version est répertoriée sur une ligne séparée.
  > Pour spécifier `VERSION` un fichier \@ de réponse pour l’argument, utilisez le personnage immédiatement suivi du nom du fichier de réponse.

#### <a name="options"></a>Options

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Supprime tous les SDKs et les temps d’exécution .NET Core.

* **`--all-below <VERSION>`**

  Supprime uniquement les SDKs core .NET et les temps d’exécution avec une version plus petite que la version spécifiée. La version spécifiée reste installée.

* **`--all-but <VERSIONS>`**

  Supprime tous les SDK core .NET et les durées d’exécution, à l’exception de celles spécifiées.

* **`--all-but-latest`**

  Supprime .NET Core SDKs et runtimes, sauf la version la plus élevée.

* **`--all-lower-patches`**

  Supprime les SDK core .NET et les temps d’exécution remplacés par des correctifs plus élevés. Cette option protège global.json.

* **`--all-previews`**

  Supprime les SDK core .NET et les temps d’exécution marqués comme aperçus.

* **`--all-previews-but-latest`**

  Supprime .NET Core SDKs et runtimes marqués comme aperçus, sauf l’aperçu le plus élevé.

* **`--aspnet-runtime`**

  Supprime ASP.NET les temps d’exécution Core seulement.

* **`--hosting-bundle`**

  Supprime le temps d’exécution .NET Core et l’hébergement des faisceaux seulement.

* **`--major-minor <MAJOR_MINOR>`**

  Supprime .NET Core SDKs et runtimes `major.minor` qui correspondent à la version spécifiée.

* **`--runtime`**

  Supprime les temps d’exécution .NET Core seulement.

* **`--sdk`**

  Supprime .NET Core SDKs seulement.

* **`-v, --verbosity <LEVEL>`**

  Définit le niveau de verbosité. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `normal`.

* **`--x64`**

  Doit être `--sdk`utilisé `--runtime`avec `--aspnet-runtime` , , et pour supprimer x64 SDKs ou runtimes.

* **`--x86`**

  Doit être `--sdk`utilisé `--runtime`avec `--aspnet-runtime` , , et pour supprimer x86 SDKs ou runtimes.

* **`-y, --yes`** Exécutez la commande sans nécessiter de confirmation oui ou non.

* **`--force`** Force le retrait des versions qui pourraient être utilisées par Visual Studio.

Remarques :

1. Exactement un `--sdk` `--runtime`de `--aspnet-runtime`, `--hosting-bundle` , , et est nécessaire.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , et sont exclusifs.
3. Si `--x64` `--x86` ou ne sont pas spécifiés, alors x64 et x86 seront supprimés.

## <a name="macos"></a>[macOS](#tab/macos)

* **`--all`**

  Supprime tous les SDKs et les temps d’exécution .NET Core.

* **`--all-below <VERSION>`**

  Supprime les SDK core .NET et les temps d’exécution en dessous de la version spécifiée. La version spécifiée restera.

* **`--all-but <VERSIONS>`**

  Supprime .NET Core SDKs et runtimes, sauf les versions spécifiées.

* **`--all-but-latest`**

  Supprime .NET Core SDKs et runtimes, sauf la version la plus élevée.

* **`--all-lower-patches`**

  Supprime les SDK core .NET et les temps d’exécution remplacés par des correctifs plus élevés. Cette option protège global.json.

* **`--all-previews`**

  Supprime les SDK core .NET et les temps d’exécution marqués comme aperçus.

* **`--all-previews-but-latest`**

  Supprime .NET Core SDKs et runtimes marqués comme aperçus, sauf l’aperçu le plus élevé.

* **`--major-minor <MAJOR_MINOR>`**

  Supprime .NET Core SDKs et runtimes `major.minor` qui correspondent à la version spécifiée.

* **`--runtime`**

  Supprime les temps d’exécution .NET Core seulement.

* **`--sdk`**

  Supprime .NET Core SDKs seulement.

* **`-v, --verbosity <LEVEL>`**

  Définit le niveau de verbosité. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `normal`.

* **`-y, --yes`** Exécutez la commande sans nécessiter la confirmation de Y/N.
  
* **`--force`** Force le retrait des versions qui pourraient être utilisées par Visual Studio ou SDKs.

Remarques :

1. Exactement un `--sdk` `--runtime` de et est nécessaire.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , et sont exclusifs.

---

#### <a name="examples"></a>Exemples

> [!NOTE]
> Par défaut, les SDK core .NET et les temps d’exécution qui peuvent être requis par Visual Studio ou d’autres SDK sont conservés. Dans les exemples suivants, certains des SDK spécifiés et les temps d’exécution peuvent rester, selon l’état de la machine. Pour supprimer tous les SDK et les temps d’exécution, les énumérer explicitement comme arguments ou utiliser l’option. `--force`

* Supprimer tous les temps d’exécution `3.0.0-preview6-27804-01` .NET Core sauf la version sans nécessiter la confirmation Y/N:

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* Supprimer tous les SDK .NET Core 1.1 sans avoir besoin d’une confirmation Y/n :

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* Supprimer le .NET Core 1.1.11 SDK sans sortie console:

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* Supprimer tous les SDK de base .NET qui peuvent être retirés en toute sécurité par cet outil :

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* Supprimer tous les SDK de base .NET qui peuvent être supprimés par cet outil, y compris les SDK qui peuvent être requis par Visual Studio (non recommandé) :

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* Supprimer tous les SDK core .NET qui sont spécifiés dans le fichier de réponse`versions.rsp`

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  Le contenu de *versions.rsp* est le suivant:
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a>Étape 4 - Supprimer le dossier de repli NuGet (facultatif)

Dans certains cas, vous `NuGetFallbackFolder` n’avez plus besoin de la et peut vouloir le supprimer. Pour plus d’informations sur la suppression de ce dossier, voir [Supprimer le NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).

## <a name="uninstall-the-tool"></a>Désinstaller l’outil

## <a name="windows"></a>[Windows](#tab/windows)

1. Ouvrez la boîte de dialogue **Ajout/Suppression de programmes**.
2. Recherchez `Microsoft .NET Core SDK Uninstall Tool`.
3. Sélectionner **Désinstaller**.

## <a name="macos"></a>[macOS](#tab/macos)

Supprimer le fichier *dotnet-core-uninstall.tar.gz* téléchargé de l’annuaire où il a été installé. Si vous avez décompressé le contenu de ce fichier dans un autre répertoire, assurez-vous de supprimer ce contenu ainsi.

---
