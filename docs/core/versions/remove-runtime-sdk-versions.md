---
title: Supprimer le SDK et le runtime .NET Core
description: Cet article explique comment déterminer quelles versions du runtime .NET Core et du SDK sont actuellement installées, puis comment les supprimer sous Windows, Mac et Linux.
ms.date: 07/28/2018
author: billwagner
ms.author: wiwagn
ms.custom: seodec18
ms.openlocfilehash: 6d1012b8ddc5fd4a5ee8227902886727dbb10739
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970293"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="6ea1b-103">Guide pratique pour supprimer un SDK et un Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ea1b-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="6ea1b-104">Si vous avez installé plusieurs versions mises à jour du SDK et du Runtime .NET Core au fil du temps, vous voulez peut-être maintenant supprimer les versions anciennes de .NET Core installées sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="6ea1b-105">La suppression de versions antérieures du Runtime peut entraîner un changement de Runtime sélectionné pour exécuter les applications de framework partagé, comme cela est expliqué dans l’article sur la [sélection de la version de .NET Core](selection.md).</span><span class="sxs-lookup"><span data-stu-id="6ea1b-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="6ea1b-106">Dois-je supprimer une version ?</span><span class="sxs-lookup"><span data-stu-id="6ea1b-106">Should I remove a version?</span></span>

<span data-ttu-id="6ea1b-107">Compte tenu des comportements de [sélection de la version de .NET Core](selection.md) et de la compatibilité des Runtimes .NET Core entre les mises à jour, vous pouvez supprimer en toute sécurité les versions précédentes.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-107">The [.NET Core version selection](selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="6ea1b-108">Les mises à jour du Runtime .NET Core sont toutes compatibles au sein d’une même version principale (par exemple, 1.x et 2.x).</span><span class="sxs-lookup"><span data-stu-id="6ea1b-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="6ea1b-109">De plus, avec les versions récentes du SDK .NET Core, vous pouvez généralement continuer à créer des applications qui ciblent des versions précédentes du Runtime de manière compatible.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="6ea1b-110">En règle générale, vous avez uniquement besoin de la dernière version du SDK et de la dernière version des correctifs pour les Runtimes requis par votre application.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="6ea1b-111">Dans certains cas, vous devez conserver des versions antérieures du SDK ou du Runtime, par exemple, pour tenir à jour des applications basées sur **project.json**.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-111">Instances where retaining older SDK or Runtime versions include maintaining **project.json**-based applications.</span></span> <span data-ttu-id="6ea1b-112">Si votre application ne nécessite pas de versions antérieures du SDK ou du Runtime pour une raison particulière, vous pouvez supprimer les versions antérieures en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="6ea1b-113">Déterminer ce qui est installé</span><span class="sxs-lookup"><span data-stu-id="6ea1b-113">Determine what is installed</span></span>

<span data-ttu-id="6ea1b-114">À compter de .NET Core 2.1, l’interface CLI .NET fournit des commandes qui vous permettent de répertorier toutes les versions du SDK et du Runtime installées sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="6ea1b-115">Utilisez la commande [`dotnet --list-sdks`](../tools/dotnet.md#options) pour afficher la liste des SDK installés sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="6ea1b-116">Utilisez la commande [`dotnet --list-runtimes`](../tools/dotnet.md#options) pour afficher la liste des Runtimes installés sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="6ea1b-117">Voici une sortie standard des commandes pour Windows, macOS ou Linux :</span><span class="sxs-lookup"><span data-stu-id="6ea1b-117">The following text shows typical output for Windows, macOS, or Linux:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="6ea1b-118">Windows</span><span class="sxs-lookup"><span data-stu-id="6ea1b-118">Windows</span></span>](#tab/windows)

```console
C:\> dotnet --list-sdks
2.1.200-preview-007474 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007480 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007509 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007570 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007576 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007587 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007589 [C:\Program Files\dotnet\sdk]
2.1.200 [C:\Program Files\dotnet\sdk]
2.1.201 [C:\Program Files\dotnet\sdk]
2.1.202 [C:\Program Files\dotnet\sdk]
2.1.300-preview2-008533 [C:\Program Files\dotnet\sdk]
2.1.300 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009063 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009088 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009171 [C:\Program Files\dotnet\sdk]

C:\> dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.0.6 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.7 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.9 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
```

# <a name="linuxtablinux"></a>[<span data-ttu-id="6ea1b-119">Linux</span><span class="sxs-lookup"><span data-stu-id="6ea1b-119">Linux</span></span>](#tab/linux)

```console
$ dotnet --list-sdks
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]

$ dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
```

# <a name="macostabmacos"></a>[<span data-ttu-id="6ea1b-120">macOS</span><span class="sxs-lookup"><span data-stu-id="6ea1b-120">macOS</span></span>](#tab/macos)

```console
$ dotnet --list-sdks
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]

$ dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

---

## <a name="uninstalling-net-core"></a><span data-ttu-id="6ea1b-121">Désinstallation de .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ea1b-121">Uninstalling .NET Core</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="6ea1b-122">Windows</span><span class="sxs-lookup"><span data-stu-id="6ea1b-122">Windows</span></span>](#tab/windows)

<span data-ttu-id="6ea1b-123">.NET Core utilise la boîte de dialogue **Ajout/Suppression de programmes** de Windows pour supprimer des versions du SDK et du Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-123">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="6ea1b-124">L’illustration suivante montre la boîte de dialogue **Ajout/Suppression de programmes** qui répertorie les différentes versions du SDK et du Runtime .NET installées.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-124">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![Ajout/Suppression de programmes pour supprimer .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="6ea1b-126">Sélectionnez la version que vous souhaitez supprimer de votre machine et cliquez sur **Désinstaller**.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-126">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="6ea1b-127">Linux</span><span class="sxs-lookup"><span data-stu-id="6ea1b-127">Linux</span></span>](#tab/linux)

<span data-ttu-id="6ea1b-128">Sur Linux, il y a davantage d’options pour désinstaller le SDK ou le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-128">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="6ea1b-129">La meilleure méthode pour désinstaller .NET Core est de reprendre celle que vous aviez utilisée pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-129">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="6ea1b-130">Les différences de processus sont fonction de la distribution que vous avez choisie et de la méthode d’installation.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-130">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6ea1b-131">Pour les installations Red Hat, consultez le [guide de prise en main de Red Hat](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) afin d’obtenir des informations sur l’installation et la désinstallation de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-131">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="6ea1b-132">À compter de .NET Core 2.1, vous n’avez plus besoin de désinstaller le SDK .NET Core quand vous le mettez à niveau à l’aide d’un gestionnaire de package.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-132">Starting with .NET Core 2.1, there is no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="6ea1b-133">Les commandes `update` ou `refresh` du gestionnaire de package suppriment automatiquement l’ancienne version une fois l’installation d’une version plus récente terminée.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-133">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="6ea1b-134">Si vous avez utilisé un gestionnaire de package pour installer .NET Core, réutilisez-le pour désinstaller le SDK ou le Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-134">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="6ea1b-135">Les installations .NET Core prennent en charge la plupart des gestionnaires de package courants.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-135">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="6ea1b-136">Consultez la documentation du gestionnaire de package de votre distribution pour connaître la syntaxe exacte à employer dans votre environnement :</span><span class="sxs-lookup"><span data-stu-id="6ea1b-136">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="6ea1b-137">[apt-get(8)](https://linux.die.net/man/8/apt-get) est utilisé sur les systèmes Debian, y compris Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-137">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="6ea1b-138">[yum(8)](https://linux.die.net/man/8/yum) est utilisé sur les systèmes Fedora, CentOS et Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-138">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="6ea1b-139">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) est utilisé sur les systèmes openSUSE et SLES (SUSE Linux Enterprise System).</span><span class="sxs-lookup"><span data-stu-id="6ea1b-139">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="6ea1b-140">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) est utilisé sur les systèmes Fedora.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-140">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="6ea1b-141">Dans presque tous les cas, la commande de suppression d’un package est `remove`.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-141">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="6ea1b-142">Avec la plupart des gestionnaires de package, le nom du package utilisé pour installer le SDK .NET Core est `dotnet-sdk`, suivi du numéro de version.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-142">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="6ea1b-143">À partir de la version 2.1.300 du SDK .NET Core et de la version `2.1` du Runtime, il suffit d’indiquer les numéros des versions principale et mineure. Par exemple, le SDK .NET Core version 2.1.300 peut être référencé en tant que package `dotnet-sdk-2.1`.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-143">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="6ea1b-144">Pour les versions antérieures, la chaîne de version complète doit être indiquée. Par exemple, le SDK .NET Core version 2.1.200 doit être référencé par `dotnet-sdk-2.1.200`.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-144">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="6ea1b-145">Sur les machines où est installé le Runtime uniquement, sans le SDK, le nom du package est `dotnet-runtime-<version>` pour le Runtime .NET Core, et `aspnetcore-runtime-<version>` pour la pile de Runtime entière.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-145">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="6ea1b-146">Les installations .NET Core antérieures à 2.0 ne désinstallent pas l’application hôte quand le SDK est désinstallé à l’aide du gestionnaire de package.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-146">.NET Core installations prior to 2.0 did not uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="6ea1b-147">Avec `apt-get`, la commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="6ea1b-147">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="6ea1b-148">Notez qu’aucune version n’est indiquée après `dotnet-host`.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-148">Note that there is no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="6ea1b-149">Si vous avez effectué l’installation à l’aide d’un tarball, vous devez supprimer .NET Core manuellement.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-149">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="6ea1b-150">Supprimez les SDK et les Runtimes séparément, en supprimant le répertoire contenant la version en question.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-150">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="6ea1b-151">Par exemple, pour supprimer la version 1.0.1 du SDK et du Runtime, utilisez les commandes bash suivantes :</span><span class="sxs-lookup"><span data-stu-id="6ea1b-151">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="6ea1b-152">Les répertoires parents du SDK et du Runtime sont répertoriés dans la sortie à l’aide des commandes `dotnet --list-sdks` et `dotnet --list-runtimes`, comme illustré plus haut.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-152">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="6ea1b-153">macOS</span><span class="sxs-lookup"><span data-stu-id="6ea1b-153">macOS</span></span>](#tab/macos)

<span data-ttu-id="6ea1b-154">Sur Mac, supprimez les SDK et les Runtimes séparément, en supprimant le répertoire contenant la version en question.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-154">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="6ea1b-155">Par exemple, pour supprimer la version 1.0.1 du SDK et du Runtime, utilisez les commandes bash suivantes :</span><span class="sxs-lookup"><span data-stu-id="6ea1b-155">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="6ea1b-156">Les répertoires parents du SDK et du Runtime sont répertoriés dans la sortie à l’aide des commandes `dotnet --list-sdks` et `dotnet --list-runtimes`, comme illustré plus haut.</span><span class="sxs-lookup"><span data-stu-id="6ea1b-156">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

---
