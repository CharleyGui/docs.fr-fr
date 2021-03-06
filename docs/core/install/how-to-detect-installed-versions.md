---
title: Vérifier les versions installées de .NET sur Windows, Linux et macOS-.NET
description: Découvrez comment répertorier les versions de .NET qui sont installées sur votre ordinateur. Cela comprend le Runtime .NET et le kit de développement logiciel (SDK).
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 2fc12c8c398b1a74d623e53884df666f4d4b85f1
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851612"
---
# <a name="how-to-check-that-net-is-already-installed"></a>Comment vérifier que .NET est déjà installé

Cet article explique comment vérifier quelles versions du Runtime .NET et du kit de développement logiciel (SDK) sont installées sur votre ordinateur. Si vous disposez d’un environnement de développement intégré, tel que Visual Studio ou Visual Studio pour Mac, .NET a peut-être déjà été installé.

L’installation d’un kit de développement logiciel installe le runtime correspondant.

En cas d’échec d’une commande de cet article, le runtime ou le kit de développement logiciel (SDK) n’est pas installé. Pour plus d’informations, consultez les articles installer pour [Windows](windows.md), [MacOS](macos.md)ou [Linux](linux.md).

## <a name="check-sdk-versions"></a>Vérifier les versions du SDK

Vous pouvez voir les versions du kit de développement logiciel (SDK) .NET actuellement installées avec un terminal. Ouvrez un terminal et exécutez la commande suivante.

```dotnetcli
dotnet --list-sdks
```

Vous recevez une sortie similaire à ce qui suit.

::: zone pivot="os-windows"

```console
2.1.500 [C:\program files\dotnet\sdk]
2.1.502 [C:\program files\dotnet\sdk]
2.1.504 [C:\program files\dotnet\sdk]
2.1.600 [C:\program files\dotnet\sdk]
2.1.602 [C:\program files\dotnet\sdk]
3.1.100 [C:\program files\dotnet\sdk]
5.0.100 [C:\program files\dotnet\sdk]
```

::: zone-end

::: zone pivot="os-linux"

```bash
2.1.500 [/home/user/dotnet/sdk]
2.1.502 [/home/user/dotnet/sdk]
2.1.504 [/home/user/dotnet/sdk]
2.1.600 [/home/user/dotnet/sdk]
2.1.602 [/home/user/dotnet/sdk]
3.1.100 [/home/user/dotnet/sdk]
5.0.100 [/home/user/dotnet/sdk]
```

::: zone-end

::: zone pivot="os-macos"

```bash
2.1.500 [/usr/local/share/dotnet/sdk]
2.1.502 [/usr/local/share/dotnet/sdk]
2.1.504 [/usr/local/share/dotnet/sdk]
2.1.600 [/usr/local/share/dotnet/sdk]
2.1.602 [/usr/local/share/dotnet/sdk]
3.1.100 [/usr/local/share/dotnet/sdk]
5.0.100 [/usr/local/share/dotnet/sdk]
```

::: zone-end

## <a name="check-runtime-versions"></a>Vérifier les versions du Runtime

Vous pouvez voir quelles versions du Runtime .NET sont actuellement installées avec la commande suivante.

```dotnetcli
dotnet --list-runtimes
```

Vous recevez une sortie similaire à ce qui suit.

::: zone pivot="os-windows"

```console
Microsoft.AspNetCore.All 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.WindowsDesktop.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
```

::: zone-end

::: zone pivot="os-linux"

```bash
Microsoft.AspNetCore.All 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

::: zone pivot="os-macos"

```bash
Microsoft.AspNetCore.All 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

## <a name="check-for-install-folders"></a>Rechercher les dossiers d’installation

Il est possible que .NET soit installé mais pas ajouté à la `PATH` variable pour votre système d’exploitation ou profil utilisateur. Dans ce cas, les commandes des sections précédentes peuvent ne pas fonctionner. Vous pouvez également vérifier que les dossiers d’installation .NET existent.

Lorsque vous installez .NET à partir d’un programme d’installation ou d’un script, il est installé dans un dossier standard. La plupart du temps, le programme d’installation ou le script que vous utilisez pour installer .NET vous donne la possibilité d’installer dans un autre dossier. Si vous choisissez d’installer dans un autre dossier, ajustez le début du chemin d’accès au dossier.

::: zone pivot="os-windows"

- **fichier exécutable dotnet**\
_C : \\ Program Files \\ dotnet \\dotnet.exe_

- **SDK .NET**\
_C : \\ Program Files \\ dotnet \\ SDK \\ {version}\\_

- **Runtime .NET**\
_C : \\ Program Files \\ dotnet \\ Shared \\ {Runtime-type} \\ {version}\\_

::: zone-end

::: zone pivot="os-linux"

- **fichier exécutable dotnet**\
_/home/user/share/dotnet/dotnet_

- **SDK .NET**\
_/home/user/share/dotnet/sdk/{version}/_

- **Runtime .NET**\
_/home/user/share/dotnet/shared/{runtime-type}/{version}/_

::: zone-end

::: zone pivot="os-macos"

- **fichier exécutable dotnet**\
_/usr/local/share/dotnet/dotnet_

- **SDK .NET**\
_/usr/local/share/dotnet/sdk/{version}/_

- **Runtime .NET**\
_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_

::: zone-end

## <a name="more-information"></a>Plus d’informations

Vous pouvez voir les versions du kit de développement logiciel (SDK) et les versions du runtime à l’aide de la commande `dotnet --info` . Vous obtiendrez également d’autres informations relatives à l’environnement, telles que la version du système d’exploitation et l’identificateur de Runtime (RID).

## <a name="next-steps"></a>Étapes suivantes

- [Installez le Runtime .net et le kit de développement logiciel (SDK) pour Windows](windows.md).
- [Installez le Runtime .net et le kit de développement logiciel (SDK) pour MacOS](macos.md).
- [Installez le Runtime .net et le kit de développement logiciel (SDK) pour Linux](linux.md).

## <a name="see-also"></a>Voir aussi

- [Identifier les versions de .NET Framework installées](../../framework/migration-guide/how-to-determine-which-versions-are-installed.md)
