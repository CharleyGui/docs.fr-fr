---
title: Nouveautés de .NET Core 3.1
description: Découvrez les nouvelles fonctionnalités de .NET Core 3,1.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 0905cbebb2d966570be4ac3aefb40f4377b97061
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742580"
---
# <a name="whats-new-in-net-core-31"></a>Nouveautés de .NET Core 3.1

Cet article décrit les nouveautés de .NET Core 3,1. Cette version contient des améliorations mineures apportées à .NET Core 3,0, en se concentrant sur les correctifs les plus petits, mais importants. La fonctionnalité la plus importante de .NET Core 3,1 est qu’il s’agit d’une version de [prise en charge à long terme (LTS)](#long-term-support) .

Si vous utilisez Visual Studio 2019, vous devez effectuer la mise à jour vers [Visual studio 2019 version 16,4](https://visualstudio.microsoft.com/downloads/) pour travailler avec les projets .net Core 3,1. Pour plus d’informations sur les nouveautés de Visual Studio, consultez [Nouveautés de Visual studio 2019 version 16,4](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164).

Visual Studio pour Mac prend également en charge et comprend .NET Core 3,1 dans Visual Studio pour Mac 8,4.

Pour plus d’informations sur la version, consultez l' [annonce de .net Core 3,1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).

- [Téléchargez et commencez à utiliser .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1) sur Windows, MacOS ou Linux.

## <a name="long-term-support"></a>Prise en charge à long terme

.NET Core 3,1 est une version LTS avec prise en charge de Microsoft au cours des trois prochaines années. Il est fortement recommandé de déplacer vos applications vers .NET Core 3,1. Le cycle de vie actuel des autres versions majeures est le suivant :

| Version finale | Remarque |
| ------- | ---- |
| .NET Core 3.0 | Fin de vie le 3 mars 2020.     |
| .NET Core 2.2 | Fin de vie le 23 décembre 2019. |
| .NET Core 2.1 | Fin de vie le 21 août 2021.    |

Pour plus d’informations, consultez la [stratégie de support .net Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

## <a name="windows-forms"></a>Windows Forms

*Windows uniquement*

> [!WARNING]
> Il existe des modifications avec rupture dans Windows Forms.

Les contrôles hérités étaient inclus dans Windows Forms qui n’étaient pas disponibles dans la boîte à outils du concepteur Visual Studio pendant un certain temps. Ils ont été remplacés par de nouveaux contrôles dans .NET Framework 2,0. Celles-ci ont été supprimées du kit de développement logiciel (SDK) pour .NET Core 3,1.

| Contrôle supprimé | Remplacement recommandé | API associées supprimées |
| --------------- | ----------------------- | ----------------------- |
| DataGrid        | <xref:System.Windows.Forms.DataGridView>      | DataGridCell<br/>DataGridRow<br/>DataGridTableCollection<br/>DataGridColumnCollection<br/>MappingName<br/>DataGridColumnStyle<br/>DataGridLineStyle<br/>DataGridParentRowsLabel<br/>DataGridParentRowsLabelStyle<br/>DataGridBoolColumn<br/>DataGridTextBox<br/>GridColumnStylesCollection<br/>GridTableStylesCollection<br/>HitTestType |
| ToolBar         | <xref:System.Windows.Forms.ToolStrip>         | ToolBarAppearance |
| ToolBarButton   | <xref:System.Windows.Forms.ToolStripButton>   | ToolBarButtonClickEventArgs<br/>ToolBarButtonClickEventHandler<br/>ToolBarButtonStyle<br/>ToolBarTextAlign |
| ContextMenu     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | MenuItemCollection |
| MainMenu        | <xref:System.Windows.Forms.MenuStrip>         |  |
| MenuItem        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

Nous vous recommandons de mettre à jour vos applications vers .NET Core 3,1 et de passer aux contrôles de remplacement. Le remplacement des contrôles est un processus simple, essentiellement « Rechercher et remplacer » sur le type.

## <a name="ccli"></a>C++/CLI

*Windows uniquement*

Une prise en charge a été C++ajoutée pour la création de projets/CLI C++(également appelés projets « gérés »). Les fichiers binaires générés à partir de ces projets sont compatibles avec .NET Core 3,0 et versions ultérieures.

Pour ajouter la prise C++en charge de/CLI dans Visual Studio 2019 version 16,4, installez le [développement bureautique avec C++ la charge de travail](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads). Cette charge de travail ajoute deux modèles à Visual Studio :

- Bibliothèque de classes CLR (.NET Core)
- Projet CLR vide (.NET Core)

## <a name="next-steps"></a>Étapes suivantes :

- [Passez en revue les modifications avec rupture entre .NET Core 3,0 et 3,1.](../compatibility/3.0-3.1.md)
- [Passez en revue les dernières modifications apportées à .NET Core 3,1 pour les applications Windows Forms.](../compatibility/winforms.md#net-core-31)
