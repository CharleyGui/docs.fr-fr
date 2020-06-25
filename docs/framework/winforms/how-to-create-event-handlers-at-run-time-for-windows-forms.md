---
title: 'Comment : créer des gestionnaires d’événements au moment de l’exécution'
description: Découvrez comment créer un gestionnaire d’événements au moment de l’exécution avec le Concepteur Windows Forms dans Visual Studio. Cette action vous permet de connecter des gestionnaires d’événements au moment de l’exécution.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handlers [Windows Forms], creating
- run time [Windows Forms], creating event handlers at
- examples [Windows Forms], event handling
- Button control [Windows Forms], event handlers
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
ms.openlocfilehash: 857076c46377b3276154d9b193d4bbe51841828f
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325806"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="20cb8-104">Procédure : créer des gestionnaires d’événements au moment de l’exécution pour Windows Forms</span><span class="sxs-lookup"><span data-stu-id="20cb8-104">How to: Create Event Handlers at Run Time for Windows Forms</span></span>

<span data-ttu-id="20cb8-105">En plus de créer des événements à l’aide de l’Concepteur Windows Forms dans Visual Studio, vous pouvez également créer un gestionnaire d’événements au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="20cb8-105">In addition to creating events using the Windows Forms Designer in Visual Studio, you can also create an event handler at run time.</span></span> <span data-ttu-id="20cb8-106">Cette action vous permet de connecter des gestionnaires d’événements en fonction de conditions spécifiées dans le code lors de l’exécution au lieu de les connecter au premier démarrage du programme.</span><span class="sxs-lookup"><span data-stu-id="20cb8-106">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>

## <a name="create-an-event-handler-at-run-time"></a><span data-ttu-id="20cb8-107">Créer un gestionnaire d’événements au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="20cb8-107">Create an event handler at run time</span></span>

1. <span data-ttu-id="20cb8-108">Ouvrez le formulaire auquel vous souhaitez ajouter un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="20cb8-108">Open the form that you want to add an event handler to.</span></span>

2. <span data-ttu-id="20cb8-109">Ajoutez une méthode à votre formulaire avec la signature de méthode pour l’événement que vous souhaitez gérer.</span><span class="sxs-lookup"><span data-stu-id="20cb8-109">Add a method to your form with the method signature for the event that you want to handle.</span></span>

     <span data-ttu-id="20cb8-110">Par exemple, si vous gérez l' <xref:System.Windows.Forms.Control.Click> événement d’un <xref:System.Windows.Forms.Button> contrôle, vous devez créer une méthode telle que la suivante :</span><span class="sxs-lookup"><span data-stu-id="20cb8-110">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>

    ```vb
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As EventArgs)
       ' Add event handler code here.
    End Sub
    ```

    ```csharp
    private void button1_Click(object sender, System.EventArgs e)
    {
    // Add event handler code here.
    }
    ```

    ```cpp
    private:
       void button1_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          // Add event handler code here.
       }
    ```

3. <span data-ttu-id="20cb8-111">Ajoutez le code au gestionnaire d’événements en fonction de votre application.</span><span class="sxs-lookup"><span data-stu-id="20cb8-111">Add code to the event handler as appropriate to your application.</span></span>

4. <span data-ttu-id="20cb8-112">Déterminez le formulaire ou le contrôle pour lequel vous souhaitez créer un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="20cb8-112">Determine which form or control you want to create an event handler for.</span></span>

5. <span data-ttu-id="20cb8-113">Dans une méthode de classe de votre formulaire, ajoutez le code qui spécifie au gestionnaire d’événements de gérer l’événement.</span><span class="sxs-lookup"><span data-stu-id="20cb8-113">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="20cb8-114">Par exemple, le code suivant spécifie que le gestionnaire `button1_Click` d’événements gère l' <xref:System.Windows.Forms.Control.Click> événement d’un <xref:System.Windows.Forms.Button> contrôle :</span><span class="sxs-lookup"><span data-stu-id="20cb8-114">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     <span data-ttu-id="20cb8-115">La <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> méthode illustrée dans le code Visual Basic ci-dessus établit un gestionnaire d’événements Click pour le bouton.</span><span class="sxs-lookup"><span data-stu-id="20cb8-115">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>

## <a name="see-also"></a><span data-ttu-id="20cb8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20cb8-116">See also</span></span>

- [<span data-ttu-id="20cb8-117">Création de gestionnaires d'événements dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="20cb8-117">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="20cb8-118">Vue d’ensemble des gestionnaires d’événements</span><span class="sxs-lookup"><span data-stu-id="20cb8-118">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
- [<span data-ttu-id="20cb8-119">Dépannage des gestionnaires d'événements hérités dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20cb8-119">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
