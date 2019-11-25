---
title: Guide pratique pour refuser la mise à niveau automatique de la boîte de dialogue Fichier
ms.date: 03/30/2017
helpviewer_keywords:
- OpenFileDialog [Windows Forms], opt out of automatic upgrade
- file dialog box [Windows Forms], opt out of automatic upgrade
- Windows Vista file dialog box [Windows Forms], opt out of automatic upgrade
- SaveFileDialog [Windows Forms], opt out of automatic upgrade
- AutoUpgradeEnabled property
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
ms.openlocfilehash: bbde260cc7f05226c9b06325b45708e1cde3cf8c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976882"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="3d4b5-102">Guide pratique pour refuser la mise à niveau automatique de la boîte de dialogue Fichier</span><span class="sxs-lookup"><span data-stu-id="3d4b5-102">How To: Opt Out of File Dialog Box Automatic Upgrade</span></span>
<span data-ttu-id="3d4b5-103">Lorsque les classes <xref:System.Windows.Forms.OpenFileDialog> et <xref:System.Windows.Forms.SaveFileDialog> sont utilisées dans une application, leur apparence et leur comportement dépendent de la version de Windows sur laquelle l’application s’exécute.</span><span class="sxs-lookup"><span data-stu-id="3d4b5-103">When the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes are used in an application, their appearance and behavior depend on the version of Windows the application is running on.</span></span> <span data-ttu-id="3d4b5-104">Quand une application créée sur la .NET Framework 2,0 ou une version antérieure s’affiche sur Windows Vista, <xref:System.Windows.Forms.OpenFileDialog> et <xref:System.Windows.Forms.SaveFileDialog> sont automatiquement affichées avec l’apparence et le comportement de Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="3d4b5-104">When an application that was created on the .NET Framework 2.0 or earlier is displayed on Windows Vista, <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> are automatically displayed with the Windows Vista appearance and behavior.</span></span> <span data-ttu-id="3d4b5-105">À partir de la .NET Framework 3,0, vous pouvez refuser la mise à niveau automatique pour afficher les <xref:System.Windows.Forms.OpenFileDialog> et les <xref:System.Windows.Forms.SaveFileDialog> avec une apparence et un comportement de style [!INCLUDE[winxp](../../../../includes/winxp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3d4b5-105">Starting in the .NET Framework 3.0, you can opt out of the automatic upgrade to display the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> with a [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-style appearance and behavior.</span></span>  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="3d4b5-106">Pour refuser la mise à niveau automatique de la boîte de dialogue Fichier</span><span class="sxs-lookup"><span data-stu-id="3d4b5-106">To opt out of file dialog box automatic upgrade</span></span>  
  
1. <span data-ttu-id="3d4b5-107">Définissez la propriété <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> de <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog> sur `false` avant d’afficher la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="3d4b5-107">Set the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property of <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> to `false` before you display the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d4b5-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d4b5-108">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
