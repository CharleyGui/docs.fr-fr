---
title: Vue d'ensemble du contrôle LinkLabel
ms.date: 03/30/2017
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
ms.openlocfilehash: 9837902bf56a402d623adbcf41558dcc568b7105
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745226"
---
# <a name="linklabel-control-overview-windows-forms"></a>Vue d'ensemble du contrôle LinkLabel (Windows Forms)
Le contrôle Windows Forms <xref:System.Windows.Forms.LinkLabel> vous permet d’ajouter des liens de style Web aux applications Windows Forms. Vous pouvez utiliser le contrôle <xref:System.Windows.Forms.LinkLabel> pour tout ce que vous pouvez utiliser pour le contrôle <xref:System.Windows.Forms.Label> ; vous pouvez également définir une partie du texte sous la forme d’un lien vers un fichier, un dossier ou une page Web.  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>Ce que vous pouvez faire avec le contrôle LinkLabel  
 En plus de toutes les propriétés, méthodes et événements du contrôle <xref:System.Windows.Forms.Label>, le contrôle <xref:System.Windows.Forms.LinkLabel> possède des propriétés pour les liens hypertexte et les couleurs des liens. La propriété <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> définit la zone du texte qui active le lien. Les propriétés <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>et <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> définissent les couleurs du lien. L’événement <xref:System.Windows.Forms.LinkLabel.LinkClicked> détermine ce qui se produit lorsque le texte du lien est sélectionné.  
  
 L’utilisation la plus simple du contrôle <xref:System.Windows.Forms.LinkLabel> consiste à afficher un lien unique à l’aide de la propriété <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, mais vous pouvez également afficher plusieurs liens hypertexte à l’aide de la propriété <xref:System.Windows.Forms.LinkLabel.Links%2A>. La propriété <xref:System.Windows.Forms.LinkLabel.Links%2A> vous permet d’accéder à une collection de liens. Vous pouvez également spécifier des données dans la propriété <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> de chaque objet <xref:System.Windows.Forms.LinkLabel.Link> individuel. La valeur de la propriété <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> peut être utilisée pour stocker l’emplacement d’un fichier à afficher ou l’adresse d’un site Web.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.LinkLabel>
- [Vue d'ensemble du contrôle Label](label-control-overview-windows-forms.md)
- [Guide pratique pour créer un lien vers un objet ou une page web à l’aide du contrôle LinkLabel Windows Forms](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [Guide pratique pour modifier l'apparence du contrôle LinkLabel Windows Forms](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
