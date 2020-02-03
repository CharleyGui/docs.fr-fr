---
title: Hériter de contrôles existants
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d0025ba136698c0a74a73e64a83fa4f526e44843
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736484"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="3ae6c-102">Comment : hériter de contrôles Windows Forms existants</span><span class="sxs-lookup"><span data-stu-id="3ae6c-102">How to: Inherit from Existing Windows Forms Controls</span></span>

<span data-ttu-id="3ae6c-103">Si vous souhaitez étendre les fonctionnalités d’un contrôle existant, vous pouvez créer un contrôle dérivé d’un contrôle existant par héritage.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="3ae6c-104">Lorsque vous héritez d’un contrôle existant, vous héritez de toutes les fonctionnalités et propriétés visuelles de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="3ae6c-105">Par exemple, si vous créez un contrôle hérité de <xref:System.Windows.Forms.Button>, votre nouveau contrôle s’affiche et agit exactement comme un contrôle <xref:System.Windows.Forms.Button> standard.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="3ae6c-106">Vous pourrez ensuite étendre ou modifier les fonctionnalités de votre nouveau contrôle en implémentant des méthodes et des propriétés personnalisées.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="3ae6c-107">Dans certains contrôles, vous pouvez également modifier l’apparence visuelle de votre contrôle hérité en substituant sa méthode <xref:System.Windows.Forms.Control.OnPaint%2A>.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

## <a name="to-create-an-inherited-control"></a><span data-ttu-id="3ae6c-108">Pour créer un contrôle hérité</span><span class="sxs-lookup"><span data-stu-id="3ae6c-108">To create an inherited control</span></span>

1. <span data-ttu-id="3ae6c-109">Dans Visual Studio, créez un projet d' **application de Windows Forms** .</span><span class="sxs-lookup"><span data-stu-id="3ae6c-109">In Visual Studio, create a new **Windows Forms Application** project.</span></span>

1. <span data-ttu-id="3ae6c-110">Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-110">From the **Project** menu, choose **Add New Item**.</span></span>

    <span data-ttu-id="3ae6c-111">La boîte de dialogue **Ajouter un nouvel élément** s'affiche.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-111">The **Add New Item** dialog box appears.</span></span>

1. <span data-ttu-id="3ae6c-112">Dans la boîte de dialogue **Ajouter un nouvel élément**, double-cliquez sur **Contrôle personnalisé**.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-112">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>

    <span data-ttu-id="3ae6c-113">Un nouveau contrôle personnalisé est ajouté à votre projet.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-113">A new custom control is added to your project.</span></span>

1. <span data-ttu-id="3ae6c-114">Si vous utilisez :</span><span class="sxs-lookup"><span data-stu-id="3ae6c-114">If you using:</span></span>

    - <span data-ttu-id="3ae6c-115">Visual Basic, en haut de **Explorateur de solutions**, cliquez sur **Afficher tous les fichiers**.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-115">Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="3ae6c-116">Développez CustomControl1.vb, puis ouvrez CustomControl1.Designer.vb dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-116">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>
    - <span data-ttu-id="3ae6c-117">C#, ouvrez CustomControl1.cs dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-117">C#, open CustomControl1.cs in the Code Editor.</span></span>

1. <span data-ttu-id="3ae6c-118">Recherchez la déclaration de classe, qui hérite de <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-118">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>

1. <span data-ttu-id="3ae6c-119">Remplacez la classe de base par le contrôle dont vous voulez hériter.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-119">Change the base class to the control that you want to inherit from.</span></span>

     <span data-ttu-id="3ae6c-120">Par exemple, si vous souhaitez hériter de <xref:System.Windows.Forms.Button>, remplacez la déclaration de classe par ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="3ae6c-120">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. <span data-ttu-id="3ae6c-121">Si vous utilisez Visual Basic, enregistrez et fermez CustomControl1.Designer.vb.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-121">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="3ae6c-122">Ouvrez CustomControl1.vb dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-122">Open CustomControl1.vb in the Code Editor.</span></span>

1. <span data-ttu-id="3ae6c-123">Implémentez les méthodes ou propriétés personnalisées que votre contrôle intégrera.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-123">Implement any custom methods or properties that your control will incorporate.</span></span>

1. <span data-ttu-id="3ae6c-124">Si vous souhaitez modifier l’apparence graphique de votre contrôle, substituez la méthode <xref:System.Windows.Forms.Control.OnPaint%2A>.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-124">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3ae6c-125">Le remplacement de <xref:System.Windows.Forms.Control.OnPaint%2A> ne vous permet pas de modifier l’apparence de tous les contrôles.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-125">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="3ae6c-126">Les contrôles qui ont tout leur dessin effectué par Windows (par exemple, <xref:System.Windows.Forms.TextBox>) n’appellent jamais leur méthode <xref:System.Windows.Forms.Control.OnPaint%2A> et n’utilisent donc jamais le code personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-126">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="3ae6c-127">Reportez-vous à la documentation d’aide relative au contrôle que vous souhaitez modifier pour déterminer si la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> est disponible.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-127">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="3ae6c-128">Pour obtenir la liste de tous les contrôles Windows Forms, consultez [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3ae6c-128">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="3ae6c-129">Si un contrôle n’a pas de <xref:System.Windows.Forms.Control.OnPaint%2A> listée en tant que méthode membre, vous ne pouvez pas modifier son apparence en substituant cette méthode.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-129">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="3ae6c-130">Pour plus d’informations sur la peinture personnalisée, consultez [Peinture et rendu personnalisés des contrôles](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="3ae6c-130">For more information about custom painting, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

    ```vb
    Protected Overrides Sub OnPaint(ByVal e As _
       System.Windows.Forms.PaintEventArgs)
       MyBase.OnPaint(e)
       ' Insert code to do custom painting.
       ' If you want to completely change the appearance of your control,
       ' do not call MyBase.OnPaint(e).
    End Sub
    ```

    ```csharp
    protected override void OnPaint(PaintEventArgs pe)
    {
       base.OnPaint(pe);
       // Insert code to do custom painting.
       // If you want to completely change the appearance of your control,
       // do not call base.OnPaint(pe).
    }
    ```

1. <span data-ttu-id="3ae6c-131">Enregistrez et testez votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="3ae6c-131">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ae6c-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ae6c-132">See also</span></span>

- [<span data-ttu-id="3ae6c-133">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="3ae6c-133">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="3ae6c-134">Guide pratique pour hériter de la classe du contrôle</span><span class="sxs-lookup"><span data-stu-id="3ae6c-134">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="3ae6c-135">Comment : hériter de la classe UserControl</span><span class="sxs-lookup"><span data-stu-id="3ae6c-135">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="3ae6c-136">Guide pratique pour créer des contrôles pour des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3ae6c-136">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="3ae6c-137">Dépannage des gestionnaires d’événements hérités en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3ae6c-137">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="3ae6c-138">Procédure pas à pas : héritage d’un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3ae6c-138">Walkthrough: Inheriting from a Windows Forms Control</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
