---
title: .NET Framework & versions du système d’exploitation Windows
description: Découvrez les principales fonctionnalités de chaque version de .NET Framework, y compris les versions et versions du CLR sous-jacentes installées par le système d’exploitation Windows.
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- versions, .NET Framework
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
ms.openlocfilehash: df44786dfd0a384ae2498a94d14b029612450fee
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475474"
---
# <a name="net-framework-versions-and-dependencies"></a>Versions et dépendances de .NET Framework

Chaque version de .NET Framework contient les common language runtime (CLR), les bibliothèques de classes de base et d’autres bibliothèques managées. Cet article décrit les principales fonctionnalités de .NET Framework par version, fournit des informations sur les versions CLR sous-jacentes et les environnements de développement associés, et identifie les versions installées par le système d’exploitation Windows.

Chaque nouvelle version de .NET Framework ajoute de nouvelles fonctionnalités, mais conserve les fonctionnalités des versions précédentes.

Le CLR est identifié par son propre numéro de version. Le numéro de version de .NET Framework est incrémenté à chaque version, mais la version du CLR n’est pas toujours incrémentée. Par exemple, .NET Framework 4, 4,5 et versions ultérieures incluent CLR 4, mais .NET Framework 2,0, 3,0 et 3,5 incluent CLR 2,0. (Il n'y avait pas de version 3 du CLR.)

> [!TIP]
>
> - Pour obtenir la liste complète des systèmes d’exploitation pris en charge, consultez [Configuration système requise](../get-started/system-requirements.md).
> - Pour les téléchargements, consultez [Installer le .NET Framework pour les développeurs](../install/guide-for-developers.md).
> - Pour plus d’informations sur la détermination des versions de .NET Framework installées sur un ordinateur, voir How to determine the [.NET Framework versions installed](how-to-determine-which-versions-are-installed.md).

## <a name="version-information"></a>Informations sur la version

Les tableaux qui suivent résument .NET Framework historique des versions et mettent en corrélation chaque version avec Visual Studio, Windows et Windows Server. Visual Studio prend en charge le multi-ciblage. vous n’êtes donc pas limité à la version de .NET Framework qui est indiquée.

- L’icône de coche ✔️ indique les versions de système d’exploitation sur lesquelles .NET Framework est installé, mais qui doivent être activées [dans le panneau de configuration](../install/dotnet-35-windows-10.md) (pour Windows) ou via le gestionnaire de serveur (pour Windows Server).
- L’icône du signe plus ➕ indique les versions de système d’exploitation sur lesquelles .NET Framework n’est pas installé, mais qui peuvent être installées.

| | |
| - | - |
| [.NET Framework 4,8](#net-framework-48) | [.NET Framework 4.7.2](#net-framework-472) | [.NET Framework 4.7.1](#net-framework-471) | [.NET Framework 4,7](#net-framework-47) |
| [.NET Framework 4.6.2](#net-framework-462) | [.NET Framework 4.6.1](#net-framework-461) | [.NET Framework 4.6](#net-framework-46) | [.NET Framework 4.5.2](#net-framework-452) |
| [.NET Framework 4.5.1](#net-framework-451) | [.NET Framework 4.5](#net-framework-45) | [.NET Framework 4](#net-framework-4) | [.NET Framework 3.5](#net-framework-35) |
| [.NET Framework 3.0](#net-framework-30) | [.NET Framework 2.0](#net-framework-20) | [.NET Framework 1.1](#net-framework-11) | [.NET Framework 1.0](#net-framework-10) |

### <a name="net-framework-48"></a>.NET Framework 4.8

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-48)
- [Nouveautés de l’accessibilité](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-48)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net48/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Versions de Windows**|✔️ 10 mai 2019 mise à jour<br/>➕ 10 octobre 2018 Update (version 1809)<br/>➕ 10 avril 2018 mise à jour (version 1803)<br/>Mise à jour des créateurs de ➕ 10 automne (version 1709)<br/>➕ 10 Creators Update (version 1703)<br/>➕ 10 mise à jour anniversaire (version 1607)<br/>➕ 8,1<br/>➕ 7|
|**Versions de Windows Server**|➕ Windows Server 2019<br/>➕ Windows Server, version 1809<br/>➕ Windows Server, version 1803<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD:<br/>- 528040 (Windows 10 Mise à jour de mai 2019)<br/>- 528049 (toutes les autres versions du système d’exploitation)<br/>(Voir [instructions](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-472"></a>.NET Framework 4.7.2

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-472)
- [Nouveautés de l’accessibilité](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-472)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net472/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Inclus dans la version Visual Studio**|2019<sup>1</sup>|
|**Versions de Windows**|✔️ 10 octobre 2018 Update (version 1809)<br/>✔️ 10 avril 2018 mise à jour (version 1803)<br/>Mise à jour des créateurs de ➕ 10 automne (version 1709)<br/>➕ 10 Creators Update (version 1703)<br/>➕ 10 mise à jour anniversaire (version 1607)<br/>➕ 8,1<br/>➕ 7|
|**Versions de Windows Server**|✔️ Windows Server 2019<br/>✔️ Windows Server, version 1809<br/>✔️ Windows Server, version 1803<br/>➕ Windows Server, version 1709<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD:<br/>- 461814 (Windows 10 Mise à jour d’octobre 2018)<br/>- 461808 (Mise à jour Windows du 10 avril 2018 et Windows Server, version 1803)<br/>- 461814 (toutes les autres versions du système d’exploitation)<br/>(Voir [instructions](how-to-determine-which-versions-are-installed.md))|

<sup>1</sup> nécessite l’installation du développement **.net Desktop**, du développement **ASP.net et Web**, du développement **Azure**, du **développement Office/SharePoint**, du **développement mobile avec .net ou des**charges de travail de **développement multiplateforme .net Core** .

### <a name="net-framework-471"></a>.NET Framework 4.7.1

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-471)
- [Nouveautés de l’accessibilité](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-471)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net471/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Versions de Windows**|Mise à jour des créateurs de ✔️ 10 automne (version 1709)<br/>➕ 10 Creators Update (version 1703)<br/>➕ 10 mise à jour anniversaire (version 1607)<br/>➕ 8,1<br/>➕ 7|
|**Versions de Windows Server**|➕ Windows Server, version 1803<br/>✔️ Windows Server, version 1709<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD:<br/>- 461308 (Windows 10 Creators Update et Windows Server, version 1709)<br/>- 461310 (toutes les autres versions de système d’exploitation)<br/>(Voir [instructions](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-47"></a>.NET Framework 4.7

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-47)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net47/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Versions de Windows**|✔️ 10 Creators Update (version 1703)<br/>➕ 10 mise à jour anniversaire (version 1607)<br/>➕ 8,1<br/>➕ 7|
|**Versions de Windows Server**|➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD:<br/>- 460798 (Windows 10 Creators Update)<br/>- 460805 (toutes les autres versions du système d’exploitation)<br/>(Voir [instructions](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-462"></a>.NET Framework 4.6.2

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-462)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net462/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Versions de Windows**|✔️ 10 mise à jour anniversaire (version 1607)<br/>➕ 10 mise à jour de novembre (version 1511)<br/>➕ 10<br/>➕ 8,1<br />➕ 7|
|**Versions de Windows Server**|✔️ 2016<br /><br/>➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD:<br /><br/>- 394802 (Mise à jour anniversaire Windows 10 et Windows Server 2016)<br/>- 394806 (toutes les autres versions du système d’exploitation)<br /><br/>(Voir [instructions](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-461"></a>.NET Framework 4.6.1

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-461)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net461/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Inclus dans la version Visual Studio**|2017<sup>1</sup>|
|**Versions de Windows**|✔️ 10 mise à jour de novembre (version 1511)<br/>➕ 10<br />➕ 8,1<br />➕ 8<br />➕ 7|
|**Versions de Windows Server**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD:<br /><br/>- 394254 (Windows 10 Mise à jour de novembre)<br />- 394271 (toutes les autres versions du système d’exploitation)<br /><br/>(Voir [instructions](how-to-determine-which-versions-are-installed.md))|

<sup>1</sup> nécessite l’installation du développement **.net Desktop**, du développement **ASP.net et Web**, du développement **Azure**, du **développement Office/SharePoint**, du **développement mobile avec .net ou des**charges de travail de **développement multiplateforme .net Core** .

### <a name="net-framework-46"></a>.NET Framework 4.6

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-2015)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net46/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Inclus dans la version Visual Studio**|2015|
|**Versions de Windows**|✔️ 10<br /><br />➕ 8,1<br />➕ 8<br />➕ 7<br />➕ Vista|
|**Versions de Windows Server**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD:<br /><br />- 393295 (Windows 10)<br />- 393297 (toutes les autres versions du système d’exploitation)<br /><br />(Voir [instructions](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-452"></a>.NET Framework 4.5.2

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-452)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net452/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Versions de Windows**|➕ 8,1<br />➕ 8<br />➕ 7<br />➕ Vista|
|**Versions de Windows Server**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD 379893<br /><br />(Voir [instructions](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-451"></a>.NET Framework 4.5.1

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-451)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net451/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Inclus dans la version Visual Studio**|2013|
|**Versions de Windows**|✔️ 8,1<br /><br />➕ 8<br />➕ 7<br />➕ Vista|
|**Versions de Windows Server**|✔️ 2012 R2<br /><br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD:<br /><br />- 378675 (Windows 8.1)<br />- 378758 (toutes les autres)<br /><br />(Voir [instructions](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-45"></a>.NET Framework 4.5

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-45)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net45/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Inclus dans la version Visual Studio**|2012|
|**Versions de Windows**|✔️ 8<br />➕ 7<br />➕ Vista|
|**Versions de Windows Server**|✔️ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD 378389<br /><br />(Voir [instructions](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-4"></a>.NET Framework 4

[Nouvelles fonctionnalités](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms171868(v=vs.100))

|||
|-|-|
|**Version CLR**|4|
|**Inclus dans la version Visual Studio**|2010|
|**Versions de Windows**|➕ 7<br />➕ Vista|
|**Versions de Windows Server**|➕ 2008 R2 SP1<br />➕ 2008 SP2<br />➕ 2003|
|**Pour déterminer la version .NET installée**|Voir les [instructions](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-35"></a>.NET Framework 3.5

[Nouvelles fonctionnalités](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms171868\(v=vs.90\)) :

- LINQ
- Arborescences de l’expression
- Prise en charge améliorée de ASP.NET pour le développement AJAX
- HashSet (collections)
- DateTimeOffset
- Intégration de WCF et WF
- Réseau pair à pair
- Compléments pour l’extensibilité

|||
|-|-|
|**Version CLR**|2.0|
|**Inclus dans la version Visual Studio**|2008|
|**Versions de Windows**|✔️ 10\*<br/>✔️ 8,1\*<br />✔️ 8\*<br />✔️ 7<br /><br />➕ Vista|
|**Versions de Windows Server**|➕ Windows Server, version 1803\*<br/>➕ Windows Server, version 1709\*<br/>➕ 2016\*<br/>➕ 2012 R2\*<br />➕ 2012\*<br /><br />✔️ 2008 R2 SP1\*<br /><br/>➕ 2008 SP2<br />➕ 2003|
|**Pour déterminer la version .NET installée**|Voir les [instructions](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-30"></a>.NET Framework 3.0

[Nouvelles fonctionnalités](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb822048(v=vs.90)) :

- Windows Presentation Foundation
- Windows Communication Foundation
- Windows Workflow Foundation
- Windows CardSpace

|||
|-|-|
|**Version CLR**|2.0|
|**Versions de Windows**|✔️ Vista|
|**Versions de Windows Server**|✔️ 2008 R2 SP1 *<br />✔️ 2008 SP2\*<br /><br />➕ 2003|
|**Pour déterminer la version .NET installée**|Consultez les [instructions](how-to-determine-which-versions-are-installed.md).|

### <a name="net-framework-20"></a>.NET Framework 2.0

[Nouvelles fonctionnalités](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t357fb32%28v%3dvs.90%29) :

- Génériques
- Modifier & Continuer du débogueur
- Évolutivité et performances améliorées
- déploiement ClickOnce
- Dans ASP.NET 2,0, nouveaux contrôles et prise en charge d’un large éventail de navigateurs
- prise en charge 64 bits

|||
|-|-|
|**Version CLR**|2.0|
|**Inclus dans la version Visual Studio**|2005|
|**Versions de Windows**|N/A|
|**Versions de Windows Server**|✔️ 2008 R2 SP1<br />✔️ 2008 SP2<br />✔️ 2003|
|**Pour déterminer la version .NET installée**|Voir les [instructions](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-11"></a>.NET Framework 1.1

[Nouvelles fonctionnalités](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/h88tthh0%28v%3dvs.90%29) :

- Contrôles mobiles ASP.NET
- Exécution côte à côte
- Prise en charge d’IPv6

|||
|-|-|
|**Version CLR**|1.1|
|**Inclus dans la version Visual Studio**|2003|
|**Versions de Windows**|N/A|
|**Versions de Windows Server**|✔️ 2003|
|**Pour déterminer la version .NET installée**|Voir les [instructions](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-10"></a>.NET Framework 1.0

|||
|-|-|
|**Version CLR**|1.0|
|**Inclus dans la version Visual Studio**|Visual Studio .NET|
|**Versions de Windows**|N/A|
|**Versions de Windows Server**|N/A|
|**Pour déterminer la version .NET installée**|Voir les [instructions](how-to-determine-which-versions-are-installed.md)|

> [!NOTE]
>
> - .NET Framework doit être activée sur ce système d’exploitation par le biais du [panneau de configuration (pour Windows) ou du gestionnaire de serveur (pour Windows Server)](../install/dotnet-35-windows-10.md#enable-the-net-framework-35-in-control-panel).
> - En général, vous ne devez pas désinstaller les versions de .NET Framework installées sur votre ordinateur, car une application que vous utilisez peut dépendre d’une version spécifique et peut s’arrêter si cette version est supprimée. Vous pouvez charger plusieurs versions de .NET Framework sur un seul ordinateur en même temps. Cela signifie que vous pouvez installer .NET Framework sans avoir à désinstaller les versions précédentes. Pour plus d’informations, consultez [prise en main](../get-started/index.md).

## <a name="remarks-for-version-45-and-later"></a>Notes pour la version 4,5 et les versions ultérieures

.NET Framework 4,5 est une mise à jour sur place qui remplace .NET Framework 4 sur votre ordinateur, et de la même façon, .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 et 4,8 sont des mises à jour sur place de .NET Framework 4,5. La mise à jour sur place signifie qu’ils utilisent la même version du runtime, mais les versions d’assembly sont mises à jour et incluent de nouveaux types et membres. Une fois l’une de ces mises à jour installée, vos applications .NET Framework 4, .NET Framework 4.5, .NET Framework 4.6 ou .NET Framework 4.7 doivent continuer à s’exécuter sans nécessiter de recompilation. En revanche, l'inverse n'est pas vrai. Nous vous déconseillons d’exécuter des applications qui ciblent une version ultérieure de .NET Framework sur une version antérieure. Par exemple, nous vous déconseillons d’exécuter une application qui cible .NET Framework 4.6 sur .NET Framework 4.5.

Les consignes suivantes s'appliquent :

- Dans Visual Studio, vous pouvez choisir .NET Framework 4.5 comme framework cible pour un projet (cela définit la propriété <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType>) pour compiler le projet en tant qu’assembly ou exécutable .NET Framework 4.5. Cet assembly ou exécutable peut ensuite être utilisé sur tout ordinateur où .NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 ou 4.8 est installé.

- Dans Visual Studio, vous pouvez choisir .NET Framework 4.5.1 comme version cible du .NET Framework d’un projet pour le compiler en tant qu’assembly ou exécutable .NET Framework 4.5.1. Exécutez cet assembly ou cet exécutable uniquement sur les ordinateurs sur lesquels .NET Framework 4.5.1 ou version ultérieure est installé. L’exécution d’un fichier exécutable ciblant .NET Framework 4.5.1 est bloquée sur un ordinateur sur lequel une version antérieure de .NET Framework, telle que .NET Framework 4,5, est installée. L’utilisateur sera invité à installer .NET Framework 4.5.1. En outre, les assemblys .NET Framework 4.5.1 ne doivent pas être appelés à partir d’une application qui cible une version antérieure de .NET Framework, comme .NET Framework 4,5.

  > [!NOTE]
  > .NET Framework 4.5.1 et .NET Framework 4.5 sont ici utilisés à titre d’exemples uniquement. Le principe décrit s’applique à toutes les applications qui ciblent une version ultérieure de .NET Framework que celle installée sur le système sur lequel elles s’exécutent.

Certaines modifications de .NET Framework peuvent nécessiter des modifications du code de votre application ; consultez [compatibilité des applications](application-compatibility.md) avant d’exécuter vos applications existantes avec .NET Framework 4,5 ou versions ultérieures. Pour plus d’informations sur l’installation de la version actuelle, consultez [Installer le .NET Framework pour les développeurs](../install/guide-for-developers.md). Pour plus d’informations sur la prise en charge de la .NET Framework, consultez [.NET Framework stratégie de support officielle](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) sur le site Web .net.

## <a name="remarks-for-older-versions"></a>Remarques sur les versions antérieures

Les versions .NET Framework 2.0, 3.0 et 3.5 sont générées avec la même version du CLR (CLR 2.0). Ces versions représentent les couches successives d'une même installation. Chaque version est générée de façon incrémentielle par-dessus les versions antérieures. Il n’est pas possible d’exécuter les versions 2,0, 3,0 et 3,5 côte à côte sur un ordinateur. Lorsque vous installez la version 3.5, vous obtenez automatiquement les couches 2.0 et 3.0, si bien que les applications conçues pour les versions 2.0, 3.0 et 3.5 peuvent toutes s'exécuter sur la version 3.5. Toutefois, .NET Framework 4 met fin à cette approche en couches et représente, ainsi que ses versions ultérieures (.NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 et 4.8), les couches successives d’une même installation. À partir de .NET Framework 4, vous pouvez utiliser l’hébergement côte à côte in-process pour exécuter plusieurs versions du CLR dans un processus unique. Pour plus d’informations, consultez [Assemblys et exécution côte à côte](../../standard/assembly/side-by-side-execution.md).

En outre, si votre application cible la version 2,0, 3,0 ou 3,5, vos utilisateurs peuvent être amenés à activer .NET Framework 3,5 sur un ordinateur Windows 8, Windows 8.1 ou Windows 10 avant de pouvoir exécuter votre application. Pour plus d’informations, consultez [Installer le .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8](../install/dotnet-35-windows-10.md).

## <a name="next-steps"></a>Étapes suivantes

- Si vous débutez avec le .NET Framework, consultez la [vue d’ensemble](../get-started/overview.md) pour obtenir une présentation des concepts et des fonctionnalités clés.

- Pour les nouvelles fonctionnalités et améliorations de la .NET Framework 4,5 et de ses versions intermédiaires, consultez [Nouveautés du .NET Framework](../whats-new/index.md).

- Pour plus d’informations sur la migration de votre application vers une version plus récente du .NET Framework, consultez le [Guide de migration](index.md).

- Pour plus d’informations sur la façon de déterminer quelles sont les versions ou mises à jour installées sur un ordinateur, consultez [Guide pratique pour déterminer les versions .NET Framework installées](how-to-determine-which-versions-are-installed.md) et [Guide pratique pour déterminer les mises à jour .NET Framework installées](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="see-also"></a>Voir aussi

- [Compatibilité](version-compatibility.md) 
|  des versions [.NET Framework la stratégie de support officielle](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Résolution des problèmes liés aux installations et désinstallations bloquées du .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)
