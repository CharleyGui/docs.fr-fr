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
# <a name="folderbrowserdialog-component-overview-windows-forms"></a><span data-ttu-id="75e3c-102">Vue d’ensemble du composant FolderBrowserDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="75e3c-102">FolderBrowserDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="75e3c-103">Le composant Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> est une boîte de dialogue modale qui permet de parcourir et de sélectionner des dossiers.</span><span class="sxs-lookup"><span data-stu-id="75e3c-103">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component is a modal dialog box that is used for browsing and selecting folders.</span></span> <span data-ttu-id="75e3c-104">De nouveaux dossiers peuvent également être créés à partir du composant <xref:System.Windows.Forms.FolderBrowserDialog>.</span><span class="sxs-lookup"><span data-stu-id="75e3c-104">New folders can also be created from within the <xref:System.Windows.Forms.FolderBrowserDialog> component.</span></span>

> [!NOTE]
> <span data-ttu-id="75e3c-105">Pour sélectionner des fichiers, au lieu de dossiers, utilisez le composant [OpenFileDialog](openfiledialog-component-windows-forms.md) .</span><span class="sxs-lookup"><span data-stu-id="75e3c-105">To select files, instead of folders, use the [OpenFileDialog](openfiledialog-component-windows-forms.md) component.</span></span>

<span data-ttu-id="75e3c-106">Le composant <xref:System.Windows.Forms.FolderBrowserDialog> s’affiche au moment de l’exécution à l’aide de la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="75e3c-106">The <xref:System.Windows.Forms.FolderBrowserDialog> component is displayed at run time using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="75e3c-107">Définissez la propriété <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> pour déterminer le dossier de niveau supérieur et tous les sous-dossiers qui s’affichent dans l’arborescence de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="75e3c-107">Set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property to determine the top-most folder and any subfolders that will appear within the tree view of the dialog box.</span></span> <span data-ttu-id="75e3c-108">Une fois la boîte de dialogue affichée, vous pouvez utiliser la propriété <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> pour récupérer le chemin d’accès du dossier qui a été sélectionné.</span><span class="sxs-lookup"><span data-stu-id="75e3c-108">Once the dialog box has been shown, you can use the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property to get the path of the folder that was selected.</span></span>

<span data-ttu-id="75e3c-109">Lorsqu’il est ajouté à un formulaire, le composant <xref:System.Windows.Forms.FolderBrowserDialog> s’affiche dans la barre d’État en bas de la Concepteur Windows Forms dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="75e3c-109">When it is added to a form, the <xref:System.Windows.Forms.FolderBrowserDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="75e3c-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75e3c-110">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="75e3c-111">Guide pratique pour sélectionner des dossiers avec le composant FolderBrowserDialog Windows Forms</span><span class="sxs-lookup"><span data-stu-id="75e3c-111">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [<span data-ttu-id="75e3c-112">FolderBrowserDialog, composant</span><span class="sxs-lookup"><span data-stu-id="75e3c-112">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
