---
title: 'Procédure : verrouiller des contrôles avec des Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: 9eb762a9691a6127e2419f9ddc25f3010d3383fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966529"
---
# <a name="how-to-lock-controls-to-windows-forms"></a><span data-ttu-id="edbe3-102">Procédure : verrouiller des contrôles avec des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="edbe3-102">How to: Lock Controls to Windows Forms</span></span>
<span data-ttu-id="edbe3-103">Lorsque vous concevez l’interface utilisateur de votre application Windows, vous pouvez verrouiller les contrôles une fois qu’ils sont positionnés correctement, afin de ne pas les déplacer ou les redimensionner par inadvertance lors de la définition d’autres propriétés.</span><span class="sxs-lookup"><span data-stu-id="edbe3-103">When you design the user interface (UI) of your Windows application, you can lock the controls once they are positioned correctly, so that you do not inadvertently move or resize them when setting other properties.</span></span>

 <span data-ttu-id="edbe3-104">En outre, vous pouvez verrouiller et déverrouiller tous les contrôles du formulaire à la fois, ce qui est utile pour les formulaires avec de nombreux contrôles, ou vous pouvez déverrouiller des contrôles individuels.</span><span class="sxs-lookup"><span data-stu-id="edbe3-104">Additionally, you can lock and unlock all the controls on the form at once, which is helpful for forms with many controls, or you can unlock individual controls.</span></span> <span data-ttu-id="edbe3-105">Une fois que vous avez placé tous les contrôles à l’emplacement souhaité sur le formulaire, verrouillez-les pour éviter tout mouvement erroné.</span><span class="sxs-lookup"><span data-stu-id="edbe3-105">Once you have placed all the controls where you want them on the form, lock them all in place to prevent erroneous movement.</span></span>

## <a name="to-lock-a-control"></a><span data-ttu-id="edbe3-106">Pour verrouiller un contrôle</span><span class="sxs-lookup"><span data-stu-id="edbe3-106">To lock a control</span></span>

1. <span data-ttu-id="edbe3-107">Dans la fenêtre **Propriétés** , cliquez sur la propriété **verrouillé** , `true`puis sélectionnez.</span><span class="sxs-lookup"><span data-stu-id="edbe3-107">In the **Properties** window, click the **Locked** property and select `true`.</span></span> <span data-ttu-id="edbe3-108">(Si vous double-cliquez sur le nom, le paramètre de propriété est activé.)</span><span class="sxs-lookup"><span data-stu-id="edbe3-108">(Double-clicking the name toggles the property setting.)</span></span>

     <span data-ttu-id="edbe3-109">Vous pouvez également cliquer avec le bouton droit sur le contrôle et choisir **verrouiller les contrôles**.</span><span class="sxs-lookup"><span data-stu-id="edbe3-109">Alternatively, right-click the control and choose **Lock Controls**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="edbe3-110">Le verrouillage des contrôles empêche leur déplacement vers une nouvelle taille ou un nouvel emplacement sur l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="edbe3-110">Locking controls prevents them from being dragged to a new size or location on the design surface.</span></span> <span data-ttu-id="edbe3-111">Toutefois, vous pouvez toujours modifier la taille ou l’emplacement des contrôles à l’aide de la fenêtre **Propriétés** ou dans le code.</span><span class="sxs-lookup"><span data-stu-id="edbe3-111">However, you can still change the size or location of controls by means of the **Properties** window or in code.</span></span>

## <a name="to-lock-all-the-controls-on-a-form"></a><span data-ttu-id="edbe3-112">Pour verrouiller tous les contrôles d’un formulaire</span><span class="sxs-lookup"><span data-stu-id="edbe3-112">To lock all the controls on a form</span></span>

1. <span data-ttu-id="edbe3-113">Dans le menu **format** , choisissez **verrouiller les contrôles**.</span><span class="sxs-lookup"><span data-stu-id="edbe3-113">From the **Format** menu, choose **Lock Controls**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="edbe3-114">Cette commande verrouille également la taille du formulaire, car un formulaire est un contrôle.</span><span class="sxs-lookup"><span data-stu-id="edbe3-114">This command locks the form's size as well, because a form is a control.</span></span>

## <a name="to-unlock-all-locked-controls-on-a-form"></a><span data-ttu-id="edbe3-115">Pour déverrouiller tous les contrôles verrouillés dans un formulaire</span><span class="sxs-lookup"><span data-stu-id="edbe3-115">To unlock all locked controls on a form</span></span>

1. <span data-ttu-id="edbe3-116">Dans le menu **format** , choisissez **verrouiller les contrôles**.</span><span class="sxs-lookup"><span data-stu-id="edbe3-116">From the **Format** menu, choose **Lock Controls**.</span></span>

     <span data-ttu-id="edbe3-117">Tous les contrôles précédemment verrouillés sur le formulaire sont maintenant déverrouillés.</span><span class="sxs-lookup"><span data-stu-id="edbe3-117">All previously locked controls on the form are now unlocked.</span></span>

## <a name="to-unlock-locked-controls-individually"></a><span data-ttu-id="edbe3-118">Pour déverrouiller des contrôles verrouillés individuellement</span><span class="sxs-lookup"><span data-stu-id="edbe3-118">To unlock locked controls individually</span></span>

1. <span data-ttu-id="edbe3-119">Dans la fenêtre **Propriétés** , cliquez sur la propriété **verrouillé** , `false`puis sélectionnez.</span><span class="sxs-lookup"><span data-stu-id="edbe3-119">In the **Properties** window, click the **Locked** property and select `false`.</span></span> <span data-ttu-id="edbe3-120">(Si vous double-cliquez sur le nom, le paramètre de propriété est activé.)</span><span class="sxs-lookup"><span data-stu-id="edbe3-120">(Double-clicking the name toggles the property setting.)</span></span>

## <a name="see-also"></a><span data-ttu-id="edbe3-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edbe3-121">See also</span></span>

- [<span data-ttu-id="edbe3-122">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="edbe3-122">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="edbe3-123">Disposition des contrôles dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="edbe3-123">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="edbe3-124">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="edbe3-124">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="edbe3-125">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="edbe3-125">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="edbe3-126">Classement par fonction des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="edbe3-126">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
