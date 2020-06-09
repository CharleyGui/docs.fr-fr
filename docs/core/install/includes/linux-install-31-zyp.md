---
ms.openlocfilehash: db89539982c1afe0df374027d54826f3265f0fee
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603012"
---

### <a name="install-the-sdk"></a>Installer le Kit de développement logiciel (SDK)

Le kit SDK .NET Core vous permet de développer des applications avec .NET Core. Pour installer le kit SDK .NET Core, exécutez les commandes suivantes.

```bash
sudo zypper install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a>Installer le runtime

Le Runtime .NET Core vous permet d’exécuter des applications qui ont été créées avec .NET Core et qui ne comportent pas le Runtime. Les commandes ci-dessous installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET Core. Dans votre terminal, exécutez les commandes suivantes.

```bash
sudo zypper install aspnetcore-runtime-3.1
```

Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET Core qui n’inclut pas ASP.NET Core prise en charge : replace `aspnetcore-runtime-2.1` dans la commande ci-dessus avec `dotnet-runtime-3.1` .

```bash
sudo zypper install dotnet-runtime-3.1
```
