---
title: Vue d'ensemble du composant OpenFileDialog
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: c519b373150a49ee41dbb0c503f7d5a4862477d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728436"
---
# <a name="openfiledialog-component-overview-windows-forms"></a><span data-ttu-id="6e49c-102">Vue d'ensemble du composant OpenFileDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6e49c-102">OpenFileDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="6e49c-103">Le composant Windows Forms <xref:System.Windows.Forms.OpenFileDialog>  est une boîte de dialogue préconfigurée.</span><span class="sxs-lookup"><span data-stu-id="6e49c-103">The Windows Forms <xref:System.Windows.Forms.OpenFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="6e49c-104">Il s’agit de la même boîte de dialogue **ouvrir le fichier** que celle exposée par le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="6e49c-104">It is the same **Open File** dialog box exposed by the Windows operating system.</span></span> <span data-ttu-id="6e49c-105">Il hérite de la classe <xref:System.Windows.Forms.CommonDialog>.</span><span class="sxs-lookup"><span data-stu-id="6e49c-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="use-this-component"></a><span data-ttu-id="6e49c-106">Utiliser ce composant</span><span class="sxs-lookup"><span data-stu-id="6e49c-106">Use this component</span></span>

<span data-ttu-id="6e49c-107">Utilisez ce composant dans votre application Windows comme solution simple pour la sélection de fichiers au lieu de configurer votre propre boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6e49c-107">Use this component within your Windows-based application as a simple solution for file selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="6e49c-108">En vous appuyant sur des boîtes de dialogue Windows standard, vous pouvez créer des applications dont la fonction de base est immédiatement familière aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="6e49c-108">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="6e49c-109">Sachez toutefois que lorsque vous utilisez le composant <xref:System.Windows.Forms.OpenFileDialog>, vous devez écrire votre propre logique d’ouverture de fichier.</span><span class="sxs-lookup"><span data-stu-id="6e49c-109">Be aware, however, that when using the <xref:System.Windows.Forms.OpenFileDialog> component, you must write your own file-opening logic.</span></span>

<span data-ttu-id="6e49c-110">Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6e49c-110">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="6e49c-111">Vous pouvez permettre aux utilisateurs de sélectionner plusieurs fichiers à ouvrir avec la propriété <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A>.</span><span class="sxs-lookup"><span data-stu-id="6e49c-111">You can enable users to multi-select files to be opened with the <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> property.</span></span> <span data-ttu-id="6e49c-112">En outre, vous pouvez utiliser la propriété <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> pour déterminer si une case à cocher en lecture seule apparaît dans la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6e49c-112">Additionally, you can use the <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> property to determine if a read-only check box appears in the dialog box.</span></span> <span data-ttu-id="6e49c-113">La propriété <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> indique si la case à cocher en lecture seule est activée.</span><span class="sxs-lookup"><span data-stu-id="6e49c-113">The <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> property indicates whether the read-only check box is selected.</span></span> <span data-ttu-id="6e49c-114">Enfin, la propriété <xref:System.Windows.Forms.FileDialog.Filter%2A> définit la chaîne de filtre de nom de fichier actuelle, qui détermine les choix qui s’affichent dans la zone « types de fichiers » de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6e49c-114">Finally, the <xref:System.Windows.Forms.FileDialog.Filter%2A> property sets the current file name filter string, which determines the choices that appear in the "Files of type" box in the dialog box.</span></span>

<span data-ttu-id="6e49c-115">Lorsqu’il est ajouté à un formulaire, le composant <xref:System.Windows.Forms.OpenFileDialog> s’affiche dans la barre d’État en bas de la Concepteur Windows Forms dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6e49c-115">When it is added to a form, the <xref:System.Windows.Forms.OpenFileDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e49c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e49c-116">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="6e49c-117">OpenFileDialog, composant</span><span class="sxs-lookup"><span data-stu-id="6e49c-117">OpenFileDialog Component</span></span>](openfiledialog-component-windows-forms.md)
