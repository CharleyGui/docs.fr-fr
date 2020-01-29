---
title: Vue d’ensemble du contrôle CheckBox
ms.date: 03/30/2017
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
ms.openlocfilehash: b42816cf1bc0ce1ab6db0a2a436b17b0d4370d59
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737094"
---
# <a name="checkbox-control-overview-windows-forms"></a>Vue d'ensemble du contrôle CheckBox (Windows Forms)
Le contrôle <xref:System.Windows.Forms.CheckBox> Windows Forms indique si une condition particulière est activée ou désactivée. Il est couramment utilisé pour présenter une sélection Oui/Non ou Vrai/Faux à l'utilisateur. Vous pouvez utiliser des contrôles de case à cocher dans des groupes pour afficher plusieurs choix à partir desquels l'utilisateur peut sélectionner un ou plusieurs éléments.  
  
 Le contrôle de case à cocher est semblable au contrôle de case d’option dans le cas où chaque est utilisé pour indiquer une sélection effectuée par l’utilisateur. Elles diffèrent dans la mesure où une seule case d’option dans un groupe peut être sélectionnée à la fois. Toutefois, avec le contrôle case à cocher, vous pouvez sélectionner n’importe quel nombre de cases à cocher.  
  
 Une case à cocher peut être connectée aux éléments d’une base de données à l’aide d’une liaison de données simple. Plusieurs cases à cocher peuvent être regroupées à l’aide du contrôle <xref:System.Windows.Forms.GroupBox>. Cela est utile pour l’apparence visuelle et pour la conception de l’interface utilisateur, car les contrôles groupés peuvent être déplacés ensemble sur le concepteur de formulaires. Pour plus d’informations, consultez [Windows Forms liaison de données](../windows-forms-data-binding.md) et [contrôle GroupBox](groupbox-control-windows-forms.md).  
  
 Le contrôle <xref:System.Windows.Forms.CheckBox> possède deux propriétés importantes, <xref:System.Windows.Forms.CheckBox.Checked%2A> et <xref:System.Windows.Forms.CheckBox.CheckState%2A>. La propriété <xref:System.Windows.Forms.CheckBox.Checked%2A> retourne `true` ou `false`. La propriété <xref:System.Windows.Forms.CheckBox.CheckState%2A> retourne <xref:System.Windows.Forms.CheckState.Checked> ou <xref:System.Windows.Forms.CheckState.Unchecked>; ou, si la propriété <xref:System.Windows.Forms.CheckBox.ThreeState%2A> est définie sur `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> peut également retourner <xref:System.Windows.Forms.CheckState.Indeterminate>. Dans l’état indéterminé, la zone est affichée avec une apparence grisée pour indiquer que l’option n’est pas disponible.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.CheckBox>
- [Guide pratique pour définir des options avec les contrôles CheckBox Windows Forms](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [Guide pratique pour répondre à un clic du contrôle CheckBox Windows Forms](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [CheckBox, contrôle](checkbox-control-windows-forms.md)
