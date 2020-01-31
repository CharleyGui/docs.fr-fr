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
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a><span data-ttu-id="3cab5-102">Procédure pas à pas : exécution de tâches courantes à l’aide de balises actives</span><span class="sxs-lookup"><span data-stu-id="3cab5-102">Walkthrough: Perform Common Tasks Using Smart Tags</span></span>

<span data-ttu-id="3cab5-103">Lorsque vous construisez des formulaires et des contrôles pour votre application Windows Forms, vous effectuez de nombreuses tâches à plusieurs reprises.</span><span class="sxs-lookup"><span data-stu-id="3cab5-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="3cab5-104">Voici quelques-unes des tâches courantes que vous pouvez rencontrer :</span><span class="sxs-lookup"><span data-stu-id="3cab5-104">These are some of the commonly performed tasks you will encounter:</span></span>

- <span data-ttu-id="3cab5-105">Ajout ou suppression d’un onglet sur un <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="3cab5-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>

- <span data-ttu-id="3cab5-106">Ancrage d’un contrôle à son parent.</span><span class="sxs-lookup"><span data-stu-id="3cab5-106">Docking a control to its parent.</span></span>

- <span data-ttu-id="3cab5-107">Modification de l’orientation d’un contrôle de <xref:System.Windows.Forms.SplitContainer>.</span><span class="sxs-lookup"><span data-stu-id="3cab5-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="3cab5-108">Pour accélérer le développement, de nombreux contrôles offrent des balises actives, qui sont des menus contextuels qui vous permettent d’effectuer des tâches courantes comme celles-ci en un seul mouvement au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="3cab5-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="3cab5-109">Ces tâches sont appelées *verbes de balise active*.</span><span class="sxs-lookup"><span data-stu-id="3cab5-109">These tasks are called *smart-tag verbs*.</span></span>

<span data-ttu-id="3cab5-110">Les balises actives restent attachées à une instance de contrôle pendant sa durée de vie dans le concepteur et sont toujours disponibles.</span><span class="sxs-lookup"><span data-stu-id="3cab5-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="3cab5-111">Créer le projet</span><span class="sxs-lookup"><span data-stu-id="3cab5-111">Create the project</span></span>

<span data-ttu-id="3cab5-112">La première étape consiste à créer le projet et à configurer le formulaire.</span><span class="sxs-lookup"><span data-stu-id="3cab5-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="3cab5-113">Dans Visual Studio, créez un projet d’application Windows appelé **SmartTagsExample**.</span><span class="sxs-lookup"><span data-stu-id="3cab5-113">In Visual Studio, create a Windows-based application project called **SmartTagsExample**.</span></span>

2. <span data-ttu-id="3cab5-114">Sélectionnez le formulaire dans la **Concepteur Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="3cab5-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-smart-tags"></a><span data-ttu-id="3cab5-115">Utiliser des balises actives</span><span class="sxs-lookup"><span data-stu-id="3cab5-115">Use smart tags</span></span>

<span data-ttu-id="3cab5-116">Les balises actives sont toujours disponibles au moment de la conception sur les contrôles qui les proposent.</span><span class="sxs-lookup"><span data-stu-id="3cab5-116">Smart tags are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="3cab5-117">Faites glisser un <xref:System.Windows.Forms.TabControl> de la **boîte à outils** vers votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="3cab5-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="3cab5-118">Notez le glyphe de balise active (![](./media/vs-winformsmttagglyph.gif)de glyphe de balise active) qui apparaît sur le côté du <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="3cab5-118">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="3cab5-119">Cliquez sur le glyphe de balise active.</span><span class="sxs-lookup"><span data-stu-id="3cab5-119">Click the smart-tag glyph.</span></span> <span data-ttu-id="3cab5-120">Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément **Ajouter un onglet** .</span><span class="sxs-lookup"><span data-stu-id="3cab5-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="3cab5-121">Notez qu’une nouvelle page d’onglets est ajoutée au <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="3cab5-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="3cab5-122">Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="3cab5-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="3cab5-123">Cliquez sur le glyphe de balise active.</span><span class="sxs-lookup"><span data-stu-id="3cab5-123">Click the smart-tag glyph.</span></span> <span data-ttu-id="3cab5-124">Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément **Ajouter une colonne** .</span><span class="sxs-lookup"><span data-stu-id="3cab5-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="3cab5-125">Notez qu’une nouvelle colonne est ajoutée au contrôle <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="3cab5-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="3cab5-126">Faites glisser un contrôle <xref:System.Windows.Forms.SplitContainer> de la **boîte à outils** vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="3cab5-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="3cab5-127">Cliquez sur le glyphe de balise active.</span><span class="sxs-lookup"><span data-stu-id="3cab5-127">Click the smart-tag glyph.</span></span> <span data-ttu-id="3cab5-128">Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément d' **orientation horizontal Splitter** .</span><span class="sxs-lookup"><span data-stu-id="3cab5-128">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="3cab5-129">Notez que la barre de fractionnement du contrôle <xref:System.Windows.Forms.SplitContainer> est maintenant orientée horizontalement.</span><span class="sxs-lookup"><span data-stu-id="3cab5-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="3cab5-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cab5-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
