---
title: Créer un service WCF compatible AJAX et un client ASP.NET dans Visual Studio
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 0bfe55c68f68bfef7b7ec2034413b53d41b0c785
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609354"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a>Comment : créer un service WCF compatible AJAX et un client ASP.NET qui accède à ce service

Cette rubrique montre comment utiliser Visual Studio pour créer un service Windows Communication Foundation (WCF) compatible AJAX et un client ASP.NET qui accède au service.

## <a name="create-an-aspnet-web-app"></a>Créez une application web ASP.NET

1. Ouvrez Visual Studio.

1. Dans le menu **fichier** , sélectionnez **nouveau**  >  **projet** .

1. Dans la boîte de dialogue **nouveau projet** , **Installed**développez la  >  catégorie Web**Visual C#** installée  >  **Web** , puis sélectionnez **application Web ASP.net (.NET Framework)**.

1. Nommez le projet **SandwichServices** , puis cliquez sur **OK**.

1. Dans la boîte de dialogue **nouvelle application Web ASP.net** , sélectionnez **vide** , puis cliquez sur **OK**.

   ![Boîte de dialogue type d’application Web ASP.NET dans Visual Studio](./media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a>Ajouter un formulaire Web

1. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet SandwichServices, puis sélectionnez **Ajouter**  >  **un nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , développez la **Installed**  >  catégorie Web**Visual C#** installée  >  **Web** , puis sélectionnez le modèle **Web Form** .

1. Acceptez le nom par défaut (**WebForm1**), puis sélectionnez **Ajouter**.

   *WebForm1. aspx* s’ouvre en mode **source** .

1. Ajoutez le balisage suivant à l’intérieur des **\<body>** Balises :

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a>Créer un service WCF compatible AJAX

1. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet SandwichServices, puis sélectionnez **Ajouter**  >  **un nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , développez la **Installed**  >  catégorie Web**Visual C#** installée  >  **Web** , puis sélectionnez le modèle **service WCF (compatible Ajax)** .

   ![Modèle d’élément de service WCF (compatible AJAX) dans Visual Studio](./media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. Nommez le service **CostService** , puis sélectionnez **Ajouter**.

   *CostService.svc.cs* s’ouvre dans l’éditeur.

1. Implémentez l’opération dans le service. Ajoutez la méthode suivante à la classe CostService pour calculer le coût d’une quantité de sandwiches :

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a>Configurer le client pour accéder au service

1. Ouvrez le fichier *WebForm1. aspx* et sélectionnez le mode **Design** .

2. Dans le menu **affichage** , sélectionnez **boîte à outils**.

3. Développez le nœud **Extensions AJAX** et glissez-déposez un **ScriptManager** sur le formulaire.

4. De retour dans la vue **source** , ajoutez le code suivant entre les **\<ScriptManager>** balises pour spécifier le chemin d’accès au service WCF :

    ```xml
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

5. Ajoutez le code de la fonction JavaScript `Calculate()` . Placez le code suivant dans la section **Head** du formulaire Web :

    ```html
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
    ```

   Ce code appelle la méthode de CostService pour calculer le prix de trois sandwichs, puis affiche le résultat dans l’étendue appelée **additionResult**.

## <a name="run-the-program"></a>Exécuter le programme

Assurez-vous que *WebForm1. aspx* a le focus, puis appuyez sur le bouton **Démarrer** pour lancer le client Web. Le bouton a un triangle vert et dit **IIS Express (Microsoft Edge)**. Vous pouvez appuyer sur <kbd>F5</kbd>. Cliquez sur le bouton **prix de 3 sandwiches** pour générer la sortie attendue de « 3,75 ».

## <a name="example"></a> Exemple

Voici le code complet dans le fichier *CostService.svc.cs* :

```csharp
using System.ServiceModel;
using System.ServiceModel.Activation;

namespace SandwichServices
{
    [ServiceContract(Namespace = "")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class CostService
    {
        [OperationContract]
        public double CostOfSandwiches(int quantity)
        {
            return 1.25 * quantity;
        }
    }
}
```

Voici le contenu complet de la page *WebForm1. aspx* :

```aspx-csharp
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SandwichServices.WebForm1" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
</head>
<body>
    <form id="form1" runat="server">
        <div>
        </div>
        <asp:ScriptManager ID="ScriptManager1" runat="server">
            <Services>
                <asp:ServiceReference Path="~/CostService.svc" />
            </Services>
        </asp:ScriptManager>

        <input type="button" value="Price of 3 sandwiches" onclick="Calculate()" />
        <br />
        <span id="additionResult"></span>
    </form>
</body>
</html>
```
