---
title: 'Procédure : créer des gestionnaires d’événements au moment de l’exécution pour Windows Forms'
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
ms.openlocfilehash: 440086bfd5384fc46aec2997dbdd9937f7a1b65f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964329"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="f3cec-102">Procédure : créer des gestionnaires d’événements au moment de l’exécution pour Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3cec-102">How to: Create Event Handlers at Run Time for Windows Forms</span></span>

<span data-ttu-id="f3cec-103">En plus de créer des événements à l’aide de l’Concepteur Windows Forms dans Visual Studio, vous pouvez également créer un gestionnaire d’événements au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f3cec-103">In addition to creating events using the Windows Forms Designer in Visual Studio, you can also create an event handler at run time.</span></span> <span data-ttu-id="f3cec-104">Cette action vous permet de connecter des gestionnaires d’événements en fonction de conditions spécifiées dans le code lors de l’exécution au lieu de les connecter au premier démarrage du programme.</span><span class="sxs-lookup"><span data-stu-id="f3cec-104">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>

## <a name="create-an-event-handler-at-run-time"></a><span data-ttu-id="f3cec-105">Créer un gestionnaire d’événements au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="f3cec-105">Create an event handler at run time</span></span>

1. <span data-ttu-id="f3cec-106">Ouvrez le formulaire auquel vous souhaitez ajouter un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="f3cec-106">Open the form that you want to add an event handler to.</span></span>

2. <span data-ttu-id="f3cec-107">Ajoutez une méthode à votre formulaire avec la signature de méthode pour l’événement que vous souhaitez gérer.</span><span class="sxs-lookup"><span data-stu-id="f3cec-107">Add a method to your form with the method signature for the event that you want to handle.</span></span>

     <span data-ttu-id="f3cec-108">Par exemple, si vous gérez l' <xref:System.Windows.Forms.Control.Click> événement d’un <xref:System.Windows.Forms.Button> contrôle, vous devez créer une méthode telle que la suivante:</span><span class="sxs-lookup"><span data-stu-id="f3cec-108">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>

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

3. <span data-ttu-id="f3cec-109">Ajoutez le code au gestionnaire d’événements en fonction de votre application.</span><span class="sxs-lookup"><span data-stu-id="f3cec-109">Add code to the event handler as appropriate to your application.</span></span>

4. <span data-ttu-id="f3cec-110">Déterminez le formulaire ou le contrôle pour lequel vous souhaitez créer un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="f3cec-110">Determine which form or control you want to create an event handler for.</span></span>

5. <span data-ttu-id="f3cec-111">Dans une méthode de classe de votre formulaire, ajoutez le code qui spécifie au gestionnaire d’événements de gérer l’événement.</span><span class="sxs-lookup"><span data-stu-id="f3cec-111">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="f3cec-112">Par exemple, le code suivant spécifie que le `button1_Click` gestionnaire d' <xref:System.Windows.Forms.Control.Click> événements gère l' <xref:System.Windows.Forms.Button> événement d’un contrôle:</span><span class="sxs-lookup"><span data-stu-id="f3cec-112">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     <span data-ttu-id="f3cec-113">La <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> méthode illustrée dans le code Visual Basic ci-dessus établit un gestionnaire d’événements Click pour le bouton.</span><span class="sxs-lookup"><span data-stu-id="f3cec-113">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3cec-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3cec-114">See also</span></span>

- [<span data-ttu-id="f3cec-115">Création de gestionnaires d’événements dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3cec-115">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="f3cec-116">Vue d'ensemble des gestionnaires d'événements</span><span class="sxs-lookup"><span data-stu-id="f3cec-116">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
- [<span data-ttu-id="f3cec-117">Dépannage des gestionnaires d’événements hérités en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f3cec-117">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
