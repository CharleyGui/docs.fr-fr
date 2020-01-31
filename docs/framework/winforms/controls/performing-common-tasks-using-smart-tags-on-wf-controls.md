---
title: Tâches courantes de performi à l’aide de balises actives sur les contrôles
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 826313d0a89410f62c034a5fba4dee32e90a1750
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744260"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a>Procédure pas à pas : exécution de tâches courantes à l’aide de balises actives

Lorsque vous construisez des formulaires et des contrôles pour votre application Windows Forms, vous effectuez de nombreuses tâches à plusieurs reprises. Voici quelques-unes des tâches courantes que vous pouvez rencontrer :

- Ajout ou suppression d’un onglet sur un <xref:System.Windows.Forms.TabControl>.

- Ancrage d’un contrôle à son parent.

- Modification de l’orientation d’un contrôle de <xref:System.Windows.Forms.SplitContainer>.

Pour accélérer le développement, de nombreux contrôles offrent des balises actives, qui sont des menus contextuels qui vous permettent d’effectuer des tâches courantes comme celles-ci en un seul mouvement au moment de la conception. Ces tâches sont appelées *verbes de balise active*.

Les balises actives restent attachées à une instance de contrôle pendant sa durée de vie dans le concepteur et sont toujours disponibles.

## <a name="create-the-project"></a>Créer le projet

La première étape consiste à créer le projet et à configurer le formulaire.

1. Dans Visual Studio, créez un projet d’application Windows appelé **SmartTagsExample**.

2. Sélectionnez le formulaire dans la **Concepteur Windows Forms**.

## <a name="use-smart-tags"></a>Utiliser des balises actives

Les balises actives sont toujours disponibles au moment de la conception sur les contrôles qui les proposent.

1. Faites glisser un <xref:System.Windows.Forms.TabControl> de la **boîte à outils** vers votre formulaire. Notez le glyphe de balise active (![](./media/vs-winformsmttagglyph.gif)de glyphe de balise active) qui apparaît sur le côté du <xref:System.Windows.Forms.TabControl>.

2. Cliquez sur le glyphe de balise active. Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément **Ajouter un onglet** . Notez qu’une nouvelle page d’onglets est ajoutée au <xref:System.Windows.Forms.TabControl>.

3. Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire.

4. Cliquez sur le glyphe de balise active. Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément **Ajouter une colonne** . Notez qu’une nouvelle colonne est ajoutée au contrôle <xref:System.Windows.Forms.TableLayoutPanel>.

5. Faites glisser un contrôle <xref:System.Windows.Forms.SplitContainer> de la **boîte à outils** vers le formulaire.

6. Cliquez sur le glyphe de balise active. Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément d' **orientation horizontal Splitter** . Notez que la barre de fractionnement du contrôle <xref:System.Windows.Forms.SplitContainer> est maintenant orientée horizontalement.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
