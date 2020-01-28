---
title: Méthodes de sélection d’un contrôle Button
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: 145166d182f1ec51068ab3e0c23c12b471b69231
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740005"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a>Méthodes de sélection du contrôle Button Windows Forms
Un bouton de Windows Forms peut être sélectionné des manières suivantes :  
  
- Utilisez la souris pour cliquer sur le bouton.  
  
- Appelez l’événement <xref:System.Windows.Forms.Control.Click> du bouton dans le code.  
  
- Déplacez le focus sur le bouton en appuyant sur la touche TAB, puis choisissez le bouton en appuyant sur la barre d’espace ou sur entrée.  
  
- Appuyez sur la touche d’accès (ALT + la lettre soulignée) pour le bouton. Pour plus d’informations sur les clés d’accès, consultez [How to : Create Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).  
  
- Si le bouton est le bouton « accepter » du formulaire, le fait d’appuyer sur entrée choisit le bouton, même si un autre contrôle a le focus, sauf s’il s’agit d’un autre bouton, d’une zone de texte multiligne ou d’un contrôle personnalisé qui intercepte la touche entrée.  
  
- Si le bouton est le bouton « Annuler » du formulaire, le fait d’appuyer sur la touche Échap choisit le bouton, même si un autre contrôle a le focus.  
  
- Appelez la méthode <xref:System.Windows.Forms.Button.PerformClick%2A> pour sélectionner le bouton par programmation.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble du contrôle Button](button-control-overview-windows-forms.md)
- [Guide pratique pour répondre à un clic du contrôle Button Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Button, contrôle](button-control-windows-forms.md)
