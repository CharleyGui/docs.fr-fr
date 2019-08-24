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
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a><span data-ttu-id="2a78e-102">Procédure pas à pas : Effectuer des tâches courantes à l’aide de balises actives</span><span class="sxs-lookup"><span data-stu-id="2a78e-102">Walkthrough: Perform Common Tasks Using Smart Tags</span></span>

<span data-ttu-id="2a78e-103">Lorsque vous construisez des formulaires et des contrôles pour votre application Windows Forms, vous effectuez de nombreuses tâches à plusieurs reprises.</span><span class="sxs-lookup"><span data-stu-id="2a78e-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="2a78e-104">Voici quelques-unes des tâches courantes que vous pouvez rencontrer:</span><span class="sxs-lookup"><span data-stu-id="2a78e-104">These are some of the commonly performed tasks you will encounter:</span></span>

- <span data-ttu-id="2a78e-105">Ajout ou suppression d’un onglet sur <xref:System.Windows.Forms.TabControl>un.</span><span class="sxs-lookup"><span data-stu-id="2a78e-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>

- <span data-ttu-id="2a78e-106">Ancrage d’un contrôle à son parent.</span><span class="sxs-lookup"><span data-stu-id="2a78e-106">Docking a control to its parent.</span></span>

- <span data-ttu-id="2a78e-107">Modification de l’orientation d' <xref:System.Windows.Forms.SplitContainer> un contrôle.</span><span class="sxs-lookup"><span data-stu-id="2a78e-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="2a78e-108">Pour accélérer le développement, de nombreux contrôles offrent des balises actives, qui sont des menus contextuels qui vous permettent d’effectuer des tâches courantes comme celles-ci en un seul mouvement au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="2a78e-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="2a78e-109">Ces tâches sont appelées *verbes de balise active*.</span><span class="sxs-lookup"><span data-stu-id="2a78e-109">These tasks are called *smart-tag verbs*.</span></span>

<span data-ttu-id="2a78e-110">Les balises actives restent attachées à une instance de contrôle pendant sa durée de vie dans le concepteur et sont toujours disponibles.</span><span class="sxs-lookup"><span data-stu-id="2a78e-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="2a78e-111">Créer le projet</span><span class="sxs-lookup"><span data-stu-id="2a78e-111">Create the project</span></span>

<span data-ttu-id="2a78e-112">La première étape consiste à créer le projet et à configurer le formulaire.</span><span class="sxs-lookup"><span data-stu-id="2a78e-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="2a78e-113">Dans Visual Studio, créez un projet d’application Windows appelé **SmartTagsExample**.</span><span class="sxs-lookup"><span data-stu-id="2a78e-113">In Visual Studio, create a Windows-based application project called **SmartTagsExample**.</span></span>

2. <span data-ttu-id="2a78e-114">Sélectionnez le formulaire dans la **Concepteur Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="2a78e-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-smart-tags"></a><span data-ttu-id="2a78e-115">Utiliser des balises actives</span><span class="sxs-lookup"><span data-stu-id="2a78e-115">Use smart tags</span></span>

<span data-ttu-id="2a78e-116">Les balises actives sont toujours disponibles au moment de la conception sur les contrôles qui les proposent.</span><span class="sxs-lookup"><span data-stu-id="2a78e-116">Smart tags are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="2a78e-117">Faites glisser <xref:System.Windows.Forms.TabControl> un de la **boîte à outils** vers votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="2a78e-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="2a78e-118">Notez le glyphe de balise active![(glyphe](./media/vs-winformsmttagglyph.gif)de balise active) qui apparaît <xref:System.Windows.Forms.TabControl>sur le côté de.</span><span class="sxs-lookup"><span data-stu-id="2a78e-118">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="2a78e-119">Cliquez sur le glyphe de balise active.</span><span class="sxs-lookup"><span data-stu-id="2a78e-119">Click the smart-tag glyph.</span></span> <span data-ttu-id="2a78e-120">Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément **Ajouter un onglet** .</span><span class="sxs-lookup"><span data-stu-id="2a78e-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="2a78e-121">Notez qu’une nouvelle page d’onglets est ajoutée <xref:System.Windows.Forms.TabControl>au.</span><span class="sxs-lookup"><span data-stu-id="2a78e-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="2a78e-122">Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="2a78e-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="2a78e-123">Cliquez sur le glyphe de balise active.</span><span class="sxs-lookup"><span data-stu-id="2a78e-123">Click the smart-tag glyph.</span></span> <span data-ttu-id="2a78e-124">Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément **Ajouter une colonne** .</span><span class="sxs-lookup"><span data-stu-id="2a78e-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="2a78e-125">Notez qu’une nouvelle colonne est ajoutée au <xref:System.Windows.Forms.TableLayoutPanel> contrôle.</span><span class="sxs-lookup"><span data-stu-id="2a78e-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="2a78e-126">Faites glisser un contrôle <xref:System.Windows.Forms.SplitContainer> de la **boîte à outils** vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="2a78e-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="2a78e-127">Cliquez sur le glyphe de balise active.</span><span class="sxs-lookup"><span data-stu-id="2a78e-127">Click the smart-tag glyph.</span></span> <span data-ttu-id="2a78e-128">Dans le menu contextuel qui s’affiche en regard du glyphe, sélectionnez l’élément d' **orientation horizontal Splitter** .</span><span class="sxs-lookup"><span data-stu-id="2a78e-128">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="2a78e-129">Notez que la <xref:System.Windows.Forms.SplitContainer> barre de fractionnement du contrôle est maintenant orientée horizontalement.</span><span class="sxs-lookup"><span data-stu-id="2a78e-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a78e-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a78e-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
