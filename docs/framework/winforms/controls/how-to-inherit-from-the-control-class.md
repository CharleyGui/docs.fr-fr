---
title: 'Procédure : hériter de la classe Control'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
ms.openlocfilehash: 0cb63be6774fd82cd94a1bc59b8a1025efa47df5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966583"
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="ac9c7-102">Procédure : hériter de la classe Control</span><span class="sxs-lookup"><span data-stu-id="ac9c7-102">How to: Inherit from the Control Class</span></span>
<span data-ttu-id="ac9c7-103">Si vous souhaitez créer un contrôle entièrement personnalisé à utiliser sur un Windows Form, vous devez hériter de la <xref:System.Windows.Forms.Control> classe.</span><span class="sxs-lookup"><span data-stu-id="ac9c7-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="ac9c7-104">L’héritage de la <xref:System.Windows.Forms.Control> classe nécessite que vous effectuiez davantage de planification et d’implémentation, mais vous offre également la plus grande variété d’options.</span><span class="sxs-lookup"><span data-stu-id="ac9c7-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="ac9c7-105">Lorsque vous héritez <xref:System.Windows.Forms.Control>de, vous héritez des fonctionnalités de base qui permettent aux contrôles de fonctionner.</span><span class="sxs-lookup"><span data-stu-id="ac9c7-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="ac9c7-106">Les fonctionnalités inhérentes à <xref:System.Windows.Forms.Control> la classe gèrent les entrées d’utilisateur par le biais du clavier et de la souris, définissent les limites et la taille du contrôle, fournissent un handle Windows et assurent la gestion et la sécurité des messages.</span><span class="sxs-lookup"><span data-stu-id="ac9c7-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="ac9c7-107">Elles n’intègrent pas la peinture, qui désigne ici le rendu réel de l’interface graphique du contrôle, ni les fonctionnalités d’interaction utilisateur spécifiques.</span><span class="sxs-lookup"><span data-stu-id="ac9c7-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="ac9c7-108">Vous devez fournir tous ces aspects par le biais de code personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ac9c7-108">You must provide all of these aspects through custom code.</span></span>

## <a name="to-create-a-custom-control"></a><span data-ttu-id="ac9c7-109">Pour créer un contrôle personnalisé</span><span class="sxs-lookup"><span data-stu-id="ac9c7-109">To create a custom control</span></span>

1. <span data-ttu-id="ac9c7-110">Créez un projet d’**application Windows** ou de **bibliothèque de contrôles Windows**.</span><span class="sxs-lookup"><span data-stu-id="ac9c7-110">Create a new **Windows Application** or **Windows Control Library** project.</span></span>

2. <span data-ttu-id="ac9c7-111">Dans le menu **Projet** , choisissez **Ajouter une classe**.</span><span class="sxs-lookup"><span data-stu-id="ac9c7-111">From the **Project** menu, choose **Add Class**.</span></span>

3. <span data-ttu-id="ac9c7-112">Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **Contrôle personnalisé**.</span><span class="sxs-lookup"><span data-stu-id="ac9c7-112">In the **Add New Item** dialog box, click **Custom Control**.</span></span>

     <span data-ttu-id="ac9c7-113">Un nouveau contrôle personnalisé est ajouté à votre projet.</span><span class="sxs-lookup"><span data-stu-id="ac9c7-113">A new custom control is added to your project.</span></span>

4. <span data-ttu-id="ac9c7-114">Appuyez sur F7 pour ouvrir l’**éditeur de code** de votre contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ac9c7-114">Press F7 to open the **Code Editor** for your custom control.</span></span>

5. <span data-ttu-id="ac9c7-115">Recherchez la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode, qui sera vide à l’exception d’un appel à <xref:System.Windows.Forms.Control.OnPaint%2A> la méthode de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="ac9c7-115">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>

6. <span data-ttu-id="ac9c7-116">Modifiez le code afin d’incorporer la peinture personnalisée pour votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="ac9c7-116">Modify the code to incorporate any custom painting you want for your control.</span></span>

     <span data-ttu-id="ac9c7-117">Pour plus d’informations sur l’écriture de code permettant d’afficher des graphiques concernant les contrôles, consultez [Peinture et rendu personnalisés des contrôles](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="ac9c7-117">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

7. <span data-ttu-id="ac9c7-118">Implémentez les méthodes, les propriétés ou les événements personnalisés que votre contrôle intégrera.</span><span class="sxs-lookup"><span data-stu-id="ac9c7-118">Implement any custom methods, properties, or events that your control will incorporate.</span></span>

8. <span data-ttu-id="ac9c7-119">Enregistrez et testez votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="ac9c7-119">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac9c7-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac9c7-120">See also</span></span>

- [<span data-ttu-id="ac9c7-121">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="ac9c7-121">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="ac9c7-122">Guide pratique : Hériter de la classe UserControl</span><span class="sxs-lookup"><span data-stu-id="ac9c7-122">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="ac9c7-123">Guide pratique pour Hériter de contrôles Windows Forms existants</span><span class="sxs-lookup"><span data-stu-id="ac9c7-123">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="ac9c7-124">Guide pratique pour Créer des contrôles pour Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ac9c7-124">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="ac9c7-125">Dépannage des gestionnaires d’événements hérités en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac9c7-125">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="ac9c7-126">Développement de contrôles Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="ac9c7-126">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
