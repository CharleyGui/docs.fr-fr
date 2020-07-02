---
title: Développer des contrôles personnalisés
description: En savoir plus sur les contrôles Windows Forms. Plus précisément, vous apprendrez à combiner des contrôles existants, à étendre des contrôles existants et à créer vos propres contrôles personnalisés.
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
ms.openlocfilehash: 12013496c9650489fdd7512206317000fc0ec78c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618374"
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="7d3a7-104">Développement de contrôles Windows Forms personnalisés avec le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7d3a7-104">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="7d3a7-105">Les contrôles Windows Forms sont des composants réutilisables qui encapsulent des fonctionnalités d'interface utilisateur et sont utilisés dans des applications Windows côté client.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-105">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="7d3a7-106">Windows Forms fournit non seulement de nombreux contrôles prêts à l'emploi, mais également l'infrastructure pour le développement de vos propres contrôles.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-106">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="7d3a7-107">Vous pouvez combiner ou étendre des contrôles existants, ou encore créer vos propres contrôles personnalisés.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-107">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="7d3a7-108">Cette section fournit des informations générales et des exemples pour vous aider à développer des contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-108">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7d3a7-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7d3a7-109">In This Section</span></span>  
 [<span data-ttu-id="7d3a7-110">Vue d’ensemble de l’utilisation des contrôles dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7d3a7-110">Overview of Using Controls in Windows Forms</span></span>](overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="7d3a7-111">Décrit les éléments essentiels de l’utilisation des contrôles dans les applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-111">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="7d3a7-112">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="7d3a7-112">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)  
 <span data-ttu-id="7d3a7-113">Décrit les différents types de contrôles personnalisés que vous pouvez créer avec l'espace de noms <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-113">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="7d3a7-114">Concepts de base du développement de contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7d3a7-114">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)  
 <span data-ttu-id="7d3a7-115">Décrit les premières étapes de développement d'un contrôle Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-115">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="7d3a7-116">Propriétés dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7d3a7-116">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)  
 <span data-ttu-id="7d3a7-117">Montre comment ajouter des propriétés à des contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-117">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="7d3a7-118">Événements dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7d3a7-118">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)  
 <span data-ttu-id="7d3a7-119">Montre comment gérer et définir des événements dans des contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-119">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="7d3a7-120">Attributs dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7d3a7-120">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="7d3a7-121">Décrit les attributs que vous pouvez appliquer aux propriétés ou aux autres membres de vos composants et contrôles personnalisés.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-121">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="7d3a7-122">Peinture et rendu personnalisés des contrôles</span><span class="sxs-lookup"><span data-stu-id="7d3a7-122">Custom Control Painting and Rendering</span></span>](custom-control-painting-and-rendering.md)  
 <span data-ttu-id="7d3a7-123">Montre comment personnaliser l'apparence de vos contrôles.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-123">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="7d3a7-124">Disposition dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7d3a7-124">Layout in Windows Forms Controls</span></span>](layout-in-windows-forms-controls.md)  
 <span data-ttu-id="7d3a7-125">Montre comment créer des dispositions sophistiquées pour vos contrôles et formulaires.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-125">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="7d3a7-126">Multithreading dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7d3a7-126">Multithreading in Windows Forms Controls</span></span>](multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="7d3a7-127">Montre comment implémenter des contrôles multithread.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-127">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7d3a7-128">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="7d3a7-128">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="7d3a7-129">Décrit cette classe et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-129">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="7d3a7-130">Décrit cette classe et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-130">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7d3a7-131">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="7d3a7-131">Related Sections</span></span>  
 <span data-ttu-id="7d3a7-132">[Attributs au moment de la conception pour les composants](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="7d3a7-132">[Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span></span>  
 <span data-ttu-id="7d3a7-133">Répertorie les attributs de métadonnées à appliquer aux composants et aux contrôles pour qu'ils s'affichent correctement au moment du design dans les concepteurs visuels.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-133">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 <span data-ttu-id="7d3a7-134">[Extension de la prise en charge au moment du design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="7d3a7-134">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>  
 <span data-ttu-id="7d3a7-135">Décrit comment implémenter des classes telles que les éditeurs et concepteurs qui fournissent la prise en charge au moment du design.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-135">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 <span data-ttu-id="7d3a7-136">[Comment : accorder la licence d'utilisation de composants et de contrôles](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="7d3a7-136">[How to: License Components and Controls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span></span>  
 <span data-ttu-id="7d3a7-137">Décrit comment implémenter la gestion des licences dans votre contrôle ou composant.</span><span class="sxs-lookup"><span data-stu-id="7d3a7-137">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="7d3a7-138">Voir aussi [Développement de contrôles Windows Forms au moment du design](developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="7d3a7-138">Also see [Developing Windows Forms Controls at Design Time](developing-windows-forms-controls-at-design-time.md).</span></span>
