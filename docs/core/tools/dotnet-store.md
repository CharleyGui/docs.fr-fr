---
title: Commande dotnet store
description: La commande « dotnet store » stocke les assemblys spécifiés dans le magasin de packages de runtime.
ms.date: 05/29/2018
ms.openlocfilehash: cc5b4b6160ba296e1529f006c15e238746d9e08a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733052"
---
# <a name="dotnet-store"></a>dotnet store

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>Name

`dotnet store` : stocke les assemblys spécifiés dans le [magasin de packages de runtime](../deploying/runtime-store.md).

## <a name="synopsis"></a>Résumé

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a>Description

`dotnet store` stocke les assemblys spécifiés dans le [magasin de packages de runtime](../deploying/runtime-store.md). Par défaut, les assemblys sont optimisés pour les runtime et framework cibles. Pour plus d’informations, consultez la rubrique [Magasin de packages de runtime](../deploying/runtime-store.md).

## <a name="required-options"></a>Options obligatoires

`-f|--framework <FRAMEWORK>`

Spécifie le [framework cible](../../standard/frameworks.md).

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

Le *fichier manifeste du magasin de packages* est un fichier XML qui contient la liste des packages à stocker. Le format du fichier manifeste est compatible avec celui du projet de style SDK. Ainsi, vous pouvez utiliser un fichier projet qui référence les packages souhaités avec l’option `-m|--manifest` pour stocker des assemblys dans le magasin de packages de runtime. Pour spécifier plusieurs fichiers manifeste, répétez l’option et le chemin pour chaque fichier. Par exemple : `--manifest packages1.csproj --manifest packages2.csproj`.

`-r|--runtime <RUNTIME_IDENTIFIER>`

[Identificateur du runtime](../rid-catalog.md) à cibler.

## <a name="optional-options"></a>Options facultatives

`--framework-version <FRAMEWORK_VERSION>`

Spécifie la version du SDK .NET Core. Cette option vous permet de sélectionner une version de framework spécifique en plus du framework indiqué par l’option `-f|--framework`.

`-h|--help`

Affiche des informations d’aide.

`-o|--output <OUTPUT_DIRECTORY>`

Spécifie le chemin du magasin de packages de runtime. Si ce chemin n’est pas spécifié, le sous-répertoire *store* du répertoire d’installation de .NET Core du profil de l’utilisateur est choisi par défaut.

`--skip-optimization`

Ignore la phase d’optimisation.

`--skip-symbols`

Ignore la génération de symboles. Vous pouvez uniquement générer des symboles sur Windows et Linux.

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

Répertoire de travail utilisé par la commande. S’il n’est pas spécifié, il utilise le sous-répertoire *obj* du répertoire actuel.

## <a name="examples"></a>Exemples

Stocker les packages spécifiés dans le fichier projet *packages.csproj* pour .NET Core 2.0.0 :

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

Stocker les packages spécifiés dans le fichier projet *packages.csproj* sans optimisation :

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a>Voir aussi

- [Magasin de packages de runtime](../deploying/runtime-store.md)
