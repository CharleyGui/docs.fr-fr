---
title: 'Procédure pas à pas : exécution de tâches courantes à l’aide de balises actives dans les contrôles Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: 1cc854d735ba88a301d6e2f6a83fe5c8bf881380
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211415"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a>Procédure pas à pas : exécution de tâches courantes à l’aide de balises actives dans les contrôles Windows Forms

Lorsque vous construisez des formulaires et contrôles pour votre application Windows Forms, il existe de nombreuses tâches que vous allez effectuer à plusieurs reprises. Il existe quelques tâches courantes que vous rencontrerez :

- Ajout ou suppression d’un onglet sur un <xref:System.Windows.Forms.TabControl>.

- Ancrage d’un contrôle à son parent.

- Modification de l’orientation d’un <xref:System.Windows.Forms.SplitContainer> contrôle.

Pour accélérer le développement, de nombreux contrôles offrent des balises actives, qui sont des menus contextuels qui vous permettent d’effectuer des tâches courantes comme celles-ci en un seul geste au moment du design. Ces tâches sont appelées *verbes de balise active*.

Balises actives restent attachées à une instance de contrôle pour sa durée de vie dans le concepteur et sont toujours disponibles.

Cette procédure pas à pas décrit notamment les tâches suivantes :

- Création d’un projet Windows Forms

- À l’aide de balises actives

- Activation et désactivation des balises actives

À l’issue de cette procédure, vous comprendrez le rôle joué par ces fonctionnalités de disposition importantes.

## <a name="create-the-project"></a>Créer le projet

La première étape consiste à créer le projet et à configurer le formulaire.

1. Dans Visual Studio, créez un projet d’application Windows appelé « SmartTagsExample » (**fichier** > **New** > **projet**  >  **Visual C#**  ou **Visual Basic** > **bureau classique** > **Windows Forms Application**).

2. Sélectionnez le formulaire dans le **Windows Forms Designer**.

## <a name="use-smart-tags"></a>Utiliser des balises actives

Balises actives sont toujours disponibles au moment du design sur les contrôles qui les proposent.

1. Faites glisser un <xref:System.Windows.Forms.TabControl> à partir de la **boîte à outils** vers votre formulaire. Notez le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) qui apparaît sur le côté du <xref:System.Windows.Forms.TabControl>.

2. Cliquez sur le glyphe de balise active. Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez le **ajouter un onglet** élément. Observez qu’une nouvelle page d’onglets est ajoutée à la <xref:System.Windows.Forms.TabControl>.

3. Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire.

4. Cliquez sur le glyphe de balise active. Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez le **ajouter une colonne** élément. Observez qu’une nouvelle colonne est ajoutée à la <xref:System.Windows.Forms.TableLayoutPanel> contrôle.

5. Faites glisser un contrôle <xref:System.Windows.Forms.SplitContainer> de la **boîte à outils** vers le formulaire.

6. Cliquez sur le glyphe de balise active. Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez le **l’orientation du fractionnement Horizontal** élément. Observez que le <xref:System.Windows.Forms.SplitContainer> barre de fractionnement du contrôle est maintenant orientée horizontalement.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
- [Procédure pas à pas : Ajout de balises actives à un composant de formulaires Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))
