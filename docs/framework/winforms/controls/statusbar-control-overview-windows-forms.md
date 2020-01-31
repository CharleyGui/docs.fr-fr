---
title: Vue d'ensemble du contrôle StatusBar
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: b0b97bc3cb0291871e1fd113d82d0b480b53cdba
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742867"
---
# <a name="statusbar-control-overview-windows-forms"></a>Vue d'ensemble du contrôle StatusBar (Windows Forms)
> [!IMPORTANT]
> Les contrôles <xref:System.Windows.Forms.StatusStrip> et <xref:System.Windows.Forms.ToolStripStatusLabel> remplacent et ajoutent des fonctionnalités aux contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> ; Toutefois, les contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> sont conservés pour la compatibilité descendante et l’utilisation future, si vous le souhaitez.  
  
 Le [contrôle Windows Forms StatusBar](statusbar-control-windows-forms.md) est utilisé sur les formulaires comme une zone, généralement affichée en bas d’une fenêtre, dans laquelle une application peut afficher différents types d’informations d’État. les contrôles <xref:System.Windows.Forms.StatusBar> peuvent comporter des panneaux de barre d’État qui affichent du texte ou des icônes pour indiquer l’État, ou une série d’icônes dans une animation indiquant qu’un processus fonctionne ; par exemple, Microsoft Word indique que le document est en cours d’enregistrement.  
  
## <a name="using-the-statusbar-control"></a>Utilisation du contrôle StatusBar  
 Internet Explorer utilise une barre d’État pour indiquer l’URL d’une page lorsque la souris passe sur le lien hypertexte ; Microsoft Word vous donne des informations sur l’emplacement de la page, l’emplacement de la section et les modes de modification tels que le défrappe et le suivi des révisions. et Visual Studio utilise la barre d’État pour fournir des informations contextuelles, telles que la manipulation des fenêtres ancrables, ancrées ou flottantes.  
  
 Vous pouvez afficher un seul message dans la barre d’État en affectant à la propriété <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> la valeur `false` (valeur par défaut) et en affectant à la propriété <xref:System.Windows.Forms.StatusBar.Text%2A> de la barre d’État le texte que vous souhaitez voir apparaître dans la barre d’État. Vous pouvez diviser la barre d’État en panneaux pour afficher plusieurs types d’informations en affectant à la propriété <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> la valeur `true` et à l’aide de la méthode <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> de <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Guide pratique pour déterminer le panneau du contrôle StatusBar Windows Forms sur lequel l’utilisateur a cliqué](determine-which-panel-wf-statusbar-control-was-clicked.md)
