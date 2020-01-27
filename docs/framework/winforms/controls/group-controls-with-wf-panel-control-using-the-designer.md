---
title: Regrouper des contrôles avec le contrôle Panel à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 927aeb5b51bc1ac4e22a45e487b49424b4e67b71
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745656"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Comment : grouper les contrôles avec le contrôle Panel Windows Forms à l'aide du concepteur
Les contrôles de <xref:System.Windows.Forms.Panel> Windows Forms sont utilisés pour regrouper d’autres contrôles. Il existe trois raisons pour regrouper des contrôles. L’un est le regroupement visuel d’éléments de formulaire associés pour une interface utilisateur claire ; un autre est le regroupement par programmation, des cases d’option, par exemple ; le dernier est de déplacer les contrôles en tant qu’unité au moment du Design.

## <a name="to-create-a-group-of-controls"></a>Pour créer un groupe de contrôles

1. Faites glisser un contrôle <xref:System.Windows.Forms.Panel> à partir de l’onglet **Windows Forms** de la boîte à outils vers un formulaire.

2. Ajoutez d’autres contrôles au panneau, en dessinant chacun à l’intérieur du panneau.

     Si vous disposez de contrôles existants que vous souhaitez encadrer dans un panneau, vous pouvez sélectionner tous les contrôles, les couper dans le presse-papiers, sélectionner le contrôle <xref:System.Windows.Forms.Panel>, puis les coller dans le panneau. Vous pouvez également les faire glisser dans le panneau.

3. Facultatif Si vous souhaitez ajouter une bordure à un panneau, définissez sa propriété <xref:System.Windows.Forms.BorderStyle>. Trois options s’offrent à vous : <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>et <xref:System.Windows.Forms.BorderStyle.None>.

## <a name="see-also"></a>Voir aussi

- [Panel, contrôle](panel-control-windows-forms.md)
- [Vue d’ensemble du contrôle Panel](panel-control-overview-windows-forms.md)
- [Guide pratique pour définir l'arrière-plan d'un contrôle Panel](how-to-set-the-background-of-a-windows-forms-panel.md)
