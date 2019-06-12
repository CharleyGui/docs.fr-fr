---
title: Contrôles Windows Forms et contrôles WPF équivalents
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
ms.assetid: 8a157e6b-8054-46db-a5cf-a78966acc7a1
ms.openlocfilehash: acb8095b32364f1e22330f22df60085016bdc664
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66834037"
---
# <a name="windows-forms-controls-and-equivalent-wpf-controls"></a><span data-ttu-id="f4389-102">Contrôles Windows Forms et contrôles WPF équivalents</span><span class="sxs-lookup"><span data-stu-id="f4389-102">Windows Forms Controls and Equivalent WPF Controls</span></span>
<span data-ttu-id="f4389-103">Nombreux [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôles ont équivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôles, mais certains [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôles n’ont pas d’équivalents dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f4389-103">Many [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls, but some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have no equivalents in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="f4389-104">Cette rubrique compare les types de contrôle fournis par les deux technologies.</span><span class="sxs-lookup"><span data-stu-id="f4389-104">This topic compares control types provided by the two technologies.</span></span>  
  
 <span data-ttu-id="f4389-105">Vous pouvez toujours utiliser l’interopérabilité à l’hôte [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôles qui n’ont pas d’équivalents dans votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-en fonction des applications.</span><span class="sxs-lookup"><span data-stu-id="f4389-105">You can always use interoperation to host [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls that do not have equivalents in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
 <span data-ttu-id="f4389-106">Le tableau suivant montre quelles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôles et composants ont équivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôlent les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="f4389-106">The following table shows which [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and components have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control functionality.</span></span>  
  
|<span data-ttu-id="f4389-107">contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f4389-107">Windows Forms control</span></span>|<span data-ttu-id="f4389-108">Contrôle WPF équivalent</span><span class="sxs-lookup"><span data-stu-id="f4389-108">WPF equivalent control</span></span>|<span data-ttu-id="f4389-109">Notes</span><span class="sxs-lookup"><span data-stu-id="f4389-109">Remarks</span></span>|  
|---------------------------|----------------------------|-------------|  
|<xref:System.Windows.Forms.BindingNavigator>|<span data-ttu-id="f4389-110">Aucun contrôle équivalent.</span><span class="sxs-lookup"><span data-stu-id="f4389-110">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.BindingSource>|<xref:System.Windows.Data.CollectionViewSource>||  
|<xref:System.Windows.Forms.Button>|<xref:System.Windows.Controls.Button>||  
|<xref:System.Windows.Forms.CheckBox>|<xref:System.Windows.Controls.CheckBox>||  
|<xref:System.Windows.Forms.CheckedListBox>|<span data-ttu-id="f4389-111"><xref:System.Windows.Controls.ListBox> avec la composition.</span><span class="sxs-lookup"><span data-stu-id="f4389-111"><xref:System.Windows.Controls.ListBox> with composition.</span></span>||  
|<xref:System.Windows.Forms.ColorDialog>|<span data-ttu-id="f4389-112">Aucun contrôle équivalent.</span><span class="sxs-lookup"><span data-stu-id="f4389-112">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ComboBox>|<xref:System.Windows.Controls.ComboBox>|<span data-ttu-id="f4389-113"><xref:System.Windows.Controls.ComboBox> ne prend pas en charge la saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="f4389-113"><xref:System.Windows.Controls.ComboBox> does not support auto-complete.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<xref:System.Windows.Controls.ContextMenu>||  
|<xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Controls.DataGrid>||  
|<xref:System.Windows.Forms.DateTimePicker>|<xref:System.Windows.Controls.DatePicker>||  
|<xref:System.Windows.Forms.DomainUpDown>|<span data-ttu-id="f4389-114"><xref:System.Windows.Controls.TextBox> et deux <xref:System.Windows.Controls.Primitives.RepeatButton> contrôles.</span><span class="sxs-lookup"><span data-stu-id="f4389-114"><xref:System.Windows.Controls.TextBox> and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.ErrorProvider>|<span data-ttu-id="f4389-115">Aucun contrôle équivalent.</span><span class="sxs-lookup"><span data-stu-id="f4389-115">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FlowLayoutPanel>|<span data-ttu-id="f4389-116"><xref:System.Windows.Controls.WrapPanel> ou <xref:System.Windows.Controls.StackPanel></span><span class="sxs-lookup"><span data-stu-id="f4389-116"><xref:System.Windows.Controls.WrapPanel> or <xref:System.Windows.Controls.StackPanel></span></span>||  
|<xref:System.Windows.Forms.FolderBrowserDialog>|<span data-ttu-id="f4389-117">Aucun contrôle équivalent.</span><span class="sxs-lookup"><span data-stu-id="f4389-117">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FontDialog>|<span data-ttu-id="f4389-118">Aucun contrôle équivalent.</span><span class="sxs-lookup"><span data-stu-id="f4389-118">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Window>|<span data-ttu-id="f4389-119"><xref:System.Windows.Window> ne prend pas en charge les fenêtres enfants.</span><span class="sxs-lookup"><span data-stu-id="f4389-119"><xref:System.Windows.Window> does not support child windows.</span></span>|  
|<xref:System.Windows.Forms.GroupBox>|<xref:System.Windows.Controls.GroupBox>||  
|<xref:System.Windows.Forms.HelpProvider>|<span data-ttu-id="f4389-120">Aucun contrôle équivalent.</span><span class="sxs-lookup"><span data-stu-id="f4389-120">No equivalent control.</span></span>|<span data-ttu-id="f4389-121">Aucune aide F1.</span><span class="sxs-lookup"><span data-stu-id="f4389-121">No F1 Help.</span></span> <span data-ttu-id="f4389-122">« Qu’est-ce » aide est remplacée par l’info-bulles.</span><span class="sxs-lookup"><span data-stu-id="f4389-122">"What's This" Help is replaced by ToolTips.</span></span>|  
|<xref:System.Windows.Forms.HScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="f4389-123">Le défilement est intégré aux contrôles de conteneur.</span><span class="sxs-lookup"><span data-stu-id="f4389-123">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.ImageList>|<span data-ttu-id="f4389-124">Aucun contrôle équivalent.</span><span class="sxs-lookup"><span data-stu-id="f4389-124">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Label>|<xref:System.Windows.Controls.Label>||  
|<xref:System.Windows.Forms.LinkLabel>|<span data-ttu-id="f4389-125">Aucun contrôle équivalent.</span><span class="sxs-lookup"><span data-stu-id="f4389-125">No equivalent control.</span></span>|<span data-ttu-id="f4389-126">Vous pouvez utiliser la <xref:System.Windows.Documents.Hyperlink> classe pour héberger des liens hypertexte dans le contenu dynamique.</span><span class="sxs-lookup"><span data-stu-id="f4389-126">You can use the <xref:System.Windows.Documents.Hyperlink> class to host hyperlinks within flow content.</span></span>|  
|<xref:System.Windows.Forms.ListBox>|<xref:System.Windows.Controls.ListBox>||  
|<xref:System.Windows.Forms.ListView>|<xref:System.Windows.Controls.ListView>|<span data-ttu-id="f4389-127">Le <xref:System.Windows.Controls.ListView> contrôle fournit une vue de détails en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="f4389-127">The <xref:System.Windows.Controls.ListView> control provides a read-only details view.</span></span>|  
|<xref:System.Windows.Forms.MaskedTextBox>|<span data-ttu-id="f4389-128">Aucun contrôle équivalent.</span><span class="sxs-lookup"><span data-stu-id="f4389-128">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.MenuStrip>|<xref:System.Windows.Controls.Menu>|<span data-ttu-id="f4389-129"><xref:System.Windows.Controls.Menu> style de contrôle peut se rapprocher le comportement et l’apparence de la <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="f4389-129"><xref:System.Windows.Controls.Menu> control styling can approximate the behavior and appearance of the <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType> class.</span></span>|  
|<xref:System.Windows.Forms.MonthCalendar>|<xref:System.Windows.Controls.Calendar>||  
|<xref:System.Windows.Forms.NotifyIcon>|<span data-ttu-id="f4389-130">Aucun contrôle équivalent.</span><span class="sxs-lookup"><span data-stu-id="f4389-130">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.NumericUpDown>|<span data-ttu-id="f4389-131"><xref:System.Windows.Controls.TextBox> et deux <xref:System.Windows.Controls.Primitives.RepeatButton> contrôles.</span><span class="sxs-lookup"><span data-stu-id="f4389-131"><xref:System.Windows.Controls.TextBox> and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:Microsoft.Win32.OpenFileDialog>|<span data-ttu-id="f4389-132">Le <xref:Microsoft.Win32.OpenFileDialog> classe est un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper autour de le [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] contrôle.</span><span class="sxs-lookup"><span data-stu-id="f4389-132">The <xref:Microsoft.Win32.OpenFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] control.</span></span>|  
|<xref:System.Windows.Forms.PageSetupDialog>|<span data-ttu-id="f4389-133">Aucun contrôle équivalent.</span><span class="sxs-lookup"><span data-stu-id="f4389-133">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Panel>|<xref:System.Windows.Controls.Canvas>||  
|<xref:System.Windows.Forms.PictureBox>|<xref:System.Windows.Controls.Image>||  
|<xref:System.Windows.Forms.PrintDialog>|<xref:System.Windows.Controls.PrintDialog>||  
|<xref:System.Drawing.Printing.PrintDocument>|<span data-ttu-id="f4389-134">Aucun contrôle équivalent.</span><span class="sxs-lookup"><span data-stu-id="f4389-134">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.PrintPreviewControl>|<xref:System.Windows.Controls.DocumentViewer>||  
|<xref:System.Windows.Forms.PrintPreviewDialog>|<span data-ttu-id="f4389-135">Aucun contrôle équivalent.</span><span class="sxs-lookup"><span data-stu-id="f4389-135">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ProgressBar>|<xref:System.Windows.Controls.ProgressBar>||  
|<xref:System.Windows.Forms.PropertyGrid>|<span data-ttu-id="f4389-136">Aucun contrôle équivalent.</span><span class="sxs-lookup"><span data-stu-id="f4389-136">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.RadioButton>|<xref:System.Windows.Controls.RadioButton>||  
|<xref:System.Windows.Forms.RichTextBox>|<xref:System.Windows.Controls.RichTextBox>||  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:Microsoft.Win32.SaveFileDialog>|<span data-ttu-id="f4389-137">Le <xref:Microsoft.Win32.SaveFileDialog> classe est un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper autour de le [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] contrôle.</span><span class="sxs-lookup"><span data-stu-id="f4389-137">The <xref:Microsoft.Win32.SaveFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] control.</span></span>|  
|<xref:System.Windows.Forms.ScrollableControl>|<xref:System.Windows.Controls.ScrollViewer>||  
|<xref:System.Media.SoundPlayer>|<xref:System.Windows.Media.MediaPlayer>||  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Controls.GridSplitter>||  
|<xref:System.Windows.Forms.StatusStrip>|<xref:System.Windows.Controls.Primitives.StatusBar>||  
|<xref:System.Windows.Forms.TabControl>|<xref:System.Windows.Controls.TabControl>||  
|<xref:System.Windows.Forms.TableLayoutPanel>|<xref:System.Windows.Controls.Grid>||  
|<xref:System.Windows.Forms.TextBox>|<xref:System.Windows.Controls.TextBox>||  
|<xref:System.Windows.Forms.Timer>|<xref:System.Windows.Threading.DispatcherTimer>||  
|<xref:System.Windows.Forms.ToolStrip>|<xref:System.Windows.Controls.ToolBar>||  
|<xref:System.Windows.Forms.ToolStripContainer>|<span data-ttu-id="f4389-138"><xref:System.Windows.Controls.ToolBar> avec la composition.</span><span class="sxs-lookup"><span data-stu-id="f4389-138"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="f4389-139"><xref:System.Windows.Controls.ToolBar> avec la composition.</span><span class="sxs-lookup"><span data-stu-id="f4389-139"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDownMenu>|<span data-ttu-id="f4389-140"><xref:System.Windows.Controls.ToolBar> avec la composition.</span><span class="sxs-lookup"><span data-stu-id="f4389-140"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripPanel>|<span data-ttu-id="f4389-141"><xref:System.Windows.Controls.ToolBar> avec la composition.</span><span class="sxs-lookup"><span data-stu-id="f4389-141"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolTip>|<xref:System.Windows.Controls.ToolTip>||  
|<xref:System.Windows.Forms.TrackBar>|<xref:System.Windows.Controls.Slider>||  
|<xref:System.Windows.Forms.TreeView>|<xref:System.Windows.Controls.TreeView>||  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Controls.UserControl>||  
|<xref:System.Windows.Forms.VScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="f4389-142">Le défilement est intégré aux contrôles de conteneur.</span><span class="sxs-lookup"><span data-stu-id="f4389-142">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.WebBrowser>|<span data-ttu-id="f4389-143"><xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f4389-143"><xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType></span></span>|<span data-ttu-id="f4389-144">Le <xref:System.Windows.Controls.Frame> contrôle peut héberger des pages HTML.</span><span class="sxs-lookup"><span data-stu-id="f4389-144">The <xref:System.Windows.Controls.Frame> control can host HTML pages.</span></span><br /><br /> <span data-ttu-id="f4389-145">À compter de .NET Framework 3.5 SP1, le <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> contrôle peut héberger des pages HTML et stocker également le <xref:System.Windows.Controls.Frame> contrôle.</span><span class="sxs-lookup"><span data-stu-id="f4389-145">Starting in the .NET Framework 3.5 SP1, the <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> control can host HTML pages and also backs the <xref:System.Windows.Controls.Frame> control.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4389-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4389-146">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- <span data-ttu-id="f4389-147">[Concepteur WPF pour les Windows Forms aux développeurs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cc165605(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f4389-147">[WPF Designer for Windows Forms Developers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cc165605(v=vs.100))</span></span>
- [<span data-ttu-id="f4389-148">Procédure pas à pas : Hébergement d’un contrôle de formulaires Windows dans WPF</span><span class="sxs-lookup"><span data-stu-id="f4389-148">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="f4389-149">Procédure pas à pas : Hébergement d’un contrôle Composite WPF dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f4389-149">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="f4389-150">Migration et interopérabilité</span><span class="sxs-lookup"><span data-stu-id="f4389-150">Migration and Interoperability</span></span>](migration-and-interoperability.md)
