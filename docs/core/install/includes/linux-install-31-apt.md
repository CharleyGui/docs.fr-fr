---
ms.openlocfilehash: cac1fbd2369277b3a322247a7008f07929502437
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507015"
---

### <a name="install-the-sdk"></a>Installer le SDK

Le kit SDK .NET Core vous permet de développer des applications avec .NET Core. Si vous installez le kit SDK .NET Core, vous n’avez pas besoin d’installer le runtime correspondant. Pour installer le kit SDK .NET Core, exécutez les commandes suivantes :

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-3.1
```

> [!IMPORTANT]
> Si vous recevez un message d’erreur semblable à **incapable de localiser le package dotnet-SDK-3,1** , consultez la section de [résolution des problèmes de apt](#apt-troubleshooting) .

### <a name="install-the-runtime"></a>Installer le runtime

Le Runtime .NET Core vous permet d’exécuter des applications qui ont été créées avec .NET Core et qui ne comportent pas le Runtime. Les commandes suivantes installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET Core. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> Si vous recevez un message d’erreur semblable à **incapable de localiser le package aspnetcore-Runtime-3,1** , consultez la section de [résolution des problèmes de apt](#apt-troubleshooting) .

Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET Core, qui n’inclut pas ASP.NET Core prise en charge : remplacez `aspnetcore-runtime-3.1` dans la commande précédente par `dotnet-runtime-3.1` .

```bash
sudo apt-get install -y dotnet-runtime-3.1
```
