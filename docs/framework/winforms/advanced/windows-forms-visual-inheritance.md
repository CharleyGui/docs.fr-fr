---
title: Héritage visuel
ms.date: 03/30/2017
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inheritance
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 857eb737-3602-4d49-bd8b-f70d33ace345
ms.openlocfilehash: c6aa104a1c9ebe6f59c11ce70e3352169132e714
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732480"
---
# <a name="windows-forms-visual-inheritance"></a><span data-ttu-id="f5625-102">Héritage visuel des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f5625-102">Windows Forms Visual Inheritance</span></span>
<span data-ttu-id="f5625-103">Parfois, vous pouvez choisir qu’un projet appelle un formulaire semblable à celui que vous avez créé dans un projet précédent.</span><span class="sxs-lookup"><span data-stu-id="f5625-103">Occasionally, you may decide that a project calls for a form similar to one that you have created in a previous project.</span></span> <span data-ttu-id="f5625-104">Ou bien vous souhaitez créer un formulaire de base avec des paramètres tels qu’un filigrane ou une disposition particulière des contrôles, que vous réutiliserez au sein d’un projet, et faire que chaque nouvelle itération contienne les modifications apportées au modèle de formulaire d’origine.</span><span class="sxs-lookup"><span data-stu-id="f5625-104">Or, you may want to create a basic form with settings such as a watermark or certain control layout that you will then use again within a project, with each iteration containing modifications to the original form template.</span></span> <span data-ttu-id="f5625-105">L’héritage de formulaire vous permet de créer un formulaire de base, puis d’en hériter et d’apporter des modifications tout en conservant les paramètres d’origine.</span><span class="sxs-lookup"><span data-stu-id="f5625-105">Form inheritance enables you to create a base form and then inherit from it and make modifications while preserving whatever original settings you need.</span></span>  
  
 <span data-ttu-id="f5625-106">Vous pouvez créer des formulaires de classe dérivée par programmation ou à l’aide du sélecteur d’héritage visuel.</span><span class="sxs-lookup"><span data-stu-id="f5625-106">You can create derived-class forms programmatically or by using the Visual Inheritance picker.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f5625-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f5625-107">In This Section</span></span>  
 [<span data-ttu-id="f5625-108">Comment : hériter des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f5625-108">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)  
 <span data-ttu-id="f5625-109">Explique comment créer des formulaires hérités dans le code.</span><span class="sxs-lookup"><span data-stu-id="f5625-109">Gives directions for creating inherited forms in code.</span></span>  
  
 [<span data-ttu-id="f5625-110">Comment : hériter de formulaires à l’aide de la boîte de dialogue Sélecteur d’héritage</span><span class="sxs-lookup"><span data-stu-id="f5625-110">How to: Inherit Forms Using the Inheritance Picker Dialog Box</span></span>](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 <span data-ttu-id="f5625-111">Explique comment créer des formulaires hérités avec le sélecteur d’héritage.</span><span class="sxs-lookup"><span data-stu-id="f5625-111">Gives directions for creating inherited forms with the Inheritance Picker.</span></span>  
  
 [<span data-ttu-id="f5625-112">Conséquences de la modification de l’aspect d’un formulaire de base</span><span class="sxs-lookup"><span data-stu-id="f5625-112">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)  
 <span data-ttu-id="f5625-113">Explique comment modifier les contrôles d’un formulaire de base et leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="f5625-113">Gives directions for changing a base form's controls and their properties.</span></span>  
  
 [<span data-ttu-id="f5625-114">Procédure pas à pas : démonstration de l’héritage visuel</span><span class="sxs-lookup"><span data-stu-id="f5625-114">Walkthrough: Demonstrating Visual Inheritance</span></span>](walkthrough-demonstrating-visual-inheritance.md)  
 <span data-ttu-id="f5625-115">Décrit comment créer un Windows Form de base et le compiler dans une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="f5625-115">Describes how to create a base Windows Form and compile it into a class library.</span></span> <span data-ttu-id="f5625-116">Vous importerez cette bibliothèque de classes dans un autre projet et créerez un formulaire qui hérite du formulaire de base.</span><span class="sxs-lookup"><span data-stu-id="f5625-116">You will import this class library into another project, and create a new form that inherits from the base form.</span></span>  
  
 [<span data-ttu-id="f5625-117">Comment : utiliser les modificateurs et les propriétés GenerateMember</span><span class="sxs-lookup"><span data-stu-id="f5625-117">How to: Use the Modifiers and GenerateMember Properties</span></span>](how-to-use-the-modifiers-and-generatemember-properties.md)  
 <span data-ttu-id="f5625-118">Explique comment utiliser les propriétés `GenerateMember` et `Modifiers`, qui sont tout à fait pertinentes lorsque le Concepteur Windows Forms génère une variable membre pour un composant.</span><span class="sxs-lookup"><span data-stu-id="f5625-118">Gives directions for using the `GenerateMember` and `Modifiers` properties, which are relevant when the Windows Forms Designer generates a member variable for a component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f5625-119">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="f5625-119">Related Sections</span></span>  
 [<span data-ttu-id="f5625-120">Éléments fondamentaux de l’héritage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5625-120">Inheritance basics (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 <span data-ttu-id="f5625-121">Décrit comment définir des classes Visual Basic qui servent de base pour les autres classes.</span><span class="sxs-lookup"><span data-stu-id="f5625-121">Describes how to define Visual Basic classes that serve as the basis for other classes.</span></span>  
  
 [<span data-ttu-id="f5625-122">classe</span><span class="sxs-lookup"><span data-stu-id="f5625-122">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 <span data-ttu-id="f5625-123">Décrit l’approche C# des classes, dans laquelle l’héritage unique est autorisé.</span><span class="sxs-lookup"><span data-stu-id="f5625-123">Describes the C# approach of classes, in which single inheritance is allowed.</span></span>  
  
 [<span data-ttu-id="f5625-124">Dépannage des gestionnaires d’événements hérités en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f5625-124">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="f5625-125">Répertorie les problèmes courants qui surviennent avec les gestionnaires d’événements dans les composants hérités</span><span class="sxs-lookup"><span data-stu-id="f5625-125">Lists common issues that arise with event handlers in inherited components</span></span>
