---
title: ajouter des contrôles
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 560089a23fbcccb0f0d5683a95ad06dd9c59556d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743955"
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="e6137-102">Comment : ajouter des contrôles à des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6137-102">How to: Add Controls to Windows Forms</span></span>

<span data-ttu-id="e6137-103">La plupart des formulaires sont conçus en ajoutant des contrôles à la surface du formulaire pour définir une interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e6137-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="e6137-104">Un *contrôle* est un composant d’un formulaire utilisé pour afficher des informations ou accepter une entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e6137-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="e6137-105">Pour plus d’informations sur les contrôles, consultez [Windows Forms des contrôles](index.md).</span><span class="sxs-lookup"><span data-stu-id="e6137-105">For more information about controls, see [Windows Forms Controls](index.md).</span></span>

## <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="e6137-106">Pour dessiner un contrôle sur un formulaire</span><span class="sxs-lookup"><span data-stu-id="e6137-106">To draw a control on a form</span></span>

1. <span data-ttu-id="e6137-107">Ouvrez le formulaire.</span><span class="sxs-lookup"><span data-stu-id="e6137-107">Open the form.</span></span> <span data-ttu-id="e6137-108">Pour plus d’informations, consultez [Comment : afficher des Windows Forms dans le concepteur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e6137-108">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="e6137-109">Dans la **boîte à outils**, cliquez sur le contrôle que vous souhaitez ajouter à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="e6137-109">In the **Toolbox**, click the control you want to add to your form.</span></span>

3. <span data-ttu-id="e6137-110">Dans le formulaire, cliquez à l’endroit où vous souhaitez placer l’angle supérieur gauche du contrôle, puis faites glisser le bouton vers l’emplacement où vous souhaitez placer le coin inférieur droit du contrôle.</span><span class="sxs-lookup"><span data-stu-id="e6137-110">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>

    <span data-ttu-id="e6137-111">Le contrôle est ajouté au formulaire avec l’emplacement et la taille spécifiés.</span><span class="sxs-lookup"><span data-stu-id="e6137-111">The control is added to the form with the specified location and size.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e6137-112">Une taille par défaut est définie pour chaque contrôle.</span><span class="sxs-lookup"><span data-stu-id="e6137-112">Each control has a default size defined.</span></span> <span data-ttu-id="e6137-113">Vous pouvez ajouter un contrôle à votre formulaire à la taille par défaut du contrôle en le faisant glisser de la **boîte à outils** vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="e6137-113">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>

## <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="e6137-114">Pour faire glisser un contrôle vers un formulaire</span><span class="sxs-lookup"><span data-stu-id="e6137-114">To drag a control to a form</span></span>

1. <span data-ttu-id="e6137-115">Ouvrez le formulaire.</span><span class="sxs-lookup"><span data-stu-id="e6137-115">Open the form.</span></span> <span data-ttu-id="e6137-116">Pour plus d’informations, consultez [Comment : afficher des Windows Forms dans le concepteur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e6137-116">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="e6137-117">Dans la **boîte à outils**, cliquez sur le contrôle souhaité et faites-le glisser vers votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="e6137-117">In the **Toolbox**, click the control you want and drag it to your form.</span></span>

    <span data-ttu-id="e6137-118">Le contrôle est ajouté au formulaire à l’emplacement spécifié dans sa taille par défaut.</span><span class="sxs-lookup"><span data-stu-id="e6137-118">The control is added to the form at the specified location in its default size.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e6137-119">Vous pouvez double-cliquer sur un contrôle dans la **boîte à outils** pour l’ajouter dans le coin supérieur gauche du formulaire dans sa taille par défaut.</span><span class="sxs-lookup"><span data-stu-id="e6137-119">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>

    <span data-ttu-id="e6137-120">Vous pouvez également ajouter dynamiquement des contrôles à un formulaire au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e6137-120">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="e6137-121">Dans l’exemple de code suivant, un contrôle de <xref:System.Windows.Forms.TextBox> est ajouté au formulaire lorsqu’un utilisateur clique sur un contrôle <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="e6137-121">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e6137-122">La procédure suivante nécessite l’existence d’un formulaire avec un contrôle **Button** , `Button1`, déjà placé sur celui-ci.</span><span class="sxs-lookup"><span data-stu-id="e6137-122">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>

## <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="e6137-123">Pour ajouter par programmation un contrôle à un formulaire</span><span class="sxs-lookup"><span data-stu-id="e6137-123">To add a control to a form programmatically</span></span>

1. <span data-ttu-id="e6137-124">Dans la méthode qui gère l’événement `Click` du bouton dans la classe de votre formulaire, insérez un code semblable au suivant pour ajouter une référence à votre variable de contrôle, définir le `Location`du contrôle et ajouter le contrôle.</span><span class="sxs-lookup"><span data-stu-id="e6137-124">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>

    ```vb
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
       Dim MyText As New TextBox()
       MyText.Location = New Point(25, 25)
       Me.Controls.Add(MyText)
    End Sub
    ```

    ```csharp
    private void button1_Click(object sender, System.EventArgs e)
    {
       TextBox myText = new TextBox();
       myText.Location = new Point(25,25);
       this.Controls.Add (myText);
    }
    ```

    ```cpp
    private:
      System::Void button1_Click(System::Object ^  sender,
        System::EventArgs ^  e)
      {
        TextBox ^ myText = gcnew TextBox();
        myText->Location = Point(25,25);
        this->Controls->Add(myText);
      }
    ```

    > [!NOTE]
    > <span data-ttu-id="e6137-125">Vous pouvez également ajouter du code pour initialiser d’autres propriétés du contrôle.</span><span class="sxs-lookup"><span data-stu-id="e6137-125">You can also add code to initialize other properties of the control.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="e6137-126">Vous pouvez exposer votre ordinateur local à un risque de sécurité sur le réseau en référençant un `UserControl`malveillant.</span><span class="sxs-lookup"><span data-stu-id="e6137-126">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="e6137-127">Cela ne serait qu’une préoccupation dans le cas d’une personne malveillante qui crée un contrôle personnalisé nuisible, puis de l’ajouter par erreur à votre projet.</span><span class="sxs-lookup"><span data-stu-id="e6137-127">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6137-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6137-128">See also</span></span>

- [<span data-ttu-id="e6137-129">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6137-129">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="e6137-130">Guide pratique pour redimensionner des contrôles sur des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6137-130">How to: Resize Controls on Windows Forms</span></span>](how-to-resize-controls-on-windows-forms.md)
- [<span data-ttu-id="e6137-131">Guide pratique pour définir le texte affiché par un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6137-131">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="e6137-132">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6137-132">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
