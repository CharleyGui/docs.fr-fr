---
title: Définir l’arrière-plan d’un panneau à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 8bdefba433632f7ba02f549a549c52c7aa56c2d7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731922"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>Comment : définir l’arrière-plan d’un panneau Windows Forms à l’aide du concepteur

Un contrôle Windows Forms <xref:System.Windows.Forms.Panel> peut afficher une couleur d’arrière-plan et une image d’arrière-plan. La propriété <xref:System.Windows.Forms.Control.BackColor%2A> définit la couleur d’arrière-plan des contrôles contenus dans le panneau, tels que les étiquettes et les cases d’option. Si la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> n’est pas définie, la sélection <xref:System.Windows.Forms.Control.BackColor%2A> remplit tout le panneau. Si la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> est définie, l’image s’affiche derrière les contrôles contenus dans le panneau.

La procédure suivante requiert un projet d' **application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.Panel>. Pour plus d’informations sur la façon de configurer un tel projet dans Visual Studio, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="set-the-background-in-the-windows-forms-designer"></a>Définir l’arrière-plan dans le Concepteur Windows Forms

1. Ouvrez le projet dans Visual Studio et sélectionnez le contrôle <xref:System.Windows.Forms.Panel>.

2. Dans la fenêtre **Propriétés** , cliquez sur le bouton fléché en regard de la propriété <xref:System.Windows.Forms.Control.BackColor%2A> pour afficher une fenêtre avec trois onglets.

3. Sélectionnez l’onglet **personnalisé** pour afficher une palette de couleurs.

4. Sélectionnez l’onglet **Web** ou **système** pour afficher une liste de noms prédéfinis pour les couleurs, puis sélectionnez une couleur.

5. Dans la fenêtre **Propriétés** , cliquez sur le bouton fléché en regard de la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A>.

6. Dans la boîte de dialogue **ouvrir** , sélectionnez le fichier que vous souhaitez afficher.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel, contrôle](panel-control-windows-forms.md)
- [Vue d’ensemble du contrôle Panel](panel-control-overview-windows-forms.md)
- [Guide pratique pour grouper les contrôles avec le contrôle Panel Windows Forms à l'aide du concepteur](group-controls-with-wf-panel-control-using-the-designer.md)
