---
title: Contrôles Windows Forms et contrôles WPF équivalents
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
ms.assetid: 8a157e6b-8054-46db-a5cf-a78966acc7a1
ms.openlocfilehash: 7f531b60d8b31181688f3d0a6753b234ffc6c7dd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735207"
---
# <a name="windows-forms-controls-and-equivalent-wpf-controls"></a>Contrôles Windows Forms et contrôles WPF équivalents
De nombreux contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ont des contrôles équivalents [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], mais certains contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] n’ont pas d’équivalents dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cette rubrique compare les types de contrôle fournis par les deux technologies.  
  
 Vous pouvez toujours utiliser l’interopérabilité pour héberger des [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] des contrôles qui n’ont pas d’équivalents dans vos applications basées sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Le tableau suivant indique les contrôles et composants de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] qui ont des fonctionnalités équivalentes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de contrôle.  
  
|contrôle Windows Forms|Contrôle équivalent WPF|Notes|  
|---------------------------|----------------------------|-------------|  
|<xref:System.Windows.Forms.BindingNavigator>|Aucun contrôle équivalent.||  
|<xref:System.Windows.Forms.BindingSource>|<xref:System.Windows.Data.CollectionViewSource>||  
|<xref:System.Windows.Forms.Button>|<xref:System.Windows.Controls.Button>||  
|<xref:System.Windows.Forms.CheckBox>|<xref:System.Windows.Controls.CheckBox>||  
|<xref:System.Windows.Forms.CheckedListBox>|<xref:System.Windows.Controls.ListBox> avec la composition.||  
|<xref:System.Windows.Forms.ColorDialog>|Aucun contrôle équivalent.||  
|<xref:System.Windows.Forms.ComboBox>|<xref:System.Windows.Controls.ComboBox>|<xref:System.Windows.Controls.ComboBox> ne prend pas en charge la saisie semi-automatique.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<xref:System.Windows.Controls.ContextMenu>||  
|<xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Controls.DataGrid>||  
|<xref:System.Windows.Forms.DateTimePicker>|<xref:System.Windows.Controls.DatePicker>||  
|<xref:System.Windows.Forms.DomainUpDown>|<xref:System.Windows.Controls.TextBox> et deux contrôles <xref:System.Windows.Controls.Primitives.RepeatButton>.||  
|<xref:System.Windows.Forms.ErrorProvider>|Aucun contrôle équivalent.||  
|<xref:System.Windows.Forms.FlowLayoutPanel>|<xref:System.Windows.Controls.WrapPanel> ou <xref:System.Windows.Controls.StackPanel>||  
|<xref:System.Windows.Forms.FolderBrowserDialog>|Aucun contrôle équivalent.||  
|<xref:System.Windows.Forms.FontDialog>|Aucun contrôle équivalent.||  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Window>|<xref:System.Windows.Window> ne prend pas en charge les fenêtres enfants.|  
|<xref:System.Windows.Forms.GroupBox>|<xref:System.Windows.Controls.GroupBox>||  
|<xref:System.Windows.Forms.HelpProvider>|Aucun contrôle équivalent.|Aucune aide (F1). L’aide « qu’est-ce que c’est » est remplacée par des info-bulles.|  
|<xref:System.Windows.Forms.HScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|Le défilement est intégré aux contrôles conteneurs.|  
|<xref:System.Windows.Forms.ImageList>|Aucun contrôle équivalent.||  
|<xref:System.Windows.Forms.Label>|<xref:System.Windows.Controls.Label>||  
|<xref:System.Windows.Forms.LinkLabel>|Aucun contrôle équivalent.|Vous pouvez utiliser la classe <xref:System.Windows.Documents.Hyperlink> pour héberger des liens hypertexte dans le contenu dynamique.|  
|<xref:System.Windows.Forms.ListBox>|<xref:System.Windows.Controls.ListBox>||  
|<xref:System.Windows.Forms.ListView>|<xref:System.Windows.Controls.ListView>|Le contrôle <xref:System.Windows.Controls.ListView> fournit un affichage des détails en lecture seule.|  
|<xref:System.Windows.Forms.MaskedTextBox>|Aucun contrôle équivalent.||  
|<xref:System.Windows.Forms.MenuStrip>|<xref:System.Windows.Controls.Menu>|<xref:System.Windows.Controls.Menu> le style de contrôle peut se rapprocher du comportement et de l’apparence de la classe <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType>.|  
|<xref:System.Windows.Forms.MonthCalendar>|<xref:System.Windows.Controls.Calendar>||  
|<xref:System.Windows.Forms.NotifyIcon>|Aucun contrôle équivalent.||  
|<xref:System.Windows.Forms.NumericUpDown>|<xref:System.Windows.Controls.TextBox> et deux contrôles <xref:System.Windows.Controls.Primitives.RepeatButton>.||  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:Microsoft.Win32.OpenFileDialog>|La classe <xref:Microsoft.Win32.OpenFileDialog> est un wrapper [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] autour du contrôle Win32.|  
|<xref:System.Windows.Forms.PageSetupDialog>|Aucun contrôle équivalent.||  
|<xref:System.Windows.Forms.Panel>|<xref:System.Windows.Controls.Canvas>||  
|<xref:System.Windows.Forms.PictureBox>|<xref:System.Windows.Controls.Image>||  
|<xref:System.Windows.Forms.PrintDialog>|<xref:System.Windows.Controls.PrintDialog>||  
|<xref:System.Drawing.Printing.PrintDocument>|Aucun contrôle équivalent.||  
|<xref:System.Windows.Forms.PrintPreviewControl>|<xref:System.Windows.Controls.DocumentViewer>||  
|<xref:System.Windows.Forms.PrintPreviewDialog>|Aucun contrôle équivalent.||  
|<xref:System.Windows.Forms.ProgressBar>|<xref:System.Windows.Controls.ProgressBar>||  
|<xref:System.Windows.Forms.PropertyGrid>|Aucun contrôle équivalent.||  
|<xref:System.Windows.Forms.RadioButton>|<xref:System.Windows.Controls.RadioButton>||  
|<xref:System.Windows.Forms.RichTextBox>|<xref:System.Windows.Controls.RichTextBox>||  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:Microsoft.Win32.SaveFileDialog>|La classe <xref:Microsoft.Win32.SaveFileDialog> est un wrapper [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] autour du contrôle Win32.|  
|<xref:System.Windows.Forms.ScrollableControl>|<xref:System.Windows.Controls.ScrollViewer>||  
|<xref:System.Media.SoundPlayer>|<xref:System.Windows.Media.MediaPlayer>||  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Controls.GridSplitter>||  
|<xref:System.Windows.Forms.StatusStrip>|<xref:System.Windows.Controls.Primitives.StatusBar>||  
|<xref:System.Windows.Forms.TabControl>|<xref:System.Windows.Controls.TabControl>||  
|<xref:System.Windows.Forms.TableLayoutPanel>|<xref:System.Windows.Controls.Grid>||  
|<xref:System.Windows.Forms.TextBox>|<xref:System.Windows.Controls.TextBox>||  
|<xref:System.Windows.Forms.Timer>|<xref:System.Windows.Threading.DispatcherTimer>||  
|<xref:System.Windows.Forms.ToolStrip>|<xref:System.Windows.Controls.ToolBar>||  
|<xref:System.Windows.Forms.ToolStripContainer>|<xref:System.Windows.Controls.ToolBar> avec la composition.||  
|<xref:System.Windows.Forms.ToolStripDropDown>|<xref:System.Windows.Controls.ToolBar> avec la composition.||  
|<xref:System.Windows.Forms.ToolStripDropDownMenu>|<xref:System.Windows.Controls.ToolBar> avec la composition.||  
|<xref:System.Windows.Forms.ToolStripPanel>|<xref:System.Windows.Controls.ToolBar> avec la composition.||  
|<xref:System.Windows.Forms.ToolTip>|<xref:System.Windows.Controls.ToolTip>||  
|<xref:System.Windows.Forms.TrackBar>|<xref:System.Windows.Controls.Slider>||  
|<xref:System.Windows.Forms.TreeView>|<xref:System.Windows.Controls.TreeView>||  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Controls.UserControl>||  
|<xref:System.Windows.Forms.VScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|Le défilement est intégré aux contrôles conteneurs.|  
|<xref:System.Windows.Forms.WebBrowser>|<xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType>|Le contrôle <xref:System.Windows.Controls.Frame> peut héberger des pages HTML.<br /><br /> À partir de la .NET Framework 3,5 SP1, le contrôle <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> peut héberger des pages HTML et également sauvegarder le contrôle <xref:System.Windows.Controls.Frame>.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Concepteur WPF pour les développeurs Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cc165605(v=vs.100))
- [Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Migration et interopérabilité](migration-and-interoperability.md)
