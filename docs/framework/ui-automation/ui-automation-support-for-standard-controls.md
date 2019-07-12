---
title: Prise en charge d'UI Automation pour les contrôles standard
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 641fc3f8dfca3ff6506354c076b98cc88073a1b7
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802119"
---
# <a name="ui-automation-support-for-standard-controls"></a>Prise en charge d'UI Automation pour les contrôles standard
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [Windows Automation API : UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique contient des informations sur la prise en charge d’ [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour les contrôles standard dans les applications développées pour les infrastructures [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]et [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] .  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a>Contrôles Windows Presentation Foundation  
 Tous les éléments du contrôle [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] qui fournissent des informations ou une prise en charge pour l’interaction utilisateur disposent d’une prise en charge native complète de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. D’autres éléments, tels que les panneaux, ne sont pas visibles par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a>Contrôles Win32  
 La plupart des contrôles [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] via des fournisseurs côté client dans UIAutomationClientsideProviders.dll. Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.  
  
 La prise en charge complète n’est fournie que pour les contrôles de la version 6 de ComCtrl32.dll (disponible avec [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] et les versions ultérieures).  
  
 Les contrôles suivants sont pris en charge.  
  
|Nom de classe|Type de contrôle|  
|----------------|------------------|  
|Bouton|Bouton|  
|Bouton|RadioButton|  
|Bouton|Regrouper|  
|Bouton|Case à cocher|  
|Bouton|Lien hypertexte|  
|Bouton|SplitButton|  
|Bouton|Case à cocher|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|Modifier|Document|  
|Modifier|Modifier|  
|SysLink|Lien hypertexte|  
|statique|Text|  
|Statique|Image|  
|SysIPAddress32|Personnalisé|  
|SysHeader32|Header/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|Énumérer|  
|ListBox|Énumérer|  
|ListBox|ListItem|  
|#32768|Menu|  
|#32768|MenuItem|  
|msctls_progress32|Barre de progression|  
|RichEdit|Document. Consultez la remarque.|  
|RichEdit20A|Document|  
|RichEdit20W|Document|  
|RichEdit50W|Document|  
|ScrollBar|Curseur|  
|msctls_trackbar32|Curseur|  
|msctls_updown32|Spinner|  
|msctls_statusbar32|StatusBar|  
|SysTabControl32|Onglet|  
|SysTabControl32|TabItem|  
|ToolbarWindow32|ToolBar|  
|ToolbarWindow32|MenuItem|  
|ToolbarWindow32|Bouton|  
|ToolbarWindow32|Case à cocher|  
|ToolbarWindow32|RadioButton|  
|ToolbarWindow32|Séparateur|  
|tooltips_class32|Info-bulle|  
|#32774|Info-bulle|  
|ReBarWindow32|ToolBar|  
|SysTreeView32|Arborescence|  
|SysTreeView32|TreeItem|  
  
 **Remarque** Le contrôle RichEdit est pris en charge uniquement pour les versions fournies avec [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (dans RichEd20.dll version 3.1 et version ultérieure, ainsi que dans MsftEdit.dll version 4.1 et version ultérieure).  
  
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
## <a name="windows-forms-controls"></a>contrôles Windows Forms  
 Contrôles Windows Forms sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] via des fournisseurs côté client dans UIAutomationClientsideProviders.dll. Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.  
  
 En règle générale, les contrôles Windows Forms qui sont des wrappers managés pour [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] contrôles communs sont pris en charge par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Les contrôles suivants sont pris en charge.  
  
|Nom de classe|  
|----------------|  
|Bouton|  
|Case à cocher|  
|CheckedListBox|  
|ColorDialog|  
|ComboBox|  
|FolderBrowser|  
|FontDialog|  
|GroupBox|  
|HscrollBar|  
|ImageList|  
|Etiquette|  
|ListBox|  
|Affichage de liste|  
|MainMenu/ContextMenu|  
|MonthCalendar|  
|NotifyIcon|  
|OpenFileDialog|  
|PageSetupDialog|  
|PrintDialog|  
|Barre de progression|  
|RadioButton|  
|RichTextBox|  
|SaveFileDialog|  
|ScrollableControl|  
|SoundPlayer|  
|StatusBar|  
|TabControl/TabPage|  
|TextBox|  
|Minuterie|  
|ToolBar|  
|Info-bulle|  
|TrackBar|  
|TreeView|  
|VscrollBar|  
|Navigateur web|  
  
 Les contrôles suivants sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] uniquement par le biais de leur prise en charge pour Microsoft Active Accessibility. Certaines fonctionnalités ne sont peut-être pas disponibles.  
  
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
|Séparateur|  
|RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>Voir aussi

- [Types de contrôle UI Automation](../../../docs/framework/ui-automation/ui-automation-control-types.md)
