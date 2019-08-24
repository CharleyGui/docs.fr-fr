---
title: 'Procédure : réattribuer des contrôles existants à un autre parent'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 84e662e0bd2689115abe128c6442e4462eed3e18
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987039"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Procédure : Réassigner des contrôles existants à un autre parent

Vous pouvez affecter des contrôles qui existent sur votre formulaire à un nouveau contrôle de conteneur.

1. Dans Visual Studio, faites glisser <xref:System.Windows.Forms.Button> trois contrôles de la **boîte à outils** vers le formulaire. Disposez-les près les uns des autres en les laissant non alignés.

2. Dans la **boîte à outils**, cliquez sur l’icône de contrôle <xref:System.Windows.Forms.FlowLayoutPanel> . (Ne faites pas glisser l’icône sur le formulaire.)

3. Placez le pointeur de la souris près des trois contrôles <xref:System.Windows.Forms.Button> .

   Le pointeur devient une croix à laquelle est attachée l’icône de contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .

4. Cliquez et maintenez le bouton de la souris enfoncé.

5. Faites glisser le pointeur de la souris pour tracer le contour du contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .

6. Tracez le contour des trois contrôles <xref:System.Windows.Forms.Button> .

7. Relâchez le bouton de la souris.

   Les trois contrôles <xref:System.Windows.Forms.Button> sont maintenant insérés dans le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide d’un TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide de lignes d’alignement](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
