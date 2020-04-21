---
title: Vue d’ensemble du contrôle LinkLabel
ms.date: 03/30/2017
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
ms.openlocfilehash: 3e8607644c858ae804e384c974b5e81c1786c6a1
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739518"
---
# <a name="linklabel-control-overview-windows-forms"></a>Vue d'ensemble du contrôle LinkLabel (Windows Forms)
Le contrôle <xref:System.Windows.Forms.LinkLabel> Des formulaires Windows vous permet d’ajouter des liens de style Web vers les applications Windows Forms. Vous pouvez <xref:System.Windows.Forms.LinkLabel> utiliser le contrôle pour <xref:System.Windows.Forms.Label> tout ce que vous pouvez utiliser le contrôle pour; vous pouvez également définir une partie du texte en lien vers un fichier, un dossier ou une page Web.  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>Ce que vous pouvez faire avec le contrôle LinkLabel  
 En plus de toutes les propriétés, <xref:System.Windows.Forms.Label> méthodes <xref:System.Windows.Forms.LinkLabel> et événements du contrôle, le contrôle a des propriétés pour les hyperliens et les couleurs de lien. La <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriété définit la zone du texte qui active le lien. Le <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> , et les propriétés définir les couleurs du lien. L’événement <xref:System.Windows.Forms.LinkLabel.LinkClicked> détermine ce qui se passe lorsque le texte du lien est sélectionné.  
  
 L’utilisation la <xref:System.Windows.Forms.LinkLabel> plus simple du contrôle est <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> d’afficher un lien unique en <xref:System.Windows.Forms.LinkLabel.Links%2A> utilisant la propriété, mais vous pouvez également afficher plusieurs hyperliens en utilisant la propriété. La <xref:System.Windows.Forms.LinkLabel.Links%2A> propriété vous permet d’accéder à une collection de liens. Vous pouvez également spécifier des données dans la <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> propriété de chaque objet individuel. <xref:System.Windows.Forms.LinkLabel.Link> La valeur <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> de la propriété peut être utilisée pour stocker l’emplacement d’un fichier à afficher ou l’adresse d’un site Web.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.LinkLabel>
- [Vue d'ensemble du contrôle Label](label-control-overview-windows-forms.md)
- [Guide pratique pour créer un lien vers un objet ou une page web à l’aide du contrôle LinkLabel Windows Forms](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [Guide pratique pour modifier l'apparence du contrôle LinkLabel Windows Forms](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
