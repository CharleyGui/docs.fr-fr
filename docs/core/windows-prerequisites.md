---
title: Configuration requise pour .NET Core sur Windows
description: Découvrez les dépendances nécessaires sur votre machine Windows pour développer et exécuter des applications .NET Core.
ms.custom: updateeachvsrelease
ms.date: 04/08/2019
ms.openlocfilehash: 7b2bf2b8353c4f02fa11e9e7531e0d936007be0b
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970284"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Configuration requise pour .NET Core sur Windows

Cet article présente les versions de système d’exploitation prises en charge pour exécuter des applications .NET Core sur Windows. Les versions de système d’exploitation et les dépendances prises en charge ci-après s’appliquent aux trois façons de développer des applications .NET Core sur Windows :

* [Ligne de commande](tutorials/using-with-xplat-cli.md)
* [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [Visual Studio Code](https://code.visualstudio.com/)

De même, si vous développez sous Windows à l’aide de Visual Studio 2017, la section [Prérequis pour Visual Studio 2017](#prerequisites-with-visual-studio-2017) explore en détail les versions minimales prises en charge pour le développement .NET Core.

## <a name="net-core-supported-operating-systems"></a>Systèmes d’exploitation pris en charge par .NET Core

Les articles suivants dressent la liste complète des systèmes d’exploitation .NET Core pris en charge par version :

* [.NET Core 3.0 (préversion)](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [.NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [.NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [.NET Core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

Pour obtenir des liens de téléchargement et plus d’informations, consultez [Téléchargements .NET](https://dotnet.microsoft.com/download) afin de télécharger la version la plus récente ou [Archive des téléchargements .NET](https://dotnet.microsoft.com/download/archives#dotnet-core) pour les versions antérieures.

## <a name="net-core-dependencies"></a>Dépendances .NET Core

.NET Core 1.1 et ses versions antérieures nécessitent le package redistribuable Visual C++ lors de l’exécution sur des versions de Windows antérieures à Windows 10 et Windows Server 2016. Cette dépendance est installée automatiquement par le programme d’installation de .NET Core.

Vous devez installer [Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) manuellement quand :

* vous installez .NET Core avec le [script du programme d’installation](./tools/dotnet-install-script.md) ;
* vous déployez une application .NET Core autonome.
* Génération du produit à partir de la source.
* Installation de .NET Core via un fichier *.zip*. Ceci peut inclure des serveurs de builds/CI/CD.

> [!NOTE]
> **Pour Windows 8.1 et versions antérieures, ou Windows Server 2012 R2 et versions antérieures :**
>
> Vérifiez que votre installation Windows est à jour et comprend le correctif logiciel [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), installable via Windows Update. Si cette mise à jour n’est pas installée, quand vous lancez une application .NET Core, vous recevez une erreur semblable à celle-ci : `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`
>
> **Pour Windows 7 ou Windows Server 2008 R2 :**
>
> Outre KB2999226, vérifiez également que la mise à jour [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) est installée. Si cette mise à jour n’est pas installée, quand vous lancez une application .NET Core, vous recevez une erreur comme celle-ci : `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.

## <a name="prerequisites-for-net-core-30-preview-3"></a>Configuration requise pour .NET Core 3.0 Preview 3

.NET Core 3.0 Preview 3 nécessite la même configuration que d’autres versions de .NET Core. Toutefois, si vous souhaitez utiliser Visual Studio pour créer des projets .NET Core 3.0, vous devez utiliser [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019). Visual Studio 2019 peut être installée côte à côte avec d’autres versions de Visual Studio, sans générer de conflits.

## <a name="prerequisites-with-visual-studio-2017"></a>Prérequis pour Visual Studio 2017
    
Vous pouvez utiliser l’éditeur de votre choix pour développer des applications .NET Core à l’aide du Kit SDK .NET Core. Visual Studio 2017 fournit un environnement de développement intégré pour les applications .NET Core sur Windows.

Vous trouverez plus d’informations sur les modifications apportées à Visual Studio 2017 dans les [notes de publication](/visualstudio/releasenotes/vs2017-relnotes).

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Pour développer des applications .NET Core dans Visual Studio 2017 à l’aide du SDK .NET Core 2.2 :

 1. [Téléchargez et installez Visual Studio 2017 version 15.9.0 ou version ultérieure](/visualstudio/install/install-visual-studio) en sélectionnant la charge de travail **Développement multiplateforme .NET Core** (dans la section **Autres ensembles d’outils**).

![Capture d’écran de l’installation de Visual Studio 2017 avec la charge de travail « Développement multiplateforme .NET Core » sélectionnée](./media/windows-prerequisites/vs-2017-workloads.jpg)

Une fois l’ensemble d’outils **Développement multiplateforme .NET Core** installé, Visual Studio installe généralement une version précédente du SDK .NET Core.
Par exemple, Visual Studio 2017 15.9 utilise par défaut le SDK .NET Core 2.1 après l’installation de la charge de travail.

Pour mettre à jour Visual Studio afin d’utiliser le SDK .NET Core 2.2 :

 1. Installez le [SDK .NET Core 2.2](https://dotnet.microsoft.com/download).

 1. Si vous souhaitez que votre projet utilise le runtime .NET Core le plus récent, reciblez les projets .NET Core existants ou nouveaux vers .NET Core 2.2 en suivant ces instructions :

    * Dans le menu **Projet** , choisissez **Propriétés**.
    * Dans le menu de sélection du **framework cible**, choisissez **.NET Core 2.2**.

![Capture d’écran de la propriété de projet Application Visual Studio 2017 avec définition de l’élément de menu framework cible sur « .NET Core 2.2 »](./media/windows-prerequisites/targeting-dotnet-core.jpg)

Une fois que vous avez configuré Visual Studio avec le SDK .NET Core 2.2, vous pouvez effectuer les actions suivantes :

* Ouvrir, générer et exécuter les projets .NET Core 1.x et 2.x existants.
* Recibler les projets .NET Core 1.x et 2.x vers .NET Core 2.2, les générer et les exécuter.
* Créer des projets .NET Core 2.2.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Pur développer des applications .NET Core 1.x dans Visual Studio, [téléchargez et installez Visual Studio 2017](/visualstudio/install/install-visual-studio) en sélectionnant la charge de travail **Développement multiplateforme .NET Core** (dans la section **Autres ensembles d’outils**).

![Capture d’écran de l’installation de Visual Studio 2017 avec la charge de travail « Développement multiplateforme .NET Core » sélectionnée](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> Bien que vous puissiez utiliser Visual Studio 2015 pour le développement .NET Core 1.x, nous vous le déconseillons pour les raisons suivantes :
>
> * Les outils .NET Core sont une préversion, qui n’est pas prise en charge.
> * Les projets sont basés sur project.json, configuration qui est dépréciée.
>
> Pour plus d’informations sur les changements de format de projet, consultez la page [Vue d’ensemble des modifications](./tools/cli-msbuild-architecture.md).

---

<a name="vs-mapping"></a>

> [!TIP]
> Pour vérifier votre version de Visual Studio :
>
> * Dans le menu **Aide**, choisissez **À propos de Microsoft Visual Studio**.
> * Dans la boîte de dialogue **À propos de Microsoft Visual Studio**, vérifiez le numéro de version.
>   * Pour les applications .NET Core 3.0 Preview 3, Visual Studio 2019 version 16.0 ou ultérieure.
>   * Pour les applications .NET Core 2.2, Visual Studio 2017 version 15.9 ou ultérieure.
>   * Pour les applications .NET Core 2.1, Visual Studio 2017 version 15.7 ou ultérieure.
>   * Pour les applications .NET Core 1.x, Visual Studio 2017 version 15.0 ou ultérieure.
