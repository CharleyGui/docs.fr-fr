---
ms.openlocfilehash: bd0953697ee3a9e928d09c1f270a4af5606ee0d9
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507056"
---

### <a name="install-the-sdk"></a>Installer le SDK

Le kit SDK .NET Core vous permet de développer des applications avec .NET Core. Si vous installez le kit SDK .NET Core, vous n’avez pas besoin d’installer le runtime correspondant. Pour installer le kit SDK .NET Core, exécutez les commandes suivantes :

```bash
sudo dnf install dotnet-sdk-2.0
```

### <a name="install-the-runtime"></a>Installer le runtime

Le Runtime .NET Core vous permet d’exécuter des applications qui ont été créées avec .NET Core et qui ne comportent pas le Runtime. Les commandes suivantes installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET Core. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo dnf install aspnetcore-runtime-2.0
```

Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET Core, qui n’inclut pas ASP.NET Core prise en charge : remplacez `aspnetcore-runtime-2.0` dans la commande précédente par `dotnet-runtime-2.0` .

```bash
sudo dnf install dotnet-runtime-2.0
```
