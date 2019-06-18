---
title: Encodage et globalisation des applications Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], lack of Unicode support
- DateTimePicker control [Windows Forms], lack of Unicode support
- TrackBar control [Windows Forms], lack of Unicode support
- ImageList component [Windows Forms], lack of Unicode support
- Unicode [Windows Forms]
- ToolBar control [Windows Forms], lack of Unicode support
- international applications [Windows Forms], character display
- StatusBar control [Windows Forms], lack of Unicode support
- MonthCalendar control [Windows Forms], lack of Unicode support
- international characters
- TabControl control [Windows Forms], lack of Unicode support
- Windows Forms, encoding
- TreeView control [Windows Forms], lack of Unicode support
- ProgressBar control [Windows Forms], Unicode-enabled forms
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: 22e8965d-a712-42b3-8167-3ee346bd70f9
ms.openlocfilehash: f8e56642b6325454d2d55cd3a3d3a83d201c2eb5
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67151994"
---
# <a name="encoding-and-windows-forms-globalization"></a>Encodage et globalisation des applications Windows Forms
Les applications Windows Forms sont totalement compatibles Unicode, ce qui signifie que chaque caractère est représenté par un nombre unique, quels que soient la plate-forme, le programme ou la langue. Pour plus d’informations sur Unicode, consultez le [site Web du consortium Unicode](https://www.unicode.org).  
  
## <a name="benefits-of-unicode"></a>Avantages d'Unicode  
 Les avantages des formulaires Unicode incluent la possibilité de travailler avec des scripts qui sont Unicode uniquement, tels que l'Hindi. En outre, vous pouvez utiliser plusieurs langues sur un même formulaire. En Unicode, tous les caractères font deux octets. Aucun effort particulier n'est donc nécessaire pour représenter des caractères codés sur deux octets. Vous pouvez aussi écrire un seul ensemble de code qui fonctionne sur toutes les plateformes. Il s’agit d’une modification des versions précédentes de Visual Basic, dans lequel vous deviez écrire du code différent pour différentes plateformes, tels que Windows NT et [!INCLUDE[win98](../../../../includes/win98-md.md)].  
  
 Toutefois, certains contrôles ne prennent pas en charge Unicode dans [!INCLUDE[win98](../../../../includes/win98-md.md)] et Windows Millennium Edition. Ces contrôles, qui héritent tous du contrôle commun, traitent les données avec les pages de codes Windows, comme ANSI. Il s'agit des contrôles suivants : <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, et <xref:System.Windows.Forms.StatusBar>. Par conséquent, vous ne pouvez pas afficher de données Unicode dans ces contrôles sur les plateformes répertoriées. Par exemple, vous ne pouvez pas afficher de caractères japonais sur un système d'exploitation [!INCLUDE[win98](../../../../includes/win98-md.md)] en anglais.  
  
 Pour disposer d'alternatives aux contrôles <xref:System.Windows.Forms.ToolBar> et <xref:System.Windows.Forms.StatusBar> prenant en charge Unicode, utilisez les contrôles <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.StatusStrip>, qui remplacent ces anciens contrôles. Pour conserver une apparence semblable entre les éléments visuels dans votre application, utilisez le contrôle <xref:System.Windows.Forms.MenuStrip> pour afficher les menus plutôt que <xref:System.Windows.Forms.MainMenu>. Comme <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> peut également traiter et afficher des caractères Unicode.  
  
## <a name="see-also"></a>Voir aussi

- [Globalisation d’applications Windows Forms](globalizing-windows-forms.md)
