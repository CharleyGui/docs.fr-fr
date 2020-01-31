---
title: Vue d’ensemble du composant SaveFileDialog
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: 7609c29b7e932ecee7dc8a289617094bd8d480e2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743101"
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="8931a-102">Vue d'ensemble du composant SaveFileDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="8931a-102">SaveFileDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="8931a-103">Le composant Windows Forms <xref:System.Windows.Forms.SaveFileDialog>  est une boîte de dialogue préconfigurée.</span><span class="sxs-lookup"><span data-stu-id="8931a-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="8931a-104">Il est identique à la boîte de dialogue standard **enregistrer le fichier** utilisée par Windows.</span><span class="sxs-lookup"><span data-stu-id="8931a-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="8931a-105">Il hérite de la classe <xref:System.Windows.Forms.CommonDialog>.</span><span class="sxs-lookup"><span data-stu-id="8931a-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="8931a-106">Utilisation du composant SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="8931a-106">Working with the SaveFileDialog Component</span></span>

<span data-ttu-id="8931a-107">Utilisez-le comme solution simple pour permettre aux utilisateurs d’enregistrer des fichiers au lieu de configurer votre propre boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8931a-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="8931a-108">En vous appuyant sur les boîtes de dialogue Windows standard, les fonctionnalités de base des applications que vous créez sont immédiatement familières aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="8931a-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="8931a-109">Sachez toutefois que lorsque vous utilisez le composant <xref:System.Windows.Forms.SaveFileDialog>, vous devez écrire votre propre logique d’enregistrement des fichiers.</span><span class="sxs-lookup"><span data-stu-id="8931a-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>

<span data-ttu-id="8931a-110">Vous pouvez utiliser la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8931a-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="8931a-111">Vous pouvez ouvrir un fichier en mode lecture/écriture à l’aide de la méthode <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="8931a-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>

<span data-ttu-id="8931a-112">Lorsqu’il est ajouté à un formulaire, le composant <xref:System.Windows.Forms.SaveFileDialog> s’affiche dans la barre d’État en bas de la Concepteur Windows Forms dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8931a-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="8931a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8931a-113">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="8931a-114">SaveFileDialog, composant</span><span class="sxs-lookup"><span data-stu-id="8931a-114">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)
