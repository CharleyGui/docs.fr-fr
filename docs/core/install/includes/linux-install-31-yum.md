---
ms.openlocfilehash: b8a1454dba1651911563557557cfddc38de24375
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93136302"
---

### <a name="install-the-sdk"></a>Installer le Kit de développement logiciel (SDK)

Kit SDK .NET Core vous permet de développer des applications avec .NET Core. Si vous installez kit SDK .NET Core, vous n’avez pas besoin d’installer le runtime correspondant. Pour installer kit SDK .NET Core, exécutez les commandes suivantes :

```bash
sudo yum install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a>Installer le runtime

Le Runtime .NET Core vous permet d’exécuter des applications qui ont été créées avec .NET Core et qui ne comportent pas le Runtime. Les commandes suivantes installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET Core. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo yum install aspnetcore-runtime-3.1
```

Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET Core qui n’inclut pas ASP.NET Core prise en charge : remplacez `aspnetcore-runtime-2.1` dans la commande précédente par `dotnet-runtime-3.1` .

```bash
sudo yum install dotnet-runtime-3.1
```
