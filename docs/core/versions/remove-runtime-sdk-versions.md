---
title: Supprimer le SDK et le runtime .NET Core
description: Cet article explique comment déterminer quelles versions du runtime .NET Core et du SDK sont actuellement installées, puis comment les supprimer sous Windows, Mac et Linux.
ms.date: 12/17/2019
author: billwagner
ms.author: wiwagn
ms.custom: seodec18,updateeachrelease
ms.openlocfilehash: 8c235a4b38e991b6ba2c9d2489151995f3031a27
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342925"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="88a0e-103">Guide pratique pour supprimer un SDK et un Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="88a0e-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="88a0e-104">Si vous avez installé plusieurs versions mises à jour du SDK et du Runtime .NET Core au fil du temps, vous voulez peut-être maintenant supprimer les versions anciennes de .NET Core installées sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="88a0e-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="88a0e-105">La suppression de versions antérieures du Runtime peut entraîner un changement de Runtime sélectionné pour exécuter les applications de framework partagé, comme cela est expliqué dans l’article sur la [sélection de la version de .NET Core](selection.md).</span><span class="sxs-lookup"><span data-stu-id="88a0e-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="88a0e-106">Dois-je supprimer une version ?</span><span class="sxs-lookup"><span data-stu-id="88a0e-106">Should I remove a version?</span></span>

<span data-ttu-id="88a0e-107">Compte tenu des comportements de [sélection de la version de .NET Core](selection.md) et de la compatibilité des Runtimes .NET Core entre les mises à jour, vous pouvez supprimer en toute sécurité les versions précédentes.</span><span class="sxs-lookup"><span data-stu-id="88a0e-107">The [.NET Core version selection](selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="88a0e-108">Les mises à jour du Runtime .NET Core sont toutes compatibles au sein d’une même version principale (par exemple, 1.x et 2.x).</span><span class="sxs-lookup"><span data-stu-id="88a0e-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="88a0e-109">De plus, avec les versions récentes du SDK .NET Core, vous pouvez généralement continuer à créer des applications qui ciblent des versions précédentes du Runtime de manière compatible.</span><span class="sxs-lookup"><span data-stu-id="88a0e-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="88a0e-110">En règle générale, vous avez uniquement besoin de la dernière version du SDK et de la dernière version des correctifs pour les Runtimes requis par votre application.</span><span class="sxs-lookup"><span data-stu-id="88a0e-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="88a0e-111">Les instances dans lesquelles les versions antérieures du SDK ou du runtime sont conservées incluent la gestion des applications **Project. JSON**.</span><span class="sxs-lookup"><span data-stu-id="88a0e-111">Instances where keeping older SDK or Runtime versions include maintaining **project.json**-based applications.</span></span> <span data-ttu-id="88a0e-112">Si votre application ne nécessite pas de versions antérieures du SDK ou du Runtime pour une raison particulière, vous pouvez supprimer les versions antérieures en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="88a0e-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="88a0e-113">Déterminer ce qui est installé</span><span class="sxs-lookup"><span data-stu-id="88a0e-113">Determine what is installed</span></span>

<span data-ttu-id="88a0e-114">À compter de .NET Core 2.1, l’interface CLI .NET fournit des commandes qui vous permettent de répertorier toutes les versions du SDK et du Runtime installées sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="88a0e-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="88a0e-115">Utilisez la commande [`dotnet --list-sdks`](../tools/dotnet.md#options) pour afficher la liste des SDK installés sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="88a0e-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="88a0e-116">Utilisez la commande [`dotnet --list-runtimes`](../tools/dotnet.md#options) pour afficher la liste des Runtimes installés sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="88a0e-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="88a0e-117">Voici une sortie standard des commandes pour Windows, macOS ou Linux :</span><span class="sxs-lookup"><span data-stu-id="88a0e-117">The following text shows typical output for Windows, macOS, or Linux:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="88a0e-118">Fenêtres</span><span class="sxs-lookup"><span data-stu-id="88a0e-118">Windows</span></span>](#tab/windows)

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

# <a name="linuxtablinux"></a>[<span data-ttu-id="88a0e-119">Linux</span><span class="sxs-lookup"><span data-stu-id="88a0e-119">Linux</span></span>](#tab/linux)

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

# <a name="macostabmacos"></a>[<span data-ttu-id="88a0e-120">macOS</span><span class="sxs-lookup"><span data-stu-id="88a0e-120">macOS</span></span>](#tab/macos)

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

## <a name="uninstalling-net-core"></a><span data-ttu-id="88a0e-121">Désinstallation de .NET Core</span><span class="sxs-lookup"><span data-stu-id="88a0e-121">Uninstalling .NET Core</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="88a0e-122">Fenêtres</span><span class="sxs-lookup"><span data-stu-id="88a0e-122">Windows</span></span>](#tab/windows)

<span data-ttu-id="88a0e-123">.NET Core utilise la boîte de dialogue **Ajout/Suppression de programmes** de Windows pour supprimer des versions du SDK et du Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="88a0e-123">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="88a0e-124">L’illustration suivante montre la boîte de dialogue **Ajout/Suppression de programmes** qui répertorie les différentes versions du SDK et du Runtime .NET installées.</span><span class="sxs-lookup"><span data-stu-id="88a0e-124">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![Ajout/Suppression de programmes pour supprimer .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="88a0e-126">Sélectionnez la version que vous souhaitez supprimer de votre machine et cliquez sur **Désinstaller**.</span><span class="sxs-lookup"><span data-stu-id="88a0e-126">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="88a0e-127">Linux</span><span class="sxs-lookup"><span data-stu-id="88a0e-127">Linux</span></span>](#tab/linux)

<span data-ttu-id="88a0e-128">Sur Linux, il y a davantage d’options pour désinstaller le SDK ou le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="88a0e-128">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="88a0e-129">La meilleure méthode pour désinstaller .NET Core est de reprendre celle que vous aviez utilisée pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="88a0e-129">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="88a0e-130">Les différences de processus sont fonction de la distribution que vous avez choisie et de la méthode d’installation.</span><span class="sxs-lookup"><span data-stu-id="88a0e-130">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="88a0e-131">Pour les installations Red Hat, consultez le [guide de prise en main de Red Hat](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) afin d’obtenir des informations sur l’installation et la désinstallation de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="88a0e-131">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="88a0e-132">À compter de .NET Core 2,1, il n’est pas nécessaire de désinstaller le kit SDK .NET Core lors de sa mise à niveau à l’aide d’un gestionnaire de package.</span><span class="sxs-lookup"><span data-stu-id="88a0e-132">Starting with .NET Core 2.1, there's no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="88a0e-133">Les commandes `update` ou `refresh` du gestionnaire de package suppriment automatiquement l’ancienne version une fois l’installation d’une version plus récente terminée.</span><span class="sxs-lookup"><span data-stu-id="88a0e-133">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="88a0e-134">Si vous avez utilisé un gestionnaire de package pour installer .NET Core, réutilisez-le pour désinstaller le SDK ou le Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="88a0e-134">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="88a0e-135">Les installations .NET Core prennent en charge la plupart des gestionnaires de package courants.</span><span class="sxs-lookup"><span data-stu-id="88a0e-135">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="88a0e-136">Consultez la documentation du gestionnaire de package de votre distribution pour connaître la syntaxe exacte à employer dans votre environnement :</span><span class="sxs-lookup"><span data-stu-id="88a0e-136">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="88a0e-137">[apt-get(8)](https://linux.die.net/man/8/apt-get) est utilisé sur les systèmes Debian, y compris Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="88a0e-137">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="88a0e-138">[yum(8)](https://linux.die.net/man/8/yum) est utilisé sur les systèmes Fedora, CentOS et Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="88a0e-138">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="88a0e-139">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) est utilisé sur les systèmes openSUSE et SLES (SUSE Linux Enterprise System).</span><span class="sxs-lookup"><span data-stu-id="88a0e-139">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="88a0e-140">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) est utilisé sur les systèmes Fedora.</span><span class="sxs-lookup"><span data-stu-id="88a0e-140">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="88a0e-141">Dans presque tous les cas, la commande de suppression d’un package est `remove`.</span><span class="sxs-lookup"><span data-stu-id="88a0e-141">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="88a0e-142">Avec la plupart des gestionnaires de package, le nom du package utilisé pour installer le SDK .NET Core est `dotnet-sdk`, suivi du numéro de version.</span><span class="sxs-lookup"><span data-stu-id="88a0e-142">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="88a0e-143">À partir de la version 2.1.300 du SDK .NET Core et de la version `2.1` du Runtime, il suffit d’indiquer les numéros des versions principale et mineure. Par exemple, le SDK .NET Core version 2.1.300 peut être référencé en tant que package `dotnet-sdk-2.1`.</span><span class="sxs-lookup"><span data-stu-id="88a0e-143">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="88a0e-144">Pour les versions antérieures, la chaîne de version complète doit être indiquée. Par exemple, le SDK .NET Core version 2.1.200 doit être référencé par `dotnet-sdk-2.1.200`.</span><span class="sxs-lookup"><span data-stu-id="88a0e-144">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="88a0e-145">Sur les machines où est installé le Runtime uniquement, sans le SDK, le nom du package est `dotnet-runtime-<version>` pour le Runtime .NET Core, et `aspnetcore-runtime-<version>` pour la pile de Runtime entière.</span><span class="sxs-lookup"><span data-stu-id="88a0e-145">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="88a0e-146">Les installations de .NET Core antérieures à 2,0 n’ont pas désinstallé l’application hôte lors de la désinstallation du kit de développement logiciel (SDK) à l’aide du gestionnaire de package.</span><span class="sxs-lookup"><span data-stu-id="88a0e-146">.NET Core installations earlier than 2.0 didn't uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="88a0e-147">Avec `apt-get`, la commande est la suivante :</span><span class="sxs-lookup"><span data-stu-id="88a0e-147">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="88a0e-148">Notez qu’aucune version n’est attachée à `dotnet-host`.</span><span class="sxs-lookup"><span data-stu-id="88a0e-148">Note that there's no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="88a0e-149">Si vous avez effectué l’installation à l’aide d’un tarball, vous devez supprimer .NET Core manuellement.</span><span class="sxs-lookup"><span data-stu-id="88a0e-149">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="88a0e-150">Supprimez les SDK et les Runtimes séparément, en supprimant le répertoire contenant la version en question.</span><span class="sxs-lookup"><span data-stu-id="88a0e-150">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="88a0e-151">Par exemple, pour supprimer la version 1.0.1 du SDK et du Runtime, utilisez les commandes bash suivantes :</span><span class="sxs-lookup"><span data-stu-id="88a0e-151">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="88a0e-152">Les répertoires parents du SDK et du Runtime sont répertoriés dans la sortie à l’aide des commandes `dotnet --list-sdks` et `dotnet --list-runtimes`, comme illustré plus haut.</span><span class="sxs-lookup"><span data-stu-id="88a0e-152">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="88a0e-153">macOS</span><span class="sxs-lookup"><span data-stu-id="88a0e-153">macOS</span></span>](#tab/macos)

<span data-ttu-id="88a0e-154">Sur Mac, supprimez les SDK et les Runtimes séparément, en supprimant le répertoire contenant la version en question.</span><span class="sxs-lookup"><span data-stu-id="88a0e-154">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="88a0e-155">Par exemple, pour supprimer la version 1.0.1 du SDK et du Runtime, utilisez les commandes bash suivantes :</span><span class="sxs-lookup"><span data-stu-id="88a0e-155">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="88a0e-156">Les répertoires parents du SDK et du Runtime sont répertoriés dans la sortie à l’aide des commandes `dotnet --list-sdks` et `dotnet --list-runtimes`, comme illustré plus haut.</span><span class="sxs-lookup"><span data-stu-id="88a0e-156">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

---

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="88a0e-157">Outil de désinstallation de .NET Core</span><span class="sxs-lookup"><span data-stu-id="88a0e-157">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="88a0e-158">L' [outil de désinstallation de .net Core](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) vous permet de supprimer des kits de développement logiciel (SDK) .net Core et des runtimes d’un système.</span><span class="sxs-lookup"><span data-stu-id="88a0e-158">The [.NET Core Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="88a0e-159">Une collection d’options est disponible pour spécifier les versions à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="88a0e-159">A collection of options is available to specify which versions should be uninstalled.</span></span>

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a><span data-ttu-id="88a0e-160">Dépendance Visual Studio sur les versions de kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="88a0e-160">Visual Studio dependency on .NET Core SDK versions</span></span>

<span data-ttu-id="88a0e-161">Avant Visual Studio 2019 version 16,3, les programmes d’installation Visual Studio appelaient le programme d’installation de kit SDK .NET Core autonome.</span><span class="sxs-lookup"><span data-stu-id="88a0e-161">Before Visual Studio 2019 version 16.3, Visual Studio installers called the standalone .NET Core SDK installer.</span></span> <span data-ttu-id="88a0e-162">Par conséquent, les versions du kit de développement logiciel (SDK) s’affichent dans la boîte de dialogue **Ajout/suppression de programmes** de Windows.</span><span class="sxs-lookup"><span data-stu-id="88a0e-162">As a result, the SDK versions appear in the Windows **Add/Remove Programs** dialog.</span></span> <span data-ttu-id="88a0e-163">La suppression des kits de développement logiciel (SDK) .NET Core qui ont été installés par Visual Studio à l’aide du programme d’installation autonome peut arrêter Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="88a0e-163">Removing .NET Core SDKs that were installed by Visual Studio using the standalone installer may break Visual Studio.</span></span> <span data-ttu-id="88a0e-164">Si Visual Studio rencontre des problèmes après avoir désinstallé les kits de développement logiciel (SDK), exécutez la réparation sur cette version spécifique de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="88a0e-164">If Visual Studio has problems after you uninstall SDKs, run Repair on that specific version of Visual Studio.</span></span> <span data-ttu-id="88a0e-165">Le tableau suivant présente certaines des dépendances Visual Studio sur les versions de kit SDK .NET Core :</span><span class="sxs-lookup"><span data-stu-id="88a0e-165">The following table shows some of the Visual Studio dependencies on .NET Core SDK versions:</span></span>

| <span data-ttu-id="88a0e-166">Version de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="88a0e-166">Visual Studio version</span></span> | <span data-ttu-id="88a0e-167">Version de kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="88a0e-167">.NET Core SDK version</span></span> |
| -- | -- |
| <span data-ttu-id="88a0e-168">Visual Studio 2019 version 16.2</span><span class="sxs-lookup"><span data-stu-id="88a0e-168">Visual Studio 2019 version 16.2</span></span> | <span data-ttu-id="88a0e-169">Kit SDK .NET Core 2.2.4 XX, 2.1.8 XX</span><span class="sxs-lookup"><span data-stu-id="88a0e-169">.NET Core SDK 2.2.4xx, 2.1.8xx</span></span> |
| <span data-ttu-id="88a0e-170">Visual Studio 2019 version 16.1</span><span class="sxs-lookup"><span data-stu-id="88a0e-170">Visual Studio 2019 version 16.1</span></span> | <span data-ttu-id="88a0e-171">Kit SDK .NET Core 2.2.3 XX, 2.1.7 XX</span><span class="sxs-lookup"><span data-stu-id="88a0e-171">.NET Core SDK 2.2.3xx, 2.1.7xx</span></span> |
| <span data-ttu-id="88a0e-172">Visual Studio 2019 version 16,0</span><span class="sxs-lookup"><span data-stu-id="88a0e-172">Visual Studio 2019 version 16.0</span></span> | <span data-ttu-id="88a0e-173">Kit SDK .NET Core 2.2.2 XX, 2.1.6 XX</span><span class="sxs-lookup"><span data-stu-id="88a0e-173">.NET Core SDK 2.2.2xx, 2.1.6xx</span></span> |
| <span data-ttu-id="88a0e-174">Visual Studio 2017 version 15,9</span><span class="sxs-lookup"><span data-stu-id="88a0e-174">Visual Studio 2017 version 15.9</span></span> | <span data-ttu-id="88a0e-175">Kit SDK .NET Core 2.2.1 XX, 2.1.5 XX</span><span class="sxs-lookup"><span data-stu-id="88a0e-175">.NET Core SDK 2.2.1xx, 2.1.5xx</span></span> |
| <span data-ttu-id="88a0e-176">Visual Studio 2017 version 15.8</span><span class="sxs-lookup"><span data-stu-id="88a0e-176">Visual Studio 2017 version 15.8</span></span> | <span data-ttu-id="88a0e-177">Kit SDK .NET Core 2.1.4 XX</span><span class="sxs-lookup"><span data-stu-id="88a0e-177">.NET Core SDK 2.1.4xx</span></span> |

<span data-ttu-id="88a0e-178">À compter de Visual Studio 2019 16,3, Visual Studio est payant de sa propre copie du kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="88a0e-178">Starting with Visual Studio 2019 16.3, Visual Studio is in charge of its own copy of the .NET Core SDK.</span></span> <span data-ttu-id="88a0e-179">Pour cette raison, vous ne voyez plus ces versions du kit de développement logiciel (SDK) dans la boîte de dialogue **Ajout/suppression de programmes** .</span><span class="sxs-lookup"><span data-stu-id="88a0e-179">For that reason, you no longer see those SDK versions in the **Add/Remove Programs** dialog.</span></span>

## <a name="remove-the-nuget-fallback-folder"></a><span data-ttu-id="88a0e-180">Supprimer le dossier NuGet Fallback</span><span class="sxs-lookup"><span data-stu-id="88a0e-180">Remove the NuGet fallback folder</span></span>

<span data-ttu-id="88a0e-181">Avant le kit de développement logiciel (SDK) .NET Core 3,0, les programmes d’installation kit SDK .NET Core utilisé le *NuGetFallbackFolder* pour stocker un cache de packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="88a0e-181">Before .NET Core 3.0 SDK, the .NET Core SDK installers used the *NuGetFallbackFolder* to store a cache of NuGet packages.</span></span> <span data-ttu-id="88a0e-182">Ce cache a été utilisé pendant des opérations telles que `dotnet restore` ou `dotnet build /t:Restore`.</span><span class="sxs-lookup"><span data-stu-id="88a0e-182">This cache was used during operations such as `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="88a0e-183">Le `NuGetFallbackFolder` se trouve dans *C:\Program Files\dotnet\sdk* sur Windows et sur */usr/local/share/dotnet/SDK* sur MacOS.</span><span class="sxs-lookup"><span data-stu-id="88a0e-183">The `NuGetFallbackFolder` is located at *C:\Program Files\dotnet\sdk* on Windows and at */usr/local/share/dotnet/sdk* on macOS.</span></span>

<span data-ttu-id="88a0e-184">Vous souhaiterez peut-être supprimer ce dossier, si :</span><span class="sxs-lookup"><span data-stu-id="88a0e-184">You may want to remove this folder, if:</span></span>

* <span data-ttu-id="88a0e-185">Vous développez uniquement à l’aide du kit de développement logiciel (SDK) .NET Core 3,0 ou des versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="88a0e-185">You're only developing using .NET Core 3.0 SDK or later versions.</span></span>
* <span data-ttu-id="88a0e-186">Vous développez à l’aide de kit SDK .NET Core versions antérieures à 3,0, mais vous pouvez travailler en ligne et les choses peuvent être plus lentes une fois.</span><span class="sxs-lookup"><span data-stu-id="88a0e-186">You're developing using .NET Core SDK versions earlier than 3.0, but you can work online and things can be slower once.</span></span>

<span data-ttu-id="88a0e-187">Si vous souhaitez supprimer le dossier NuGet Fallback, vous pouvez le supprimer, mais vous aurez besoin de privilèges d’administrateur pour le faire.</span><span class="sxs-lookup"><span data-stu-id="88a0e-187">If you want to remove the NuGet fallback folder, you can delete it, but you'll need admin privileges to do so.</span></span>

<span data-ttu-id="88a0e-188">Il n’est pas recommandé de supprimer le dossier *dotnet* .</span><span class="sxs-lookup"><span data-stu-id="88a0e-188">It's not recommended to delete the *dotnet* folder.</span></span> <span data-ttu-id="88a0e-189">Cela entraînerait la suppression de tous les outils globaux que vous avez déjà installés.</span><span class="sxs-lookup"><span data-stu-id="88a0e-189">Doing so would remove any global tools you've previously installed.</span></span> <span data-ttu-id="88a0e-190">En outre, sur Windows :</span><span class="sxs-lookup"><span data-stu-id="88a0e-190">Also, on Windows:</span></span>

- <span data-ttu-id="88a0e-191">Vous allez rompre la version 16,3 et les versions ultérieures de Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="88a0e-191">You'll break Visual Studio 2019 version 16.3 and later versions.</span></span> <span data-ttu-id="88a0e-192">Vous pouvez exécuter la **réparation** pour récupérer.</span><span class="sxs-lookup"><span data-stu-id="88a0e-192">You can run **Repair** to recover.</span></span>
- <span data-ttu-id="88a0e-193">S’il existe kit SDK .NET Core entrées dans la boîte de dialogue **Ajout/suppression de programmes** , elles seront orphelines.</span><span class="sxs-lookup"><span data-stu-id="88a0e-193">If there are .NET Core SDK entries in the **Add/Remove Programs** dialog, they'll be orphaned.</span></span>
