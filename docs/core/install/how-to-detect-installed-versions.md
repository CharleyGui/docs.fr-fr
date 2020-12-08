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
# <a name="how-to-check-that-net-is-already-installed"></a><span data-ttu-id="21a0b-104">Comment vérifier que .NET est déjà installé</span><span class="sxs-lookup"><span data-stu-id="21a0b-104">How to check that .NET is already installed</span></span>

<span data-ttu-id="21a0b-105">Cet article explique comment vérifier quelles versions du Runtime .NET et du kit de développement logiciel (SDK) sont installées sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="21a0b-105">This article teaches you how to check which versions of the .NET runtime and SDK are installed on your computer.</span></span> <span data-ttu-id="21a0b-106">Si vous disposez d’un environnement de développement intégré, tel que Visual Studio ou Visual Studio pour Mac, .NET a peut-être déjà été installé.</span><span class="sxs-lookup"><span data-stu-id="21a0b-106">If you have an integrated development environment, such as Visual Studio or Visual Studio for Mac, .NET may have already been installed.</span></span>

<span data-ttu-id="21a0b-107">L’installation d’un kit de développement logiciel installe le runtime correspondant.</span><span class="sxs-lookup"><span data-stu-id="21a0b-107">Installing an SDK installs the corresponding runtime.</span></span>

<span data-ttu-id="21a0b-108">En cas d’échec d’une commande de cet article, le runtime ou le kit de développement logiciel (SDK) n’est pas installé.</span><span class="sxs-lookup"><span data-stu-id="21a0b-108">If any command in this article fails, you don't have the runtime or SDK installed.</span></span> <span data-ttu-id="21a0b-109">Pour plus d’informations, consultez les articles installer pour [Windows](windows.md), [MacOS](macos.md)ou [Linux](linux.md).</span><span class="sxs-lookup"><span data-stu-id="21a0b-109">For more information, see the install articles for [Windows](windows.md), [macOS](macos.md), or [Linux](linux.md).</span></span>

## <a name="check-sdk-versions"></a><span data-ttu-id="21a0b-110">Vérifier les versions du SDK</span><span class="sxs-lookup"><span data-stu-id="21a0b-110">Check SDK versions</span></span>

<span data-ttu-id="21a0b-111">Vous pouvez voir les versions du kit de développement logiciel (SDK) .NET actuellement installées avec un terminal.</span><span class="sxs-lookup"><span data-stu-id="21a0b-111">You can see which versions of the .NET SDK are currently installed with a terminal.</span></span> <span data-ttu-id="21a0b-112">Ouvrez un terminal et exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="21a0b-112">Open a terminal and run the following command.</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="21a0b-113">Vous recevez une sortie similaire à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="21a0b-113">You get output similar to the following.</span></span>

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

## <a name="check-runtime-versions"></a><span data-ttu-id="21a0b-114">Vérifier les versions du Runtime</span><span class="sxs-lookup"><span data-stu-id="21a0b-114">Check runtime versions</span></span>

<span data-ttu-id="21a0b-115">Vous pouvez voir quelles versions du Runtime .NET sont actuellement installées avec la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="21a0b-115">You can see which versions of the .NET runtime are currently installed with the following command.</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="21a0b-116">Vous recevez une sortie similaire à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="21a0b-116">You get output similar to the following.</span></span>

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

## <a name="check-for-install-folders"></a><span data-ttu-id="21a0b-117">Rechercher les dossiers d’installation</span><span class="sxs-lookup"><span data-stu-id="21a0b-117">Check for install folders</span></span>

<span data-ttu-id="21a0b-118">Il est possible que .NET soit installé mais pas ajouté à la `PATH` variable pour votre système d’exploitation ou profil utilisateur.</span><span class="sxs-lookup"><span data-stu-id="21a0b-118">It's possible that .NET is installed but not added to the `PATH` variable for your operating system or user profile.</span></span> <span data-ttu-id="21a0b-119">Dans ce cas, les commandes des sections précédentes peuvent ne pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="21a0b-119">In this case, the commands from the previous sections may not work.</span></span> <span data-ttu-id="21a0b-120">Vous pouvez également vérifier que les dossiers d’installation .NET existent.</span><span class="sxs-lookup"><span data-stu-id="21a0b-120">As an alternative, you can check that the .NET install folders exist.</span></span>

<span data-ttu-id="21a0b-121">Lorsque vous installez .NET à partir d’un programme d’installation ou d’un script, il est installé dans un dossier standard.</span><span class="sxs-lookup"><span data-stu-id="21a0b-121">When you install .NET from an installer or script, it's installed to a standard folder.</span></span> <span data-ttu-id="21a0b-122">La plupart du temps, le programme d’installation ou le script que vous utilisez pour installer .NET vous donne la possibilité d’installer dans un autre dossier.</span><span class="sxs-lookup"><span data-stu-id="21a0b-122">Much of the time the installer or script you're using to install .NET gives you an option to install to a different folder.</span></span> <span data-ttu-id="21a0b-123">Si vous choisissez d’installer dans un autre dossier, ajustez le début du chemin d’accès au dossier.</span><span class="sxs-lookup"><span data-stu-id="21a0b-123">If you choose to install to a different folder, adjust the start of the folder path.</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="21a0b-124">**fichier exécutable dotnet**</span><span class="sxs-lookup"><span data-stu-id="21a0b-124">**dotnet executable**</span></span>\
<span data-ttu-id="21a0b-125">_C : \\ Program Files \\ dotnet \\dotnet.exe_</span><span class="sxs-lookup"><span data-stu-id="21a0b-125">_C:\\program files\\dotnet\\dotnet.exe_</span></span>

- <span data-ttu-id="21a0b-126">**SDK .NET**</span><span class="sxs-lookup"><span data-stu-id="21a0b-126">**.NET SDK**</span></span>\
<span data-ttu-id="21a0b-127">_C : \\ Program Files \\ dotnet \\ SDK \\ {version}\\_</span><span class="sxs-lookup"><span data-stu-id="21a0b-127">_C:\\program files\\dotnet\\sdk\\{version}\\_</span></span>

- <span data-ttu-id="21a0b-128">**Runtime .NET**</span><span class="sxs-lookup"><span data-stu-id="21a0b-128">**.NET Runtime**</span></span>\
<span data-ttu-id="21a0b-129">_C : \\ Program Files \\ dotnet \\ Shared \\ {Runtime-type} \\ {version}\\_</span><span class="sxs-lookup"><span data-stu-id="21a0b-129">_C:\\program files\\dotnet\\shared\\{runtime-type}\\{version}\\_</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="21a0b-130">**fichier exécutable dotnet**</span><span class="sxs-lookup"><span data-stu-id="21a0b-130">**dotnet executable**</span></span>\
<span data-ttu-id="21a0b-131">_/home/user/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="21a0b-131">_/home/user/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="21a0b-132">**SDK .NET**</span><span class="sxs-lookup"><span data-stu-id="21a0b-132">**.NET SDK**</span></span>\
<span data-ttu-id="21a0b-133">_/home/user/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="21a0b-133">_/home/user/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="21a0b-134">**Runtime .NET**</span><span class="sxs-lookup"><span data-stu-id="21a0b-134">**.NET Runtime**</span></span>\
<span data-ttu-id="21a0b-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="21a0b-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="21a0b-136">**fichier exécutable dotnet**</span><span class="sxs-lookup"><span data-stu-id="21a0b-136">**dotnet executable**</span></span>\
<span data-ttu-id="21a0b-137">_/usr/local/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="21a0b-137">_/usr/local/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="21a0b-138">**SDK .NET**</span><span class="sxs-lookup"><span data-stu-id="21a0b-138">**.NET SDK**</span></span>\
<span data-ttu-id="21a0b-139">_/usr/local/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="21a0b-139">_/usr/local/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="21a0b-140">**Runtime .NET**</span><span class="sxs-lookup"><span data-stu-id="21a0b-140">**.NET Runtime**</span></span>\
<span data-ttu-id="21a0b-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="21a0b-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

## <a name="more-information"></a><span data-ttu-id="21a0b-142">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="21a0b-142">More information</span></span>

<span data-ttu-id="21a0b-143">Vous pouvez voir les versions du kit de développement logiciel (SDK) et les versions du runtime à l’aide de la commande `dotnet --info` .</span><span class="sxs-lookup"><span data-stu-id="21a0b-143">You can see both the SDK versions and runtime versions with the command `dotnet --info`.</span></span> <span data-ttu-id="21a0b-144">Vous obtiendrez également d’autres informations relatives à l’environnement, telles que la version du système d’exploitation et l’identificateur de Runtime (RID).</span><span class="sxs-lookup"><span data-stu-id="21a0b-144">You'll also get other environmental related information, such as the operating system version and runtime identifier (RID).</span></span>

## <a name="next-steps"></a><span data-ttu-id="21a0b-145">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="21a0b-145">Next steps</span></span>

- <span data-ttu-id="21a0b-146">[Installez le Runtime .net et le kit de développement logiciel (SDK) pour Windows](windows.md).</span><span class="sxs-lookup"><span data-stu-id="21a0b-146">[Install the .NET Runtime and SDK for Windows](windows.md).</span></span>
- <span data-ttu-id="21a0b-147">[Installez le Runtime .net et le kit de développement logiciel (SDK) pour MacOS](macos.md).</span><span class="sxs-lookup"><span data-stu-id="21a0b-147">[Install the .NET Runtime and SDK for macOS](macos.md).</span></span>
- <span data-ttu-id="21a0b-148">[Installez le Runtime .net et le kit de développement logiciel (SDK) pour Linux](linux.md).</span><span class="sxs-lookup"><span data-stu-id="21a0b-148">[Install the .NET Runtime and SDK for Linux](linux.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="21a0b-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21a0b-149">See also</span></span>

- [<span data-ttu-id="21a0b-150">Identifier les versions de .NET Framework installées</span><span class="sxs-lookup"><span data-stu-id="21a0b-150">Determine which .NET Framework versions are installed</span></span>](../../framework/migration-guide/how-to-determine-which-versions-are-installed.md)
