---
title: Prise en charge d'UI Automation pour les contrôles standard
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 49277073706444fd611ae41e762442388ac50b71
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789600"
---
# <a name="ui-automation-support-for-standard-controls"></a>Prise en charge d'UI Automation pour les contrôles standard
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique contient des informations sur la prise en charge de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour les contrôles standard dans les applications développées pour les frameworks [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32 et Windows Forms.  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a>Contrôles Windows Presentation Foundation  
 Tous les éléments du contrôle [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] qui fournissent des informations ou une prise en charge pour l’interaction utilisateur disposent d’une prise en charge native complète de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. D’autres éléments, tels que les panneaux, ne sont pas visibles par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a>Contrôles Win32  
 La plupart des contrôles Win32 sont exposés à des [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] via des fournisseurs côté client dans UIAutomationClientsideProviders. dll. Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.  
  
 La prise en charge complète n’est fournie que pour les contrôles de la version 6 de *ComCtrl32. dll*.  
  
 Les contrôles suivants sont pris en charge.  
  
|Nom de classe|Type de contrôle|  
|----------------|------------------|  
|Button|Button|  
|Button|RadioButton|  
|Button|Groupe|  
|Button|Case à cocher|  
|Button|Lien hypertexte|  
|Button|SplitButton|  
|Button|Case à cocher|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|Edit|Document|  
|Edit|Edit|  
|SysLink|Lien hypertexte|  
|Static|Text|  
|Static|Image|  
|SysIPAddress32|Personnalisé|  
|SysHeader32|Header/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|Liste|  
|ListBox|Liste|  
|ListBox|ListItem|  
|#32768|Menu|  
|#32768|MenuItem|  
|msctls_progress32|ProgressBar|  
|RichEdit|Document. Consultez la remarque.|  
|RichEdit20A|Document|  
|RichEdit20W|Document|  
|RichEdit50W|Document|  
|ScrollBar|Curseur|  
|msctls_trackbar32|Curseur|  
|msctls_updown32|Spinner|  
|msctls_statusbar32|StatusBar|  
|SysTabControl32|Tab|  
|SysTabControl32|TabItem|  
|ToolbarWindow32|ToolBar|  
|ToolbarWindow32|MenuItem|  
|ToolbarWindow32|Button|  
|ToolbarWindow32|Case à cocher|  
|ToolbarWindow32|RadioButton|  
|ToolbarWindow32|Séparateur|  
|tooltips_class32|Info-bulle|  
|#32774|Info-bulle|  
|ReBarWindow32|ToolBar|  
|SysTreeView32|Arborescence|  
|SysTreeView32|TreeItem|  
  
 **Remarque** Le contrôle RichEdit est pris en charge uniquement pour les versions fournies avec Windows Vista (dans RichEd20. dll version 3,1 et ultérieure, et que dans msftedit. dll version 4,1 et versions ultérieures).  
  
 Les contrôles suivants ne sont pas pris en charge.  
  
|Nom de classe|Type de contrôle|  
|----------------|------------------|  
|SysAnimate32|Image|  
|SysPager|Spinner|  
|SysDateTimePick32|Personnalisé|  
|SysMonthCal32|Calendrier|  
|MS_WINNOTE|Info-bulle|  
|VBBubble|Info-bulle|  
|ScrollBar (quand il est utilisé comme contrôle autonome)|Curseur|  
|SuperGrid|Personnalisé|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a>Contrôles Windows Forms  
 Les contrôles Windows Forms sont exposés à des [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] via des fournisseurs côté client dans UIAutomationClientsideProviders. dll. Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.  
  
 En général, les contrôles Windows Forms qui sont des wrappers managés pour les contrôles communs Win32 sont pris en charge par les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Les contrôles suivants sont pris en charge.  
  
|Nom de classe|  
|----------------|  
|Button|  
|Case à cocher|  
|CheckedListBox|  
|ColorDialog|  
|ComboBox|  
|FolderBrowser|  
|FontDialog|  
|GroupBox|  
|HscrollBar|  
|ImageList|  
|Ajouter des contrôles|  
|ListBox|  
|Affichage de liste|  
|MainMenu/ContextMenu|  
|MonthCalendar|  
|NotifyIcon|  
|OpenFileDialog|  
|PageSetupDialog|  
|PrintDialog|  
|ProgressBar|  
|RadioButton|  
|RichTextBox|  
|SaveFileDialog|  
|ScrollableControl|  
|SoundPlayer|  
|StatusBar|  
|TabControl/TabPage|  
|TextBox|  
|Minuteur|  
|ToolBar|  
|Info-bulle|  
|TrackBar|  
|TreeView|  
|VscrollBar|  
|Navigateur web|  
  
 Les contrôles suivants sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] uniquement par le biais de leur prise en charge de Microsoft Active Accessibility. Certaines fonctionnalités ne sont peut-être pas disponibles.  
  
|Nom du contrôle|  
|------------------|  
|BindingSource|  
|DataGrid|  
|DataGridView|  
|DataNavigator|  
|DomainUpDown|  
|ErrorProvider|  
|FlowLayoutPanel|  
|Formulaire|  
|LinkLabel|  
|HelpProvider|  
|MaskedTextBox|  
|MenuStrip/ContextMenuStrip|  
|NumericUpDown|  
|Volet|  
|PictureBox|  
|PrintDocument|  
|PrintPreviewControl|  
|PrintPreviewDialog|  
|PropertyGrid|  
|UserControl|  
|ToolStrip|  
|TableLayoutPanel|  
|SplitContainer/SplitterPanel|  
|Séparation|  
|RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>Voir aussi

- [UI Automation Control Types](ui-automation-control-types.md)
