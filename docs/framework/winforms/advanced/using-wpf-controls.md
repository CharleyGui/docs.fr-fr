---
title: Utilisation de contrôles WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9883e9d31fc9e3e2ec3ca06b4fc830bcdc338ae
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460695"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a><span data-ttu-id="fabc9-102">Utiliser des contrôles WPF dans les applications Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fabc9-102">Use WPF controls in Windows Forms apps</span></span>

<span data-ttu-id="fabc9-103">Vous pouvez utiliser des contrôles Windows Presentation Foundation (WPF) dans des applications basées sur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fabc9-103">You can use Windows Presentation Foundation (WPF) controls in Windows Forms-based applications.</span></span> <span data-ttu-id="fabc9-104">Bien qu’il s’agisse de deux technologies de vue différentes, elles interagissent correctement.</span><span class="sxs-lookup"><span data-stu-id="fabc9-104">Although these are two different view technologies, they interoperate smoothly.</span></span>

<span data-ttu-id="fabc9-105">Le Concepteur Windows Forms dans Visual Studio fournit un environnement de conception visuelle pour l’hébergement de contrôles Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="fabc9-105">The Windows Forms Designer in Visual Studio provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="fabc9-106">Un contrôle WPF est hébergé par un contrôle Windows Forms spécial nommé <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="fabc9-106">A WPF control is hosted by a special Windows Forms control that's named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="fabc9-107">Ce contrôle permet au contrôle WPF de participer à la mise en page du formulaire et de recevoir des messages du clavier et de la souris.</span><span class="sxs-lookup"><span data-stu-id="fabc9-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="fabc9-108">Au moment du design, vous pouvez réorganiser le contrôle <xref:System.Windows.Forms.Integration.ElementHost> comme vous le feriez pour n’importe quel contrôle Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fabc9-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>

<span data-ttu-id="fabc9-109">Vous pouvez également utiliser des contrôles de Windows Forms dans des applications WPF.</span><span class="sxs-lookup"><span data-stu-id="fabc9-109">You can also use Windows Forms controls in WPF-based applications.</span></span> <span data-ttu-id="fabc9-110">Pour plus d’informations, consultez [conception XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="fabc9-110">For more information, see [Design XAML in Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).</span></span>

## <a name="see-also"></a><span data-ttu-id="fabc9-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fabc9-111">See also</span></span>

- [<span data-ttu-id="fabc9-112">Interopérabilité entre WPF et Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fabc9-112">WPF and Windows Forms interoperation</span></span>](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)
