---
title: 'Procédure : Générer une application web ASP.NET MVC prenant en charge les revendications à l’aide de WIF'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: 4d245288b04d8ed3d997bc5572b40c7f8a9334e5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045446"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a><span data-ttu-id="0c250-102">Procédure : Générer une application web ASP.NET MVC prenant en charge les revendications à l’aide de WIF</span><span class="sxs-lookup"><span data-stu-id="0c250-102">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="0c250-103">S'applique à</span><span class="sxs-lookup"><span data-stu-id="0c250-103">Applies To</span></span>  
  
- <span data-ttu-id="0c250-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="0c250-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="0c250-105">ASP.NET® MVC</span><span class="sxs-lookup"><span data-stu-id="0c250-105">ASP.NET® MVC</span></span>  
  
## <a name="summary"></a><span data-ttu-id="0c250-106">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="0c250-106">Summary</span></span>  
 <span data-ttu-id="0c250-107">Cette procédure fournit des procédures pas à pas détaillées pour la création d’une simple application web ASP.NET MVC prenant en charge les revendications.</span><span class="sxs-lookup"><span data-stu-id="0c250-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET MVC web application.</span></span> <span data-ttu-id="0c250-108">Elle fournit également des instructions afin de tester cette simple application web ASP.NET MVC prenant en charge les revendications pour une implémentation réussie de l’authentification basée sur les revendications.</span><span class="sxs-lookup"><span data-stu-id="0c250-108">It also provides instructions how to test the simple claims-aware ASP.NET MVC web application for successful implementation of claims-based authentication.</span></span> <span data-ttu-id="0c250-109">Cette procédure ne comprend pas d’instructions détaillées pour créer un service d’émission de jeton de sécurité (STS) et suppose que vous en avez déjà configuré un.</span><span class="sxs-lookup"><span data-stu-id="0c250-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="0c250-110">Sommaire</span><span class="sxs-lookup"><span data-stu-id="0c250-110">Contents</span></span>  
  
- <span data-ttu-id="0c250-111">Objectifs</span><span class="sxs-lookup"><span data-stu-id="0c250-111">Objectives</span></span>  
  
- <span data-ttu-id="0c250-112">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="0c250-112">Summary of Steps</span></span>  
  
- <span data-ttu-id="0c250-113">Étape 1 : créer une simple application ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="0c250-113">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
- <span data-ttu-id="0c250-114">Étape 2 : configurer l’application ASP.NET MVC pour l’authentification basée sur les revendications</span><span class="sxs-lookup"><span data-stu-id="0c250-114">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
- <span data-ttu-id="0c250-115">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="0c250-115">Step 3 – Test Your Solution</span></span>  
  
- <span data-ttu-id="0c250-116">Éléments associés</span><span class="sxs-lookup"><span data-stu-id="0c250-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="0c250-117">Objectifs</span><span class="sxs-lookup"><span data-stu-id="0c250-117">Objectives</span></span>  
  
- <span data-ttu-id="0c250-118">Configurer l’application web ASP.NET MVC pour l’authentification basée sur les revendications</span><span class="sxs-lookup"><span data-stu-id="0c250-118">Configure ASP.NET MVC web application for claims-based authentication</span></span>  
  
- <span data-ttu-id="0c250-119">Tester le bon fonctionnement de l’application web ASP.NET MVC prenant en charge les revendications</span><span class="sxs-lookup"><span data-stu-id="0c250-119">Test successful claims-aware ASP.NET MVC web application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="0c250-120">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="0c250-120">Summary of Steps</span></span>  
  
- <span data-ttu-id="0c250-121">Étape 1 : créer une simple application ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="0c250-121">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
- <span data-ttu-id="0c250-122">Étape 2 : configurer l’application ASP.NET MVC pour l’authentification basée sur les revendications</span><span class="sxs-lookup"><span data-stu-id="0c250-122">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
- <span data-ttu-id="0c250-123">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="0c250-123">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a><span data-ttu-id="0c250-124">Étape 1 : créer une simple application ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="0c250-124">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
 <span data-ttu-id="0c250-125">Dans cette étape, vous allez créer une application ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="0c250-125">In this step, you will create a new ASP.NET MVC application.</span></span>  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a><span data-ttu-id="0c250-126">Pour créer une simple application ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="0c250-126">To create simple ASP.NET MVC application</span></span>  
  
1. <span data-ttu-id="0c250-127">Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.</span><span class="sxs-lookup"><span data-stu-id="0c250-127">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="0c250-128">Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web ASP.NET MVC 3**.</span><span class="sxs-lookup"><span data-stu-id="0c250-128">In the **New Project** window, click **ASP.NET MVC 3 Web Application**.</span></span>  
  
3. <span data-ttu-id="0c250-129">Dans **Nom**, entrez `TestApp` et appuyez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0c250-129">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4. <span data-ttu-id="0c250-130">Dans la boîte de dialogue **Nouveau projet ASP.NET MVC 3**, sélectionnez **Application Internet** dans les modèles disponibles, vérifiez que **Moteur de vue** a la valeur **Razor**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0c250-130">In the **New ASP.NET MVC 3 Project** dialog, select **Internet Application** from the available templates, ensure **View Engine** is set to **Razor**, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="0c250-131">Quand le nouveau projet s’ouvre, cliquez avec le bouton droit sur le projet **TestApp** dans l’**Explorateur de solutions** et sélectionnez l’option **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="0c250-131">When the new project opens, right-click the **TestApp** project in **Solution Explorer** and select the **Properties** option.</span></span>  
  
6. <span data-ttu-id="0c250-132">Dans la page de propriétés du projet, cliquez sur l’onglet **Web** sur la gauche et vérifiez que l’option **Utiliser le serveur Web IIS local** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="0c250-132">On the project’s properties page, click on the **Web** tab on the left and ensure that the **Use Local IIS Web Server** option is selected.</span></span>  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="0c250-133">Étape 2 : configurer l’application ASP.NET MVC pour l’authentification basée sur les revendications</span><span class="sxs-lookup"><span data-stu-id="0c250-133">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="0c250-134">Dans cette étape, vous allez ajouter des entrées de configuration au fichier de configuration *Web.config* de votre application web ASP.NET MVC pour qu’elle prenne en charge les revendications.</span><span class="sxs-lookup"><span data-stu-id="0c250-134">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET MVC web application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="0c250-135">Pour configurer une application ASP.NET MVC pour l’authentification basée sur les revendications</span><span class="sxs-lookup"><span data-stu-id="0c250-135">To configure ASP.NET MVC application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="0c250-136">Ajoutez les définitions des sections de configuration suivantes au fichier de configuration *Web.config*.</span><span class="sxs-lookup"><span data-stu-id="0c250-136">Add the following configuration section definitions to the *Web.config* configuration file.</span></span> <span data-ttu-id="0c250-137">Elles définissent les sections de configuration requises par Windows Identity Foundation.</span><span class="sxs-lookup"><span data-stu-id="0c250-137">These define configuration sections required by Windows Identity Foundation.</span></span> <span data-ttu-id="0c250-138">Ajoutez les définitions immédiatement après l’élément d’ouverture **\<configuration>**  :</span><span class="sxs-lookup"><span data-stu-id="0c250-138">Add the definitions immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. <span data-ttu-id="0c250-139">Ajoutez un élément **\<location>** qui permet d’accéder aux métadonnées de fédération de l’application :</span><span class="sxs-lookup"><span data-stu-id="0c250-139">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3. <span data-ttu-id="0c250-140">Ajoutez les entrées de configuration suivantes dans les éléments **\<system.web>** pour refuser des utilisateurs, désactiver l’authentification native et activer WIF afin de gérer l’authentification.</span><span class="sxs-lookup"><span data-stu-id="0c250-140">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. <span data-ttu-id="0c250-141">Ajoutez les entrées de configuration liées à Windows Identity Foundation suivantes et vérifiez que l’URL et le numéro de port de votre application ASP.NET correspondent aux valeurs dans l’entrée **\<audienceUris>** , l’attribut **realm** de l’élément **\<wsFederation>** et l’attribut **reply** de l’élément **\<wsFederation>** .</span><span class="sxs-lookup"><span data-stu-id="0c250-141">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="0c250-142">Vérifiez également que la valeur **issuer** correspond à l’URL de votre service d’émission de jeton de sécurité (STS).</span><span class="sxs-lookup"><span data-stu-id="0c250-142">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <audienceUris>  
                <add value="http://localhost:28503/" />  
            </audienceUris>  
            <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
                <trustedIssuers>  
                    <add thumbprint="1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ1234" name="YourSTSName" />  
                </trustedIssuers>   
            </issuerNameRegistry>  
            <certificateValidation certificateValidationMode="None" />  
        </identityConfiguration>  
    </system.identityModel>  
    <system.identityModel.services>  
        <federationConfiguration>  
            <cookieHandler requireSsl="false" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="false" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
5. <span data-ttu-id="0c250-143">Ajoutez une référence à l’assembly <xref:System.IdentityModel>.</span><span class="sxs-lookup"><span data-stu-id="0c250-143">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
6. <span data-ttu-id="0c250-144">Compilez la solution pour vérifier la présence d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="0c250-144">Compile the solution to make sure there are errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="0c250-145">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="0c250-145">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="0c250-146">Dans cette étape, vous allez tester votre application web ASP.NET MVC configurée pour l’authentification basée sur les revendications.</span><span class="sxs-lookup"><span data-stu-id="0c250-146">In this step you will test your ASP.NET MVC web application configured for claims-based authentication.</span></span> <span data-ttu-id="0c250-147">Pour effectuer un test de base, vous allez ajouter un code simple qui affiche les revendications dans le jeton émis par le service d’émission de jeton de sécurité (STS).</span><span class="sxs-lookup"><span data-stu-id="0c250-147">To perform basic test you will add simple code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="0c250-148">Pour tester votre application ASP.NET MVC pour l’authentification basée sur les revendications</span><span class="sxs-lookup"><span data-stu-id="0c250-148">To test your ASP.NET MVC application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="0c250-149">Dans l’**Explorateur de solutions**, développez le dossier **Contrôleurs** et ouvrez le fichier *HomeController.cs* dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="0c250-149">In the **Solution Explorer**, expand the **Controllers** folder and open *HomeController.cs* file in the editor.</span></span> <span data-ttu-id="0c250-150">Ajoutez le code suivant à la méthode **Index** :</span><span class="sxs-lookup"><span data-stu-id="0c250-150">Add the following code to the **Index** method:</span></span>  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2. <span data-ttu-id="0c250-151">Dans l’**Explorateur de solutions**, développez les dossiers **Vues**, puis **Accueil**, et ouvrez le fichier *Index.cshtml* dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="0c250-151">In the **Solution Explorer** expand **Views** and then **Home** folders and open *Index.cshtml* file in the editor.</span></span> <span data-ttu-id="0c250-152">Supprimez son contenu et ajoutez le balisage suivant :</span><span class="sxs-lookup"><span data-stu-id="0c250-152">Delete its contents and add the following markup:</span></span>  
  
    ```html  
    @{  
        ViewBag.Title = "Home Page";  
    }  
  
    <h2>Welcome: @ViewBag.ClaimsIdentity.Name</h2>  
    <h3>Values from Identity</h3>  
    <table>  
        <tr>  
            <th>  
                IsAuthenticated   
            </th>  
            <td>  
                @ViewBag.ClaimsIdentity.IsAuthenticated   
            </td>  
        </tr>  
        <tr>  
            <th>  
                Name   
            </th>          
            <td>  
                @ViewBag.ClaimsIdentity.Name  
            </td>          
        </tr>  
    </table>  
    <h3>Claims from ClaimsIdentity</h3>  
    <table>  
        <tr>  
            <th>  
                Claim Type  
            </th>  
            <th>  
                Claim Value  
            </th>  
            <th>  
                Value Type  
            </th>  
            <th>  
                Subject Name  
            </th>          
            <th>  
                Issuer Name  
            </th>          
        </tr>  
            @foreach (System.Security.Claims.Claim claim in ViewBag.ClaimsIdentity.Claims ) {  
        <tr>  
            <td>  
                @claim.Type  
            </td>  
            <td>  
                @claim.Value  
            </td>  
            <td>  
                @claim.ValueType  
            </td>  
            <td>  
                @claim.Subject.Name  
            </td>  
            <td>  
                @claim.Issuer  
            </td>  
        </tr>  
    }  
    </table>  
    ```  
  
3. <span data-ttu-id="0c250-153">Exécutez la solution en appuyant sur la touche **F5**.</span><span class="sxs-lookup"><span data-stu-id="0c250-153">Run the solution by pressing the **F5** key.</span></span>  
  
4. <span data-ttu-id="0c250-154">La page qui affiche les revendications dans le jeton émis par le service d’émission de jeton de sécurité doit s’afficher.</span><span class="sxs-lookup"><span data-stu-id="0c250-154">You should be presented with the page that displays the claims in the token that was issued to you by Security Token Service.</span></span>  
  
## <a name="related-items"></a><span data-ttu-id="0c250-155">Éléments associés</span><span class="sxs-lookup"><span data-stu-id="0c250-155">Related Items</span></span>  
  
- [<span data-ttu-id="0c250-156">Guide pratique pour Générer des ASP.NET Web Forms application prenant en charge les revendications à l’aide de WIF</span><span class="sxs-lookup"><span data-stu-id="0c250-156">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
