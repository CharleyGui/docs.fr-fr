---
title: 'Comment : copier et coller un contrôle ElementHost au moment du design'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3d1887eb1161f714962c2c26d6fe618749b26c0f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197482"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a><span data-ttu-id="b4db9-102">Comment : copier et coller un contrôle ElementHost</span><span class="sxs-lookup"><span data-stu-id="b4db9-102">How to: Copy and paste an ElementHost control</span></span>

<span data-ttu-id="b4db9-103">Cette procédure vous montre comment copier un contrôle Windows Presentation Foundation (WPF) sur un Windows Form dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b4db9-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form in Visual Studio.</span></span>

1. <span data-ttu-id="b4db9-104">Dans Visual Studio, ajoutez un nouveau <xref:System.Windows.Controls.UserControl> WPF à un projet Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b4db9-104">In Visual Studio, add a new WPF <xref:System.Windows.Controls.UserControl> to a Windows Forms project.</span></span> <span data-ttu-id="b4db9-105">Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="b4db9-105">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="b4db9-106">Pour plus d’informations, consultez [procédure pas à pas : création de contenu WPF sur Windows Forms au moment du design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="b4db9-106">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="b4db9-107">Dans la fenêtre **Propriétés** , définissez la valeur des propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> de `UserControl1` sur **200**.</span><span class="sxs-lookup"><span data-stu-id="b4db9-107">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to **200**.</span></span>

3. <span data-ttu-id="b4db9-108">Affectez à la propriété <xref:System.Windows.Controls.Control.Background%2A> la valeur **Blue**.</span><span class="sxs-lookup"><span data-stu-id="b4db9-108">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span></span>

4. <span data-ttu-id="b4db9-109">Générez le projet.</span><span class="sxs-lookup"><span data-stu-id="b4db9-109">Build the project.</span></span>

5. <span data-ttu-id="b4db9-110">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b4db9-110">Open `Form1` in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="b4db9-111">À partir de la **boîte à outils**, faites glisser une instance de `UserControl1` vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="b4db9-111">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>

   <span data-ttu-id="b4db9-112">Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="b4db9-112">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

7. <span data-ttu-id="b4db9-113">Avec `elementHost1` sélectionné, appuyez sur **Ctrl**+**C** pour le copier dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="b4db9-113">With `elementHost1` selected, press **Ctrl**+**C** to copy it to the clipboard.</span></span>

8. <span data-ttu-id="b4db9-114">Appuyez sur **Ctrl**+**V** pour coller le contrôle copié dans le formulaire.</span><span class="sxs-lookup"><span data-stu-id="b4db9-114">Press **Ctrl**+**V** to paste the copied control onto the form.</span></span>

   <span data-ttu-id="b4db9-115">Un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost2` est créé sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="b4db9-115">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4db9-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4db9-116">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="b4db9-117">Migration et interopérabilité</span><span class="sxs-lookup"><span data-stu-id="b4db9-117">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="b4db9-118">Utilisation de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="b4db9-118">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="b4db9-119">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b4db9-119">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
