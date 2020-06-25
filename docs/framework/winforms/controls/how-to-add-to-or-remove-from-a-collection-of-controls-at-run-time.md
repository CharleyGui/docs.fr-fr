---
title: 'Comment : ajouter des contrôles dans une collection au moment de l’exécution, ou comment les supprimer'
description: Découvrez comment ajouter et supprimer des contrôles dans un contrôle conteneur de vos formulaires, tels que le contrôle Panel ou GroupBox, ou même le formulaire lui-même.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- run time [Windows Forms], removing controls
- controls [Windows Forms], adding using collections
- controls collections
- collections [Windows Forms], adding items
- run time [Windows Forms], adding controls
- controls [Windows Forms], removing using collections
ms.assetid: 771bf895-3d5f-469b-a324-3528f343657e
ms.openlocfilehash: 6c3f2d1f42b130de4d808871265b50510cfb8f47
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325873"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a><span data-ttu-id="4c6dd-103">Comment : ajouter des contrôles dans une collection au moment de l’exécution, ou comment les supprimer</span><span class="sxs-lookup"><span data-stu-id="4c6dd-103">How to: Add to or Remove from a Collection of Controls at Run Time</span></span>
<span data-ttu-id="4c6dd-104">Les tâches courantes dans le développement d’applications sont l’ajout et la suppression de contrôles dans n’importe quel contrôle conteneur de vos formulaires (tels que le <xref:System.Windows.Forms.Panel> <xref:System.Windows.Forms.GroupBox> contrôle ou, ou même le formulaire lui-même).</span><span class="sxs-lookup"><span data-stu-id="4c6dd-104">Common tasks in application development are adding controls to and removing controls from any container control on your forms (such as the <xref:System.Windows.Forms.Panel> or <xref:System.Windows.Forms.GroupBox> control, or even the form itself).</span></span> <span data-ttu-id="4c6dd-105">Au moment de la conception, vous pouvez faire glisser les contrôles directement vers un panneau ou une zone de groupe.</span><span class="sxs-lookup"><span data-stu-id="4c6dd-105">At design time, controls can be dragged directly onto a panel or group box.</span></span> <span data-ttu-id="4c6dd-106">Au moment de l’exécution, ces contrôles gèrent une collection `Controls`, qui assure le suivi des contrôles qui y sont placés.</span><span class="sxs-lookup"><span data-stu-id="4c6dd-106">At run time, these controls maintain a `Controls` collection, which keeps track of what controls are placed on them.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c6dd-107">L’exemple de code suivant s’applique à n’importe quel contrôle qui gère une collection de contrôles qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="4c6dd-107">The following code example applies to any control that maintains a collection of controls within it.</span></span>  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a><span data-ttu-id="4c6dd-108">Pour ajouter un contrôle à une collection par programme</span><span class="sxs-lookup"><span data-stu-id="4c6dd-108">To add a control to a collection programmatically</span></span>  
  
1. <span data-ttu-id="4c6dd-109">Créez une instance du contrôle à ajouter.</span><span class="sxs-lookup"><span data-stu-id="4c6dd-109">Create an instance of the control to be added.</span></span>  
  
2. <span data-ttu-id="4c6dd-110">Définissez les propriétés du nouveau contrôle.</span><span class="sxs-lookup"><span data-stu-id="4c6dd-110">Set properties of the new control.</span></span>  
  
3. <span data-ttu-id="4c6dd-111">Ajoutez le contrôle à la collection `Controls` du contrôle parent.</span><span class="sxs-lookup"><span data-stu-id="4c6dd-111">Add the control to the `Controls` collection of the parent control.</span></span>  
  
     <span data-ttu-id="4c6dd-112">L’exemple de code suivant montre comment créer une instance du <xref:System.Windows.Forms.Button> contrôle.</span><span class="sxs-lookup"><span data-stu-id="4c6dd-112">The following code example shows how to create an instance of the <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="4c6dd-113">Elle requiert un formulaire avec un <xref:System.Windows.Forms.Panel> contrôle et que la méthode de gestion des événements pour le bouton en cours de création, `NewPanelButton_Click` , existe déjà.</span><span class="sxs-lookup"><span data-stu-id="4c6dd-113">It requires a form with a <xref:System.Windows.Forms.Panel> control and that the event-handling method for the button being created, `NewPanelButton_Click`, already exists.</span></span>  
  
    ```vb  
    Public NewPanelButton As New Button()  
  
    Public Sub AddNewControl()  
       ' The Add method will accept as a parameter any object that derives  
       ' from the Control class. In this case, it is a Button control.  
       Panel1.Controls.Add(NewPanelButton)  
       ' The event handler indicated for the Click event in the code
       ' below is used as an example. Substite the appropriate event  
       ' handler for your application.  
       AddHandler NewPanelButton.Click, AddressOf NewPanelButton_Click  
    End Sub  
    ```  
  
    ```csharp  
    public Button newPanelButton = new Button();  
  
    public void addNewControl()  
    {
       // The Add method will accept as a parameter any object that derives  
       // from the Control class. In this case, it is a Button control.  
       panel1.Controls.Add(newPanelButton);  
       // The event handler indicated for the Click event in the code
       // below is used as an example. Substitute the appropriate event  
       // handler for your application.  
       this.newPanelButton.Click += new System.EventHandler(this. NewPanelButton_Click);  
    }  
    ```  
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a><span data-ttu-id="4c6dd-114">Pour supprimer des contrôles d’une collection par programme</span><span class="sxs-lookup"><span data-stu-id="4c6dd-114">To remove controls from a collection programmatically</span></span>  
  
1. <span data-ttu-id="4c6dd-115">Supprimez le gestionnaire d’événements de l’événement.</span><span class="sxs-lookup"><span data-stu-id="4c6dd-115">Remove the event handler from the event.</span></span> <span data-ttu-id="4c6dd-116">Dans Visual Basic, utilisez le mot clé [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) . en C#, utilisez l' [opérateur-=](../../../csharp/language-reference/operators/subtraction-operator.md).</span><span class="sxs-lookup"><span data-stu-id="4c6dd-116">In Visual Basic, use the [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) keyword; in C#, use the [-= operator](../../../csharp/language-reference/operators/subtraction-operator.md).</span></span>  
  
2. <span data-ttu-id="4c6dd-117">Utilisez la méthode `Remove` pour supprimer le contrôle souhaité dans la collection `Controls` du panneau.</span><span class="sxs-lookup"><span data-stu-id="4c6dd-117">Use the `Remove` method to delete the desired control from the panel's `Controls` collection.</span></span>  
  
3. <span data-ttu-id="4c6dd-118">Appelez la <xref:System.Windows.Forms.Control.Dispose%2A> méthode pour libérer toutes les ressources utilisées par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="4c6dd-118">Call the <xref:System.Windows.Forms.Control.Dispose%2A> method to release all the resources used by the control.</span></span>  
  
    ```vb  
    Public Sub RemoveControl()  
    ' NOTE: The code below uses the instance of
    ' the button (NewPanelButton) from the previous example.  
       If Panel1.Controls.Contains(NewPanelButton) Then  
          RemoveHandler NewPanelButton.Click, AddressOf _
             NewPanelButton_Click  
          Panel1.Controls.Remove(NewPanelButton)  
          NewPanelButton.Dispose()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void removeControl(object sender, System.EventArgs e)  
    {  
    // NOTE: The code below uses the instance of
    // the button (newPanelButton) from the previous example.  
       if(panel1.Controls.Contains(newPanelButton))  
       {  
          this.newPanelButton.Click -= new System.EventHandler(this.
             NewPanelButton_Click);  
          panel1.Controls.Remove(newPanelButton);  
          newPanelButton.Dispose();  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4c6dd-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c6dd-119">See also</span></span>

- <xref:System.Windows.Forms.Panel>
- [<span data-ttu-id="4c6dd-120">Panel, contrôle</span><span class="sxs-lookup"><span data-stu-id="4c6dd-120">Panel Control</span></span>](panel-control-windows-forms.md)
