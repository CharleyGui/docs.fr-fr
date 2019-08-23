---
title: 'Procédure : superposer des objets dans des Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: 818f36633575b248d92da475c462cc0f211fe969
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966537"
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="c06e4-102">Procédure : superposer des objets dans des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c06e4-102">How to: Layer Objects on Windows Forms</span></span>
<span data-ttu-id="c06e4-103">Lorsque vous créez une interface utilisateur complexe ou que vous utilisez un formulaire d’interface multidocument (MDI), vous souhaiterez souvent superposer les contrôles et les formulaires enfants pour créer des interfaces utilisateur plus complexes.</span><span class="sxs-lookup"><span data-stu-id="c06e4-103">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="c06e4-104">Pour déplacer et suivre les contrôles et les fenêtres dans le contexte d’un groupe, vous manipulez leur ordre de plan.</span><span class="sxs-lookup"><span data-stu-id="c06e4-104">To move and keep track of controls and windows within the context of a group, you manipulate their z-order.</span></span> <span data-ttu-id="c06e4-105">L' *ordre de plan* est la superposition visuelle des contrôles sur un formulaire le long de l’axe Z (profondeur) du formulaire.</span><span class="sxs-lookup"><span data-stu-id="c06e4-105">*Z-order* is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="c06e4-106">La fenêtre située en haut de l’ordre de plan chevauche toutes les autres fenêtres.</span><span class="sxs-lookup"><span data-stu-id="c06e4-106">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="c06e4-107">Toutes les autres fenêtres chevauchent la fenêtre en bas de l’ordre de plan.</span><span class="sxs-lookup"><span data-stu-id="c06e4-107">All other windows overlap the window at the bottom of the z-order.</span></span>

## <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="c06e4-108">Pour superposer des contrôles au moment du design</span><span class="sxs-lookup"><span data-stu-id="c06e4-108">To layer controls at design time</span></span>

1. <span data-ttu-id="c06e4-109">Sélectionnez un contrôle que vous souhaitez coucher.</span><span class="sxs-lookup"><span data-stu-id="c06e4-109">Select a control that you want to layer.</span></span>

2. <span data-ttu-id="c06e4-110">Dans le menu **format** , pointez sur **ordre**, puis cliquez sur **mettre au premier plan** ou mettre à l' **arrière**-plan.</span><span class="sxs-lookup"><span data-stu-id="c06e4-110">On the **Format** menu, point to **Order**, and then click **Bring To Front** or **Send To Back**.</span></span>

## <a name="to-layer-controls-programmatically"></a><span data-ttu-id="c06e4-111">Pour superposer des contrôles par programmation</span><span class="sxs-lookup"><span data-stu-id="c06e4-111">To layer controls programmatically</span></span>

- <span data-ttu-id="c06e4-112">Utilisez les <xref:System.Windows.Forms.Control.BringToFront%2A> méthodes <xref:System.Windows.Forms.Control.SendToBack%2A> et pour manipuler l’ordre de plan des contrôles.</span><span class="sxs-lookup"><span data-stu-id="c06e4-112">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>

     <span data-ttu-id="c06e4-113">Par exemple, si un <xref:System.Windows.Forms.TextBox> contrôle, `txtFirstName`, se trouve sous un autre contrôle et que vous souhaitez l’utiliser en premier, utilisez le code suivant:</span><span class="sxs-lookup"><span data-stu-id="c06e4-113">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>

    ```vb
    txtFirstName.BringToFront()
    ```

    ```csharp
    txtFirstName.BringToFront();
    ```

    ```cpp
    txtFirstName->BringToFront();
    ```

> [!NOTE]
> <span data-ttu-id="c06e4-114">Windows Forms prend en charge la *relation contenant-contenu des contrôles*.</span><span class="sxs-lookup"><span data-stu-id="c06e4-114">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="c06e4-115">La relation contenant-contenu de contrôle implique de placer un certain nombre de contrôles dans un contrôle conteneur <xref:System.Windows.Forms.RadioButton> , tel qu' <xref:System.Windows.Forms.GroupBox> un certain nombre de contrôles dans un contrôle.</span><span class="sxs-lookup"><span data-stu-id="c06e4-115">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="c06e4-116">Vous pouvez ensuite superposer les contrôles dans le contrôle conteneur.</span><span class="sxs-lookup"><span data-stu-id="c06e4-116">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="c06e4-117">Le déplacement de la zone de groupe déplace également les contrôles, car ils sont contenus à l’intérieur de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="c06e4-117">Moving the group box moves the controls as well, because they are contained inside it.</span></span>

## <a name="see-also"></a><span data-ttu-id="c06e4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c06e4-118">See also</span></span>

- [<span data-ttu-id="c06e4-119">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c06e4-119">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="c06e4-120">Disposition des contrôles dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c06e4-120">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="c06e4-121">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c06e4-121">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="c06e4-122">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c06e4-122">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="c06e4-123">Classement par fonction des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c06e4-123">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
