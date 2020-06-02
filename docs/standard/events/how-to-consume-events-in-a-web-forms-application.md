---
title: 'Comment : consommer des événements dans une application Web Forms'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [.NET Framework], Web Forms
- Web Forms controls, and events
- event handlers [.NET Framework], Web Forms
- events [.NET Framework], consuming
- Web Forms, event handling
ms.assetid: 73bf8638-c4ec-4069-b0bb-a1dc79b92e32
ms.openlocfilehash: 3490b6fb89bfe6d7ac778078f58381bb5172e2fe
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288483"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="ecb89-102">Comment : consommer des événements dans une application Web Forms</span><span class="sxs-lookup"><span data-stu-id="ecb89-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="ecb89-103">Un scénario courant dans les applications ASP.NET Web Forms consiste à remplir une page web avec des contrôles, puis d’effectuer une action spécifique selon le contrôle sur lequel l’utilisateur clique.</span><span class="sxs-lookup"><span data-stu-id="ecb89-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="ecb89-104">Par exemple, un contrôle <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> déclenche un événement lorsque l’utilisateur clique dessus dans la page web.</span><span class="sxs-lookup"><span data-stu-id="ecb89-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="ecb89-105">En gérant l’événement, votre application peut exécuter la logique d’application appropriée pour ce clic de bouton.</span><span class="sxs-lookup"><span data-stu-id="ecb89-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="ecb89-106">Pour gérer un événement Click du bouton dans une page Web</span><span class="sxs-lookup"><span data-stu-id="ecb89-106">To handle a button click event on a webpage</span></span>  
  
1. <span data-ttu-id="ecb89-107">Créez une page web ASP.NET Web Forms qui a un contrôle <xref:System.Web.UI.WebControls.Button> avec la valeur `OnClick` définie sur le nom de la méthode que vous allez définir dans l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="ecb89-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. <span data-ttu-id="ecb89-108">Définissez un gestionnaire d’événements qui correspond à la signature du délégué d’événement <xref:System.Web.UI.WebControls.Button.Click> et qui porte le nom que vous avez défini pour la valeur `OnClick`.</span><span class="sxs-lookup"><span data-stu-id="ecb89-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
    ```csharp  
    protected void Button1_Click(object sender, EventArgs e)  
    {  
        // perform action  
    }  
    ```  
  
    ```vb  
    Protected Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' perform action  
    End Sub  
    ```  
  
     <span data-ttu-id="ecb89-109">L’événement <xref:System.Web.UI.WebControls.Button.Click> utilise la classe <xref:System.EventHandler> pour le type délégué et la classe <xref:System.EventArgs> pour les données d’événement.</span><span class="sxs-lookup"><span data-stu-id="ecb89-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="ecb89-110">L’infrastructure de page ASP.NET génère automatiquement du code qui crée une instance de <xref:System.EventHandler> et ajoute cette instance de délégué à l’événement <xref:System.Web.UI.WebControls.Button.Click> de l’instance <xref:System.Web.UI.WebControls.Button>.</span><span class="sxs-lookup"><span data-stu-id="ecb89-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3. <span data-ttu-id="ecb89-111">Dans la méthode de gestionnaire d’événements que vous avez définie à l’étape 2, ajoutez du code pour effectuer les actions qui sont requises lorsque l’événement se produit.</span><span class="sxs-lookup"><span data-stu-id="ecb89-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecb89-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ecb89-112">See also</span></span>

- [<span data-ttu-id="ecb89-113">Événements</span><span class="sxs-lookup"><span data-stu-id="ecb89-113">Events</span></span>](index.md)
