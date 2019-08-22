---
title: Utilisation de contrôles WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5ea92b24a2ca30c0ad137d83c8f521a952ad0c6b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658499"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a><span data-ttu-id="dafde-102">Utiliser des contrôles WPF dans les applications Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dafde-102">Use WPF controls in Windows Forms apps</span></span>

<span data-ttu-id="dafde-103">Vous pouvez utiliser des contrôles Windows Presentation Foundation (WPF) dans des applications basées sur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="dafde-103">You can use Windows Presentation Foundation (WPF) controls in Windows Forms-based applications.</span></span> <span data-ttu-id="dafde-104">Bien qu’il s’agisse de deux technologies de vue différentes, elles interagissent correctement.</span><span class="sxs-lookup"><span data-stu-id="dafde-104">Although these are two different view technologies, they interoperate smoothly.</span></span>

<span data-ttu-id="dafde-105">Le Concepteur Windows Forms dans Visual Studio fournit un environnement de conception visuelle pour l’hébergement de contrôles Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="dafde-105">The Windows Forms Designer in Visual Studio provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="dafde-106">Un contrôle WPF est hébergé par un contrôle Windows Forms spécial nommé <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="dafde-106">A WPF control is hosted by a special Windows Forms control that's named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="dafde-107">Ce contrôle permet au contrôle WPF de participer à la mise en page du formulaire et de recevoir des messages du clavier et de la souris.</span><span class="sxs-lookup"><span data-stu-id="dafde-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="dafde-108">Au moment du design, vous pouvez réorganiser le contrôle comme vous le <xref:System.Windows.Forms.Integration.ElementHost> feriez pour n’importe quel contrôle de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="dafde-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>

<span data-ttu-id="dafde-109">Vous pouvez également utiliser des contrôles de Windows Forms dans des applications WPF.</span><span class="sxs-lookup"><span data-stu-id="dafde-109">You can also use Windows Forms controls in WPF-based applications.</span></span> <span data-ttu-id="dafde-110">Pour plus d’informations, consultez [conception XAML dans Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="dafde-110">For more information, see [Design XAML in Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).</span></span>

## <a name="see-also"></a><span data-ttu-id="dafde-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dafde-111">See also</span></span>

- [<span data-ttu-id="dafde-112">Interopérabilité entre WPF et Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dafde-112">WPF and Windows Forms interoperation</span></span>](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)
