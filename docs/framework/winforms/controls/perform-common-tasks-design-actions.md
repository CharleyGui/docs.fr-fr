---
title: Effectuer des tâches courantes à l’aide d’actions de concepteur sur les contrôles
ms.date: 02/13/2019
helpviewer_keywords:
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 342741b9ce032b1b8ec50a6c689d9109d12f5b3b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634882"
---
# <a name="walkthrough-perform-common-tasks-using-designer-actions"></a>Procédure pas à pas : effectuer des tâches courantes à l’aide d’actions de concepteur

Lorsque vous construisez des formulaires et des contrôles pour votre application Windows Forms, vous effectuez de nombreuses tâches à plusieurs reprises. La liste suivante présente certaines des tâches couramment exécutées :

- Ajout ou suppression d’un onglet sur un <xref:System.Windows.Forms.TabControl>.
- Ancrage d’un contrôle à son parent.
- Modification de l’orientation d’un contrôle de <xref:System.Windows.Forms.SplitContainer>.

Pour accélérer le développement, de nombreux contrôles offrent des actions de concepteur, qui sont des menus contextuels qui vous permettent d’effectuer des tâches courantes comme celles-ci dans un seul geste au moment de la conception. Ces tâches sont appelées *verbes d’actions de concepteur*.

Les actions de concepteur restent attachées à une instance de contrôle pendant sa durée de vie dans le concepteur et sont toujours disponibles.

## <a name="create-the-project"></a>Créer le projet

La première étape consiste à créer le projet et à configurer le formulaire.

1. Dans Visual Studio, créez un projet d’application Windows appelé **DesignerActionsExample**.

2. Sélectionnez le formulaire dans la **Concepteur Windows Forms**.

## <a name="use-designer-actions"></a>Utiliser des actions du concepteur

Les actions de concepteur sont toujours disponibles au moment de la conception sur les contrôles qui les proposent.

1. Faites glisser un <xref:System.Windows.Forms.TabControl> de la **boîte à outils** vers votre formulaire. Notez le glyphe des actions du concepteur (![petite flèche noire](./media/designer-actions-glyph.gif)) qui apparaît sur le côté du <xref:System.Windows.Forms.TabControl>.

2. Cliquez sur le glyphe actions du concepteur. Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément **Ajouter un onglet** . Notez qu’une nouvelle page d’onglets est ajoutée au <xref:System.Windows.Forms.TabControl>.

3. Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire.

4. Cliquez sur le glyphe actions du concepteur. Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément **Ajouter une colonne** . Notez qu’une nouvelle colonne est ajoutée au contrôle <xref:System.Windows.Forms.TableLayoutPanel>.

5. Faites glisser un contrôle <xref:System.Windows.Forms.SplitContainer> de la **boîte à outils** vers le formulaire.

6. Cliquez sur le glyphe actions du concepteur. Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément d' **orientation horizontal Splitter** . Notez que la barre de fractionnement du contrôle <xref:System.Windows.Forms.SplitContainer> est maintenant orientée horizontalement.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
