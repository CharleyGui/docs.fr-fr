---
title: Grouper des contrôles RadioButton pour qu’ils fonctionnent comme un ensemble
description: Découvrez comment regrouper Windows Forms contrôles RadioButton pour fonctionner indépendamment des autres jeux.
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 9f6795330922e739cca1f2b5c11bb2ec68bb4e84
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325923"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>Comment : grouper des contrôles RadioButton Windows Forms en un ensemble fonctionnant indépendamment
Les <xref:System.Windows.Forms.RadioButton> contrôles Windows Forms sont conçus pour permettre aux utilisateurs de choisir entre plusieurs paramètres, dont un seul peut être assigné à une procédure ou à un objet. Par exemple, un groupe de <xref:System.Windows.Forms.RadioButton> contrôles peut afficher un choix de porte-lots pour une commande, mais un seul de ces opérateurs sera utilisé. Par conséquent, un seul <xref:System.Windows.Forms.RadioButton> élément à la fois peut être sélectionné, même s’il fait partie d’un groupe fonctionnel.  
  
 Vous regroupez des cases d’option en les dessinant à l’intérieur d’un conteneur tel qu’un <xref:System.Windows.Forms.Panel> contrôle, un <xref:System.Windows.Forms.GroupBox> contrôle ou un formulaire. Toutes les cases d’option ajoutées directement à un formulaire deviennent un groupe. Pour ajouter des groupes distincts, vous devez les placer à l’intérieur de panneaux ou de zones de groupe. Pour plus d’informations sur les panneaux ou les zones de groupe, consultez [vue d’ensemble du contrôle Panel](panel-control-overview-windows-forms.md) ou [vue d’ensemble du contrôle GroupBox](groupbox-control-overview-windows-forms.md).  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>Pour regrouper des contrôles RadioButton comme un jeu pour fonctionner indépendamment d’autres jeux  
  
1. Faites glisser <xref:System.Windows.Forms.GroupBox> un <xref:System.Windows.Forms.Panel> contrôle ou de l’onglet **Windows Forms** de la **boîte à outils** vers le formulaire.  
  
2. Dessinez <xref:System.Windows.Forms.RadioButton> des contrôles sur le <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> contrôle ou.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.RadioButton>
- [Vue d’ensemble du contrôle RadioButton](radiobutton-control-overview-windows-forms.md)
- [Vue d’ensemble du contrôle Panel](panel-control-overview-windows-forms.md)
- [Vue d'ensemble du contrôle GroupBox](groupbox-control-overview-windows-forms.md)
- [Vue d’ensemble du contrôle CheckBox](checkbox-control-overview-windows-forms.md)
- [RadioButton, contrôle](radiobutton-control-windows-forms.md)
