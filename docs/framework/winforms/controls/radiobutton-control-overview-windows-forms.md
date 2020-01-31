---
title: Vue d'ensemble du contrôle RadioButton
ms.date: 03/30/2017
f1_keywords:
- RadioButton
helpviewer_keywords:
- RadioButton control [Windows Forms], about RadioButton control
- RadioButton control [Windows Forms], determining state
- radio buttons [Windows Forms], determining state
- radio buttons [Windows Forms], about radio buttons
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
ms.openlocfilehash: bbc93046b69d39caadde4986ff56f067fc206a9e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741136"
---
# <a name="radiobutton-control-overview-windows-forms"></a>Vue d'ensemble du contrôle RadioButton (Windows Forms)
Windows Forms contrôles de <xref:System.Windows.Forms.RadioButton> présentent un ensemble de deux ou de plusieurs choix mutuellement exclusifs à l’utilisateur. Alors que les cases d’option et les cases à cocher peuvent sembler fonctionner de la même façon, il existe une différence importante : lorsqu’un utilisateur sélectionne une case d’option, les autres cases d’option du même groupe ne peuvent pas être sélectionnées. En revanche, vous pouvez sélectionner n’importe quel nombre de cases à cocher. La définition d’un groupe de cases d’option indique à l’utilisateur « Voici un ensemble de choix parmi lesquels vous pouvez choisir un et un seul ».  
  
## <a name="using-the-control"></a>Utilisation du contrôle  
 Lorsqu’un utilisateur clique sur un contrôle <xref:System.Windows.Forms.RadioButton>, sa propriété <xref:System.Windows.Forms.RadioButton.Checked%2A> a la valeur `true` et le gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> est appelé. L’événement <xref:System.Windows.Forms.RadioButton.CheckedChanged> est déclenché lorsque la valeur de la propriété <xref:System.Windows.Forms.RadioButton.Checked%2A> change. Si la propriété <xref:System.Windows.Forms.RadioButton.AutoCheck%2A> est définie sur `true` (valeur par défaut), lorsque la case d’option est sélectionnée, tous les autres éléments du groupe sont automatiquement effacés. En règle générale, cette propriété est uniquement définie sur `false` lorsque le code de validation est utilisé pour s’assurer que la case d’option sélectionnée est une option autorisée. Le texte affiché dans le contrôle est défini avec la propriété <xref:System.Windows.Forms.Control.Text%2A>, qui peut contenir des raccourcis de touches d’accès. Une clé d’accès permet à un utilisateur de « cliquer » sur le contrôle en appuyant sur la touche ALT et sur la touche d’accès. Pour plus d’informations, consultez [Comment : créer des clés d’accès pour les contrôles Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md) et [Comment : définir le texte affiché par un contrôle Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
 Le contrôle <xref:System.Windows.Forms.RadioButton> peut apparaître comme un bouton de commande, qui semble avoir été enfoncé si vous l’avez sélectionné, si la propriété <xref:System.Windows.Forms.RadioButton.Appearance%2A> est définie sur <xref:System.Windows.Forms.Appearance.Button>. Les cases d’option peuvent également afficher des images à l’aide des propriétés <xref:System.Windows.Forms.ButtonBase.Image%2A> et <xref:System.Windows.Forms.ButtonBase.ImageList%2A>. Pour plus d’informations, consultez [Comment : définir l’image affichée par un contrôle Windows Forms](how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.RadioButton>
- [Vue d’ensemble du contrôle Panel](panel-control-overview-windows-forms.md)
- [Vue d’ensemble du contrôle GroupBox](groupbox-control-overview-windows-forms.md)
- [Vue d'ensemble du contrôle CheckBox](checkbox-control-overview-windows-forms.md)
- [Guide pratique pour créer des touches d'accès rapide pour des contrôles Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md)
- [Guide pratique pour définir le texte affiché par un contrôle Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Guide pratique pour grouper des contrôles RadioButton Windows Forms en un ensemble fonctionnant indépendamment](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)
- [RadioButton, contrôle](radiobutton-control-windows-forms.md)
