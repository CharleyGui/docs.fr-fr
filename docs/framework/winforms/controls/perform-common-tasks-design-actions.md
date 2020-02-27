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
# <a name="walkthrough-perform-common-tasks-using-designer-actions"></a><span data-ttu-id="da613-102">Procédure pas à pas : effectuer des tâches courantes à l’aide d’actions de concepteur</span><span class="sxs-lookup"><span data-stu-id="da613-102">Walkthrough: Perform common tasks using designer actions</span></span>

<span data-ttu-id="da613-103">Lorsque vous construisez des formulaires et des contrôles pour votre application Windows Forms, vous effectuez de nombreuses tâches à plusieurs reprises.</span><span class="sxs-lookup"><span data-stu-id="da613-103">As you construct forms and controls for your Windows Forms application, there are many tasks you'll perform repeatedly.</span></span> <span data-ttu-id="da613-104">La liste suivante présente certaines des tâches couramment exécutées :</span><span class="sxs-lookup"><span data-stu-id="da613-104">The following list shows some of the commonly performed tasks you'll come across:</span></span>

- <span data-ttu-id="da613-105">Ajout ou suppression d’un onglet sur un <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="da613-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>
- <span data-ttu-id="da613-106">Ancrage d’un contrôle à son parent.</span><span class="sxs-lookup"><span data-stu-id="da613-106">Docking a control to its parent.</span></span>
- <span data-ttu-id="da613-107">Modification de l’orientation d’un contrôle de <xref:System.Windows.Forms.SplitContainer>.</span><span class="sxs-lookup"><span data-stu-id="da613-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="da613-108">Pour accélérer le développement, de nombreux contrôles offrent des actions de concepteur, qui sont des menus contextuels qui vous permettent d’effectuer des tâches courantes comme celles-ci dans un seul geste au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="da613-108">To speed development, many controls offer designer actions, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="da613-109">Ces tâches sont appelées *verbes d’actions de concepteur*.</span><span class="sxs-lookup"><span data-stu-id="da613-109">These tasks are called *designer actions verbs*.</span></span>

<span data-ttu-id="da613-110">Les actions de concepteur restent attachées à une instance de contrôle pendant sa durée de vie dans le concepteur et sont toujours disponibles.</span><span class="sxs-lookup"><span data-stu-id="da613-110">Designer actions remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="da613-111">Créer le projet</span><span class="sxs-lookup"><span data-stu-id="da613-111">Create the project</span></span>

<span data-ttu-id="da613-112">La première étape consiste à créer le projet et à configurer le formulaire.</span><span class="sxs-lookup"><span data-stu-id="da613-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="da613-113">Dans Visual Studio, créez un projet d’application Windows appelé **DesignerActionsExample**.</span><span class="sxs-lookup"><span data-stu-id="da613-113">In Visual Studio, create a Windows-based application project called **DesignerActionsExample**.</span></span>

2. <span data-ttu-id="da613-114">Sélectionnez le formulaire dans la **Concepteur Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="da613-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-designer-actions"></a><span data-ttu-id="da613-115">Utiliser des actions du concepteur</span><span class="sxs-lookup"><span data-stu-id="da613-115">Use designer actions</span></span>

<span data-ttu-id="da613-116">Les actions de concepteur sont toujours disponibles au moment de la conception sur les contrôles qui les proposent.</span><span class="sxs-lookup"><span data-stu-id="da613-116">Designer actions are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="da613-117">Faites glisser un <xref:System.Windows.Forms.TabControl> de la **boîte à outils** vers votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="da613-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="da613-118">Notez le glyphe des actions du concepteur (![petite flèche noire](./media/designer-actions-glyph.gif)) qui apparaît sur le côté du <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="da613-118">Note the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="da613-119">Cliquez sur le glyphe actions du concepteur.</span><span class="sxs-lookup"><span data-stu-id="da613-119">Click the designer actions glyph.</span></span> <span data-ttu-id="da613-120">Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément **Ajouter un onglet** .</span><span class="sxs-lookup"><span data-stu-id="da613-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="da613-121">Notez qu’une nouvelle page d’onglets est ajoutée au <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="da613-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="da613-122">Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="da613-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="da613-123">Cliquez sur le glyphe actions du concepteur.</span><span class="sxs-lookup"><span data-stu-id="da613-123">Click the designer actions glyph.</span></span> <span data-ttu-id="da613-124">Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément **Ajouter une colonne** .</span><span class="sxs-lookup"><span data-stu-id="da613-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="da613-125">Notez qu’une nouvelle colonne est ajoutée au contrôle <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="da613-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="da613-126">Faites glisser un contrôle <xref:System.Windows.Forms.SplitContainer> de la **boîte à outils** vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="da613-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="da613-127">Cliquez sur le glyphe actions du concepteur.</span><span class="sxs-lookup"><span data-stu-id="da613-127">Click the designer actions glyph.</span></span> <span data-ttu-id="da613-128">Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément d' **orientation horizontal Splitter** .</span><span class="sxs-lookup"><span data-stu-id="da613-128">In the shortcut menu that appears next to the glyph, select the **Horizontal Splitter Orientation** item.</span></span> <span data-ttu-id="da613-129">Notez que la barre de fractionnement du contrôle <xref:System.Windows.Forms.SplitContainer> est maintenant orientée horizontalement.</span><span class="sxs-lookup"><span data-stu-id="da613-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="da613-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da613-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
