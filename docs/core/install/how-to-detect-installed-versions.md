---
title: Vérifiez les versions .NET Core installées sur Windows, Linux et macOS - .NET Core
description: Découvrez comment répertorier les versions de .NET Core installées sur votre ordinateur. Cela inclut le temps d’exécution .NET Core et SDK.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 3a78acee6cf427085e98f14353fc2c0ac65d3d80
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645346"
---
# <a name="how-to-check-that-net-core-is-already-installed"></a><span data-ttu-id="d95db-104">Comment vérifier que .NET Core est déjà installé</span><span class="sxs-lookup"><span data-stu-id="d95db-104">How to check that .NET Core is already installed</span></span>

<span data-ttu-id="d95db-105">Cet article vous apprend à vérifier quelles versions de l’exécution .NET Core et SDK sont installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d95db-105">This article teaches you how to check which versions of the .NET Core runtime and SDK are installed on your computer.</span></span> <span data-ttu-id="d95db-106">.NET core peut avoir déjà été installé si vous avez un environnement de développement intégré, comme Visual Studio ou Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="d95db-106">.NET core may have already been installed if you have an integrated development environment, such as Visual Studio or Visual Studio for Mac.</span></span>

<span data-ttu-id="d95db-107">L’installation d’un SDK installe l’heure d’exécution correspondante.</span><span class="sxs-lookup"><span data-stu-id="d95db-107">Installing an SDK installs the corresponding runtime.</span></span>

<span data-ttu-id="d95db-108">Si une commande dans cet article échoue, vous n’avez pas le temps d’exécution ou SDK installé.</span><span class="sxs-lookup"><span data-stu-id="d95db-108">If any command in this article fails, you don't have the runtime or SDK installed.</span></span> <span data-ttu-id="d95db-109">Pour plus d’informations, voir [Télécharger et installer .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="d95db-109">For more information, see [Download and install .NET Core](index.md).</span></span>

## <a name="check-sdk-versions"></a><span data-ttu-id="d95db-110">Consultez les versions SDK</span><span class="sxs-lookup"><span data-stu-id="d95db-110">Check SDK versions</span></span>

<span data-ttu-id="d95db-111">Vous pouvez voir quelles versions du .NET Core SDK sont actuellement installées avec un terminal.</span><span class="sxs-lookup"><span data-stu-id="d95db-111">You can see which versions of the .NET Core SDK are currently installed with a terminal.</span></span> <span data-ttu-id="d95db-112">Ouvrez un terminal et exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="d95db-112">Open a terminal and run the following command.</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="d95db-113">Vous obtenez la sortie similaire à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="d95db-113">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
2.1.500 [C:\program files\dotnet\sdk]
2.1.502 [C:\program files\dotnet\sdk]
2.1.504 [C:\program files\dotnet\sdk]
2.1.600 [C:\program files\dotnet\sdk]
2.1.602 [C:\program files\dotnet\sdk]
2.2.101 [C:\program files\dotnet\sdk]
3.0.100 [C:\program files\dotnet\sdk]
3.1.100 [C:\program files\dotnet\sdk]
```

::: zone-end

::: zone pivot="os-linux"

```bash
2.1.500 [/home/user/dotnet/sdk]
2.1.502 [/home/user/dotnet/sdk]
2.1.504 [/home/user/dotnet/sdk]
2.1.600 [/home/user/dotnet/sdk]
2.1.602 [/home/user/dotnet/sdk]
2.2.101 [/home/user/dotnet/sdk]
3.0.100 [/home/user/dotnet/sdk]
3.1.100 [/home/user/dotnet/sdk]
```

::: zone-end

::: zone pivot="os-macos"

```bash
2.1.500 [/usr/local/share/dotnet/sdk]
2.1.502 [/usr/local/share/dotnet/sdk]
2.1.504 [/usr/local/share/dotnet/sdk]
2.1.600 [/usr/local/share/dotnet/sdk]
2.1.602 [/usr/local/share/dotnet/sdk]
2.2.101 [/usr/local/share/dotnet/sdk]
3.0.100 [/usr/local/share/dotnet/sdk]
3.1.100 [/usr/local/share/dotnet/sdk]
```

::: zone-end

## <a name="check-runtime-versions"></a><span data-ttu-id="d95db-114">Vérifier les versions en temps d’exécution</span><span class="sxs-lookup"><span data-stu-id="d95db-114">Check runtime versions</span></span>

<span data-ttu-id="d95db-115">Vous pouvez voir quelles versions du temps d’exécution .NET Core sont actuellement installées avec la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="d95db-115">You can see which versions of the .NET Core runtime are currently installed with the following command.</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="d95db-116">Vous obtenez la sortie similaire à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="d95db-116">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
Microsoft.AspNetCore.All 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.WindowsDesktop.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
```

::: zone-end

::: zone pivot="os-linux"

```bash
Microsoft.AspNetCore.All 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

::: zone pivot="os-macos"

```bash
Microsoft.AspNetCore.All 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

## <a name="check-for-install-folders"></a><span data-ttu-id="d95db-117">Vérifier s’il y a des dossiers d’installation</span><span class="sxs-lookup"><span data-stu-id="d95db-117">Check for install folders</span></span>

<span data-ttu-id="d95db-118">Il est possible que .NET Core soit `PATH` installé mais non ajouté à la variable de votre système d’exploitation ou de votre profil d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d95db-118">It's possible that .NET Core is installed but not added to the `PATH` variable for your operating system or user profile.</span></span> <span data-ttu-id="d95db-119">L’exécution des commandes des sections précédentes peut ne pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="d95db-119">Running the commands from the previous sections may not work.</span></span> <span data-ttu-id="d95db-120">Comme alternative, vous pouvez vérifier que les dossiers d’installation .NET Core existent.</span><span class="sxs-lookup"><span data-stu-id="d95db-120">As an alternative, you can check that the .NET Core install folders exist.</span></span>

<span data-ttu-id="d95db-121">Lorsque vous installez .NET Core à partir d’un installateur ou d’un script, il est installé dans un dossier standard.</span><span class="sxs-lookup"><span data-stu-id="d95db-121">When you install .NET Core from an installer or script, it's installed to a standard folder.</span></span> <span data-ttu-id="d95db-122">La plupart du temps, l’installateur ou le script que vous utilisez pour installer .NET Core vous donne une option à installer à un dossier différent.</span><span class="sxs-lookup"><span data-stu-id="d95db-122">Much of the time the installer or script you're using to install .NET Core gives you an option to install to a different folder.</span></span> <span data-ttu-id="d95db-123">Si vous choisissez d’installer un dossier différent, ajustez le début du chemin du dossier.</span><span class="sxs-lookup"><span data-stu-id="d95db-123">If you choose to install to a different folder, adjust the start of the folder path.</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="d95db-124">**dotnet exécutable**</span><span class="sxs-lookup"><span data-stu-id="d95db-124">**dotnet executable**</span></span>\
<span data-ttu-id="d95db-125">_C:\\fichiers\\de\\programme dotnet dotnet.exe_</span><span class="sxs-lookup"><span data-stu-id="d95db-125">_C:\\program files\\dotnet\\dotnet.exe_</span></span>

- <span data-ttu-id="d95db-126">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="d95db-126">**.NET SDK**</span></span>\
<span data-ttu-id="d95db-127">_C\\:\\fichiers\\de programme\\dotnet sdk version\\_</span><span class="sxs-lookup"><span data-stu-id="d95db-127">_C:\\program files\\dotnet\\sdk\\{version}\\_</span></span>

- <span data-ttu-id="d95db-128">**.NET Runtime (net Runtime)**</span><span class="sxs-lookup"><span data-stu-id="d95db-128">**.NET Runtime**</span></span>\
<span data-ttu-id="d95db-129">_C\\:\\fichiers\\de\\programme dotnet\\partagés 'runtime-type' 'version'\\_</span><span class="sxs-lookup"><span data-stu-id="d95db-129">_C:\\program files\\dotnet\\shared\\{runtime-type}\\{version}\\_</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="d95db-130">**dotnet exécutable**</span><span class="sxs-lookup"><span data-stu-id="d95db-130">**dotnet executable**</span></span>\
<span data-ttu-id="d95db-131">_/home/user/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="d95db-131">_/home/user/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="d95db-132">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="d95db-132">**.NET SDK**</span></span>\
<span data-ttu-id="d95db-133">_/home/user/share/dotnet/sdk/'version' /_</span><span class="sxs-lookup"><span data-stu-id="d95db-133">_/home/user/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="d95db-134">**.NET Runtime (net Runtime)**</span><span class="sxs-lookup"><span data-stu-id="d95db-134">**.NET Runtime**</span></span>\
<span data-ttu-id="d95db-135">_/home/user/share/dotnet/shared/runtime-type/ 'version'/_</span><span class="sxs-lookup"><span data-stu-id="d95db-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="d95db-136">**dotnet exécutable**</span><span class="sxs-lookup"><span data-stu-id="d95db-136">**dotnet executable**</span></span>\
<span data-ttu-id="d95db-137">_/usr/local/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="d95db-137">_/usr/local/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="d95db-138">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="d95db-138">**.NET SDK**</span></span>\
<span data-ttu-id="d95db-139">_/usr/local/share/dotnet/sdk/version//_</span><span class="sxs-lookup"><span data-stu-id="d95db-139">_/usr/local/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="d95db-140">**.NET Runtime (net Runtime)**</span><span class="sxs-lookup"><span data-stu-id="d95db-140">**.NET Runtime**</span></span>\
<span data-ttu-id="d95db-141">_/usr/local/share/dotnet/shared/runtime-type/'version'/_</span><span class="sxs-lookup"><span data-stu-id="d95db-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

## <a name="more-information"></a><span data-ttu-id="d95db-142">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="d95db-142">More information</span></span>

<span data-ttu-id="d95db-143">Vous pouvez voir à la fois les versions SDK et les versions d’exécution avec la commande `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="d95db-143">You can see both the SDK versions and runtime versions with the command `dotnet --info`.</span></span> <span data-ttu-id="d95db-144">Vous obtiendrez également d’autres informations liées à l’environnement, telles que la version du système d’exploitation et l’identifiant de temps d’exécution (RID).</span><span class="sxs-lookup"><span data-stu-id="d95db-144">You'll also get other environmental related information, such as the operating system version and runtime identifier (RID).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d95db-145">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="d95db-145">Next steps</span></span>

- <span data-ttu-id="d95db-146">[Installez le .NET Core Runtime](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="d95db-146">[Install the .NET Core Runtime](runtime.md).</span></span>
- <span data-ttu-id="d95db-147">[Installer le .NET Core SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="d95db-147">[Install the .NET Core SDK](sdk.md).</span></span>
