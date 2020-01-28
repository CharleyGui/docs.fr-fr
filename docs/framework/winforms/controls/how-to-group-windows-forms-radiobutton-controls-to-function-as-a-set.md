---
title: Grouper des contrôles RadioButton pour qu’ils fonctionnent comme un ensemble
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: c4b37c84bf0f93837b91c743c7681d39fd83a659
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732952"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>Comment : grouper des contrôles RadioButton Windows Forms en un ensemble fonctionnant indépendamment
Les contrôles Windows Forms <xref:System.Windows.Forms.RadioButton> sont conçus pour permettre aux utilisateurs de choisir entre plusieurs paramètres, dont un seul peut être assigné à une procédure ou à un objet. Par exemple, un groupe de <xref:System.Windows.Forms.RadioButton> contrôles peut afficher un choix de porte-packages pour une commande, mais un seul de ces opérateurs sera utilisé. Par conséquent, vous ne pouvez sélectionner qu’un seul <xref:System.Windows.Forms.RadioButton> à la fois, même s’il fait partie d’un groupe fonctionnel.  
  
 Vous regroupez des cases d’option en les dessinant à l’intérieur d’un conteneur tel qu’un contrôle <xref:System.Windows.Forms.Panel>, un contrôle <xref:System.Windows.Forms.GroupBox> ou un formulaire. Toutes les cases d’option ajoutées directement à un formulaire deviennent un groupe. Pour ajouter des groupes distincts, vous devez les placer à l’intérieur de panneaux ou de zones de groupe. Pour plus d’informations sur les panneaux ou les zones de groupe, consultez [vue d’ensemble du contrôle Panel](panel-control-overview-windows-forms.md) ou [vue d’ensemble du contrôle GroupBox](groupbox-control-overview-windows-forms.md).  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>Pour regrouper des contrôles RadioButton comme un jeu pour fonctionner indépendamment d’autres jeux  
  
1. Faites glisser un contrôle <xref:System.Windows.Forms.GroupBox> ou <xref:System.Windows.Forms.Panel> de l’onglet **Windows Forms** de la **boîte à outils** vers le formulaire.  
  
2. Dessinez <xref:System.Windows.Forms.RadioButton> contrôles sur le contrôle <xref:System.Windows.Forms.GroupBox> ou <xref:System.Windows.Forms.Panel>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.RadioButton>
- [Vue d’ensemble du contrôle RadioButton](radiobutton-control-overview-windows-forms.md)
- [Vue d’ensemble du contrôle Panel](panel-control-overview-windows-forms.md)
- [Vue d’ensemble du contrôle GroupBox](groupbox-control-overview-windows-forms.md)
- [Vue d'ensemble du contrôle CheckBox](checkbox-control-overview-windows-forms.md)
- [RadioButton, contrôle](radiobutton-control-windows-forms.md)
