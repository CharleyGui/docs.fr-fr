---
title: Supprimer le SDK et le runtime .NET Core
description: Cet article explique comment déterminer quelles versions du runtime .NET Core et du SDK sont actuellement installées, puis comment les supprimer sous Windows, Mac et Linux.
ms.date: 12/17/2019
author: billwagner
ms.author: wiwagn
ms.custom: updateeachrelease
ms.openlocfilehash: 82fbccdec0323b54d313960279fcbfeeb6033319
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920399"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a>Guide pratique pour supprimer un SDK et un Runtime .NET Core

Si vous avez installé plusieurs versions mises à jour du SDK et du Runtime .NET Core au fil du temps, vous voulez peut-être maintenant supprimer les versions anciennes de .NET Core installées sur votre machine. La suppression de versions antérieures du Runtime peut entraîner un changement de Runtime sélectionné pour exécuter les applications de framework partagé, comme cela est expliqué dans l’article sur la [sélection de la version de .NET Core](selection.md).

## <a name="should-i-remove-a-version"></a>Dois-je supprimer une version ?

Compte tenu des comportements de [sélection de la version de .NET Core](selection.md) et de la compatibilité des Runtimes .NET Core entre les mises à jour, vous pouvez supprimer en toute sécurité les versions précédentes. Les mises à jour du Runtime .NET Core sont toutes compatibles au sein d’une même version principale (par exemple, 1.x et 2.x). De plus, avec les versions récentes du SDK .NET Core, vous pouvez généralement continuer à créer des applications qui ciblent des versions précédentes du Runtime de manière compatible.

En règle générale, vous avez uniquement besoin de la dernière version du SDK et de la dernière version des correctifs pour les Runtimes requis par votre application. Les instances dans lesquelles les versions antérieures du SDK ou du runtime sont conservées incluent la gestion des applications **Project. JSON**. Si votre application ne nécessite pas de versions antérieures du SDK ou du Runtime pour une raison particulière, vous pouvez supprimer les versions antérieures en toute sécurité.

## <a name="determine-what-is-installed"></a>Déterminer ce qui est installé

À compter de .NET Core 2.1, l’interface CLI .NET fournit des commandes qui vous permettent de répertorier toutes les versions du SDK et du Runtime installées sur votre machine.  Utilisez la commande [`dotnet --list-sdks`](../tools/dotnet.md#options) pour afficher la liste des SDK installés sur votre machine. Utilisez la commande [`dotnet --list-runtimes`](../tools/dotnet.md#options) pour afficher la liste des Runtimes installés sur votre machine. Voici une sortie standard des commandes pour Windows, macOS ou Linux :

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Fenêtres](#tab/windows)

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

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

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

# <a name="macostabmacos"></a>[macOS](#tab/macos)

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

## <a name="uninstall-net-core"></a>Désinstaller .NET Core

# <a name="windowstabwindows"></a>[Fenêtres](#tab/windows)

.NET Core utilise la boîte de dialogue **Ajout/Suppression de programmes** de Windows pour supprimer des versions du SDK et du Runtime .NET Core. L’illustration suivante montre la boîte de dialogue **Ajout/Suppression de programmes** qui répertorie les différentes versions du SDK et du Runtime .NET installées.

![Ajout/Suppression de programmes pour supprimer .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

Sélectionnez la version que vous souhaitez supprimer de votre machine et cliquez sur **Désinstaller**.

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

Sur Linux, il y a davantage d’options pour désinstaller le SDK ou le Runtime .NET Core. La meilleure méthode pour désinstaller .NET Core est de reprendre celle que vous aviez utilisée pour installer .NET Core. Les différences de processus sont fonction de la distribution que vous avez choisie et de la méthode d’installation.

> [!IMPORTANT]
> Pour les installations Red Hat, consultez le [guide de prise en main de Red Hat](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) afin d’obtenir des informations sur l’installation et la désinstallation de .NET Core.

À compter de .NET Core 2,1, il n’est pas nécessaire de désinstaller le kit SDK .NET Core lors de sa mise à niveau à l’aide d’un gestionnaire de package. Les commandes `update` ou `refresh` du gestionnaire de package suppriment automatiquement l’ancienne version une fois l’installation d’une version plus récente terminée.

Si vous avez utilisé un gestionnaire de package pour installer .NET Core, réutilisez-le pour désinstaller le SDK ou le Runtime .NET. Les installations .NET Core prennent en charge la plupart des gestionnaires de package courants. Consultez la documentation du gestionnaire de package de votre distribution pour connaître la syntaxe exacte à employer dans votre environnement :

- [apt-get(8)](https://linux.die.net/man/8/apt-get) est utilisé sur les systèmes Debian, y compris Ubuntu.
- [yum(8)](https://linux.die.net/man/8/yum) est utilisé sur les systèmes Fedora, CentOS et Oracle Linux.
- [zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) est utilisé sur les systèmes openSUSE et SLES (SUSE Linux Enterprise System).
- [dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) est utilisé sur les systèmes Fedora.

Dans presque tous les cas, la commande de suppression d’un package est `remove`.

Avec la plupart des gestionnaires de package, le nom du package utilisé pour installer le SDK .NET Core est `dotnet-sdk`, suivi du numéro de version. À partir de la version 2.1.300 du SDK .NET Core et de la version `2.1` du Runtime, il suffit d’indiquer les numéros des versions principale et mineure. Par exemple, le SDK .NET Core version 2.1.300 peut être référencé en tant que package `dotnet-sdk-2.1`. Pour les versions antérieures, la chaîne de version complète doit être indiquée. Par exemple, le SDK .NET Core version 2.1.200 doit être référencé par `dotnet-sdk-2.1.200`.

Sur les machines où est installé le Runtime uniquement, sans le SDK, le nom du package est `dotnet-runtime-<version>` pour le Runtime .NET Core, et `aspnetcore-runtime-<version>` pour la pile de Runtime entière.

Les installations de .NET Core antérieures à 2,0 n’ont pas désinstallé l’application hôte lors de la désinstallation du kit de développement logiciel (SDK) à l’aide du gestionnaire de package. Avec `apt-get`, la commande est la suivante :

```bash
apt-get remove dotnet-host
```

Notez qu’aucune version n’est attachée à `dotnet-host`.

Si vous avez effectué l’installation à l’aide d’un tarball, vous devez supprimer .NET Core manuellement.

Supprimez les SDK et les Runtimes séparément, en supprimant le répertoire contenant la version en question. Par exemple, pour supprimer la version 1.0.1 du SDK et du Runtime, utilisez les commandes bash suivantes :

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

Les répertoires parents du SDK et du Runtime sont répertoriés dans la sortie à l’aide des commandes `dotnet --list-sdks` et `dotnet --list-runtimes`, comme illustré plus haut.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Sur Mac, supprimez les SDK et les Runtimes séparément, en supprimant le répertoire contenant la version en question. Par exemple, pour supprimer la version 1.0.1 du SDK et du Runtime, utilisez les commandes bash suivantes :

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

Les répertoires parents du SDK et du Runtime sont répertoriés dans la sortie à l’aide des commandes `dotnet --list-sdks` et `dotnet --list-runtimes`, comme illustré plus haut.

---

## <a name="net-core-uninstall-tool"></a>Outil de désinstallation de .NET Core

L' [outil de désinstallation de .net Core](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) vous permet de supprimer des kits de développement logiciel (SDK) .net Core et des runtimes d’un système. Une collection d’options est disponible pour spécifier les versions à désinstaller.

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a>Dépendance Visual Studio sur les versions de kit SDK .NET Core

Avant Visual Studio 2019 version 16,3, les programmes d’installation Visual Studio appelaient le programme d’installation de kit SDK .NET Core autonome. Par conséquent, les versions du kit de développement logiciel (SDK) s’affichent dans la boîte de dialogue **Ajout/suppression de programmes** de Windows. La suppression des kits de développement logiciel (SDK) .NET Core qui ont été installés par Visual Studio à l’aide du programme d’installation autonome peut arrêter Visual Studio. Si Visual Studio rencontre des problèmes après avoir désinstallé les kits de développement logiciel (SDK), exécutez la réparation sur cette version spécifique de Visual Studio. Le tableau suivant présente certaines des dépendances Visual Studio sur les versions de kit SDK .NET Core :

| Version de Visual Studio | Version de kit SDK .NET Core |
| -- | -- |
| Visual Studio 2019 version 16.2 | Kit SDK .NET Core 2.2.4 XX, 2.1.8 XX |
| Visual Studio 2019 version 16.1 | Kit SDK .NET Core 2.2.3 XX, 2.1.7 XX |
| Visual Studio 2019 version 16,0 | Kit SDK .NET Core 2.2.2 XX, 2.1.6 XX |
| Visual Studio 2017 version 15,9 | Kit SDK .NET Core 2.2.1 XX, 2.1.5 XX |
| Visual Studio 2017 version 15.8 | Kit SDK .NET Core 2.1.4 XX |

À compter de Visual Studio 2019 version 16,3, Visual Studio est payant de sa propre copie du kit SDK .NET Core. Pour cette raison, vous ne voyez plus ces versions du kit de développement logiciel (SDK) dans la boîte de dialogue **Ajout/suppression de programmes** .

## <a name="remove-the-nuget-fallback-folder"></a>Supprimer le dossier NuGet Fallback

Avant le kit de développement logiciel (SDK) .NET Core 3,0, les programmes d’installation kit SDK .NET Core utilisé le *NuGetFallbackFolder* pour stocker un cache de packages NuGet. Ce cache a été utilisé pendant des opérations telles que `dotnet restore` ou `dotnet build /t:Restore`. Le `NuGetFallbackFolder` se trouve dans *C:\Program Files\dotnet\sdk* sur Windows et sur */usr/local/share/dotnet/SDK* sur MacOS.

Vous souhaiterez peut-être supprimer ce dossier, si :

* Vous développez uniquement à l’aide du kit de développement logiciel (SDK) .NET Core 3,0 ou des versions ultérieures.
* Vous développez à l’aide de kit SDK .NET Core versions antérieures à 3,0, mais vous pouvez travailler en ligne et les choses peuvent être plus lentes une fois.

Si vous souhaitez supprimer le dossier NuGet Fallback, vous pouvez le supprimer, mais vous aurez besoin de privilèges d’administrateur pour le faire.

Il n’est pas recommandé de supprimer le dossier *dotnet* . Cela entraînerait la suppression de tous les outils globaux que vous avez déjà installés. En outre, sur Windows :

- Vous allez rompre la version 16,3 et les versions ultérieures de Visual Studio 2019. Vous pouvez exécuter la **réparation** pour récupérer.
- S’il existe kit SDK .NET Core entrées dans la boîte de dialogue **Ajout/suppression de programmes** , elles seront orphelines.
