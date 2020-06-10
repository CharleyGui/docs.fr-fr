---
ms.openlocfilehash: 164d7a8277cf985735b959c73eb87391944e795b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602900"
---

### <a name="install-the-sdk"></a>Installer le Kit de développement logiciel (SDK)

Kit SDK .NET Core vous permet de développer des applications avec .NET Core. Si vous installez kit SDK .NET Core, vous n’avez pas besoin d’installer le runtime correspondant. Pour installer kit SDK .NET Core, exécutez les commandes suivantes :

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-2.1
```

> [!IMPORTANT]
> Si vous recevez un message d’erreur semblable à **incapable de localiser le package dotnet-SDK-2,1**, consultez la section de [résolution des problèmes de apt](#apt-troubleshooting) .

### <a name="install-the-runtime"></a>Installer le runtime

Le Runtime .NET Core vous permet d’exécuter des applications qui ont été créées avec .NET Core et qui ne comportent pas le Runtime. Les commandes ci-dessous installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET Core. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-2.1
```

> [!IMPORTANT]
> Si vous recevez un message d’erreur semblable à **incapable de localiser le package aspnetcore-Runtime-2,1**, consultez la section de [résolution des problèmes de apt](#apt-troubleshooting) .

Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET Core qui n’inclut pas ASP.NET Core prise en charge : replace `aspnetcore-runtime-2.1` dans la commande ci-dessus avec `dotnet-runtime-2.1` .

```bash
sudo apt-get install -y dotnet-runtime-2.1
```
