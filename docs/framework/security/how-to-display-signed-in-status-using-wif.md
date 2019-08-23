---
title: 'Procédure : Afficher l’état Connecté à l’aide de WIF'
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: e44dc80260e46b81ac723ada32085390a18a153a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945699"
---
# <a name="how-to-display-signed-in-status-using-wif"></a><span data-ttu-id="a8077-102">Procédure : Afficher l’état Connecté à l’aide de WIF</span><span class="sxs-lookup"><span data-stu-id="a8077-102">How To: Display Signed In Status Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="a8077-103">S'applique à</span><span class="sxs-lookup"><span data-stu-id="a8077-103">Applies To</span></span>  
  
- <span data-ttu-id="a8077-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span><span class="sxs-lookup"><span data-stu-id="a8077-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span></span>  
  
- <span data-ttu-id="a8077-105">Web Forms ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="a8077-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="a8077-106">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="a8077-106">Summary</span></span>  
 <span data-ttu-id="a8077-107">Cette rubrique décrit comment afficher l’état de la connexion dans une application ASP.NET WIF.</span><span class="sxs-lookup"><span data-stu-id="a8077-107">This topic describes how to display the sign in status in a WIF-enabled ASP.NET application.</span></span> <span data-ttu-id="a8077-108">WIF fournit le mécanisme permettant à votre application de prendre en charge les revendications, ainsi que pour gérer l’authentification et l’autorisation pour les ressources d’applications.</span><span class="sxs-lookup"><span data-stu-id="a8077-108">WIF provides the mechanism for making your application claims-aware, and managing authentication and authorization for application resources.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="a8077-109">Sommaire</span><span class="sxs-lookup"><span data-stu-id="a8077-109">Contents</span></span>  
  
- <span data-ttu-id="a8077-110">Présentation</span><span class="sxs-lookup"><span data-stu-id="a8077-110">Overview</span></span>  
  
- <span data-ttu-id="a8077-111">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="a8077-111">Summary of Steps</span></span>  
  
- <span data-ttu-id="a8077-112">Étape 1 : installer l’extension Identity and Access Tool</span><span class="sxs-lookup"><span data-stu-id="a8077-112">Step 1 – Install the Identity and Access Extension</span></span>  
  
- <span data-ttu-id="a8077-113">Étape 2 : créer une application ASP.NET par partie de confiance</span><span class="sxs-lookup"><span data-stu-id="a8077-113">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
- <span data-ttu-id="a8077-114">Étape 3 : activer le service STS de développement local pour authentifier les utilisateurs</span><span class="sxs-lookup"><span data-stu-id="a8077-114">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
- <span data-ttu-id="a8077-115">Étape 4 : modifier votre application ASP.NET pour afficher l’état de connexion</span><span class="sxs-lookup"><span data-stu-id="a8077-115">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
- <span data-ttu-id="a8077-116">Étape 5 : tester l’intégration entre WIF et votre application ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a8077-116">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="overview"></a><span data-ttu-id="a8077-117">Présentation</span><span class="sxs-lookup"><span data-stu-id="a8077-117">Overview</span></span>  
 <span data-ttu-id="a8077-118">Cette rubrique montre comment créer une simple application prenant en charge les revendications à l’aide de WIF et indiquer facilement si un utilisateur est connecté ou non.</span><span class="sxs-lookup"><span data-stu-id="a8077-118">This topic demonstrates how to create a simple claims-aware application using WIF and how to easily display whether a user is signed in or not.</span></span> <span data-ttu-id="a8077-119">Les étapes suivantes utilisent le service STS de développement local qui est inclus avec l’extension Visual Studio Identity and Access Tool.</span><span class="sxs-lookup"><span data-stu-id="a8077-119">The following steps use the Local Development STS that is included with the Identity and Access Visual Studio Extension.</span></span> <span data-ttu-id="a8077-120">Le service STS de développement local est conçu pour un environnement de développement et de test afin de fournir une méthode simple d’intégration des revendications dans votre application.</span><span class="sxs-lookup"><span data-stu-id="a8077-120">The Local Development STS is intended for a testing and development environment to provide a simple method of integrating claims into your application.</span></span> <span data-ttu-id="a8077-121">Il ne doit jamais être utilisé dans un environnement de production, car il n’effectue pas de véritable authentification et les informations d’identification ne sont pas requises.</span><span class="sxs-lookup"><span data-stu-id="a8077-121">It should never be used in a production environment, as it does not perform real authentication and credentials are not required.</span></span> <span data-ttu-id="a8077-122">Toutefois, le code impératif dans les étapes suivantes est le même pour une application prête pour la production qui utilise l’authentification réelle.</span><span class="sxs-lookup"><span data-stu-id="a8077-122">However, the imperative code in the following steps is the same for a production-ready application using real authentication.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="a8077-123">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="a8077-123">Summary of Steps</span></span>  
  
- <span data-ttu-id="a8077-124">Étape 1 : installer l’extension Identity and Access Tool</span><span class="sxs-lookup"><span data-stu-id="a8077-124">Step 1 – Install the Identity and Access Extension</span></span>  
  
- <span data-ttu-id="a8077-125">Étape 2 : créer une application ASP.NET par partie de confiance</span><span class="sxs-lookup"><span data-stu-id="a8077-125">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
- <span data-ttu-id="a8077-126">Étape 3 : activer le service STS de développement local pour authentifier les utilisateurs</span><span class="sxs-lookup"><span data-stu-id="a8077-126">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
- <span data-ttu-id="a8077-127">Étape 4 : modifier votre application ASP.NET pour afficher l’état de connexion</span><span class="sxs-lookup"><span data-stu-id="a8077-127">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
- <span data-ttu-id="a8077-128">Étape 5 : tester l’intégration entre WIF et votre application ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a8077-128">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="step-1--install-the-identity-and-access-extension"></a><span data-ttu-id="a8077-129">Étape 1 : installer l’extension Identity and Access Tool</span><span class="sxs-lookup"><span data-stu-id="a8077-129">Step 1 – Install the Identity and Access Extension</span></span>  
 <span data-ttu-id="a8077-130">Cette étape explique comment configurer l’extension Identity and Access Tool pour Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="a8077-130">This step describes how to configure the Identity and Access extension to Visual Studio 2012.</span></span> <span data-ttu-id="a8077-131">Cette extension automatise le processus de configuration de votre application afin de communiquer avec les points de terminaison STS.</span><span class="sxs-lookup"><span data-stu-id="a8077-131">This extension automates the process of configuring your application to communicate with STS endpoints.</span></span>  
  
### <a name="to-install-the-identity-and-access-extension"></a><span data-ttu-id="a8077-132">Pour installer l’extension Identity and Access Tool</span><span class="sxs-lookup"><span data-stu-id="a8077-132">To install the Identity and Access extension</span></span>  
  
1. <span data-ttu-id="a8077-133">Démarrez Visual Studio en mode élevé en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="a8077-133">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2. <span data-ttu-id="a8077-134">Dans Visual Studio, cliquez sur **Outils**, puis sur **Gestionnaire d’extensions**.</span><span class="sxs-lookup"><span data-stu-id="a8077-134">In Visual Studio, click **Tools** and click **Extension Manager**.</span></span> <span data-ttu-id="a8077-135">La fenêtre **Gestionnaire d’extensions** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="a8077-135">The **Extension Manager** window appears.</span></span>  
  
3. <span data-ttu-id="a8077-136">Dans le **Gestionnaire d’extensions**, cliquez sur **Online Extensions** (Extensions en ligne) dans le menu de gauche, puis sélectionnez **Galerie Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a8077-136">In **Extension Manager**, click **Online Extensions** from the left menu, then select **Visual Studio Gallery**.</span></span>  
  
4. <span data-ttu-id="a8077-137">Dans l’angle supérieur droit du **Gestionnaire d’extensions**, recherchez *Identity and Access* (Identity and Access Tool).</span><span class="sxs-lookup"><span data-stu-id="a8077-137">In the top right corner of **Extension Manager**, search for *Identity and Access*.</span></span>  
  
5. <span data-ttu-id="a8077-138">L’élément **Identity and Access** (Identity and Access Tool) apparaît dans les résultats de la recherche.</span><span class="sxs-lookup"><span data-stu-id="a8077-138">The **Identity and Access** item will appear in the search results.</span></span> <span data-ttu-id="a8077-139">Cliquez dessus, puis sur **Télécharger**.</span><span class="sxs-lookup"><span data-stu-id="a8077-139">Click it, and then click **Download**.</span></span>  
  
6. <span data-ttu-id="a8077-140">La boîte de dialogue **Télécharger et installer** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="a8077-140">The **Download and Install** dialog appears.</span></span> <span data-ttu-id="a8077-141">Si vous êtes d’accord avec les termes du contrat de licence, cliquez sur **Installer**.</span><span class="sxs-lookup"><span data-stu-id="a8077-141">If you agree with the license terms, click **Install**.</span></span>  
  
7. <span data-ttu-id="a8077-142">Quand l’installation de l’extension **Identity and Access** (Identity and Access Tool) est terminée, redémarrez Visual Studio en mode administrateur.</span><span class="sxs-lookup"><span data-stu-id="a8077-142">When the **Identity and Access** extension has finished installing, restart Visual Studio in administrator mode.</span></span>  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a><span data-ttu-id="a8077-143">Étape 2 : créer une application ASP.NET par partie de confiance</span><span class="sxs-lookup"><span data-stu-id="a8077-143">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
 <span data-ttu-id="a8077-144">Cette étape décrit comment créer une application Web Forms ASP.NET par partie de confiance qui s’intègre avec WIF.</span><span class="sxs-lookup"><span data-stu-id="a8077-144">This step describes how to create a relying party ASP.NET Web Forms application that will integrate with WIF.</span></span>  
  
### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="a8077-145">Pour créer une application ASP.NET simple</span><span class="sxs-lookup"><span data-stu-id="a8077-145">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="a8077-146">Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.</span><span class="sxs-lookup"><span data-stu-id="a8077-146">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="a8077-147">Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web Forms ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="a8077-147">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="a8077-148">Dans **Nom**, entrez `TestApp` et appuyez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a8077-148">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a><span data-ttu-id="a8077-149">Étape 3 : activer le service STS de développement local pour authentifier les utilisateurs</span><span class="sxs-lookup"><span data-stu-id="a8077-149">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
 <span data-ttu-id="a8077-150">Cette étape décrit comment activer le service STS de développement local dans votre application.</span><span class="sxs-lookup"><span data-stu-id="a8077-150">This step describes how to enable Local Development STS in your application.</span></span> <span data-ttu-id="a8077-151">Le service STS de développement local est activé à l’aide de l’extension Identity and Access Tool pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a8077-151">Local Development STS is enabled by using the Identity and Access extension for Visual Studio.</span></span>  
  
### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a><span data-ttu-id="a8077-152">Pour activer le service STS de développement local dans votre application ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a8077-152">To enable Local Development STS in your ASP.NET application</span></span>  
  
1. <span data-ttu-id="a8077-153">Dans Visual Studio, cliquez avec le bouton droit sur le projet **TestApp** sous l’**Explorateur de solutions**, puis sélectionnez **Identity and Access** (Identity and Access Tool).</span><span class="sxs-lookup"><span data-stu-id="a8077-153">In Visual Studio, right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
2. <span data-ttu-id="a8077-154">La fenêtre **Identity and Access** (Identity and Access Tool) s’affiche.</span><span class="sxs-lookup"><span data-stu-id="a8077-154">The **Identity and Access** window appears.</span></span> <span data-ttu-id="a8077-155">Sous **Fournisseurs**, sélectionnez **Test your application with the Local Development STS** (Tester votre application avec le service STS de développement local), puis cliquez sur **Appliquer**.</span><span class="sxs-lookup"><span data-stu-id="a8077-155">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a><span data-ttu-id="a8077-156">Étape 4 : modifier votre application ASP.NET pour afficher l’état de connexion</span><span class="sxs-lookup"><span data-stu-id="a8077-156">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
 <span data-ttu-id="a8077-157">Cette étape explique comment modifier votre application ASP.NET afin d’indiquer dynamiquement si l’utilisateur actuel est connecté.</span><span class="sxs-lookup"><span data-stu-id="a8077-157">This step describes how to modify your ASP.NET application to dynamically display whether the current user is signed in.</span></span> <span data-ttu-id="a8077-158">Une fois que votre fournisseur STS a été configuré, WIF traite les revendications entrantes.</span><span class="sxs-lookup"><span data-stu-id="a8077-158">Once your STS provider has been configured, WIF handles the incoming claims.</span></span> <span data-ttu-id="a8077-159">Vous devez maintenant configurer le code de votre application pour afficher le résultat de l’authentification.</span><span class="sxs-lookup"><span data-stu-id="a8077-159">Now you need to configure your application’s code to display the result of the authentication.</span></span>  
  
### <a name="to-display-sign-in-status"></a><span data-ttu-id="a8077-160">Pour afficher l’état de connexion</span><span class="sxs-lookup"><span data-stu-id="a8077-160">To display sign in status</span></span>  
  
1. <span data-ttu-id="a8077-161">Dans Visual Studio, ouvrez le fichier **Default.aspx** sous le projet **TestApp**.</span><span class="sxs-lookup"><span data-stu-id="a8077-161">In Visual Studio, open the **Default.aspx** file under the **TestApp** project.</span></span>  
  
2. <span data-ttu-id="a8077-162">Remplacez le balisage existant dans le fichier **Default.aspx** par le balisage suivant :</span><span class="sxs-lookup"><span data-stu-id="a8077-162">Replace the existing markup in the **Default.aspx** file with the following markup:</span></span>  
  
    ```  
    <%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head runat="server">  
        <title>Logged In Status</title>  
    </head>  
    <body>  
        <asp:label ID="myLabel" runat="server" />  
    </body>  
    </html>  
    ```  
  
3. <span data-ttu-id="a8077-163">Enregistrez **Default.aspx**, puis ouvrez son fichier code-behind nommé **Default.aspx.cs**.</span><span class="sxs-lookup"><span data-stu-id="a8077-163">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a8077-164">**Default.aspx.cs** peut être masqué sous **Default.aspx** dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="a8077-164">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="a8077-165">Si **Default.aspx.cs** n’est pas visible, développez **Default.aspx** en cliquant sur le triangle en regard de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="a8077-165">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
4. <span data-ttu-id="a8077-166">Remplacez le code existant dans **Default.aspx.cs** par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="a8077-166">Replace the existing code in **Default.aspx.cs** with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        protected void Page_Load(object sender, EventArgs e)  
        {  
            ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
            if (claimsPrincipal != null)  
            {  
                myLabel.Text = "You are signed in.";  
            }  
            else  
            {  
                myLabel.Text = "You are not signed in.";  
            }  
        }  
    }  
    ```  
  
5. <span data-ttu-id="a8077-167">Enregistrez **Default.aspx.cs** et générez l’application.</span><span class="sxs-lookup"><span data-stu-id="a8077-167">Save **Default.aspx.cs**, and build the application.</span></span>  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a><span data-ttu-id="a8077-168">Étape 5 : tester l’intégration entre WIF et votre application ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a8077-168">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
 <span data-ttu-id="a8077-169">Cette étape explique comment tester l’intégration entre WIF et votre application ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a8077-169">This step describes how you can test the integration between WIF and your ASP.NET application.</span></span>  
  
### <a name="to-test-the-integration-between-wif-and-aspnet"></a><span data-ttu-id="a8077-170">Pour tester l’intégration entre WIF et ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a8077-170">To test the integration between WIF and ASP.NET</span></span>  
  
1. <span data-ttu-id="a8077-171">Dans Visual Studio, appuyez sur **F5** pour démarrer le débogage de l’application.</span><span class="sxs-lookup"><span data-stu-id="a8077-171">In Visual Studio, press **F5** to start debugging your application.</span></span> <span data-ttu-id="a8077-172">Si aucune erreur n’est trouvée, une nouvelle fenêtre de navigateur s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="a8077-172">If no errors are found, a new browser window will open.</span></span>  
  
2. <span data-ttu-id="a8077-173">Vous pouvez remarquer que le navigateur redirige en mode silencieux votre demande vers le service STS, puis ouvre la page Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="a8077-173">You may notice that the browser silently redirects your request to the STS, and then opens the Default.aspx page.</span></span> <span data-ttu-id="a8077-174">Si WIF est correctement configuré, le site doit afficher le texte suivant: **«Vous êtes connecté»** .</span><span class="sxs-lookup"><span data-stu-id="a8077-174">If WIF is properly configured, you should see the site display the following text: **"You are signed in"**.</span></span>
