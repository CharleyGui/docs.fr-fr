---
title: 'Procédure : hériter de contrôles Windows Forms existants'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
ms.openlocfilehash: 198dd630a08ae454ad1d9d9af460b1f288b2a1d8
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037772"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="fcf67-102">Procédure : hériter de contrôles Windows Forms existants</span><span class="sxs-lookup"><span data-stu-id="fcf67-102">How to: Inherit from Existing Windows Forms Controls</span></span>
<span data-ttu-id="fcf67-103">Si vous souhaitez étendre les fonctionnalités d’un contrôle existant, vous pouvez créer un contrôle dérivé d’un contrôle existant par héritage.</span><span class="sxs-lookup"><span data-stu-id="fcf67-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="fcf67-104">Lorsque vous héritez d’un contrôle existant, vous héritez de toutes les fonctionnalités et propriétés visuelles de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="fcf67-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="fcf67-105">Par exemple, si vous créez un contrôle hérité de <xref:System.Windows.Forms.Button>, votre nouveau contrôle s’affiche et agit exactement comme un contrôle standard. <xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="fcf67-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="fcf67-106">Vous pourrez ensuite étendre ou modifier les fonctionnalités de votre nouveau contrôle en implémentant des méthodes et des propriétés personnalisées.</span><span class="sxs-lookup"><span data-stu-id="fcf67-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="fcf67-107">Dans certains contrôles, vous pouvez également modifier l’apparence visuelle de votre contrôle hérité en substituant sa <xref:System.Windows.Forms.Control.OnPaint%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="fcf67-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

## <a name="to-create-an-inherited-control"></a><span data-ttu-id="fcf67-108">Pour créer un contrôle hérité</span><span class="sxs-lookup"><span data-stu-id="fcf67-108">To create an inherited control</span></span>

1. <span data-ttu-id="fcf67-109">Créez un projet d’**application Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="fcf67-109">Create a new **Windows Forms Application** project.</span></span>

2. <span data-ttu-id="fcf67-110">Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="fcf67-110">From the **Project** menu, choose **Add New Item**.</span></span>

     <span data-ttu-id="fcf67-111">La boîte de dialogue **Ajouter un nouvel élément** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="fcf67-111">The **Add New Item** dialog box appears.</span></span>

3. <span data-ttu-id="fcf67-112">Dans la boîte de dialogue **Ajouter un nouvel élément**, double-cliquez sur **Contrôle personnalisé**.</span><span class="sxs-lookup"><span data-stu-id="fcf67-112">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>

     <span data-ttu-id="fcf67-113">Un contrôle personnalisé est ajouté à votre projet.</span><span class="sxs-lookup"><span data-stu-id="fcf67-113">A new custom control is added to your project.</span></span>

4. <span data-ttu-id="fcf67-114">Si vous utilisez Visual Basic, en haut de l’**Explorateur de solutions**, cliquez sur **Afficher tous les fichiers**.</span><span class="sxs-lookup"><span data-stu-id="fcf67-114">If you using Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="fcf67-115">Développez CustomControl1.vb, puis ouvrez CustomControl1.Designer.vb dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="fcf67-115">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>

5. <span data-ttu-id="fcf67-116">Si vous utilisez C#, ouvrez CustomControl1.cs dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="fcf67-116">If you are using C#, open CustomControl1.cs in the Code Editor.</span></span>

6. <span data-ttu-id="fcf67-117">Recherchez la déclaration de classe, qui hérite <xref:System.Windows.Forms.Control>de.</span><span class="sxs-lookup"><span data-stu-id="fcf67-117">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>

7. <span data-ttu-id="fcf67-118">Remplacez la classe de base par le contrôle dont vous voulez hériter.</span><span class="sxs-lookup"><span data-stu-id="fcf67-118">Change the base class to the control that you want to inherit from.</span></span>

     <span data-ttu-id="fcf67-119">Par exemple, si vous souhaitez hériter de <xref:System.Windows.Forms.Button>, remplacez la déclaration de classe par ce qui suit:</span><span class="sxs-lookup"><span data-stu-id="fcf67-119">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

8. <span data-ttu-id="fcf67-120">Si vous utilisez Visual Basic, enregistrez et fermez CustomControl1.Designer.vb.</span><span class="sxs-lookup"><span data-stu-id="fcf67-120">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="fcf67-121">Ouvrez CustomControl1.vb dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="fcf67-121">Open CustomControl1.vb in the Code Editor.</span></span>

9. <span data-ttu-id="fcf67-122">Implémentez les méthodes ou propriétés personnalisées que votre contrôle intégrera.</span><span class="sxs-lookup"><span data-stu-id="fcf67-122">Implement any custom methods or properties that your control will incorporate.</span></span>

10. <span data-ttu-id="fcf67-123">Si vous souhaitez modifier l’apparence graphique de votre contrôle, substituez la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="fcf67-123">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="fcf67-124">Le remplacement <xref:System.Windows.Forms.Control.OnPaint%2A> ne vous permettra pas de modifier l’apparence de tous les contrôles.</span><span class="sxs-lookup"><span data-stu-id="fcf67-124">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="fcf67-125">Les contrôles qui ont tout leur dessin effectué par Windows (par exemple, <xref:System.Windows.Forms.TextBox>) n’appellent jamais leur <xref:System.Windows.Forms.Control.OnPaint%2A> méthode et n’utilisent donc jamais le code personnalisé.</span><span class="sxs-lookup"><span data-stu-id="fcf67-125">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="fcf67-126">Reportez-vous à la documentation d’aide relative au contrôle que vous souhaitez modifier <xref:System.Windows.Forms.Control.OnPaint%2A> pour déterminer si la méthode est disponible.</span><span class="sxs-lookup"><span data-stu-id="fcf67-126">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="fcf67-127">Pour obtenir la liste de tous les contrôles Windows Forms, consultez [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="fcf67-127">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="fcf67-128">Si un contrôle n’a <xref:System.Windows.Forms.Control.OnPaint%2A> pas de liste en tant que méthode membre, vous ne pouvez pas modifier son apparence en substituant cette méthode.</span><span class="sxs-lookup"><span data-stu-id="fcf67-128">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="fcf67-129">Pour plus d’informations sur la peinture personnalisée, consultez [Peinture et rendu personnalisés des contrôles](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="fcf67-129">For more information about custom painting, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

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

11. <span data-ttu-id="fcf67-130">Enregistrez et testez votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="fcf67-130">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcf67-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcf67-131">See also</span></span>

- [<span data-ttu-id="fcf67-132">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="fcf67-132">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="fcf67-133">Guide pratique pour Hériter de la classe de contrôle</span><span class="sxs-lookup"><span data-stu-id="fcf67-133">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="fcf67-134">Guide pratique pour Hériter de la classe UserControl</span><span class="sxs-lookup"><span data-stu-id="fcf67-134">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="fcf67-135">Guide pratique pour Créer des contrôles pour Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcf67-135">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="fcf67-136">Dépannage des gestionnaires d’événements hérités en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fcf67-136">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="fcf67-137">Procédure pas à pas : Héritage d’un contrôle Windows Forms avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fcf67-137">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [<span data-ttu-id="fcf67-138">Procédure pas à pas : Héritage à partir d’un contrôle Windows Forms avec VisualC#</span><span class="sxs-lookup"><span data-stu-id="fcf67-138">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
