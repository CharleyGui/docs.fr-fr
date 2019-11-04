---
title: 'Comment : réassignation de contrôles existants à un parent différent'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1767fcff1742f4ad630b4b996c709b7ded53a129
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459198"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Comment : réassigner des contrôles existants à un autre parent

Vous pouvez affecter des contrôles qui existent sur votre formulaire à un nouveau contrôle de conteneur.

1. Dans Visual Studio, faites glisser trois contrôles <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire. Disposez-les près les uns des autres en les laissant non alignés.

2. Dans la **Boîte à outils**, cliquez sur l’icône de contrôle <xref:System.Windows.Forms.FlowLayoutPanel> . (Ne faites pas glisser l’icône sur le formulaire.)

3. Déplacez le pointeur de la souris près des trois contrôles <xref:System.Windows.Forms.Button> .

   Le pointeur devient une croix à laquelle est attachée l’icône de contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .

4. Cliquez et maintenez le bouton de la souris enfoncé.

5. Faites glisser le pointeur de la souris pour tracer le contour du contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .

6. Tracez le contour des trois contrôles <xref:System.Windows.Forms.Button> .

7. Relâchez le bouton de la souris.

   Les trois contrôles <xref:System.Windows.Forms.Button> sont maintenant insérés dans le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
