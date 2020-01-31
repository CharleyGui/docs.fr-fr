---
title: 'Comment : activer des styles visuels dans une application hybride'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
ms.openlocfilehash: dd52313e9100f9c6a1141b53ccc5a23a4b54410a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789918"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a><span data-ttu-id="6c510-102">Comment : activer des styles visuels dans une application hybride</span><span class="sxs-lookup"><span data-stu-id="6c510-102">How to: Enable Visual Styles in a Hybrid Application</span></span>
<span data-ttu-id="6c510-103">Cette rubrique montre comment activer des styles visuels sur un contrôle de Windows Forms hébergé dans une application basée sur des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c510-103">This topic shows how to enable visual styles on a Windows Forms control hosted in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
 <span data-ttu-id="6c510-104">Si votre application appelle la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>, la plupart de vos contrôles Windows Forms utiliseront automatiquement les styles visuels.</span><span class="sxs-lookup"><span data-stu-id="6c510-104">If your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method, most of your Windows Forms controls will automatically use visual styles.</span></span> <span data-ttu-id="6c510-105">Pour plus d’informations, consultez [Rendu des contrôles avec les styles visuels](../../winforms/controls/rendering-controls-with-visual-styles.md).</span><span class="sxs-lookup"><span data-stu-id="6c510-105">For more information, see [Rendering Controls with Visual Styles](../../winforms/controls/rendering-controls-with-visual-styles.md).</span></span>  
  
 <span data-ttu-id="6c510-106">Pour obtenir le code complet des tâches illustrées dans cette rubrique, consultez [activation de styles visuels dans un exemple d’application hybride](https://go.microsoft.com/fwlink/?LinkID=159986).</span><span class="sxs-lookup"><span data-stu-id="6c510-106">For a complete code listing of the tasks illustrated in this topic, see [Enabling Visual Styles in a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=159986).</span></span>  
  
## <a name="enabling-windows-forms-visual-styles"></a><span data-ttu-id="6c510-107">Activation de styles visuels Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6c510-107">Enabling Windows Forms Visual Styles</span></span>  
  
#### <a name="to-enable-windows-forms-visual-styles"></a><span data-ttu-id="6c510-108">Pour activer les styles visuels Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6c510-108">To enable Windows Forms visual styles</span></span>  
  
1. <span data-ttu-id="6c510-109">Créez un projet d’application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nommé `HostingWfWithVisualStyles`.</span><span class="sxs-lookup"><span data-stu-id="6c510-109">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Application project named `HostingWfWithVisualStyles`.</span></span>  
  
2. <span data-ttu-id="6c510-110">Dans l’Explorateur de solutions, ajoutez des références aux assemblys suivants.</span><span class="sxs-lookup"><span data-stu-id="6c510-110">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    - <span data-ttu-id="6c510-111">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="6c510-111">WindowsFormsIntegration</span></span>  
  
    - <span data-ttu-id="6c510-112">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="6c510-112">System.Windows.Forms</span></span>  
  
3. <span data-ttu-id="6c510-113">Dans la boîte à outils, double-cliquez sur l’icône <xref:System.Windows.Controls.Grid> pour placer un élément <xref:System.Windows.Controls.Grid> sur l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="6c510-113">In the Toolbox, double-click the <xref:System.Windows.Controls.Grid> icon to place a <xref:System.Windows.Controls.Grid> element on the design surface.</span></span>  
  
4. <span data-ttu-id="6c510-114">Dans la Fenêtre Propriétés, définissez les valeurs des propriétés <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.Width%2A> sur **auto**.</span><span class="sxs-lookup"><span data-stu-id="6c510-114">In the Properties window, set the values of the <xref:System.Windows.FrameworkElement.Height%2A> and <xref:System.Windows.FrameworkElement.Width%2A> properties to **Auto**.</span></span>  
  
5. <span data-ttu-id="6c510-115">Dans Mode Création ou la vue XAML, sélectionnez l' <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="6c510-115">In Design view or XAML view, select the <xref:System.Windows.Window>.</span></span>  
  
6. <span data-ttu-id="6c510-116">Dans l’Fenêtre Propriétés, cliquez sur l’onglet **événements** .</span><span class="sxs-lookup"><span data-stu-id="6c510-116">In the Properties window, click the **Events** tab.</span></span>  
  
7. <span data-ttu-id="6c510-117">Double-cliquez sur l’événement <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="6c510-117">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>
  
8. <span data-ttu-id="6c510-118">Dans MainWindow. Xaml. vb ou MainWindow.xaml.cs, insérez le code suivant pour gérer l’événement <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="6c510-118">In MainWindow.xaml.vb or MainWindow.xaml.cs, insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfWithVisualStyles#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. <span data-ttu-id="6c510-119">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="6c510-119">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="6c510-120">Le contrôle Windows Forms est peint avec les styles visuels.</span><span class="sxs-lookup"><span data-stu-id="6c510-120">The Windows Forms control is painted with visual styles.</span></span>  
  
## <a name="disabling-windows-forms-visual-styles"></a><span data-ttu-id="6c510-121">Désactivation de styles visuels Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6c510-121">Disabling Windows Forms Visual Styles</span></span>  
 <span data-ttu-id="6c510-122">Pour désactiver les styles visuels, supprimez simplement l’appel à la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c510-122">To disable visual styles, simply remove the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
#### <a name="to-disable-windows-forms-visual-styles"></a><span data-ttu-id="6c510-123">Pour désactiver les styles visuels Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6c510-123">To disable Windows Forms visual styles</span></span>  
  
1. <span data-ttu-id="6c510-124">Ouvrez MainWindow.xaml.vb ou MainWindow.xaml.cs dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="6c510-124">Open MainWindow.xaml.vb or MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2. <span data-ttu-id="6c510-125">Commentez l’appel à la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c510-125">Comment out the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
3. <span data-ttu-id="6c510-126">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="6c510-126">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="6c510-127">Le contrôle Windows Forms est peint avec le style système par défaut.</span><span class="sxs-lookup"><span data-stu-id="6c510-127">The Windows Forms control is painted with the default system style.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c510-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c510-128">See also</span></span>

- <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>
- <xref:System.Windows.Forms.VisualStyles>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="6c510-129">Rendu des contrôles avec les styles visuels</span><span class="sxs-lookup"><span data-stu-id="6c510-129">Rendering Controls with Visual Styles</span></span>](../../winforms/controls/rendering-controls-with-visual-styles.md)
- [<span data-ttu-id="6c510-130">Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="6c510-130">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
