---
title: SplitContainer, contrôle
ms.date: 03/30/2017
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
ms.openlocfilehash: ac04f60847aa6f77c11637f37b5ec94b6f7ef341
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742906"
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="40778-102">SplitContainer, contrôle (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="40778-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="40778-103">Le contrôle Windows Forms `SplitContainer` peut être considéré comme un composite ; il s'agit de deux panneaux séparés par une barre mobile.</span><span class="sxs-lookup"><span data-stu-id="40778-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="40778-104">Quand le pointeur de la souris est sur la barre, il change de forme pour montrer que la barre est mobile.</span><span class="sxs-lookup"><span data-stu-id="40778-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40778-105">Dans la **boîte à outils**, ce contrôle remplace le contrôle <xref:System.Windows.Forms.Splitter> qui était dans la version précédente de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="40778-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="40778-106">Il vaut beaucoup mieux utiliser le contrôle `SplitContainer` que le contrôle <xref:System.Windows.Forms.Splitter>.</span><span class="sxs-lookup"><span data-stu-id="40778-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="40778-107">La classe <xref:System.Windows.Forms.Splitter> est toujours incluse dans .NET Framework pour la compatibilité avec les applications existantes, mais nous vous encourageons vivement à utiliser le contrôle `SplitContainer` pour les nouveaux projets.</span><span class="sxs-lookup"><span data-stu-id="40778-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="40778-108">Le contrôle `SplitContainer` vous permet de créer des interfaces utilisateur complexes ; souvent, une sélection dans un panneau détermine les objets affichés dans l'autre panneau.</span><span class="sxs-lookup"><span data-stu-id="40778-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="40778-109">Cette disposition est très efficace pour afficher et parcourir des informations.</span><span class="sxs-lookup"><span data-stu-id="40778-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="40778-110">Le fait d'avoir deux panneaux vous permet de regrouper les informations dans des zones et la barre, ou « séparateur », permet aux utilisateurs de redimensionner facilement les panneaux.</span><span class="sxs-lookup"><span data-stu-id="40778-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="40778-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="40778-111">In This Section</span></span>  
 [<span data-ttu-id="40778-112">Vue d’ensemble du contrôle SplitContainer</span><span class="sxs-lookup"><span data-stu-id="40778-112">SplitContainer Control Overview</span></span>](splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="40778-113">Présente le contrôle `SplitContainer` et décrit les propriétés, méthodes et événements couramment utilisés.</span><span class="sxs-lookup"><span data-stu-id="40778-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="40778-114">Guide pratique pour définir le redimensionnement et le positionnement du comportement dans une fenêtre fractionnée</span><span class="sxs-lookup"><span data-stu-id="40778-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="40778-115">Décrit comment contrôler le séparateur dans le contrôle `SplitContainer`.</span><span class="sxs-lookup"><span data-stu-id="40778-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="40778-116">Guide pratique pour fractionner une fenêtre horizontalement</span><span class="sxs-lookup"><span data-stu-id="40778-116">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="40778-117">Décrit comment contrôler l'orientation du séparateur dans le contrôle `SplitContainer`.</span><span class="sxs-lookup"><span data-stu-id="40778-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="40778-118">Guide pratique pour créer une interface utilisateur à plusieurs volets à l'aide des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40778-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="40778-119">Crée une interface utilisateur à plusieurs volets semblable à celle utilisée dans Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="40778-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="40778-120">Consultez également [Comment : fractionner une fenêtre horizontalement à l’aide du concepteur](how-to-split-a-window-horizontally-using-the-designer.md), [Comment : créer une interface de style Explorateur Windows sur un Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [Comment : créer une interface utilisateur multivolet avec Windows Forms à l’aide du concepteur](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="40778-120">Also see [How to: Split a Window Horizontally Using the Designer](how-to-split-a-window-horizontally-using-the-designer.md), [How to: Create a Windows Explorer–Style Interface on a Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="40778-121">Référence</span><span class="sxs-lookup"><span data-stu-id="40778-121">Reference</span></span>  
 <span data-ttu-id="40778-122">Classe <xref:System.Windows.Forms.SplitContainer></span><span class="sxs-lookup"><span data-stu-id="40778-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="40778-123">Décrit cette classe et fournit des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="40778-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="40778-124">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="40778-124">Related Sections</span></span>  
 [<span data-ttu-id="40778-125">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40778-125">Windows Forms Controls</span></span>](index.md)  
 <span data-ttu-id="40778-126">Fournit des liens vers des rubriques sur les contrôles conçus spécifiquement pour fonctionner avec Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="40778-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="40778-127">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40778-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="40778-128">Fournit une liste complète de contrôles Windows Forms, avec des liens vers des informations sur leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="40778-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
