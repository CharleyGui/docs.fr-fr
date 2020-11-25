---
title: Supprimer le Runtime .NET et le kit de développement logiciel (SDK)
description: Cet article explique comment déterminer quelles versions du Runtime .NET et du kit de développement logiciel (SDK) sont actuellement installées, puis comment les supprimer sur Windows, Mac et Linux.
author: adegeo
ms.author: adegeo
ms.date: 11/20/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: f07a9acdc5be310d38da18602dde2ebf678e9a1b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031720"
---
# <a name="how-to-remove-the-net-runtime-and-sdk"></a>Comment supprimer le Runtime .NET et le kit de développement logiciel (SDK)

Au fil du temps, lorsque vous installez des versions mises à jour du Runtime .NET et du kit de développement logiciel (SDK), vous souhaiterez peut-être supprimer de votre ordinateur les versions obsolètes de .NET. La suppression des anciennes versions du runtime peut modifier le runtime choisi pour exécuter des applications d’infrastructure partagées, comme indiqué dans l’article sur la [sélection des versions .net](../versions/selection.md).

## <a name="should-i-remove-a-version"></a>Dois-je supprimer une version ?

Les comportements de [sélection de version .net](../versions/selection.md) et la compatibilité du runtime de .net entre les mises à jour permettent la suppression sécurisée des versions précédentes. Les mises à jour du Runtime .NET sont compatibles dans une **bande** de version majeure telle que 1. x et 2. x. En outre, les versions plus récentes du kit de développement logiciel (SDK) .NET maintiennent généralement la possibilité de créer des applications qui ciblent des versions antérieures du runtime de manière compatible.

En règle générale, vous avez uniquement besoin de la dernière version du SDK et de la dernière version des correctifs pour les Runtimes requis par votre application. Les instances dans lesquelles vous pouvez conserver des versions antérieures du kit de développement logiciel (SDK) ou du runtime incluent la gestion *desproject.js* applications basées sur. Si votre application ne nécessite pas de versions antérieures du SDK ou du Runtime pour une raison particulière, vous pouvez supprimer les versions antérieures en toute sécurité.

## <a name="determine-what-is-installed"></a>Déterminer ce qui est installé

L’interface CLI .NET propose des options que vous pouvez utiliser pour répertorier les versions du kit de développement logiciel (SDK) et du runtime installées sur votre ordinateur.  Utilisez [`dotnet --list-sdks`](../tools/dotnet.md#options) pour afficher la liste des kits de développement logiciel (SDK) installés sur votre ordinateur. Utilisez [`dotnet --list-runtimes`](../tools/dotnet.md#options) pour afficher la liste des runtimes installés sur votre ordinateur. Pour plus d’informations, consultez [Comment vérifier que .net est déjà installé](how-to-detect-installed-versions.md).

## <a name="uninstall-net"></a>Désinstaller .NET

::: zone pivot="os-windows"

.NET utilise la boîte de dialogue **& des fonctionnalités des applications** Windows pour supprimer les versions du kit de développement logiciel (SDK) et du Runtime .net. La figure suivante illustre la boîte de dialogue **applications & fonctionnalités** . Vous pouvez rechercher le **Kit de développement logiciel (** SDK) principal ou le **SDK .net** pour filtrer et afficher les versions installées de .net.

![Ajout/suppression de programmes pour supprimer .NET](./media/remove-runtime-sdk-versions/programs-and-features.png)

Sélectionnez la version que vous souhaitez supprimer de votre machine et cliquez sur **Désinstaller**.

::: zone-end

::: zone pivot="os-linux"

Il existe d’autres options pour désinstaller .NET (kit de développement logiciel (SDK) ou Runtime) sur Linux. La meilleure façon de désinstaller .NET est de mettre en miroir l’action que vous avez utilisée pour installer .NET. Les différences de processus sont fonction de la distribution que vous avez choisie et de la méthode d’installation.

> [!IMPORTANT]
> Pour les installations Red Hat, consultez la [documentation du produit Red Hat pour .net](https://access.redhat.com/documentation/en-us/net/5.0/).

Il est inutile de désinstaller le kit de développement logiciel (SDK) .NET lors de sa mise à niveau à l’aide d’un gestionnaire de package, sauf si vous effectuez une mise à niveau à partir d’une version préliminaire. Les commandes `update` ou `refresh` du gestionnaire de package suppriment automatiquement l’ancienne version une fois l’installation d’une version plus récente terminée. Si vous disposez d’une version préliminaire installée, désinstallez-la.

Si vous avez installé .NET à l’aide d’un gestionnaire de package, utilisez le même gestionnaire de package pour désinstaller le kit de développement logiciel (SDK) .NET ou le Runtime. Les installations .NET prennent en charge les gestionnaires de packages les plus populaires. Consultez la documentation du gestionnaire de package de votre distribution pour obtenir une syntaxe précise dans votre environnement :

- [apt-get(8)](https://linux.die.net/man/8/apt-get) est utilisé sur les systèmes Debian, y compris Ubuntu.
- [yum(8)](https://linux.die.net/man/8/yum) est utilisé sur les systèmes Fedora, CentOS et Oracle Linux.
- [zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) est utilisé sur les systèmes openSUSE et SLES (SUSE Linux Enterprise System).
- [dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) est utilisé sur les systèmes Fedora.

Dans presque tous les cas, la commande de suppression d’un package est `remove`.

Le nom du package pour l’installation du kit de développement logiciel (SDK) .NET pour la plupart des gestionnaires de package est `dotnet-sdk` , suivi du numéro de version. À partir de la version 2.1.300 du kit de développement logiciel (SDK) .NET et de la version `2.1` du runtime, seuls les numéros de version majeure et mineure sont nécessaires : par exemple, la version 2.1.300 du kit de développement logiciel (SDK) .net peut être référencée en tant que package `dotnet-sdk-2.1` . Les versions antérieures requièrent l’intégralité de la chaîne de version : par exemple, elle `dotnet-sdk-2.1.200` est requise pour la version 2.1.200 du kit de développement logiciel (SDK) .net.

Pour les ordinateurs qui n’ont installé que le runtime, et non le kit de développement logiciel (SDK), le nom du package est `dotnet-runtime-<version>` pour le Runtime .net et `aspnetcore-runtime-<version>` pour la pile Runtime entière.

> [!TIP]
> Les installations de .NET Core antérieures à 2,0 n’ont pas désinstallé l’application hôte lors de la désinstallation du kit de développement logiciel (SDK) à l’aide du gestionnaire de package. Avec `apt-get`, la commande est la suivante :
>
> ```bash
> apt-get remove dotnet-host
> ```
>
> Aucune version n’est attachée à `dotnet-host` .

Si vous avez installé à l’aide d’un tarball, vous devez supprimer .NET à l’aide de la méthode manuelle.

Sur Linux, vous devez supprimer les kits de développement logiciel (SDK) et les runtimes séparément, en supprimant les répertoires avec version. Leur suppression supprime le kit de développement logiciel (SDK) et le runtime du disque. Par exemple, pour supprimer la version 1.0.1 du SDK et du Runtime, utilisez les commandes bash suivantes :

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

Les répertoires parents du SDK et du Runtime sont répertoriés dans la sortie à l’aide des commandes `dotnet --list-sdks` et `dotnet --list-runtimes`, comme illustré plus haut.

::: zone-end

::: zone pivot="os-macos"

Sur Mac, vous devez supprimer les kits de développement logiciel (SDK) et les runtimes séparément, en supprimant les répertoires avec version. Leur suppression supprime le kit de développement logiciel (SDK) et le runtime du disque. Par exemple, pour supprimer la version 1.0.1 du SDK et du Runtime, utilisez les commandes bash suivantes :

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

Les répertoires parents du SDK et du Runtime sont répertoriés dans la sortie à l’aide des commandes `dotnet --list-sdks` et `dotnet --list-runtimes`, comme illustré plus haut.

::: zone-end

## <a name="net-uninstall-tool"></a>Outil de désinstallation .NET

L' [outil de désinstallation de .net](../additional-tools/uninstall-tool.md) ( `dotnet-core-uninstall` ) vous permet de supprimer les kits de développement logiciel (SDK) et runtimes .net d’un système. Une collection d’options est disponible pour spécifier les versions à désinstaller.

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a>Dépendance Visual Studio sur les versions de kit SDK .NET Core

Avant Visual Studio 2019 version 16,3, les programmes d’installation Visual Studio appelaient le programme d’installation de kit SDK .NET Core autonome. Par conséquent, les versions du kit de développement logiciel (SDK) s’affichent dans la boîte de dialogue **applications Windows & fonctionnalités** . La suppression des kits de développement logiciel (SDK) .NET Core qui ont été installés par Visual Studio à l’aide du programme d’installation autonome peut arrêter Visual Studio. Si Visual Studio rencontre des problèmes après avoir désinstallé les kits de développement logiciel (SDK), exécutez la réparation sur cette version spécifique de Visual Studio. Le tableau suivant présente certaines des dépendances Visual Studio sur les versions de kit SDK .NET Core :

| Version de Visual Studio           | Version de kit SDK .NET Core          |
|---------------------------------|--------------------------------|
| Visual Studio 2019 version 16.2 | Kit SDK .NET Core 2.2.4 XX, 2.1.8 XX |
| Visual Studio 2019 version 16.1 | Kit SDK .NET Core 2.2.3 XX, 2.1.7 XX |
| Visual Studio 2019 version 16,0 | Kit SDK .NET Core 2.2.2 XX, 2.1.6 XX |
| Visual Studio 2017 version 15,9 | Kit SDK .NET Core 2.2.1 XX, 2.1.5 XX |
| Visual Studio 2017 version 15.8 | Kit SDK .NET Core 2.1.4 XX          |

À compter de Visual Studio 2019 version 16,3, Visual Studio est en facturation de sa propre copie du kit de développement logiciel (SDK) .NET. Pour cette raison, vous ne voyez plus ces versions du kit de développement logiciel (SDK) dans la boîte de dialogue **applications & fonctionnalités** .

## <a name="remove-the-nuget-fallback-folder"></a>Supprimer le dossier NuGet Fallback

Avant le kit de développement logiciel (SDK) .NET Core 3,0, les programmes d’installation kit SDK .NET Core utilisaient un dossier nommé *NuGetFallbackFolder* pour stocker un cache de packages NuGet. Ce cache a été utilisé pendant des opérations telles que `dotnet restore` ou `dotnet build /t:Restore` . Le *NuGetFallbackFolder* se trouve dans *C:\Program Files\dotnet\sdk* sur Windows et sur */usr/local/share/dotnet/SDK* sur MacOS.

Vous souhaiterez peut-être supprimer ce dossier, si :

- Vous développez uniquement à l’aide du kit de développement logiciel (SDK) .NET Core 3,0 ou de .NET 5,0 ou versions ultérieures.
- Vous développez à l’aide de kit SDK .NET Core versions antérieures à 3,0, mais vous pouvez travailler en ligne.

Si vous souhaitez supprimer le dossier NuGet Fallback, vous pouvez le supprimer, mais vous aurez besoin de privilèges d’administrateur pour le faire.

Il n’est pas recommandé de supprimer le dossier *dotnet* . Cela entraînerait la suppression de tous les outils globaux que vous avez déjà installés. En outre, sur Windows :

- Vous allez rompre la version 16,3 et les versions ultérieures de Visual Studio 2019. Vous pouvez exécuter la **réparation** pour récupérer.
- S’il existe kit SDK .NET Core entrées dans la boîte de dialogue **applications & fonctionnalités** , elles seront orphelines.
