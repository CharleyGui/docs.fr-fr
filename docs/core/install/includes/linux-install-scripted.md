---
ms.openlocfilehash: 07dd58c314c826c426193b829ea1f64669fb888b
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594569"
---

Les [scripts dotnet-install](../../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du **Kit de développement logiciel (SDK)** et du **Runtime**. Vous pouvez télécharger le script depuis <https://dot.net/v1/dotnet-install.sh>.

Par défaut, le script installe la version la plus récente du kit de développement logiciel [(SDK) LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net 3,1. Pour installer la version actuelle, qui ne peut pas être une version (LTS), utilisez le `-c Current` paramètre.

```bash
./dotnet-install.sh -c Current
```

Pour installer le Runtime .NET au lieu du kit de développement logiciel (SDK), utilisez le `--runtime` paramètre.

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

Vous pouvez installer une version spécifique en modifiant le `-c` paramètre pour indiquer la version spécifique. La commande suivante installe le kit de développement logiciel (SDK) .NET 5,0.

```bash
./dotnet-install.sh -c 5.0
```

Pour plus d’informations, consultez informations de référence sur les [scripts dotnet-install](../../tools/dotnet-install-script.md).
