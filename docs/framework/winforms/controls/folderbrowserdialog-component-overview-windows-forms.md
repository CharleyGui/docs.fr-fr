---
title: Vue d’ensemble du composant FolderBrowserDialog
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: 8b017ba08ae4205e930ac00177c89a89fde17d3b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745724"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a>Vue d’ensemble du composant FolderBrowserDialog (Windows Forms)

Le composant Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> est une boîte de dialogue modale qui permet de parcourir et de sélectionner des dossiers. De nouveaux dossiers peuvent également être créés à partir du composant <xref:System.Windows.Forms.FolderBrowserDialog>.

> [!NOTE]
> Pour sélectionner des fichiers, au lieu de dossiers, utilisez le composant [OpenFileDialog](openfiledialog-component-windows-forms.md) .

Le composant <xref:System.Windows.Forms.FolderBrowserDialog> s’affiche au moment de l’exécution à l’aide de la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>. Définissez la propriété <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> pour déterminer le dossier de niveau supérieur et tous les sous-dossiers qui s’affichent dans l’arborescence de la boîte de dialogue. Une fois la boîte de dialogue affichée, vous pouvez utiliser la propriété <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> pour récupérer le chemin d’accès du dossier qui a été sélectionné.

Lorsqu’il est ajouté à un formulaire, le composant <xref:System.Windows.Forms.FolderBrowserDialog> s’affiche dans la barre d’État en bas de la Concepteur Windows Forms dans Visual Studio.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [Guide pratique pour sélectionner des dossiers avec le composant FolderBrowserDialog Windows Forms](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [FolderBrowserDialog, composant](folderbrowserdialog-component-windows-forms.md)
