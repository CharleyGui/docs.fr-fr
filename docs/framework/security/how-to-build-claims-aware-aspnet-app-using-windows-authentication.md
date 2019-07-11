---
title: 'Procédure : Générer une application ASP.NET prenant en charge les revendications à l’aide de l’authentification Windows'
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
ms.openlocfilehash: 9b58a4066538441a48bc6646f364e846a25cc8c8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742500"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a><span data-ttu-id="bae01-102">Procédure : Générer une application ASP.NET prenant en charge les revendications à l’aide de l’authentification Windows</span><span class="sxs-lookup"><span data-stu-id="bae01-102">How To: Build Claims-Aware ASP.NET Application Using Windows Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="bae01-103">S'applique à</span><span class="sxs-lookup"><span data-stu-id="bae01-103">Applies To</span></span>  
  
- <span data-ttu-id="bae01-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="bae01-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="bae01-105">Web Forms ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="bae01-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="bae01-106">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="bae01-106">Summary</span></span>  
 <span data-ttu-id="bae01-107">Cette procédure fournit des procédures pas à pas détaillées pour la création d’une simple application Web Forms ASP.NET prenant en charge les revendications et qui utilise l’authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="bae01-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Windows authentication.</span></span> <span data-ttu-id="bae01-108">Elle fournit également des instructions pour tester l’application afin de vérifier que les revendications s’affichent quand un utilisateur se connecte à l’aide de l’authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="bae01-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in using Windows authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="bae01-109">Sommaire</span><span class="sxs-lookup"><span data-stu-id="bae01-109">Contents</span></span>  
  
- <span data-ttu-id="bae01-110">Objectifs</span><span class="sxs-lookup"><span data-stu-id="bae01-110">Objectives</span></span>  
  
- <span data-ttu-id="bae01-111">Présentation</span><span class="sxs-lookup"><span data-stu-id="bae01-111">Overview</span></span>  
  
- <span data-ttu-id="bae01-112">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="bae01-112">Summary of Steps</span></span>  
  
- <span data-ttu-id="bae01-113">Étape 1 : Créer une application Web Forms ASP.NET simple</span><span class="sxs-lookup"><span data-stu-id="bae01-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
- <span data-ttu-id="bae01-114">Étape 2 : configurer l’application Web Forms ASP.NET pour les revendications à l’aide de l’authentification Windows</span><span class="sxs-lookup"><span data-stu-id="bae01-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
- <span data-ttu-id="bae01-115">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="bae01-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="bae01-116">Objectifs</span><span class="sxs-lookup"><span data-stu-id="bae01-116">Objectives</span></span>  
  
- <span data-ttu-id="bae01-117">Configurer une application Web Forms ASP.NET pour les revendications à l’aide de l’authentification Windows</span><span class="sxs-lookup"><span data-stu-id="bae01-117">Configure an ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
- <span data-ttu-id="bae01-118">Tester l’application Web Forms ASP.NET pour vérifier si elle fonctionne correctement</span><span class="sxs-lookup"><span data-stu-id="bae01-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="bae01-119">Présentation</span><span class="sxs-lookup"><span data-stu-id="bae01-119">Overview</span></span>  
 <span data-ttu-id="bae01-120">Dans .NET 4.5, WIF et son autorisation basée sur les revendications ont été ajoutés en tant que partie intégrante du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bae01-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="bae01-121">Auparavant, si vous vouliez obtenir des revendications d’un utilisateur ASP.NET, vous deviez installer WIF et convertir les interfaces en objets Entité de sécurité tels que `Thread.CurrentPrincipal` ou `HttpContext.Current.User`.</span><span class="sxs-lookup"><span data-stu-id="bae01-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="bae01-122">À présent, les revendications sont prises en charge automatiquement par ces objets Entité de sécurité.</span><span class="sxs-lookup"><span data-stu-id="bae01-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="bae01-123">L’authentification Windows a bénéficié de l’ajout de WIF dans .NET 4.5, car tous les utilisateurs authentifiés par les informations d’identification Windows sont automatiquement associés à des revendications.</span><span class="sxs-lookup"><span data-stu-id="bae01-123">Windows authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Windows credentials automatically have claims associated with them.</span></span> <span data-ttu-id="bae01-124">Vous pouvez commencer à utiliser ces revendications immédiatement dans une application ASP.NET qui utilise l’authentification Windows, comme l’illustre cette procédure.</span><span class="sxs-lookup"><span data-stu-id="bae01-124">You can begin using these claims immediately in an ASP.NET application that uses Windows authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="bae01-125">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="bae01-125">Summary of Steps</span></span>  
  
- <span data-ttu-id="bae01-126">Étape 1 : Créer une application Web Forms ASP.NET simple</span><span class="sxs-lookup"><span data-stu-id="bae01-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
- <span data-ttu-id="bae01-127">Étape 2 : configurer l’application Web Forms ASP.NET pour les revendications à l’aide de l’authentification Windows</span><span class="sxs-lookup"><span data-stu-id="bae01-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
- <span data-ttu-id="bae01-128">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="bae01-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="bae01-129">Étape 1 : Créer une application Web Forms ASP.NET simple</span><span class="sxs-lookup"><span data-stu-id="bae01-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="bae01-130">Lors de cette étape, vous allez créer une application Web Forms ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="bae01-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="bae01-131">Pour créer une application ASP.NET simple</span><span class="sxs-lookup"><span data-stu-id="bae01-131">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="bae01-132">Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.</span><span class="sxs-lookup"><span data-stu-id="bae01-132">Start Visual Studio, then click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="bae01-133">Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web Forms ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="bae01-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="bae01-134">Dans **Nom**, entrez `TestApp` et appuyez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bae01-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4. <span data-ttu-id="bae01-135">Une fois le projet **TestApp** créé, cliquez dessus dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="bae01-135">After the **TestApp** project has been created, click on it in **Solution Explorer**.</span></span> <span data-ttu-id="bae01-136">Les propriétés du projet s’affichent dans le volet **Propriétés** sous l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="bae01-136">The project’s properties will appear in the **Properties** pane below **Solution Explorer**.</span></span> <span data-ttu-id="bae01-137">Affectez à la propriété **Authentification Windows** la valeur **Enabled** (Activée).</span><span class="sxs-lookup"><span data-stu-id="bae01-137">Set the **Windows Authentication** property to **Enabled**.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="bae01-138">L’authentification Windows étant désactivée par défaut dans les nouvelles applications ASP.NET, vous devez l’activer manuellement.</span><span class="sxs-lookup"><span data-stu-id="bae01-138">Windows authentication is disabled by default in new ASP.NET applications, so you must manually enable it.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="bae01-139">Étape 2 : configurer l’application Web Forms ASP.NET pour les revendications à l’aide de l’authentification Windows</span><span class="sxs-lookup"><span data-stu-id="bae01-139">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
 <span data-ttu-id="bae01-140">Dans cette étape, vous allez ajouter une entrée de configuration au fichier de configuration *Web.config* et modifier le fichier *Default.aspx* pour afficher les informations sur les revendications d’un compte.</span><span class="sxs-lookup"><span data-stu-id="bae01-140">In this step you will add a configuration entry to the *Web.config* configuration file and modify the *Default.aspx* file to display claims information for an account.</span></span>  
  
### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a><span data-ttu-id="bae01-141">Pour configurer une application ASP.NET pour les revendications à l’aide de l’authentification Windows</span><span class="sxs-lookup"><span data-stu-id="bae01-141">To configure ASP.NET application for claims using Windows authentication</span></span>  
  
1. <span data-ttu-id="bae01-142">Dans le fichier *Default.aspx* du projet **TestApp**, remplacez le balisage existant par le suivant :</span><span class="sxs-lookup"><span data-stu-id="bae01-142">In the **TestApp** project’s *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"  
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Windows authenticated user.          
        </p>  
        <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
     <span data-ttu-id="bae01-143">Cette étape ajoute un contrôle GridView à votre page *Default.aspx* qui sera remplie avec les revendications récupérées à partir de l’authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="bae01-143">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Windows authentication.</span></span>  
  
2. <span data-ttu-id="bae01-144">Enregistrez le fichier *Default.aspx*, puis ouvrez son fichier code-behind nommé *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="bae01-144">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="bae01-145">Remplacez le code existant par le code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="bae01-145">Replace the existing code with the following:</span></span>  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        public partial class _Default : Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Page.User as ClaimsPrincipal;  
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                this.ClaimsGridView.DataBind();  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="bae01-146">Le code ci-dessus affiche les revendications relatives à un utilisateur authentifié.</span><span class="sxs-lookup"><span data-stu-id="bae01-146">The above code will display claims about an authenticated user.</span></span>  
  
3. <span data-ttu-id="bae01-147">Pour modifier le type d’authentification de l’application, modifiez le bloc **\<authentication>** dans la section **\<system.web>** du fichier *Web.config* de la racine du projet afin d’inclure uniquement l’entrée de configuration suivante :</span><span class="sxs-lookup"><span data-stu-id="bae01-147">To change the application’s authentication type, modify the **\<authentication>** block in the **\<system.web>** section of the project’s root *Web.config* file so that it only includes the following configuration entry:</span></span>  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4. <span data-ttu-id="bae01-148">Enfin, modifiez le bloc **\<authorization>** dans la section **\<system.web>** du même fichier *Web.config* pour forcer l’authentification :</span><span class="sxs-lookup"><span data-stu-id="bae01-148">Finally, modify the **\<authorization>** block in the **\<system.web>** section of the same *Web.config* file to force authentication:</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="bae01-149">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="bae01-149">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="bae01-150">Dans cette étape, vous allez tester votre application Web Forms ASP.NET et vérifier que les revendications s’affichent quand un utilisateur se connecte à l’aide de l’authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="bae01-150">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Windows authentication.</span></span>  
  
### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="bae01-151">Pour tester votre application Web Forms ASP.NET pour les revendications à l’aide de l’authentification Windows</span><span class="sxs-lookup"><span data-stu-id="bae01-151">To test your ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
1. <span data-ttu-id="bae01-152">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="bae01-152">Press **F5** to build and run the application.</span></span> <span data-ttu-id="bae01-153">La page *Default.aspx* doit s’afficher, avec le nom de votre compte Windows (dont le nom de domaine) comme utilisateur authentifié dans la partie supérieure droite de la page.</span><span class="sxs-lookup"><span data-stu-id="bae01-153">You should be presented with *Default.aspx*, and your Windows account name (including domain name) should already appear as the authenticated user in the top right of the page.</span></span> <span data-ttu-id="bae01-154">Le contenu de la page doit inclure un tableau rempli avec les revendications récupérées à partir de votre compte Windows.</span><span class="sxs-lookup"><span data-stu-id="bae01-154">The page’s content should include a table filled with claims retrieved from your Windows account.</span></span>
