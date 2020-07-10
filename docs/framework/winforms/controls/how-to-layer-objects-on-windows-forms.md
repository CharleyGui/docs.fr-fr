---
title: mettre en couche des objets
description: Découvrez comment superposer des objets sur des contrôles de Windows Forms et des formulaires enfants pour créer des interfaces utilisateur plus complexes.
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6269b09c56963fefd500b9e1e6c9d7f51f9619cf
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174508"
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="ec283-103">Comment : superposer des objets sur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec283-103">How to: Layer objects on Windows Forms</span></span>

<span data-ttu-id="ec283-104">Lorsque vous créez une interface utilisateur complexe ou que vous utilisez un formulaire d’interface multidocument (MDI), vous souhaiterez souvent superposer les contrôles et les formulaires enfants pour créer des interfaces utilisateur plus complexes.</span><span class="sxs-lookup"><span data-stu-id="ec283-104">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="ec283-105">Pour déplacer et suivre les contrôles et les fenêtres dans le contexte d’un groupe, vous manipulez leur *ordre de plan*.</span><span class="sxs-lookup"><span data-stu-id="ec283-105">To move and keep track of controls and windows within the context of a group, you manipulate their *z-order*.</span></span> <span data-ttu-id="ec283-106">L’ordre de plan est la superposition visuelle des contrôles sur un formulaire le long de l’axe z (profondeur) du formulaire.</span><span class="sxs-lookup"><span data-stu-id="ec283-106">Z-order is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="ec283-107">La fenêtre située en haut de l’ordre de plan chevauche toutes les autres fenêtres.</span><span class="sxs-lookup"><span data-stu-id="ec283-107">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="ec283-108">Toutes les autres fenêtres chevauchent la fenêtre en bas de l’ordre de plan.</span><span class="sxs-lookup"><span data-stu-id="ec283-108">All other windows overlap the window at the bottom of the z-order.</span></span>

## <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="ec283-109">Pour superposer des contrôles au moment du design</span><span class="sxs-lookup"><span data-stu-id="ec283-109">To layer controls at design time</span></span>

1. <span data-ttu-id="ec283-110">Dans Visual Studio, sélectionnez un contrôle que vous souhaitez superposer.</span><span class="sxs-lookup"><span data-stu-id="ec283-110">In Visual Studio, select a control that you want to layer.</span></span>

2. <span data-ttu-id="ec283-111">Dans le menu **format** , sélectionnez **ordre**, puis sélectionnez **mettre au premier plan ou mettre** à l' **arrière**-plan.</span><span class="sxs-lookup"><span data-stu-id="ec283-111">On the **Format** menu, select **Order**, and then select **Bring To Front** or **Send To Back**.</span></span>

## <a name="to-layer-controls-programmatically"></a><span data-ttu-id="ec283-112">Pour superposer des contrôles par programmation</span><span class="sxs-lookup"><span data-stu-id="ec283-112">To layer controls programmatically</span></span>

<span data-ttu-id="ec283-113">Utilisez les <xref:System.Windows.Forms.Control.BringToFront%2A> <xref:System.Windows.Forms.Control.SendToBack%2A> méthodes et pour manipuler l’ordre de plan des contrôles.</span><span class="sxs-lookup"><span data-stu-id="ec283-113">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>

<span data-ttu-id="ec283-114">Par exemple, si un <xref:System.Windows.Forms.TextBox> contrôle, `txtFirstName` , se trouve sous un autre contrôle et que vous souhaitez l’utiliser en premier, utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="ec283-114">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>

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
> <span data-ttu-id="ec283-115">Windows Forms prend en charge la *relation contenant-contenu des contrôles*.</span><span class="sxs-lookup"><span data-stu-id="ec283-115">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="ec283-116">La relation contenant-contenu de contrôle implique de placer un certain nombre de contrôles dans un contrôle conteneur, tel qu’un certain nombre de <xref:System.Windows.Forms.RadioButton> contrôles dans un <xref:System.Windows.Forms.GroupBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="ec283-116">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="ec283-117">Vous pouvez ensuite superposer les contrôles dans le contrôle conteneur.</span><span class="sxs-lookup"><span data-stu-id="ec283-117">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="ec283-118">Le déplacement de la zone de groupe déplace également les contrôles, car ils sont contenus à l’intérieur de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="ec283-118">Moving the group box moves the controls as well, because they are contained inside it.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec283-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec283-119">See also</span></span>

- [<span data-ttu-id="ec283-120">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec283-120">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="ec283-121">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec283-121">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="ec283-122">Contrôles à utiliser sur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec283-122">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="ec283-123">Classement par fonction des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec283-123">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
