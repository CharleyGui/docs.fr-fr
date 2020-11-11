---
ms.openlocfilehash: ed269683f5c4569c21ae53e9a3c1ec65eb5ebd43
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506850"
---

### <a name="install-the-sdk"></a>Installer le SDK

Le kit de développement logiciel (SDK) .NET vous permet de développer des applications avec .NET. Si vous installez le kit de développement logiciel (SDK) .NET, vous n’avez pas besoin d’installer le runtime correspondant. Pour installer le kit de développement logiciel (SDK) .NET, exécutez les commandes suivantes :

```bash
sudo zypper install dotnet-sdk-5.0
```

### <a name="install-the-runtime"></a>Installer le runtime

Le runtime ASP.NET Core vous permet d’exécuter des applications qui ont été créées avec .NET et qui n’ont pas fourni le Runtime. Les commandes suivantes installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET. Sur votre terminal, exécutez les commandes suivantes :

```bash
sudo zypper install aspnetcore-runtime-5.0
```

Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET, qui n’inclut pas ASP.NET Core prise en charge : remplacer `aspnetcore-runtime-5.0` dans la commande précédente par `dotnet-runtime-5.0` :

```bash
sudo zypper install dotnet-runtime-5.0
```
