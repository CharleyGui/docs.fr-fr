---
title: Commande dotnet clean
description: La commande dotnet clean nettoie le répertoire actif.
ms.date: 06/26/2019
ms.openlocfilehash: 113bc076b9f14a471c631801fe4a7cb1e044a411
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168058"
---
# <a name="dotnet-clean"></a>dotnet clean

**Cette rubrique s’applique à : ✓** SDK .NET Core 1.x et ultérieur

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet clean` : Nettoie la sortie d’un projet.

## <a name="synopsis"></a>Résumé

```console
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive] 
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a>Description

La commande `dotnet clean` nettoie la sortie de la génération précédente. Comme elle est implémentée en tant que [cible MSBuild](/visualstudio/msbuild/msbuild-targets), le projet est évalué lorsque la commande est exécutée. Seules les sorties créées lors de la génération sont nettoyées. Les dossiers de sortie intermédiaire (*obj*) et de sortie finale (*bin*) sont tous deux nettoyés.

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Projet ou solution MSBuild à nettoyer. Si vous ne spécifiez pas de fichier projet ou solution, MSBuild recherche dans le répertoire de travail actif un fichier dont l’extension se termine par *proj* ou *sln* et l’utilise.

## <a name="options"></a>Options

* **`-c|--configuration {Debug|Release}`**

  Définit la configuration de build. La valeur par défaut est `Debug`. Cette option est uniquement requise durant le nettoyage si vous l’avez spécifiée au moment de la génération.

* **`-f|--framework <FRAMEWORK>`**

  Le [framework](../../standard/frameworks.md) spécifié au moment de la génération. Le framework doit être défini dans le [fichier projet](csproj.md). Si vous avez spécifié le framework au moment de la génération, vous devez spécifier le framework lors du nettoyage.

* **`-h|--help`**

  Affiche une aide brève pour la commande.

* **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur. Par exemple, pour effectuer une authentification. Option disponible à partir du kit SDK .NET Core 3.0.

* **`--nologo`**

  N’affiche pas la bannière de démarrage ni le message de copyright. Option disponible à partir du kit SDK .NET Core 3.0.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Répertoire contenant les artefacts de build à nettoyer. Spécifiez le commutateur `-f|--framework <FRAMEWORK>` avec le commutateur de répertoire de sortie si vous avez spécifié le framework lorsque le projet a été généré.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Nettoie le dossier de sortie du runtime spécifié. Cette option est utilisée à la création d’un [déploiement autonome](../deploying/index.md#self-contained-deployments-scd). Option disponible à partir du kit SDK .NET Core 2.0.

* **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail MSBuild. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `normal`.

## <a name="examples"></a>Exemples

* Nettoyez une génération par défaut du projet :

  ```console
  dotnet clean
  ```

* Nettoyez un projet généré à l’aide de la configuration Release :

  ```console
  dotnet clean --configuration Release
  ```
