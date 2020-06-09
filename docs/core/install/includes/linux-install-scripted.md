---
ms.openlocfilehash: 0d29407896145bc3b2ed8284c839ae8f2f0521b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602949"
---

Les [scripts dotnet-install](../../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du **Kit de développement logiciel (SDK)**. Vous pouvez télécharger le script depuis <https://dot.net/v1/dotnet-install.sh>.

Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1. Pour installer la version actuelle, qui ne peut pas être une version (LTS), utilisez le `-c Current` paramètre.

```bash
./dotnet-install.sh -c Current
```

Pour installer le Runtime .NET Core au lieu du kit de développement logiciel (SDK), utilisez le `--runtime` paramètre.

```bash
./dotnet-install.sh -c Current --runtime
```

Vous pouvez installer une version spécifique en modifiant le `-c` paramètre pour indiquer la version spécifique. La commande suivante installe kit SDK .NET Core 3,1.

```bash
./dotnet-install.sh -c 3.1
```

Pour plus d’informations, consultez informations de référence sur les [scripts dotnet-install](../../tools/dotnet-install-script.md).
