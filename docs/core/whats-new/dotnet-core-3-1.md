---
title: Nouveautés de .NET Core 3.1
description: Découvrez les nouvelles fonctionnalités trouvées dans .NET Core 3.1.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 323a2390f079c17b81db01e4e3787916251943bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156554"
---
# <a name="whats-new-in-net-core-31"></a>Nouveautés de .NET Core 3.1

Cet article décrit ce qui est nouveau dans .NET Core 3.1. Cette version contient des améliorations mineures à .NET Core 3.0, en se concentrant sur les petites, mais importantes, correctifs. La caractéristique la plus importante sur .NET Core 3.1 est qu’il s’agit d’une [version de support à long terme (LTS).](#long-term-support)

Si vous utilisez Visual Studio 2019, vous devez mettre à jour sur [Visual Studio 2019 version 16.4](https://visualstudio.microsoft.com/downloads/) pour travailler avec des projets .NET Core 3.1. Pour plus d’informations sur les nouveautés de Visual Studio, voir [What’s New in Visual Studio 2019 version 16.4](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164).

Visual Studio for Mac prend également en charge et inclut .NET Core 3.1 dans Visual Studio pour Mac 8.4.

Pour plus d’informations sur la version, voir [l’annonce .NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).

- [Téléchargez et lancez-vous avec .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) sur Windows, macOS ou Linux.

## <a name="long-term-support"></a>Prise en charge à long terme

.NET Core 3.1 est une version LTS avec le soutien de Microsoft pour les trois prochaines années. Il est fortement recommandé de déplacer vos applications vers .NET Core 3.1. Le cycle de vie actuel d’autres versions majeures est le suivant :

| Libérer | Remarque |
| ------- | ---- |
| .NET Core 3.0 | Fin de vie le 3 mars 2020.     |
| .NET Core 2.2 | Fin de vie le 23 décembre 2019. |
| .NET Core 2.1 | Fin de vie le 21 août 2021.    |

Pour plus d’informations, voir la [politique de soutien .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

## <a name="macos-apphost-and-notarization"></a>macOS appHost et notarisation

*macOS seulement*

En commençant par le .NET Core SDK 3.1 notarié pour macOS, le paramètre appHost est désactivé par défaut. Pour plus d’informations, voir [macOS Catalina Notarization et l’impact sur les téléchargements et les projets .NET Core](../install/macos-notarization-issues.md).

Lorsque le paramètre appHost est activé, .NET Core génère un Mach-O natif exécutable lorsque vous construisez ou publiez. Votre application s’exécute dans le cadre de l’appHost lorsqu’elle est exécutée à partir du code source avec la `dotnet run` commande, ou en commençant le Mach-O exécutable directement.

Sans l’appHost, la seule façon pour un utilisateur de `dotnet <filename.dll>` démarrer une application dépendante du temps [d’exécution](../deploying/index.md#publish-runtime-dependent) est la commande. Un appHost est toujours créé lorsque vous publiez votre application [autonome](../deploying/index.md#publish-self-contained).

Vous pouvez configurer l’appHost au niveau du projet, soit `dotnet` basculer `-p:UseAppHost` l’appHost pour une commande spécifique avec le paramètre :

- Fichier projet

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- Paramètre de ligne de commande

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

Pour plus d’informations sur le `UseAppHost` paramètre, voir [propriétés MSBuild pour Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).

## <a name="windows-forms"></a>Windows Forms

*Windows uniquement*

> [!WARNING]
> Il y a des changements de rupture dans les formulaires Windows.

Les contrôles hérités ont été inclus dans les formulaires Windows qui n’ont pas été disponibles dans la boîte à outils Visual Studio Designer pendant un certain temps. Ceux-ci ont été remplacés par de nouveaux contrôles de retour dans .NET Framework 2.0. Ceux-ci ont été supprimés du bureau SDK pour .NET Core 3.1.

| Contrôle supprimé | Remplacement recommandé | API associées supprimées |
| --------------- | ----------------------- | ----------------------- |
| DataGrid        | <xref:System.Windows.Forms.DataGridView>      | DataGridCell (en)<br/>DataGridRow (en)<br/>DataGridTableCollection<br/>DataGridColumnCollection<br/>Datagridtablestyle<br/>Datagridcolumnstyle<br/>DataGridLineStyle (en)<br/>DataGridParentRowsLabel<br/>DataGridParentsLabelStyle<br/>DataGridBoolColumn<br/>DataGridTextBox (en)<br/>GridColumnStylesCollection<br/>GridTableStylesCollection<br/>HitTestType HitTestType HitTestType HitTest |
| ToolBar         | <xref:System.Windows.Forms.ToolStrip>         | ToolBarAppearance (en) |
| Toolbarbutton   | <xref:System.Windows.Forms.ToolStripButton>   | ToolBarButtonClickEventArgs<br/>ToolBarButtonClickEventHandler<br/>ToolBarButtonStyle (en)<br/>ToolBarTextAlign |
| ContextMenu     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | MenuItemCollection |
| MainMenu        | <xref:System.Windows.Forms.MenuStrip>         |  |
| MenuItem        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

Nous vous recommandons de mettre à jour vos applications à .NET Core 3.1 et de passer aux contrôles de remplacement. Le remplacement des contrôles est un processus simple, essentiellement «trouver et remplacer» sur le type.

## <a name="ccli"></a>C++/CLI

*Windows uniquement*

Un soutien a été ajouté pour la création de projets CMD/CLI (également connus sous le nom de « C «géré ».). Les binaires produits à partir de ces projets sont compatibles avec .NET Core 3.0 et les versions ultérieures.

Pour ajouter de la prise en charge de la version 16.4 de Visual Studio 2019, installez le [développement de bureau avec une charge de travail .](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads) Cette charge de travail ajoute deux modèles à Visual Studio :

- Bibliothèque de classe CLR (.NET Core)
- Projet vide CLR (.NET Core)

## <a name="next-steps"></a>Étapes suivantes

- [Passez en revue les changements de rupture entre .NET Core 3.0 et 3.1.](../compatibility/3.0-3.1.md)
- [Passez en revue les changements de rupture dans .NET Core 3.1 pour les applications Windows Forms.](../compatibility/winforms.md#net-core-31)
