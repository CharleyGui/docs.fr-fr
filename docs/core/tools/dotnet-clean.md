---
title: Commande dotnet clean
description: La commande dotnet clean nettoie le répertoire actif.
ms.date: 02/14/2020
ms.openlocfilehash: 1023f13c7662abb7dad613128631c7644ca15bb9
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189601"
---
# <a name="dotnet-clean"></a>dotnet clean

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures

## <a name="name"></a>Name

`dotnet clean` : Nettoie la sortie d’un projet.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--interactive]
    [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-v|--verbosity <LEVEL>]

dotnet clean -h|--help
```

## <a name="description"></a>Description

La commande `dotnet clean` nettoie la sortie de la génération précédente. Comme elle est implémentée en tant que [cible MSBuild](/visualstudio/msbuild/msbuild-targets), le projet est évalué lorsque la commande est exécutée. Seules les sorties créées lors de la génération sont nettoyées. Les dossiers de sortie intermédiaire (*obj*) et de sortie finale (*bin*) sont tous deux nettoyés.

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Projet ou solution MSBuild à nettoyer. Si vous ne spécifiez pas de fichier projet ou solution, MSBuild recherche dans le répertoire de travail actif un fichier dont l’extension se termine par *proj* ou *sln* et l’utilise.

## <a name="options"></a>Options

* **`-c|--configuration <CONFIGURATION>`**

  Définit la configuration de build. La valeur par défaut pour la plupart des projets est `Debug` , mais vous pouvez remplacer les paramètres de configuration de build dans votre projet. Cette option est uniquement requise durant le nettoyage si vous l’avez spécifiée au moment de la génération.

* **`-f|--framework <FRAMEWORK>`**

  Le [framework](../../standard/frameworks.md) spécifié au moment de la génération. Le framework doit être défini dans le [fichier projet](../project-sdk/overview.md). Si vous avez spécifié le framework au moment de la génération, vous devez spécifier le framework lors du nettoyage.

* **`-h|--help`**

  Affiche une aide brève pour la commande.

* **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur. Par exemple, pour effectuer une authentification. Option disponible à partir du kit SDK .NET Core 3.0.

* **`--nologo`**

  N’affiche pas la bannière de démarrage ni le message de copyright. Option disponible à partir du kit SDK .NET Core 3.0.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Répertoire contenant les artefacts de build à nettoyer. Spécifiez le commutateur `-f|--framework <FRAMEWORK>` avec le commutateur de répertoire de sortie si vous avez spécifié le framework lorsque le projet a été généré.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Nettoie le dossier de sortie du runtime spécifié. Cette option est utilisée à la création d’un [déploiement autonome](../deploying/index.md#publish-self-contained).

* **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail MSBuild. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `normal`.

## <a name="examples"></a>Exemples

* Nettoyez une génération par défaut du projet :

  ```dotnetcli
  dotnet clean
  ```

* Nettoyez un projet généré à l’aide de la configuration Release :

  ```dotnetcli
  dotnet clean --configuration Release
  ```
