---
title: Configuration requise pour .NET Core sur Windows
description: Découvrez les dépendances nécessaires sur votre machine Windows pour développer et exécuter des applications .NET Core.
f1_keywords:
- NETSDK1045
ms.custom: updateeachvsrelease
ms.date: 09/20/2019
ms.openlocfilehash: c46a1f12ca20c0e21ee205e409a2a5a89e3389b3
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214548"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Configuration requise pour .NET Core sur Windows

Cet article présente les versions de système d’exploitation prises en charge pour exécuter des applications .NET Core sur Windows. Les versions de système d’exploitation et les dépendances prises en charge ci-après s’appliquent aux trois façons de développer des applications .NET Core sur Windows :

* [Ligne de commande](./tutorials/using-with-xplat-cli.md)
* [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)
* [Visual Studio Code](https://code.visualstudio.com/)

En outre, si vous développez sur Windows à l’aide de Visual Studio, la section [conditions préalables au développement d’applications .net core avec Visual Studio](#prerequisites-to-develop-net-core-apps-with-visual-studio) est plus détaillée sur les versions minimales prises en charge pour le développement .net core.

## <a name="net-core-supported-operating-systems"></a>Systèmes d’exploitation pris en charge par .NET Core

Les articles suivants dressent la liste complète des systèmes d’exploitation .NET Core pris en charge par version :

* [.NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
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

## <a name="prerequisites-to-develop-net-core-apps-with-visual-studio"></a>Conditions préalables au développement d’applications .NET Core avec Visual Studio
    
Même si vous pouvez utiliser n’importe quel éditeur pour développer des applications .NET Core à l’aide de l’kit SDK .NET Core, Visual Studio 2017 et versions ultérieures fournissent un environnement de développement intégré pour les applications .NET Core sur Windows.

<a name="vs-mapping"></a>

Une version minimale de Visual Studio est requise pour chaque version de .NET Core. Pour vérifier votre version de Visual Studio :

* Dans le menu **Aide**, choisissez **À propos de Microsoft Visual Studio**.
* Dans la boîte de dialogue **À propos de Microsoft Visual Studio**, vérifiez le numéro de version.

Le tableau suivant répertorie la version minimale pour chaque kit de développement logiciel (SDK) :

| Version de kit SDK .NET Core | Version de Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 3.0                   | Visual Studio 2019 version 16,3 ou ultérieure. |
| 2.2                   | Visual Studio 2017 version 15,9 ou ultérieure. |
| 2.1                   | Visual Studio 2017 version 15,7 ou ultérieure. |
| 1.x                   | Visual Studio 2017 version 15,0 ou ultérieure. |

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

Pour développer des applications .NET Core dans Visual Studio 2019 à l’aide du kit de développement logiciel (SDK) .NET Core 3,0 :

* [Téléchargez et installez Visual Studio 2019 version 16,3 ou ultérieure](/visualstudio/install/install-visual-studio) et sélectionnez l’une des charges de travail suivantes, qui comprend le kit SDK .net Core, selon le type d’application que vous créez :

  * La charge de travail **développement multiplateforme .net Core** dans la section **autres ensembles d’outils** .
  * La charge de travail **ASP.net et développement Web** dans la section **Web & Cloud** .
  * La charge de travail **développement net Desktop** dans la section **Windows** .

L’illustration suivante montre la charge de travail de **développement multiplateforme .net Core** sélectionnée dans l’interface utilisateur de Visual Studio :

![Capture d’écran de l’installation de Visual Studio 2019 avec la charge de travail « développement multiplateforme .NET Core » sélectionnée](./media/windows-prerequisites/vs-2019-workloads.jpg)

Visual Studio 2019 16,3 utilise le kit de développement logiciel (SDK) .NET Core 3,0 par défaut après l’installation de l’une de ces charges de travail.

Si vous souhaitez que vos projets existants utilisent la dernière version du Runtime .NET Core, reciblez chaque projet .NET Core existant vers .NET Core 3,0 à l’aide des instructions suivantes :

* Dans le menu **Projet** , choisissez **Propriétés**.
* Dans le menu de sélection du **Framework cible** , définissez la valeur sur **.net Core 3,0**.

![Capture d’écran de la propriété de projet d’application Visual Studio 2019 avec l’élément de menu Framework cible « .NET Core 3,0 » sélectionné](./media/windows-prerequisites/target-dotnet-core-3-0.jpg)

Une fois que Visual Studio est configuré avec le kit de développement logiciel (SDK) .NET Core 3,0, vous pouvez effectuer les actions suivantes :

* Ouvrir, générer et exécuter les projets .NET Core 1.x et 2.x existants.
* Reciblez les projets .NET Core 1. x et 2. x vers .NET Core 3,0, générez et exécutez.
* Créez de nouveaux projets .NET Core 3,0.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Pour développer des applications .NET Core dans Visual Studio 2017 à l’aide du SDK .NET Core 2.2 :

* [Téléchargez et installez Visual Studio 2017 version 15.9.0 ou version ultérieure](/visualstudio/install/install-visual-studio) en sélectionnant la charge de travail **Développement multiplateforme .NET Core** (dans la section **Autres ensembles d’outils**).

![Capture d’écran de l’installation de Visual Studio 2017 avec la charge de travail « Développement multiplateforme .NET Core » sélectionnée](./media/windows-prerequisites/vs-2017-workloads.jpg)

Une fois l’ensemble d’outils **Développement multiplateforme .NET Core** installé, Visual Studio installe généralement une version précédente du SDK .NET Core.
Par exemple, Visual Studio 2017 15.9 utilise par défaut le SDK .NET Core 2.1 après l’installation de la charge de travail.

Pour mettre à jour Visual Studio afin d’utiliser le SDK .NET Core 2.2 :

 1. Installez le [SDK .NET Core 2.2](https://dotnet.microsoft.com/download).

 1. Si vous souhaitez que votre projet utilise la dernière version du Runtime .NET Core, reciblez chaque projet .NET Core existant ou nouveau dans .NET Core 2,2 à l’aide des instructions suivantes :

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
