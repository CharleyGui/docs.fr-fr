---
title: .NET Framework & versions Windows OS
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- versions, .NET Framework
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
ms.openlocfilehash: 486b320ca30323684d301630ad29f8f4615764ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77504050"
---
# <a name="net-framework-versions-and-dependencies"></a>Versions et dépendances de .NET Framework

Chaque version du cadre .NET contient l’heure courante de l’exécution de la langue (CLR), les bibliothèques de classe de base et d’autres bibliothèques gérées. Cet article décrit les principales caractéristiques de .NET Framework par version, fournit des informations sur les versions sous-jacentes CLR et les environnements de développement associés, et identifie les versions qui sont installées par le système d’exploitation Windows (OS).

Chaque nouvelle version de .NET Framework ajoute de nouvelles fonctionnalités mais conserve les fonctionnalités des versions précédentes.

Le CLR est identifié par son propre numéro de version. Le numéro de version cadre .NET est incrémenté à chaque version, mais la version CLR n’est pas toujours incrémentée. Par exemple, .NET Framework 4, 4.5, et les versions ultérieures incluent CLR 4, mais .NET Framework 2.0, 3.0, et 3.5 incluent CLR 2.0. (Il n'y avait pas de version 3 du CLR.)

> [!TIP]
>
> - Pour une liste complète des systèmes d’exploitation pris en charge, voir [exigences du système](../get-started/system-requirements.md).
> - Pour les téléchargements, consultez [Installer le .NET Framework pour les développeurs](../install/guide-for-developers.md).
> - Pour obtenir de l’information sur la détermination des versions de .NET Framework sont installées sur un ordinateur, voir [comment déterminer quelles versions cadre .NET sont installées](how-to-determine-which-versions-are-installed.md).

## <a name="version-information"></a>Informations sur la version

Les tableaux qui suivent résument l’historique de la version cadre .NET et corrèlent chaque version avec Visual Studio, Windows et Windows Server. Visual Studio prend en charge le multi-ciblage, de sorte que vous n’êtes pas limité à la version de .NET Framework qui est répertorié.

- L’icône de la marque de contrôle ✔️ désigne les versions OS sur lesquelles .NET Framework est installé mais doivent être activés [dans le panneau de contrôle](../install/dotnet-35-windows-10.md) (pour Windows) ou via le gestionnaire de serveur (pour Windows Server).
- L’icône de signe plus ➕ dénote les versions OS sur lesquelles .NET Framework n’est pas installé mais peut être installé.

| | |
| - | - |
| [.NET Framework 4.8](#net-framework-48) | [.NET Framework 4.7.2](#net-framework-472) | [.NET Framework 4.7.1](#net-framework-471) | [.NET Framework 4.7](#net-framework-47) |
| [.NET Framework 4.6.2](#net-framework-462) | [.NET Framework 4.6.1](#net-framework-461) | [.NET Framework 4.6](#net-framework-46) | [.NET Framework 4.5.2](#net-framework-452) |
| [.NET Framework 4.5.1](#net-framework-451) | [.NET Framework 4.5](#net-framework-45) | [.NET Cadre 4](#net-framework-4) | [.NET Framework 3.5](#net-framework-35) |
| [.NET Framework 3.0](#net-framework-30) | [.NET Framework 2.0](#net-framework-20) | [.NET Framework 1.1](#net-framework-11) | [.NET Framework 1.0](#net-framework-10) |

### <a name="net-framework-48"></a>.NET Framework 4.8

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-48)
- [Nouveautés de l’accessibilité](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-48)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net48/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Versions Windows**|✔️ 10 mai 2019 Mise à jour<br/>➕ 10 octobre 2018 Mise à jour (Version 1809)<br/>➕ 10 avril 2018 Mise à jour (Version 1803)<br/>➕ mise à jour des créateurs d’automne 10 (Version 1709)<br/>➕ 10 Creators Update (Version 1703)<br/>➕ mise à jour anniversaire du 10e anniversaire (Version 1607)<br/>➕ 8,1<br/>➕7|
|**Versions Windows Server**|➕ Windows Server 2019<br/>➕ Windows Server, version 1809<br/>➕ Windows Server, version 1803<br/>➕ 2016<br/>➕ R2 2012<br/>➕ 2012<br/>➕ R2 SP1 2008|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD:<br/>- 528040 (Windows 10 Mise à jour de mai 2019)<br/>- 528049 (toutes les autres versions du système d’exploitation)<br/>(Voir [les instructions](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-472"></a>.NET Framework 4.7.2

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-472)
- [Nouveautés de l’accessibilité](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-472)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net472/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Inclus dans la version Visual Studio**|2019<sup>1</sup>|
|**Versions Windows**|✔️ 10 octobre 2018 Mise à jour (Version 1809)<br/>✔️ 10 avril 2018 Mise à jour (Version 1803)<br/>➕ mise à jour des créateurs d’automne 10 (Version 1709)<br/>➕ 10 Creators Update (Version 1703)<br/>➕ mise à jour anniversaire du 10e anniversaire (Version 1607)<br/>➕ 8,1<br/>➕7|
|**Versions Windows Server**|✔️ Windows Server 2019<br/>✔️ Windows Server, version 1809<br/>✔️ Windows Server, version 1803<br/>➕ Windows Server, version 1709<br/>➕ 2016<br/>➕ R2 2012<br/>➕ 2012<br/>➕ R2 SP1 2008|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD:<br/>- 461814 (Windows 10 Mise à jour d’octobre 2018)<br/>- 461808 (Mise à jour Windows du 10 avril 2018 et Windows Server, version 1803)<br/>- 461814 (toutes les autres versions du système d’exploitation)<br/>(Voir [les instructions](how-to-determine-which-versions-are-installed.md))|

<sup>1</sup> Nécessite l’installation du **développement de bureau .NET**, **ASP.NET et le développement web**, le **développement Azure**, **le développement Office/SharePoint**, **le développement mobile avec .NET**, ou **.NET Core multi-plateforme** charge de travail de développement.

### <a name="net-framework-471"></a>.NET Framework 4.7.1

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-471)
- [Nouveautés de l’accessibilité](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-471)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net471/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Versions Windows**|✔️ mise à jour des créateurs d’automne 10 (Version 1709)<br/>➕ 10 Creators Update (Version 1703)<br/>➕ mise à jour anniversaire du 10e anniversaire (Version 1607)<br/>➕ 8,1<br/>➕7|
|**Versions Windows Server**|➕ Windows Server, version 1803<br/>✔️ Windows Server, version 1709<br/>➕ 2016<br/>➕ R2 2012<br/>➕ 2012<br/>➕ R2 SP1 2008|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD:<br/>- 461308 (Windows 10 Creators Update et Windows Server, version 1709)<br/>- 461310 (toutes les autres versions de système d’exploitation)<br/>(Voir [les instructions](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-47"></a>.NET Framework 4.7

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-47)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net47/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Versions Windows**|✔️ 10 Creators Update (Version 1703)<br/>➕ mise à jour anniversaire du 10e anniversaire (Version 1607)<br/>➕ 8,1<br/>➕7|
|**Versions Windows Server**|➕ 2016<br/>➕ R2 2012<br/>➕ 2012<br/>➕ R2 SP1 2008|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD:<br/>- 460798 (Windows 10 Creators Update)<br/>- 460805 (toutes les autres versions du système d’exploitation)<br/>(Voir [les instructions](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-462"></a>.NET Framework 4.6.2

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-462)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net462/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Versions Windows**|✔️ mise à jour anniversaire de 10 (Version 1607)<br/>➕ mise à jour du 10 novembre (Version 1511)<br/>➕ 10<br/>➕ 8,1<br />➕ 7|
|**Versions Windows Server**|✔️ 2016<br /><br/>➕ R2 2012<br />➕ 2012<br />➕ R2 SP1 2008|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD:<br /><br/>- 394802 (Mise à jour anniversaire Windows 10 et Windows Server 2016)<br/>- 394806 (toutes les autres versions du système d’exploitation)<br /><br/>(Voir [les instructions](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-461"></a>.NET Framework 4.6.1

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-461)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net461/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Inclus dans la version Visual Studio**|2017<sup>1</sup>|
|**Versions Windows**|✔️ mise à jour du 10 novembre (Version 1511)<br/>➕ 10<br />➕ 8,1<br />➕ 8<br />➕ 7|
|**Versions Windows Server**|➕ R2 2012<br />➕ 2012<br />➕ R2 SP1 2008|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD:<br /><br/>- 394254 (Windows 10 Mise à jour de novembre)<br />- 394271 (toutes les autres versions du système d’exploitation)<br /><br/>(Voir [les instructions](how-to-determine-which-versions-are-installed.md))|

<sup>1</sup> Nécessite l’installation du **développement de bureau .NET**, **ASP.NET et le développement web**, le **développement Azure**, **le développement Office/SharePoint**, **le développement mobile avec .NET**, ou **.NET Core multi-plateforme** charge de travail de développement.

### <a name="net-framework-46"></a>.NET Framework 4.6

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-2015)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net46/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Inclus dans la version Visual Studio**|2015|
|**Versions Windows**|✔️ 10<br /><br />➕ 8,1<br />➕ 8<br />➕ 7<br />➕ Vista|
|**Versions Windows Server**|➕ R2 2012<br />➕ 2012<br />➕ R2 SP1 2008<br />➕ SP2 2008|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD:<br /><br />- 393295 (Windows 10)<br />- 393297 (toutes les autres versions du système d’exploitation)<br /><br />(Voir [les instructions](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-452"></a>.NET Framework 4.5.2

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-452)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net452/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Versions Windows**|➕ 8,1<br />➕ 8<br />➕ 7<br />➕ Vista|
|**Versions Windows Server**|➕ R2 2012<br />➕ 2012<br />➕ R2 SP1 2008<br />➕ SP2 2008|
|**Pour déterminer la version .NET installée**|Utiliser `Release` DWORD 379893<br /><br />(Voir [les instructions](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-451"></a>.NET Framework 4.5.1

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-451)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net451/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Inclus dans la version Visual Studio**|2013|
|**Versions Windows**|✔️ 8,1<br /><br />➕ 8<br />➕ 7<br />➕ Vista|
|**Versions Windows Server**|✔️ R2 2012<br /><br />➕ 2012<br />➕ R2 SP1 2008<br />➕ SP2 2008|
|**Pour déterminer la version .NET installée**|Utilisez `Release` DWORD:<br /><br />- 378675 (Windows 8.1)<br />- 378758 (toutes les autres)<br /><br />(Voir [les instructions](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-45"></a>.NET Framework 4.5

- [Nouvelles fonctionnalités](../whats-new/index.md#whats-new-in-net-framework-45)
- [Notes de publication](https://github.com/Microsoft/dotnet/tree/master/releases/net45/README.md)

|||
|-|-|
|**Version CLR**|4|
|**Inclus dans la version Visual Studio**|2012|
|**Versions Windows**|✔️ 8<br />➕ 7<br />➕ Vista|
|**Versions Windows Server**|✔️ 2012<br />➕ R2 SP1 2008<br />➕ SP2 2008|
|**Pour déterminer la version .NET installée**|Utiliser `Release` DWORD 378389<br /><br />(Voir [les instructions](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-4"></a>.NET Framework 4

[Nouvelles fonctionnalités](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms171868(v=vs.100))

|||
|-|-|
|**Version CLR**|4|
|**Inclus dans la version Visual Studio**|2010|
|**Versions Windows**|➕ 7<br />➕ Vista|
|**Versions Windows Server**|➕ R2 SP1 2008<br />➕ SP2 2008<br />➕ 2003|
|**Pour déterminer la version .NET installée**|Voir [les instructions](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-35"></a>.NET Framework 3.5

[Nouvelles fonctionnalités](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms171868\(v=vs.90\)) :

- LINQ
- Arborescences de l’expression
- Amélioration du soutien ASP.NET au développement d’AJAX
- HashSet (collections)
- DateTimeOffset
- Intégration WCF et WF
- Réseautage peer-to-Peer
- Ajouts pour l’extéabilité

|||
|-|-|
|**Version CLR**|2|
|**Inclus dans la version Visual Studio**|2008|
|**Versions Windows**|✔️ 10\*<br/>✔️ 8,1\*<br />✔️ 8\*<br />✔️ 7<br /><br />➕ Vista|
|**Versions Windows Server**|➕ Windows Server, version 1803\*<br/>➕ Windows Server, version 1709\*<br/>➕ 2016\*<br/>➕ R2 2012\*<br />➕ 2012\*<br /><br />✔️2008 R2 SP1\*<br /><br/>➕ SP2 2008<br />➕ 2003|
|**Pour déterminer la version .NET installée**|Voir [les instructions](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-30"></a>.NET Framework 3.0

[Nouvelles fonctionnalités](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb822048(v=vs.90)) :

- Windows Presentation Foundation
- Windows Communication Foundation
- Windows Workflow Foundation
- Windows CardSpace

|||
|-|-|
|**Version CLR**|2|
|**Versions Windows**|✔️ Vista|
|**Versions Windows Server**|✔️ R2 SP1 2008<br />✔️ SP2 2008\*<br /><br />➕ 2003|
|**Pour déterminer la version .NET installée**|Consultez les [instructions](how-to-determine-which-versions-are-installed.md).|

### <a name="net-framework-20"></a>.NET Framework 2.0

[Nouvelles fonctionnalités](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t357fb32%28v%3dvs.90%29) :

- Génériques
- Debugger modifier et continuer
- Amélioration de l’évolutivité et des performances
- déploiement ClickOnce
- Dans ASP.NET 2.0, de nouveaux contrôles et prise en charge pour un large éventail de navigateurs
- prise en charge 64 bits

|||
|-|-|
|**Version CLR**|2|
|**Inclus dans la version Visual Studio**|2005|
|**Versions Windows**|N/A|
|**Versions Windows Server**|✔️ R2 SP1 2008<br />✔️ SP2 2008<br />✔️ 2003|
|**Pour déterminer la version .NET installée**|Voir [les instructions](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-11"></a>.NET Framework 1.1

[Nouvelles fonctionnalités](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/h88tthh0%28v%3dvs.90%29) :

- ASP.NET des commandes mobiles
- Exécution côte à côte
- Prise en charge d’IPv6

|||
|-|-|
|**Version CLR**|1.1|
|**Inclus dans la version Visual Studio**|2003|
|**Versions Windows**|N/A|
|**Versions Windows Server**|✔️ 2003|
|**Pour déterminer la version .NET installée**|Voir [les instructions](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-10"></a>.NET Framework 1.0

|||
|-|-|
|**Version CLR**|1.0|
|**Inclus dans la version Visual Studio**|Visual Studio .NET|
|**Versions Windows**|N/A|
|**Versions Windows Server**|N/A|
|**Pour déterminer la version .NET installée**|Voir [les instructions](how-to-determine-which-versions-are-installed.md)|

> [!NOTE]
>
> - .NET Framework doit être activé sur ce système d’exploitation via [Control Panel (pour Windows) ou le Server Manager (pour Windows Server)](../install/dotnet-35-windows-10.md#enable-the-net-framework-35-in-control-panel).
> - En général, vous ne devez pas désinstaller les versions de .NET Framework qui sont installés sur votre ordinateur, parce qu’une application que vous utilisez peut dépendre d’une version spécifique et peut se casser si cette version est supprimée. Vous pouvez charger plusieurs versions de .NET Framework sur un seul ordinateur en même temps. Cela signifie que vous pouvez installer .NET Framework sans avoir à désinstaller les versions précédentes. Pour plus d’informations, voir [Getting Started](../get-started/index.md).

## <a name="remarks-for-version-45-and-later"></a>Remarques pour la version 4.5 et plus tard

.NET Framework 4.5 est une mise à jour en place qui remplace .NET Framework 4 sur votre ordinateur, et de même, .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2, et 4.8 sont en place mises à jour à .NET Framework 4.5. La mise à jour place signifie qu’ils utilisent la même version de temps d’exécution, mais les versions d’assemblage sont mises à jour et incluent de nouveaux types et membres. Une fois l’une de ces mises à jour installée, vos applications .NET Framework 4, .NET Framework 4.5, .NET Framework 4.6 ou .NET Framework 4.7 doivent continuer à s’exécuter sans nécessiter de recompilation. En revanche, l'inverse n'est pas vrai. Nous ne recommandons pas d’exécuter des applications qui ciblent une version ultérieure de .NET Framework sur une version antérieure. Par exemple, nous vous déconseillons d’exécuter une application qui cible .NET Framework 4.6 sur .NET Framework 4.5.

Les consignes suivantes s'appliquent :

- Dans Visual Studio, vous pouvez choisir .NET Framework 4.5 comme framework cible pour un projet (cela définit la propriété <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType>) pour compiler le projet en tant qu’assembly ou exécutable .NET Framework 4.5. Cet assembly ou exécutable peut ensuite être utilisé sur tout ordinateur où .NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 ou 4.8 est installé.

- Dans Visual Studio, vous pouvez choisir .NET Framework 4.5.1 comme cadre cible pour un projet de le compiler comme un assemblage .NET Framework 4.5.1 ou exécutable. Exécutez seulement cet assemblage ou exécutable sur les ordinateurs qui ont .NET Framework 4.5.1 ou plus tard installé. Un cadre exécutable qui cible .NET Framework 4.5.1 sera bloqué de s’exécuter sur un ordinateur qui n’a qu’une version antérieure de .NET Framework, comme .NET Framework 4.5, installé. L’utilisateur sera invité à installer .NET Framework 4.5.1. En outre, les assemblages .NET Framework 4.5.1 ne devraient pas être appelés à partir d’une application qui cible une version antérieure du cadre .NET, comme .NET Framework 4.5.

  > [!NOTE]
  > .NET Framework 4.5.1 et .NET Framework 4.5 sont ici utilisés à titre d’exemples uniquement. Le principe décrit s’applique à toute application qui cible une version ultérieure de .NET Framework que celle installée sur le système sur lequel il est en cours d’exécution.

Certains changements dans .NET Framework peuvent nécessiter des modifications à votre code d’application; voir [la compatibilité d’application](application-compatibility.md) avant d’exécuter vos applications existantes avec .NET Framework 4.5 ou des versions ultérieures. Pour plus d’informations sur l’installation de la version actuelle, consultez [Installer le .NET Framework pour les développeurs](../install/guide-for-developers.md). Pour plus d’informations sur le soutien au cadre .NET, voir [.NET Framework politique de soutien officiel](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) sur le site Web .NET.

## <a name="remarks-for-older-versions"></a>Remarques pour les versions plus anciennes

Les versions .NET Framework 2.0, 3.0 et 3.5 sont générées avec la même version du CLR (CLR 2.0). Ces versions représentent les couches successives d'une même installation. Chaque version est générée de façon incrémentielle par-dessus les versions antérieures. Il n’est pas possible d’exécuter les versions 2.0, 3.0 et 3.5 côte à côte sur un ordinateur. Lorsque vous installez la version 3.5, vous obtenez automatiquement les couches 2.0 et 3.0, si bien que les applications conçues pour les versions 2.0, 3.0 et 3.5 peuvent toutes s'exécuter sur la version 3.5. Toutefois, .NET Framework 4 met fin à cette approche en couches et représente, ainsi que ses versions ultérieures (.NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 et 4.8), les couches successives d’une même installation. En commençant par .NET Framework 4, vous pouvez utiliser en cours de traitement, hébergement côte à côte pour exécuter plusieurs versions du CLR en un seul processus. Pour plus d’informations, consultez [Assemblys et exécution côte à côte](../../standard/assembly/side-by-side-execution.md).

En outre, si votre application cible la version 2.0, 3.0 ou 3.5, vos utilisateurs peuvent être tenus d’activer .NET Framework 3.5 sur un ordinateur Windows 8, Windows 8.1 ou Windows 10 avant de pouvoir exécuter votre application. Pour plus d’informations, consultez [Installer le .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8](../install/dotnet-35-windows-10.md).

## <a name="next-steps"></a>Étapes suivantes

- Si vous débutez avec le .NET Framework, consultez la [vue d’ensemble](../get-started/overview.md) pour obtenir une présentation des concepts et des fonctionnalités clés.

- Pour les nouvelles fonctionnalités et améliorations dans le cadre .NET 4.5 et ses versions point, voir [Ce qui est nouveau dans le cadre .NET](../whats-new/index.md).

- Pour plus d’informations sur la migration de votre application vers une version plus récente du cadre .NET, consultez le [guide de migration](index.md).

- Pour plus d’informations sur la façon de déterminer quelles sont les versions ou mises à jour installées sur un ordinateur, consultez [Guide pratique pour déterminer les versions .NET Framework installées](how-to-determine-which-versions-are-installed.md) et [Guide pratique pour déterminer les mises à jour .NET Framework installées](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="see-also"></a>Voir aussi

- [Compatibilité de version](version-compatibility.md)
| [.NET Politique de soutien officiel du Cadre](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Résolution des problèmes liés aux installations et désinstallations bloquées du .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)
