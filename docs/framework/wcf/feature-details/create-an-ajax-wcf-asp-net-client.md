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
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="c0e02-102">Comment : créer un service WCF compatible AJAX et un client ASP.NET qui accède à ce service</span><span class="sxs-lookup"><span data-stu-id="c0e02-102">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>

<span data-ttu-id="c0e02-103">Cette rubrique montre comment utiliser Visual Studio pour créer un service Windows Communication Foundation (WCF) compatible AJAX et un client ASP.NET qui accède au service.</span><span class="sxs-lookup"><span data-stu-id="c0e02-103">This topic shows how to use Visual Studio to create an AJAX-enabled Windows Communication Foundation (WCF) service and an ASP.NET client that accesses the service.</span></span>

## <a name="create-an-aspnet-web-app"></a><span data-ttu-id="c0e02-104">Créez une application web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c0e02-104">Create an ASP.NET web app</span></span>

1. <span data-ttu-id="c0e02-105">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c0e02-105">Open Visual Studio.</span></span>

1. <span data-ttu-id="c0e02-106">Dans le menu **fichier** , sélectionnez **nouveau**  >  **projet** .</span><span class="sxs-lookup"><span data-stu-id="c0e02-106">From the **File** menu, select **New** > **Project**</span></span>

1. <span data-ttu-id="c0e02-107">Dans la boîte de dialogue **nouveau projet** , **Installed**développez la  >  catégorie Web**Visual C#** installée  >  **Web** , puis sélectionnez **application Web ASP.net (.NET Framework)**.</span><span class="sxs-lookup"><span data-stu-id="c0e02-107">In the **New Project** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select **ASP.NET Web Application (.NET Framework)**.</span></span>

1. <span data-ttu-id="c0e02-108">Nommez le projet **SandwichServices** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c0e02-108">Name the Project **SandwichServices** and click **OK**.</span></span>

1. <span data-ttu-id="c0e02-109">Dans la boîte de dialogue **nouvelle application Web ASP.net** , sélectionnez **vide** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c0e02-109">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

   ![Boîte de dialogue type d’application Web ASP.NET dans Visual Studio](./media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a><span data-ttu-id="c0e02-111">Ajouter un formulaire Web</span><span class="sxs-lookup"><span data-stu-id="c0e02-111">Add a web form</span></span>

1. <span data-ttu-id="c0e02-112">Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet SandwichServices, puis sélectionnez **Ajouter**  >  **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="c0e02-112">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="c0e02-113">Dans la boîte de dialogue **Ajouter un nouvel élément** , développez la **Installed**  >  catégorie Web**Visual C#** installée  >  **Web** , puis sélectionnez le modèle **Web Form** .</span><span class="sxs-lookup"><span data-stu-id="c0e02-113">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **Web Form** template.</span></span>

1. <span data-ttu-id="c0e02-114">Acceptez le nom par défaut (**WebForm1**), puis sélectionnez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="c0e02-114">Accept the default name (**WebForm1**), and then select **Add**.</span></span>

   <span data-ttu-id="c0e02-115">*WebForm1. aspx* s’ouvre en mode **source** .</span><span class="sxs-lookup"><span data-stu-id="c0e02-115">*WebForm1.aspx* opens in **Source** view.</span></span>

1. <span data-ttu-id="c0e02-116">Ajoutez le balisage suivant à l’intérieur des **\<body>** Balises :</span><span class="sxs-lookup"><span data-stu-id="c0e02-116">Add the following markup inside the **\<body>** tags:</span></span>

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a><span data-ttu-id="c0e02-117">Créer un service WCF compatible AJAX</span><span class="sxs-lookup"><span data-stu-id="c0e02-117">Create an AJAX-enabled WCF service</span></span>

1. <span data-ttu-id="c0e02-118">Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet SandwichServices, puis sélectionnez **Ajouter**  >  **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="c0e02-118">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="c0e02-119">Dans la boîte de dialogue **Ajouter un nouvel élément** , développez la **Installed**  >  catégorie Web**Visual C#** installée  >  **Web** , puis sélectionnez le modèle **service WCF (compatible Ajax)** .</span><span class="sxs-lookup"><span data-stu-id="c0e02-119">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **WCF Service (AJAX-enabled)** template.</span></span>

   ![Modèle d’élément de service WCF (compatible AJAX) dans Visual Studio](./media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. <span data-ttu-id="c0e02-121">Nommez le service **CostService** , puis sélectionnez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="c0e02-121">Name the service **CostService** and then select **Add**.</span></span>

   <span data-ttu-id="c0e02-122">*CostService.svc.cs* s’ouvre dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="c0e02-122">*CostService.svc.cs* opens in the editor.</span></span>

1. <span data-ttu-id="c0e02-123">Implémentez l’opération dans le service.</span><span class="sxs-lookup"><span data-stu-id="c0e02-123">Implement the operation in the service.</span></span> <span data-ttu-id="c0e02-124">Ajoutez la méthode suivante à la classe CostService pour calculer le coût d’une quantité de sandwiches :</span><span class="sxs-lookup"><span data-stu-id="c0e02-124">Add the following method to the CostService class to calculate the cost of a quantity of sandwiches:</span></span>

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a><span data-ttu-id="c0e02-125">Configurer le client pour accéder au service</span><span class="sxs-lookup"><span data-stu-id="c0e02-125">Configure the client to access the service</span></span>

1. <span data-ttu-id="c0e02-126">Ouvrez le fichier *WebForm1. aspx* et sélectionnez le mode **Design** .</span><span class="sxs-lookup"><span data-stu-id="c0e02-126">Open the *WebForm1.aspx* file and select the **Design** view.</span></span>

2. <span data-ttu-id="c0e02-127">Dans le menu **affichage** , sélectionnez **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="c0e02-127">From the **View** menu, select **Toolbox**.</span></span>

3. <span data-ttu-id="c0e02-128">Développez le nœud **Extensions AJAX** et glissez-déposez un **ScriptManager** sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="c0e02-128">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** onto the form.</span></span>

4. <span data-ttu-id="c0e02-129">De retour dans la vue **source** , ajoutez le code suivant entre les **\<ScriptManager>** balises pour spécifier le chemin d’accès au service WCF :</span><span class="sxs-lookup"><span data-stu-id="c0e02-129">Back in the **Source** view, add the following code between the **\<ScriptManager>** tags to specify the path to the WCF service:</span></span>

    ```xml
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

5. <span data-ttu-id="c0e02-130">Ajoutez le code de la fonction JavaScript `Calculate()` .</span><span class="sxs-lookup"><span data-stu-id="c0e02-130">Add the code for the JavaScript function `Calculate()`.</span></span> <span data-ttu-id="c0e02-131">Placez le code suivant dans la section **Head** du formulaire Web :</span><span class="sxs-lookup"><span data-stu-id="c0e02-131">Place the following code in the **head** section of the web form:</span></span>

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

   <span data-ttu-id="c0e02-132">Ce code appelle la méthode de CostService pour calculer le prix de trois sandwichs, puis affiche le résultat dans l’étendue appelée **additionResult**.</span><span class="sxs-lookup"><span data-stu-id="c0e02-132">This code calls the method of CostService to calculate the price for three sandwiches, and then displays the result in the span called **additionResult**.</span></span>

## <a name="run-the-program"></a><span data-ttu-id="c0e02-133">Exécuter le programme</span><span class="sxs-lookup"><span data-stu-id="c0e02-133">Run the program</span></span>

<span data-ttu-id="c0e02-134">Assurez-vous que *WebForm1. aspx* a le focus, puis appuyez sur le bouton **Démarrer** pour lancer le client Web.</span><span class="sxs-lookup"><span data-stu-id="c0e02-134">Make sure that *WebForm1.aspx* has focus, and then press **Start** button to launch the web client.</span></span> <span data-ttu-id="c0e02-135">Le bouton a un triangle vert et dit **IIS Express (Microsoft Edge)**.</span><span class="sxs-lookup"><span data-stu-id="c0e02-135">The button has a green triangle and says something like **IIS Express (Microsoft Edge)**.</span></span> <span data-ttu-id="c0e02-136">Vous pouvez appuyer sur <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c0e02-136">Or, you can press <kbd>F5</kbd>.</span></span> <span data-ttu-id="c0e02-137">Cliquez sur le bouton **prix de 3 sandwiches** pour générer la sortie attendue de « 3,75 ».</span><span class="sxs-lookup"><span data-stu-id="c0e02-137">Click the **Price of 3 sandwiches** button to generate the expected output of "3.75".</span></span>

## <a name="example"></a><span data-ttu-id="c0e02-138"> Exemple</span><span class="sxs-lookup"><span data-stu-id="c0e02-138">Example</span></span>

<span data-ttu-id="c0e02-139">Voici le code complet dans le fichier *CostService.svc.cs* :</span><span class="sxs-lookup"><span data-stu-id="c0e02-139">The following is the full code in the *CostService.svc.cs* file:</span></span>

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

<span data-ttu-id="c0e02-140">Voici le contenu complet de la page *WebForm1. aspx* :</span><span class="sxs-lookup"><span data-stu-id="c0e02-140">The following is the full contents of the *WebForm1.aspx* page:</span></span>

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
