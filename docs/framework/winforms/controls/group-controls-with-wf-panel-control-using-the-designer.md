---
title: 'Procédure : regrouper des contrôles avec le contrôle Panel Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: cadfa715b140c63b216ec0ca2e6d6a6589ae3458
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040389"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Procédure : regrouper des contrôles avec le contrôle Panel Windows Forms à l’aide du concepteur
Les <xref:System.Windows.Forms.Panel> contrôles Windows Forms sont utilisés pour regrouper d’autres contrôles. Il existe trois raisons pour regrouper des contrôles. L’un est le regroupement visuel d’éléments de formulaire associés pour une interface utilisateur claire; un autre est le regroupement par programmation, des cases d’option, par exemple; le dernier est de déplacer les contrôles en tant qu’unité au moment du Design.

## <a name="to-create-a-group-of-controls"></a>Pour créer un groupe de contrôles

1. Faites glisser <xref:System.Windows.Forms.Panel> un contrôle de l’onglet **Windows Forms** de la boîte à outils vers un formulaire.

2. Ajoutez d’autres contrôles au panneau, en dessinant chacun à l’intérieur du panneau.

     Si vous disposez de contrôles existants que vous souhaitez encadrer dans un panneau, vous pouvez sélectionner tous les contrôles, les couper dans le presse- <xref:System.Windows.Forms.Panel> papiers, sélectionner le contrôle, puis les coller dans le panneau. Vous pouvez également les faire glisser dans le panneau.

3. Facultatif Si vous souhaitez ajouter une bordure à un panneau, définissez sa <xref:System.Windows.Forms.BorderStyle> propriété. Trois options s’offrent à <xref:System.Windows.Forms.BorderStyle.Fixed3D>vous <xref:System.Windows.Forms.BorderStyle.FixedSingle>:, <xref:System.Windows.Forms.BorderStyle.None>et.

## <a name="see-also"></a>Voir aussi

- [Panel, contrôle](panel-control-windows-forms.md)
- [Vue d’ensemble du contrôle Panel](panel-control-overview-windows-forms.md)
- [Guide pratique : Définir l’arrière-plan d’un panneau](how-to-set-the-background-of-a-windows-forms-panel.md)
