---
ms.openlocfilehash: fb78e1439a680a8dbb9fc0eb8afdeee3efef7ead
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768393"
---

Les [scripts dotnet-install](../../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du **Kit de développement logiciel (SDK)** et du **Runtime**. Vous pouvez télécharger le script depuis <https://dot.net/v1/dotnet-install.sh>.

Par défaut, le script installe la version la plus récente du kit de développement logiciel [(SDK) LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1. Pour installer la version actuelle, qui ne peut pas être une version (LTS), utilisez le `-c Current` paramètre.

```bash
./dotnet-install.sh -c Current
```

Pour installer le Runtime .NET Core au lieu du kit de développement logiciel (SDK), utilisez le `--runtime` paramètre.

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

Vous pouvez installer une version spécifique en modifiant le `-c` paramètre pour indiquer la version spécifique. La commande suivante installe kit SDK .NET Core 3,1.

```bash
./dotnet-install.sh -c 3.1
```

Pour plus d’informations, consultez informations de référence sur les [scripts dotnet-install](../../tools/dotnet-install-script.md).
