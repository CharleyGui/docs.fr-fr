---
title: 'Procédure pas à pas : exécution de tâches courantes à l’aide de balises actives dans les contrôles Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 34c14c0afd9632b06947fd72e46ddbda070cfb0f
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015764"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a>Procédure pas à pas : Effectuer des tâches courantes à l’aide de balises actives

Lorsque vous construisez des formulaires et des contrôles pour votre application Windows Forms, vous effectuez de nombreuses tâches à plusieurs reprises. Voici quelques-unes des tâches courantes que vous pouvez rencontrer:

- Ajout ou suppression d’un onglet sur <xref:System.Windows.Forms.TabControl>un.

- Ancrage d’un contrôle à son parent.

- Modification de l’orientation d' <xref:System.Windows.Forms.SplitContainer> un contrôle.

Pour accélérer le développement, de nombreux contrôles offrent des balises actives, qui sont des menus contextuels qui vous permettent d’effectuer des tâches courantes comme celles-ci en un seul mouvement au moment de la conception. Ces tâches sont appelées *verbes de balise active*.

Les balises actives restent attachées à une instance de contrôle pendant sa durée de vie dans le concepteur et sont toujours disponibles.

## <a name="create-the-project"></a>Créer le projet

La première étape consiste à créer le projet et à configurer le formulaire.

1. Dans Visual Studio, créez un projet d’application Windows appelé **SmartTagsExample**.

2. Sélectionnez le formulaire dans la **Concepteur Windows Forms**.

## <a name="use-smart-tags"></a>Utiliser des balises actives

Les balises actives sont toujours disponibles au moment de la conception sur les contrôles qui les proposent.

1. Faites glisser <xref:System.Windows.Forms.TabControl> un de la **boîte à outils** vers votre formulaire. Notez le glyphe de balise active![(glyphe](./media/vs-winformsmttagglyph.gif)de balise active) qui apparaît <xref:System.Windows.Forms.TabControl>sur le côté de.

2. Cliquez sur le glyphe de balise active. Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément **Ajouter un onglet** . Notez qu’une nouvelle page d’onglets est ajoutée <xref:System.Windows.Forms.TabControl>au.

3. Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire.

4. Cliquez sur le glyphe de balise active. Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément **Ajouter une colonne** . Notez qu’une nouvelle colonne est ajoutée au <xref:System.Windows.Forms.TableLayoutPanel> contrôle.

5. Faites glisser un contrôle <xref:System.Windows.Forms.SplitContainer> de la **boîte à outils** vers le formulaire.

6. Cliquez sur le glyphe de balise active. Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément d' **orientation horizontal Splitter** . Notez que la <xref:System.Windows.Forms.SplitContainer> barre de fractionnement du contrôle est maintenant orientée horizontalement.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
