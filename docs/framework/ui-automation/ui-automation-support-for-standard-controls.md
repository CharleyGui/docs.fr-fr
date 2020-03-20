---
title: Prise en charge d'UI Automation pour les contrôles standard
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 36028d589e98177f6a0e83092edd656860b1a8d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179852"
---
# <a name="ui-automation-support-for-standard-controls"></a>Prise en charge d'UI Automation pour les contrôles standard
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ce sujet contient [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] des informations sur la [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]prise en charge des contrôles standard dans les applications développées pour les cadres , Win32 et Windows Forms.  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a>Contrôles Windows Presentation Foundation  
 Tous les éléments du contrôle [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] qui fournissent des informations ou une prise en charge pour l’interaction utilisateur disposent d’une prise en charge native complète de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. D’autres éléments, tels que les panneaux, ne sont pas visibles par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a>Contrôles Win32  
 La plupart des contrôles [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Win32 sont exposés par l’intermédiaire de fournisseurs côté client dans UIAutomationClientsideProviders.dll. Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.  
  
 Le support complet est fourni uniquement pour les contrôles de la version 6 de *ComCtrl32.dll*.  
  
 Les contrôles suivants sont pris en charge.  
  
|Nom de classe|Type de contrôle|  
|----------------|------------------|  
|Bouton|Bouton|  
|Bouton|RadioButton|  
|Bouton|Groupe|  
|Bouton|Case à cocher|  
|Bouton|Hyperlink|  
|Bouton|SplitButton|  
|Bouton|Case à cocher|  
|ComboBoxEx32|Liste déroulante|  
|Liste déroulante|Liste déroulante|  
|Modifier|Document|  
|Modifier|Modifier|  
|SysLink|Hyperlink|  
|statique|Texte|  
|statique|Image|  
|SysIPAddress32|Custom|  
|SysHeader32|Header/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|List|  
|Zone de liste|List|  
|Zone de liste|ListItem|  
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
|ReBarWindow32|Barre d'outils|  
|SysTreeView32|Arborescence|  
|SysTreeView32|TreeItem|  
  
 **Note** Le contrôle RichEdit est pris en charge uniquement pour les versions expédiées avec Windows Vista (dans la version 3.1 richEd20.dll et plus tard, et MsftEdit.dll version 4.1 et plus tard).  
  
 Les contrôles suivants ne sont pas pris en charge.  
  
|Nom de classe|Type de contrôle|  
|----------------|------------------|  
|SysAnimate32|Image|  
|SysPager|Spinner|  
|SysDateTimePick32|Custom|  
|SysMonthCal32|Calendrier|  
|MS_WINNOTE|Info-bulle|  
|VBBubble|Info-bulle|  
|ScrollBar (quand il est utilisé comme contrôle autonome)|Curseur|  
|SuperGrid|Custom|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a>contrôles Windows Forms  
 Les contrôles des [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] formulaires Windows sont exposés par l’intermédiaire de fournisseurs côté client dans UIAutomationClientsideProviders.dll. Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.  
  
 Typiquement, les contrôles de formulaires Windows qui sont des [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]emballages gérés pour les contrôles communs Win32 sont pris en charge par . Les contrôles suivants sont pris en charge.  
  
|Nom de la classe|  
|----------------|  
|Bouton|  
|Case à cocher|  
|CheckedListBox|  
|ColorDialog|  
|Liste déroulante|  
|FolderBrowser|  
|FontDialog|  
|GroupBox|  
|HscrollBar|  
|ImageList|  
|Étiquette|  
|Zone de liste|  
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
|Barre d'outils|  
|Info-bulle|  
|TrackBar|  
|TreeView|  
|VscrollBar|  
|Navigateur web|  
  
 Les contrôles suivants [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ne sont exposés qu’en supportant Microsoft Active Accessibility. Certaines fonctionnalités ne sont peut-être pas disponibles.  
  
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

- [UI Automation Control Types](ui-automation-control-types.md)
