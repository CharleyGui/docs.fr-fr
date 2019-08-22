---
title: 'Procédure : copier et coller un contrôle ElementHost au moment du design'
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
ms.openlocfilehash: dfe5244e0c5b61fdf6d940dd16d8c280f013b12c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666182"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a><span data-ttu-id="26dff-102">Procédure : Copier et coller un contrôle ElementHost</span><span class="sxs-lookup"><span data-stu-id="26dff-102">How to: Copy and paste an ElementHost control</span></span>

<span data-ttu-id="26dff-103">Cette procédure vous montre comment copier un contrôle Windows Presentation Foundation (WPF) sur un Windows Form dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="26dff-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form in Visual Studio.</span></span>

1. <span data-ttu-id="26dff-104">Dans Visual Studio, ajoutez un nouveau WPF <xref:System.Windows.Controls.UserControl> à un projet de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="26dff-104">In Visual Studio, add a new WPF <xref:System.Windows.Controls.UserControl> to a Windows Forms project.</span></span> <span data-ttu-id="26dff-105">Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="26dff-105">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="26dff-106">Pour plus d’informations, consultez [Procédure pas à pas : Création d’un contenu WPF sur Windows Forms au moment](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)de la conception.</span><span class="sxs-lookup"><span data-stu-id="26dff-106">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="26dff-107">Dans la fenêtre **Propriétés** , affectez à la valeur <xref:System.Windows.FrameworkElement.Width%2A> des <xref:System.Windows.FrameworkElement.Height%2A> propriétés et `UserControl1` de la valeur **200**.</span><span class="sxs-lookup"><span data-stu-id="26dff-107">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to **200**.</span></span>

3. <span data-ttu-id="26dff-108">Affectez à la <xref:System.Windows.Controls.Control.Background%2A> propriété la valeur **Blue**.</span><span class="sxs-lookup"><span data-stu-id="26dff-108">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span></span>

4. <span data-ttu-id="26dff-109">Générez le projet.</span><span class="sxs-lookup"><span data-stu-id="26dff-109">Build the project.</span></span>

5. <span data-ttu-id="26dff-110">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="26dff-110">Open `Form1` in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="26dff-111">À partir de la **boîte à outils**, `UserControl1` faites glisser une instance de sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="26dff-111">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>

   <span data-ttu-id="26dff-112">Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="26dff-112">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

7. <span data-ttu-id="26dff-113">Avec `elementHost1` l’option sélectionné, appuyez sur **CTRL**+**C** pour le copier dans le presse-papiers.</span><span class="sxs-lookup"><span data-stu-id="26dff-113">With `elementHost1` selected, press **Ctrl**+**C** to copy it to the clipboard.</span></span>

8. <span data-ttu-id="26dff-114">Appuyez sur **CTRL**+**V** pour coller le contrôle copié dans le formulaire.</span><span class="sxs-lookup"><span data-stu-id="26dff-114">Press **Ctrl**+**V** to paste the copied control onto the form.</span></span>

   <span data-ttu-id="26dff-115">Un nouveau <xref:System.Windows.Forms.Integration.ElementHost> contrôle nommé `elementHost2` est créé sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="26dff-115">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>

## <a name="see-also"></a><span data-ttu-id="26dff-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26dff-116">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="26dff-117">Migration et interopérabilité</span><span class="sxs-lookup"><span data-stu-id="26dff-117">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="26dff-118">Utilisation de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="26dff-118">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="26dff-119">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="26dff-119">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
