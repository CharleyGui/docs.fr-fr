---
title: Vue d'ensemble du contrôle StatusBar (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: bd58d4c70e3a3c88e57fe242957f669d1944fd71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964438"
---
# <a name="statusbar-control-overview-windows-forms"></a>Vue d'ensemble du contrôle StatusBar (Windows Forms)
> [!IMPORTANT]
> Les <xref:System.Windows.Forms.StatusStrip> contrôles <xref:System.Windows.Forms.ToolStripStatusLabel> et <xref:System.Windows.Forms.StatusBar> remplacent et ajoutent des fonctionnalités <xref:System.Windows.Forms.StatusBarPanel> aux contrôles et; toutefois <xref:System.Windows.Forms.StatusBar> , <xref:System.Windows.Forms.StatusBarPanel> les contrôles et sont conservés pour la compatibilité descendante et l’utilisation future, si vous Choisissez.  
  
 Le [contrôle Windows Forms StatusBar](statusbar-control-windows-forms.md) est utilisé sur les formulaires comme une zone, généralement affichée en bas d’une fenêtre, dans laquelle une application peut afficher différents types d’informations d’État. <xref:System.Windows.Forms.StatusBar>les contrôles peuvent comporter des panneaux de barre d’État qui affichent du texte ou des icônes pour indiquer l’État, ou une série d’icônes dans une animation indiquant qu’un processus fonctionne; par exemple, Microsoft Word indique que le document est en cours d’enregistrement.  
  
## <a name="using-the-statusbar-control"></a>Utilisation du contrôle StatusBar  
 Internet Explorer utilise une barre d’État pour indiquer l’URL d’une page lorsque la souris passe sur le lien hypertexte; Microsoft Word vous donne des informations sur l’emplacement de la page, l’emplacement de la section et les modes de modification tels que le défrappe et le suivi des révisions. et Visual Studio utilise la barre d’État pour fournir des informations contextuelles, telles que la manipulation des fenêtres ancrables, ancrées ou flottantes.  
  
 Vous pouvez afficher un seul message dans la barre d’État en affectant <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> à `false` la propriété la valeur (valeur par <xref:System.Windows.Forms.StatusBar.Text%2A> défaut) et en affectant à la propriété de la barre d’État le texte que vous souhaitez voir apparaître dans la barre d’État. Vous pouvez diviser la barre d’État en panneaux pour afficher plusieurs types d’informations en affectant à <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> `true` la propriété la valeur et <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> en utilisant <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>la méthode de.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Guide pratique pour Déterminer le panneau du contrôle Windows Forms StatusBar sur lequel l’utilisateur a cliqué](determine-which-panel-wf-statusbar-control-was-clicked.md)
