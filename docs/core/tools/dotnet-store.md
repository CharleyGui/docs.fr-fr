---
title: Commande dotnet store
description: La commande « dotnet store » stocke les assemblys spécifiés dans le magasin de packages de runtime.
ms.date: 02/14/2020
ms.openlocfilehash: da1d132b2b873ff55ec104b5bb092d0194889bdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503582"
---
# <a name="dotnet-store"></a>dotnet store

**Cet article s’applique à:** ✔️ .NET Core 2.x SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet store` : stocke les assemblys spécifiés dans le [magasin de packages de runtime](../deploying/runtime-store.md).

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]
```

## <a name="description"></a>Description

`dotnet store` stocke les assemblys spécifiés dans le [magasin de packages de runtime](../deploying/runtime-store.md). Par défaut, les assemblys sont optimisés pour les runtime et framework cibles. Pour plus d’informations, consultez la rubrique [Magasin de packages de runtime](../deploying/runtime-store.md).

## <a name="required-options"></a>Options obligatoires

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [framework cible](../../standard/frameworks.md). Le framework cible doit être spécifié dans le fichier projet.

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  Le *fichier manifeste du magasin de packages* est un fichier XML qui contient la liste des packages à stocker. Le format du fichier manifeste est compatible avec celui du projet de style SDK. Ainsi, vous pouvez utiliser un fichier projet qui référence les packages souhaités avec l’option `-m|--manifest` pour stocker des assemblys dans le magasin de packages de runtime. Pour spécifier plusieurs fichiers manifeste, répétez l’option et le chemin pour chaque fichier. Par exemple : `--manifest packages1.csproj --manifest packages2.csproj`.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  [L’identifiant de temps d’exécution](../rid-catalog.md) à cibler.

## <a name="optional-options"></a>Options facultatives

- **`--framework-version <FRAMEWORK_VERSION>`**

  Spécifie la version du SDK .NET Core. Cette option vous permet de sélectionner une version de framework spécifique en plus du framework indiqué par l’option `-f|--framework`.

- **`-h|--help`**

  Affiche des informations d’aide.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Spécifie le chemin du magasin de packages de runtime. Si ce chemin n’est pas spécifié, le sous-répertoire *store* du répertoire d’installation de .NET Core du profil de l’utilisateur est choisi par défaut.

- **`--skip-optimization`**

  Ignore la phase d’optimisation.

- **`--skip-symbols`**

  Ignore la génération de symboles. Vous pouvez uniquement générer des symboles sur Windows et Linux.

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  Répertoire de travail utilisé par la commande. S’il n’est pas spécifié, il utilise le sous-répertoire *obj* du répertoire actuel.

## <a name="examples"></a>Exemples

- Stocker les packages spécifiés dans le fichier projet *packages.csproj* pour .NET Core 2.0.0 :

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- Stocker les packages spécifiés dans le fichier projet *packages.csproj* sans optimisation :

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a>Voir aussi

- [Magasin de packages de runtime](../deploying/runtime-store.md)
