---
title: 'Comment : hériter de la classe du contrôle'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7af7d1fe8f14c71dfc90836d84023b98feb44961
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458386"
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="f030e-102">Comment : hériter de la classe du contrôle</span><span class="sxs-lookup"><span data-stu-id="f030e-102">How to: Inherit from the Control Class</span></span>

<span data-ttu-id="f030e-103">Si vous souhaitez créer un contrôle entièrement personnalisé à utiliser sur un Windows Form, vous devez hériter de la classe <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="f030e-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="f030e-104">Bien qu’hérite de la classe <xref:System.Windows.Forms.Control> nécessite que vous effectuiez davantage de planification et d’implémentation, elle vous fournit également la plus grande variété d’options.</span><span class="sxs-lookup"><span data-stu-id="f030e-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="f030e-105">Lorsque vous héritez de <xref:System.Windows.Forms.Control>, vous héritez des fonctionnalités de base qui permettent aux contrôles de fonctionner.</span><span class="sxs-lookup"><span data-stu-id="f030e-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="f030e-106">Les fonctionnalités inhérentes à la classe <xref:System.Windows.Forms.Control> gèrent les entrées d’utilisateur par le biais du clavier et de la souris, définissent les limites et la taille du contrôle, fournissent un handle Windows et assurent la gestion et la sécurité des messages.</span><span class="sxs-lookup"><span data-stu-id="f030e-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="f030e-107">Elles n’intègrent pas la peinture, qui désigne ici le rendu réel de l’interface graphique du contrôle, ni les fonctionnalités d’interaction utilisateur spécifiques.</span><span class="sxs-lookup"><span data-stu-id="f030e-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="f030e-108">Vous devez fournir tous ces aspects par le biais de code personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f030e-108">You must provide all of these aspects through custom code.</span></span>

## <a name="to-create-a-custom-control"></a><span data-ttu-id="f030e-109">Pour créer un contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="f030e-109">To create a custom control</span></span>

1. <span data-ttu-id="f030e-110">Dans Visual Studio, créez une **application Windows** ou un projet de **bibliothèque de contrôles Windows** .</span><span class="sxs-lookup"><span data-stu-id="f030e-110">In Visual Studio, create a new **Windows Application** or **Windows Control Library** project.</span></span>

2. <span data-ttu-id="f030e-111">Dans le menu **Projet** , choisissez **Ajouter une classe**.</span><span class="sxs-lookup"><span data-stu-id="f030e-111">From the **Project** menu, choose **Add Class**.</span></span>

3. <span data-ttu-id="f030e-112">Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **Contrôle personnalisé**.</span><span class="sxs-lookup"><span data-stu-id="f030e-112">In the **Add New Item** dialog box, click **Custom Control**.</span></span>

   <span data-ttu-id="f030e-113">Un contrôle personnalisé est ajouté à votre projet.</span><span class="sxs-lookup"><span data-stu-id="f030e-113">A new custom control is added to your project.</span></span>

4. <span data-ttu-id="f030e-114">Appuyez sur **F7** pour ouvrir l' **éditeur de code** de votre contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f030e-114">Press **F7** to open the **Code Editor** for your custom control.</span></span>

5. <span data-ttu-id="f030e-115">Recherchez la méthode <xref:System.Windows.Forms.Control.OnPaint%2A>, qui sera vide, à l’exception d’un appel à la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="f030e-115">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>

6. <span data-ttu-id="f030e-116">Modifiez le code afin d’incorporer la peinture personnalisée pour votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="f030e-116">Modify the code to incorporate any custom painting you want for your control.</span></span>

   <span data-ttu-id="f030e-117">Pour plus d’informations sur l’écriture de code permettant d’afficher des graphiques concernant les contrôles, consultez [Peinture et rendu personnalisés des contrôles](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="f030e-117">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

7. <span data-ttu-id="f030e-118">Implémentez les méthodes, les propriétés ou les événements personnalisés que votre contrôle intégrera.</span><span class="sxs-lookup"><span data-stu-id="f030e-118">Implement any custom methods, properties, or events that your control will incorporate.</span></span>

8. <span data-ttu-id="f030e-119">Enregistrez et testez votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="f030e-119">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="f030e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f030e-120">See also</span></span>

- [<span data-ttu-id="f030e-121">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="f030e-121">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="f030e-122">Comment : hériter de la classe UserControl</span><span class="sxs-lookup"><span data-stu-id="f030e-122">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="f030e-123">Guide pratique pour hériter de contrôles Windows Forms existants</span><span class="sxs-lookup"><span data-stu-id="f030e-123">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="f030e-124">Guide pratique pour créer des contrôles pour des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f030e-124">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="f030e-125">Dépannage des gestionnaires d’événements hérités en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f030e-125">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="f030e-126">Développement de contrôles Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="f030e-126">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
