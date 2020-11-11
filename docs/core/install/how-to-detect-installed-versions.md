---
title: Vérifier les versions installées de .NET sur Windows, Linux et macOS-.NET
description: Découvrez comment répertorier les versions de .NET qui sont installées sur votre ordinateur. Cela comprend le Runtime .NET et le kit de développement logiciel (SDK).
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: d924e5bc58052cd760f367e906666d68ab79b764
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507213"
---
# <a name="how-to-check-that-net-is-already-installed"></a><span data-ttu-id="00255-104">Comment vérifier que .NET est déjà installé</span><span class="sxs-lookup"><span data-stu-id="00255-104">How to check that .NET is already installed</span></span>

<span data-ttu-id="00255-105">Cet article explique comment vérifier quelles versions du Runtime .NET et du kit de développement logiciel (SDK) sont installées sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="00255-105">This article teaches you how to check which versions of the .NET runtime and SDK are installed on your computer.</span></span> <span data-ttu-id="00255-106">.NET a peut-être déjà été installé si vous disposez d’un environnement de développement intégré, tel que Visual Studio ou Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="00255-106">.NET may have already been installed if you have an integrated development environment, such as Visual Studio or Visual Studio for Mac.</span></span>

<span data-ttu-id="00255-107">L’installation d’un kit de développement logiciel installe le runtime correspondant.</span><span class="sxs-lookup"><span data-stu-id="00255-107">Installing an SDK installs the corresponding runtime.</span></span>

<span data-ttu-id="00255-108">En cas d’échec d’une commande de cet article, le runtime ou le kit de développement logiciel (SDK) n’est pas installé.</span><span class="sxs-lookup"><span data-stu-id="00255-108">If any command in this article fails, you don't have the runtime or SDK installed.</span></span> <span data-ttu-id="00255-109">Pour plus d’informations, consultez les articles installer pour [Windows](windows.md), [MacOS](macos.md)ou [Linux](linux.md).</span><span class="sxs-lookup"><span data-stu-id="00255-109">For more information, see the install articles for [Windows](windows.md), [macOS](macos.md), or [Linux](linux.md).</span></span>

## <a name="check-sdk-versions"></a><span data-ttu-id="00255-110">Vérifier les versions du SDK</span><span class="sxs-lookup"><span data-stu-id="00255-110">Check SDK versions</span></span>

<span data-ttu-id="00255-111">Vous pouvez voir les versions du kit de développement logiciel (SDK) .NET actuellement installées avec un terminal.</span><span class="sxs-lookup"><span data-stu-id="00255-111">You can see which versions of the .NET SDK are currently installed with a terminal.</span></span> <span data-ttu-id="00255-112">Ouvrez un terminal et exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="00255-112">Open a terminal and run the following command.</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="00255-113">Vous recevez une sortie similaire à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="00255-113">You get output similar to the following.</span></span>

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

## <a name="check-runtime-versions"></a><span data-ttu-id="00255-114">Vérifier les versions du Runtime</span><span class="sxs-lookup"><span data-stu-id="00255-114">Check runtime versions</span></span>

<span data-ttu-id="00255-115">Vous pouvez voir quelles versions du Runtime .NET sont actuellement installées avec la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="00255-115">You can see which versions of the .NET runtime are currently installed with the following command.</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="00255-116">Vous recevez une sortie similaire à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="00255-116">You get output similar to the following.</span></span>

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

## <a name="check-for-install-folders"></a><span data-ttu-id="00255-117">Rechercher les dossiers d’installation</span><span class="sxs-lookup"><span data-stu-id="00255-117">Check for install folders</span></span>

<span data-ttu-id="00255-118">Il est possible que .NET soit installé mais pas ajouté à la `PATH` variable pour votre système d’exploitation ou profil utilisateur.</span><span class="sxs-lookup"><span data-stu-id="00255-118">It's possible that .NET is installed but not added to the `PATH` variable for your operating system or user profile.</span></span> <span data-ttu-id="00255-119">L’exécution des commandes des sections précédentes peut ne pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="00255-119">Running the commands from the previous sections may not work.</span></span> <span data-ttu-id="00255-120">Vous pouvez également vérifier que les dossiers d’installation .NET existent.</span><span class="sxs-lookup"><span data-stu-id="00255-120">As an alternative, you can check that the .NET install folders exist.</span></span>

<span data-ttu-id="00255-121">Lorsque vous installez .NET à partir d’un programme d’installation ou d’un script, il est installé dans un dossier standard.</span><span class="sxs-lookup"><span data-stu-id="00255-121">When you install .NET from an installer or script, it's installed to a standard folder.</span></span> <span data-ttu-id="00255-122">La plupart du temps, le programme d’installation ou le script que vous utilisez pour installer .NET vous donne la possibilité d’installer dans un autre dossier.</span><span class="sxs-lookup"><span data-stu-id="00255-122">Much of the time the installer or script you're using to install .NET gives you an option to install to a different folder.</span></span> <span data-ttu-id="00255-123">Si vous choisissez d’installer dans un autre dossier, ajustez le début du chemin d’accès au dossier.</span><span class="sxs-lookup"><span data-stu-id="00255-123">If you choose to install to a different folder, adjust the start of the folder path.</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="00255-124">**fichier exécutable dotnet**</span><span class="sxs-lookup"><span data-stu-id="00255-124">**dotnet executable**</span></span>\
<span data-ttu-id="00255-125">_C : \\ Program Files \\ dotnet \\dotnet.exe_</span><span class="sxs-lookup"><span data-stu-id="00255-125">_C:\\program files\\dotnet\\dotnet.exe_</span></span>

- <span data-ttu-id="00255-126">**SDK .NET**</span><span class="sxs-lookup"><span data-stu-id="00255-126">**.NET SDK**</span></span>\
<span data-ttu-id="00255-127">_C : \\ Program Files \\ dotnet \\ SDK \\ {version}\\_</span><span class="sxs-lookup"><span data-stu-id="00255-127">_C:\\program files\\dotnet\\sdk\\{version}\\_</span></span>

- <span data-ttu-id="00255-128">**Runtime .NET**</span><span class="sxs-lookup"><span data-stu-id="00255-128">**.NET Runtime**</span></span>\
<span data-ttu-id="00255-129">_C : \\ Program Files \\ dotnet \\ Shared \\ {Runtime-type} \\ {version}\\_</span><span class="sxs-lookup"><span data-stu-id="00255-129">_C:\\program files\\dotnet\\shared\\{runtime-type}\\{version}\\_</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="00255-130">**fichier exécutable dotnet**</span><span class="sxs-lookup"><span data-stu-id="00255-130">**dotnet executable**</span></span>\
<span data-ttu-id="00255-131">_/home/user/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="00255-131">_/home/user/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="00255-132">**SDK .NET**</span><span class="sxs-lookup"><span data-stu-id="00255-132">**.NET SDK**</span></span>\
<span data-ttu-id="00255-133">_/home/user/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="00255-133">_/home/user/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="00255-134">**Runtime .NET**</span><span class="sxs-lookup"><span data-stu-id="00255-134">**.NET Runtime**</span></span>\
<span data-ttu-id="00255-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="00255-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="00255-136">**fichier exécutable dotnet**</span><span class="sxs-lookup"><span data-stu-id="00255-136">**dotnet executable**</span></span>\
<span data-ttu-id="00255-137">_/usr/local/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="00255-137">_/usr/local/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="00255-138">**SDK .NET**</span><span class="sxs-lookup"><span data-stu-id="00255-138">**.NET SDK**</span></span>\
<span data-ttu-id="00255-139">_/usr/local/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="00255-139">_/usr/local/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="00255-140">**Runtime .NET**</span><span class="sxs-lookup"><span data-stu-id="00255-140">**.NET Runtime**</span></span>\
<span data-ttu-id="00255-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="00255-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

## <a name="more-information"></a><span data-ttu-id="00255-142">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="00255-142">More information</span></span>

<span data-ttu-id="00255-143">Vous pouvez voir les versions du kit de développement logiciel (SDK) et les versions du runtime à l’aide de la commande `dotnet --info` .</span><span class="sxs-lookup"><span data-stu-id="00255-143">You can see both the SDK versions and runtime versions with the command `dotnet --info`.</span></span> <span data-ttu-id="00255-144">Vous obtiendrez également d’autres informations relatives à l’environnement, telles que la version du système d’exploitation et l’identificateur de Runtime (RID).</span><span class="sxs-lookup"><span data-stu-id="00255-144">You'll also get other environmental related information, such as the operating system version and runtime identifier (RID).</span></span>

## <a name="next-steps"></a><span data-ttu-id="00255-145">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="00255-145">Next steps</span></span>

- <span data-ttu-id="00255-146">[Installez le Runtime .net et le kit de développement logiciel (SDK) pour Windows](windows.md).</span><span class="sxs-lookup"><span data-stu-id="00255-146">[Install the .NET Runtime and SDK for Windows](windows.md).</span></span>
- <span data-ttu-id="00255-147">[Installez le Runtime .net et le kit de développement logiciel (SDK) pour MacOS](linux.md).</span><span class="sxs-lookup"><span data-stu-id="00255-147">[Install the .NET Runtime and SDK for MacOS](linux.md).</span></span>
- <span data-ttu-id="00255-148">[Installez le Runtime .net et le kit de développement logiciel (SDK) pour Linux](macos.md).</span><span class="sxs-lookup"><span data-stu-id="00255-148">[Install the .NET Runtime and SDK for Linux](macos.md).</span></span>
