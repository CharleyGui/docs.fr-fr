---
title: ToolBar, contrôle
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: 027c96bb49e9446244e4b08ba93c551ef043b3c0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735455"
---
# <a name="toolbar-control-windows-forms"></a><span data-ttu-id="1ef9e-102">ToolBar, contrôle (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1ef9e-102">ToolBar Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="1ef9e-103">Le contrôle <xref:System.Windows.Forms.ToolStrip> remplace le contrôle `ToolBar` et lui ajoute des fonctionnalités ; toutefois, le contrôle `ToolBar` est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the `ToolBar` control; however, the `ToolBar` control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="1ef9e-104">Le contrôle Windows Forms `ToolBar` est utilisé sur les formulaires comme barre de contrôle affichant une rangée de menus déroulants et de boutons bitmap qui activent des commandes.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-104">The Windows Forms `ToolBar` control is used on forms as a control bar that displays a row of drop-down menus and bitmapped buttons that activate commands.</span></span> <span data-ttu-id="1ef9e-105">Ainsi, un clic sur un bouton de barre d'outils revient à choisir une commande de menu.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-105">Thus, clicking a toolbar button is equivalent to choosing a menu command.</span></span> <span data-ttu-id="1ef9e-106">Vous pouvez configurer les boutons pour qu'ils apparaissent et se comportent comme des boutons de commande, des menus déroulants ou des séparateurs.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-106">The buttons can be configured to appear and behave as push buttons, drop-down menus, or separators.</span></span> <span data-ttu-id="1ef9e-107">En règle générale, une barre d'outils contient des boutons et des menus qui correspondent à des éléments dans la structure de menu de l'application et fournissent un accès rapide aux commandes et aux fonctions les plus fréquemment utilisées d'une application.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-107">Typically, a toolbar contains buttons and menus that correspond to items in an application's menu structure, providing quick access to an application's most frequently used functions and commands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ef9e-108">La propriété <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> du contrôle `ToolBar` prend une instance de la classe <xref:System.Windows.Forms.ContextMenu> comme référence.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-108">The `ToolBar` control's <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span> <span data-ttu-id="1ef9e-109">Vous devez faire attention à la référence que vous passez lors de l'implémentation de ce genre de bouton sur les barres d'outils de votre application, car la propriété accepte tout objet qui hérite de la classe <xref:System.Windows.Forms.Menu>.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-109">Carefully consider the reference you pass when implementing this sort of button on toolbars in your application, as the property will accept any object that inherits from the <xref:System.Windows.Forms.Menu> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ef9e-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1ef9e-110">In This Section</span></span>  
 [<span data-ttu-id="1ef9e-111">Vue d’ensemble du contrôle ToolBar</span><span class="sxs-lookup"><span data-stu-id="1ef9e-111">ToolBar Control Overview</span></span>](toolbar-control-overview-windows-forms.md)  
 <span data-ttu-id="1ef9e-112">Présente les concepts généraux du contrôle `ToolBar`, qui vous permet de concevoir des barres d'outils personnalisées avec lesquelles les utilisateurs peuvent travailler.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-112">Introduces the general concepts of the `ToolBar` control, which allows you to design custom toolbars that your users can work with.</span></span>  
  
 [<span data-ttu-id="1ef9e-113">Guide pratique pour ajouter des boutons à un contrôle ToolBar</span><span class="sxs-lookup"><span data-stu-id="1ef9e-113">How to: Add Buttons to a ToolBar Control</span></span>](how-to-add-buttons-to-a-toolbar-control.md)  
 <span data-ttu-id="1ef9e-114">Décrit comment ajouter des boutons à un contrôle `ToolBar`.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-114">Describes how to add buttons to a `ToolBar` control.</span></span>  
  
 [<span data-ttu-id="1ef9e-115">Guide pratique pour définir une icône pour un bouton de barre d’outils</span><span class="sxs-lookup"><span data-stu-id="1ef9e-115">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)  
 <span data-ttu-id="1ef9e-116">Décrit comment afficher des icônes dans les boutons d'un contrôle `ToolBar`.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-116">Describes how to display icons within a `ToolBar` control's buttons.</span></span>  
  
 [<span data-ttu-id="1ef9e-117">Guide pratique pour déclencher des événements de menu pour les boutons de barre d’outils</span><span class="sxs-lookup"><span data-stu-id="1ef9e-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)  
 <span data-ttu-id="1ef9e-118">Explique comment écrire du code pour interpréter le bouton sur lequel l'utilisateur clique dans un contrôle `ToolBar`.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-118">Gives directions on writing code to interpret which button the user clicks in a `ToolBar` control.</span></span>  
  
 <span data-ttu-id="1ef9e-119">Consultez également [Comment : définir une icône pour un bouton de barre d’outils à l’aide du concepteur](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [Comment : ajouter des boutons à un contrôle ToolBar à l’aide du concepteur](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="1ef9e-119">Also see [How to: Define an Icon for a ToolBar Button Using the Designer](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [How to: Add Buttons to a ToolBar Control Using the Designer](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1ef9e-120">Reference</span><span class="sxs-lookup"><span data-stu-id="1ef9e-120">Reference</span></span>  
 <span data-ttu-id="1ef9e-121">Classe <xref:System.Windows.Forms.ToolBar></span><span class="sxs-lookup"><span data-stu-id="1ef9e-121"><xref:System.Windows.Forms.ToolBar> class</span></span>  
 <span data-ttu-id="1ef9e-122">Fournit des informations de référence sur la classe et ses membres.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-122">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1ef9e-123">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="1ef9e-123">Related Sections</span></span>  
 [<span data-ttu-id="1ef9e-124">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1ef9e-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="1ef9e-125">Fournit une liste complète de contrôles Windows Forms, avec des liens vers des informations sur leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="1ef9e-126">ToolStrip, contrôle</span><span class="sxs-lookup"><span data-stu-id="1ef9e-126">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)  
 <span data-ttu-id="1ef9e-127">Décrit les barres d’outils qui peuvent héberger des menus, des contrôles et des contrôles utilisateur dans les applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1ef9e-127">Describes toolbars that can host menus, controls, and user controls in Windows Forms applications.</span></span>
