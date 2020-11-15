---
title: Commande dotnet store
description: La commande « dotnet store » stocke les assemblys spécifiés dans le magasin de packages de runtime.
ms.date: 02/14/2020
ms.openlocfilehash: 8efb11c6bf648bc7787d5627e02b180abb8a0afd
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634335"
---
# <a name="dotnet-store"></a>dotnet store

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures

## <a name="name"></a>Name

`dotnet store` : stocke les assemblys spécifiés dans le [magasin de packages de runtime](../deploying/runtime-store.md).

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet store -m|--manifest <PATH_TO_MANIFEST_FILE>
    -f|--framework <FRAMEWORK_VERSION> -r|--runtime <RUNTIME_IDENTIFIER>
    [--framework-version <FRAMEWORK_VERSION>] [--output <OUTPUT_DIRECTORY>]
    [--skip-optimization] [--skip-symbols] [-v|--verbosity <LEVEL>]
    [--working-dir <WORKING_DIRECTORY>]

dotnet store -h|--help
```

## <a name="description"></a>Description

`dotnet store` stocke les assemblys spécifiés dans le [magasin de packages de runtime](../deploying/runtime-store.md). Par défaut, les assemblys sont optimisés pour les runtime et framework cibles. Pour plus d’informations, consultez la rubrique [Magasin de packages de runtime](../deploying/runtime-store.md).

## <a name="required-options"></a>Options obligatoires

- **`-f|--framework <FRAMEWORK>`**

  Spécifie le [framework cible](../../standard/frameworks.md). Le framework cible doit être spécifié dans le fichier projet.

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  Le *fichier manifeste du magasin de packages* est un fichier XML qui contient la liste des packages à stocker. Le format du fichier manifeste est compatible avec celui du projet de style SDK. Ainsi, vous pouvez utiliser un fichier projet qui référence les packages souhaités avec l’option `-m|--manifest` pour stocker des assemblys dans le magasin de packages de runtime. Pour spécifier plusieurs fichiers manifeste, répétez l’option et le chemin pour chaque fichier. Par exemple : `--manifest packages1.csproj --manifest packages2.csproj`.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  [Identificateur du runtime](../rid-catalog.md) à cibler.

## <a name="optional-options"></a>Options facultatives

- **`--framework-version <FRAMEWORK_VERSION>`**

  Spécifie la version du kit de développement logiciel (SDK) .NET. Cette option vous permet de sélectionner une version de framework spécifique en plus du framework indiqué par l’option `-f|--framework`.

- **`-h|--help`**

  Affiche des informations d’aide.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Spécifie le chemin du magasin de packages de runtime. S’il n’est pas spécifié, le sous-répertoire *Store* du répertoire d’installation .net du profil utilisateur est utilisé par défaut.

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
