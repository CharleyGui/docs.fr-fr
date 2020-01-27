---
title: Vue d'ensemble du composant FontDialog
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 664b756dc068ca283e4f43edbdd0f3266f5d1142
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745705"
---
# <a name="fontdialog-component-overview-windows-forms"></a>Vue d'ensemble du composant FontDialog (Windows Forms)
Le composant Windows Forms <xref:System.Windows.Forms.FontDialog> est une boîte de dialogue préconfigurée, qui est la boîte de dialogue **police** Windows standard utilisée pour exposer les polices qui sont actuellement installées sur le système. Utilisez-le au sein de votre application Windows comme une solution simple pour la sélection des polices au lieu de configurer votre propre boîte de dialogue.  
  
 Par défaut, la boîte de dialogue affiche les zones de liste pour la police, le style de police et la taille ; cases à cocher pour les effets tels que barré et souligné ; liste déroulante de script ; et un exemple de la façon dont la police s’affiche. (Le script fait référence à différents scripts de caractères disponibles pour une police donnée, par exemple l’hébreu ou le japonais.) Pour afficher la boîte de dialogue police, appelez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.  
  
## <a name="key-properties"></a>Propriétés de clé  
 Le composant possède un certain nombre de propriétés qui configurent son apparence. Les propriétés qui définissent les sélections de la boîte de dialogue sont <xref:System.Windows.Forms.FontDialog.Font%2A> et <xref:System.Windows.Forms.FontDialog.Color%2A>. La propriété <xref:System.Windows.Forms.FontDialog.Font%2A> définit la police, le style, la taille, le script et les effets. par exemple, `Arial, 10pt, style=Italic, Strikeout`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.FontDialog>
- [FontDialog, composant](fontdialog-component-windows-forms.md)
