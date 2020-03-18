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
ms.openlocfilehash: 1f95fd0dcc12f2d4e47ee07e1e6bb15d91000f0f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124784"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a>Comment : consommer des événements dans une application Web Forms
Un scénario courant dans les applications ASP.NET Web Forms consiste à remplir une page web avec des contrôles, puis d’effectuer une action spécifique selon le contrôle sur lequel l’utilisateur clique. Par exemple, un contrôle <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> déclenche un événement lorsque l’utilisateur clique dessus dans la page web. En gérant l’événement, votre application peut exécuter la logique d’application appropriée pour ce clic de bouton.  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a>Pour gérer un événement Click du bouton dans une page Web  
  
1. Créez une page web ASP.NET Web Forms qui a un contrôle <xref:System.Web.UI.WebControls.Button> avec la valeur `OnClick` définie sur le nom de la méthode que vous allez définir dans l’étape suivante.  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. Définissez un gestionnaire d’événements qui correspond à la signature du délégué d’événement <xref:System.Web.UI.WebControls.Button.Click> et qui porte le nom que vous avez défini pour la valeur `OnClick`.  
  
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
  
     L’événement <xref:System.Web.UI.WebControls.Button.Click> utilise la classe <xref:System.EventHandler> pour le type délégué et la classe <xref:System.EventArgs> pour les données d’événement. L’infrastructure de page ASP.NET génère automatiquement du code qui crée une instance de <xref:System.EventHandler> et ajoute cette instance de délégué à l’événement <xref:System.Web.UI.WebControls.Button.Click> de l’instance <xref:System.Web.UI.WebControls.Button>.  
  
3. Dans la méthode de gestionnaire d’événements que vous avez définie à l’étape 2, ajoutez du code pour effectuer les actions qui sont requises lorsque l’événement se produit.  
  
## <a name="see-also"></a>Voir aussi

- [Événements](../../../docs/standard/events/index.md)
