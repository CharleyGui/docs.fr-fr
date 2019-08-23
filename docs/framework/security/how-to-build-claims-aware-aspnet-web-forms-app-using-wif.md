---
title: 'Procédure : Générer une application Web Forms ASP.NET prenant en charge les revendications à l’aide de WIF'
ms.date: 03/30/2017
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
author: BrucePerlerMS
ms.openlocfilehash: 82b0649a7324987581cc3c97570a0fc42ffdf6d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941295"
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a><span data-ttu-id="93c0a-102">Procédure : Générer une application Web Forms ASP.NET prenant en charge les revendications à l’aide de WIF</span><span class="sxs-lookup"><span data-stu-id="93c0a-102">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="93c0a-103">S'applique à</span><span class="sxs-lookup"><span data-stu-id="93c0a-103">Applies To</span></span>  
  
- <span data-ttu-id="93c0a-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="93c0a-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="93c0a-105">Web Forms ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="93c0a-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="93c0a-106">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="93c0a-106">Summary</span></span>  
 <span data-ttu-id="93c0a-107">Cette procédure fournit des procédures pas à pas détaillées pour la création d’une simple application Web Forms ASP.NET prenant en charge les revendications.</span><span class="sxs-lookup"><span data-stu-id="93c0a-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET Web Forms application.</span></span> <span data-ttu-id="93c0a-108">Elle fournit également des instructions afin de tester cette simple application Web Forms ASP.NET prenant en charge les revendications pour une implémentation réussie de l’authentification fédérée.</span><span class="sxs-lookup"><span data-stu-id="93c0a-108">It also provides instructions for how to test the simple claims-aware ASP.NET Web Forms application for successful implementation of federated authentication.</span></span> <span data-ttu-id="93c0a-109">Cette procédure ne comprend pas d’instructions détaillées pour créer un service d’émission de jeton de sécurité (STS) et suppose que vous en avez déjà configuré un.</span><span class="sxs-lookup"><span data-stu-id="93c0a-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="93c0a-110">Sommaire</span><span class="sxs-lookup"><span data-stu-id="93c0a-110">Contents</span></span>  
  
- <span data-ttu-id="93c0a-111">Objectifs</span><span class="sxs-lookup"><span data-stu-id="93c0a-111">Objectives</span></span>  
  
- <span data-ttu-id="93c0a-112">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="93c0a-112">Summary of Steps</span></span>  
  
- <span data-ttu-id="93c0a-113">Étape 1 : Créer une application Web Forms ASP.NET simple</span><span class="sxs-lookup"><span data-stu-id="93c0a-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
- <span data-ttu-id="93c0a-114">Étape 2 : configurer l’application Web Forms ASP.NET pour l’authentification basée sur les revendications</span><span class="sxs-lookup"><span data-stu-id="93c0a-114">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
  
- <span data-ttu-id="93c0a-115">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="93c0a-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="93c0a-116">Objectifs</span><span class="sxs-lookup"><span data-stu-id="93c0a-116">Objectives</span></span>  
  
- <span data-ttu-id="93c0a-117">Configurer l’application Web Forms ASP.NET pour l’authentification basée sur les revendications</span><span class="sxs-lookup"><span data-stu-id="93c0a-117">Configure ASP.NET Web Forms application for claims-based authentication</span></span>  
  
- <span data-ttu-id="93c0a-118">Tester le bon fonctionnement de l’application Web Forms ASP.NET prenant en charge les revendications</span><span class="sxs-lookup"><span data-stu-id="93c0a-118">Test successful claims-aware ASP.NET Web Forms application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="93c0a-119">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="93c0a-119">Summary of Steps</span></span>  
  
- <span data-ttu-id="93c0a-120">Étape 1 : créer une simple application Web Forms ASP.NET</span><span class="sxs-lookup"><span data-stu-id="93c0a-120">Step 1 – Create Simple ASP.NET Web Forms Application</span></span>  
  
- <span data-ttu-id="93c0a-121">Étape 2 : configurer l’application Web Forms ASP.NET pour l’authentification fédérée</span><span class="sxs-lookup"><span data-stu-id="93c0a-121">Step 2 – Configure ASP.NET Web Forms Application for Federated Authentication</span></span>  
  
- <span data-ttu-id="93c0a-122">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="93c0a-122">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="93c0a-123">Étape 1 : Créer une application Web Forms ASP.NET simple</span><span class="sxs-lookup"><span data-stu-id="93c0a-123">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="93c0a-124">Lors de cette étape, vous allez créer une application Web Forms ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="93c0a-124">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="93c0a-125">Pour créer une simple application ASP.NET</span><span class="sxs-lookup"><span data-stu-id="93c0a-125">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="93c0a-126">Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.</span><span class="sxs-lookup"><span data-stu-id="93c0a-126">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="93c0a-127">Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web Forms ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="93c0a-127">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="93c0a-128">Dans **Nom**, entrez `TestApp` et appuyez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="93c0a-128">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a><span data-ttu-id="93c0a-129">Étape 2 : configurer l’application Web Forms ASP.NET pour l’authentification basée sur les revendications</span><span class="sxs-lookup"><span data-stu-id="93c0a-129">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="93c0a-130">Dans cette étape, vous allez ajouter des entrées de configuration au fichier de configuration *Web.config* de votre application Web Forms ASP.NET pour qu’elle prenne en charge les revendications.</span><span class="sxs-lookup"><span data-stu-id="93c0a-130">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET Web Forms application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a><span data-ttu-id="93c0a-131">Pour configurer une application ASP.NET pour l’authentification basée sur les revendications</span><span class="sxs-lookup"><span data-stu-id="93c0a-131">To configure ASP.NET application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="93c0a-132">Ajoutez les entrées des sections de configuration suivantes au fichier de configuration *Web.config* immédiatement après l’élément d’ouverture **\<configuration>**  :</span><span class="sxs-lookup"><span data-stu-id="93c0a-132">Add the following configuration section entries to the *Web.config* configuration file immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
      <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
      <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. <span data-ttu-id="93c0a-133">Ajoutez un élément **\<location>** qui permet d’accéder aux métadonnées de fédération de l’application :</span><span class="sxs-lookup"><span data-stu-id="93c0a-133">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
      <system.web>  
        <authorization>  
          <allow users="*" />  
        </authorization>  
      </system.web>  
    </location>  
    ```  
  
3. <span data-ttu-id="93c0a-134">Ajoutez les entrées de configuration suivantes dans les éléments **\<system.web>** pour refuser des utilisateurs, désactiver l’authentification native et activer WIF afin de gérer l’authentification.</span><span class="sxs-lookup"><span data-stu-id="93c0a-134">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
      <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. <span data-ttu-id="93c0a-135">Ajoutez un élément **\<system.webServer>** qui définit les modules pour l’authentification fédérée.</span><span class="sxs-lookup"><span data-stu-id="93c0a-135">Add a **\<system.webServer>** element that defines the modules for federated authentication.</span></span> <span data-ttu-id="93c0a-136">Notez que l’attribut*PublicKeyToken* doit être le même que l’attribut *PublicKeyToken* pour les entrées **\<configSections>** ajoutées précédemment :</span><span class="sxs-lookup"><span data-stu-id="93c0a-136">Note that the *PublicKeyToken* attribute must be the same as the *PublicKeyToken* attribute for the **\<configSections>** entries added earlier:</span></span>  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5. <span data-ttu-id="93c0a-137">Ajoutez les entrées de configuration liées à Windows Identity Foundation suivantes et vérifiez que l’URL et le numéro de port de votre application ASP.NET correspondent aux valeurs dans l’entrée **\<audienceUris>** , l’attribut **realm** de l’élément **\<wsFederation>** et l’attribut **reply** de l’élément **\<wsFederation>** .</span><span class="sxs-lookup"><span data-stu-id="93c0a-137">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="93c0a-138">Vérifiez également que la valeur **issuer** correspond à l’URL de votre service d’émission de jeton de sécurité (STS).</span><span class="sxs-lookup"><span data-stu-id="93c0a-138">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
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
            <cookieHandler requireSsl="true" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="true" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
6. <span data-ttu-id="93c0a-139">Ajoutez une référence à l’assembly <xref:System.IdentityModel>.</span><span class="sxs-lookup"><span data-stu-id="93c0a-139">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
7. <span data-ttu-id="93c0a-140">Compilez la solution pour vérifier l’absence d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="93c0a-140">Compile the solution to make sure there are no errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="93c0a-141">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="93c0a-141">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="93c0a-142">Dans cette étape, vous allez tester votre application Web Forms ASP.NET configurée pour l’authentification basée sur les revendications.</span><span class="sxs-lookup"><span data-stu-id="93c0a-142">In this step you will test your ASP.NET Web Forms application configured for claims-based authentication.</span></span> <span data-ttu-id="93c0a-143">Pour effectuer un test de base, vous allez ajouter le code qui affiche les revendications dans le jeton émis par le service d’émission de jeton de sécurité (STS).</span><span class="sxs-lookup"><span data-stu-id="93c0a-143">To perform a basic test, you will add code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a><span data-ttu-id="93c0a-144">Pour tester votre application Web Forms ASP.NET pour l’authentification basée sur les revendications</span><span class="sxs-lookup"><span data-stu-id="93c0a-144">To test your ASP.NET Web Form application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="93c0a-145">Ouvrez le fichier **Default.aspx** sous le projet **TestApp** et remplacez le balisage existant par le suivant :</span><span class="sxs-lookup"><span data-stu-id="93c0a-145">Open the **Default.aspx** file under the **TestApp** project and replace its existing markup with the following markup:</span></span>  
  
    ```  
    %@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head id="Head1" runat="server">  
        <title></title>  
    </head>  
    <body>  
        <h1><asp:label ID="signedIn" runat="server" /></h1>  
        <asp:label ID="claimType" runat="server" />  
        <asp:label ID="claimValue" runat="server" />  
        <asp:label ID="claimValueType" runat="server" />  
        <asp:label ID="claimSubjectName" runat="server" />  
        <asp:label ID="claimIssuer" runat="server" />  
    </body>  
    </html>  
    ```  
  
2. <span data-ttu-id="93c0a-146">Enregistrez **Default.aspx**, puis ouvrez son fichier code-behind nommé **Default.aspx.cs**.</span><span class="sxs-lookup"><span data-stu-id="93c0a-146">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="93c0a-147">**Default.aspx.cs** peut être masqué sous **Default.aspx** dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="93c0a-147">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="93c0a-148">Si **Default.aspx.cs** n’est pas visible, développez **Default.aspx** en cliquant sur le triangle en regard de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="93c0a-148">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
3. <span data-ttu-id="93c0a-149">Remplacez le code existant dans la méthode **Page_Load** de **Default.aspx.cs** par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="93c0a-149">Replace the existing code in the **Page_Load** method of **Default.aspx.cs** with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.IdentityModel;  
    using System.Security.Claims;  
    using System.Threading;  
    using System.Web.UI;  
  
    namespace TestApp  
    {  
        public partial class _Default : System.Web.UI.Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
                if (claimsPrincipal != null)  
                {  
                    signedIn.Text = "You are signed in.";  
  
                    foreach (Claim claim in claimsPrincipal.Claims)  
                    {  
                        claimType.Text = claim.Type;  
                        claimValue.Text = claim.Value;  
                        claimValueType.Text = claim.ValueType;  
                        claimSubjectName.Text = claim.Subject.Name;  
                        claimIssuer.Text = claim.Issuer;  
                    }  
                }  
                else  
                {  
                    signedIn.Text = "You are not signed in.";  
                }  
            }  
        }  
    }  
    ```  
  
4. <span data-ttu-id="93c0a-150">Enregistrez **Default.aspx.cs** et générez la solution.</span><span class="sxs-lookup"><span data-stu-id="93c0a-150">Save **Default.aspx.cs**, and build the solution.</span></span>  
  
5. <span data-ttu-id="93c0a-151">Exécutez la solution en appuyant sur la touche **F5**.</span><span class="sxs-lookup"><span data-stu-id="93c0a-151">Run the solution by pressing the **F5** key.</span></span>  
  
6. <span data-ttu-id="93c0a-152">La page qui affiche les revendications dans le jeton émis par le service d’émission de jeton de sécurité doit s’afficher.</span><span class="sxs-lookup"><span data-stu-id="93c0a-152">You should be presented with the page that displays the claims in the token that was issued to you by the Security Token Service.</span></span>
