---
title: 'Procédure : Transformer les revendications entrantes'
ms.date: 03/30/2017
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
author: BrucePerlerMS
ms.openlocfilehash: ce99b97007bf7608856345d6da87cd9e422d2266
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041478"
---
# <a name="how-to-transform-incoming-claims"></a><span data-ttu-id="bbf3f-102">Procédure : Transformer les revendications entrantes</span><span class="sxs-lookup"><span data-stu-id="bbf3f-102">How To: Transform Incoming Claims</span></span>

## <a name="applies-to"></a><span data-ttu-id="bbf3f-103">S'applique à</span><span class="sxs-lookup"><span data-stu-id="bbf3f-103">Applies To</span></span>

- <span data-ttu-id="bbf3f-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="bbf3f-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>

- <span data-ttu-id="bbf3f-105">Web Forms ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="bbf3f-105">ASP.NET® Web Forms</span></span>

## <a name="summary"></a><span data-ttu-id="bbf3f-106">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="bbf3f-106">Summary</span></span>

<span data-ttu-id="bbf3f-107">Cette procédure fournit des procédures pas à pas détaillées pour créer une application Web Forms ASP.NET simple prenant en charge les revendications et pour transformer les revendications entrantes.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application and transforming incoming claims.</span></span> <span data-ttu-id="bbf3f-108">Elle fournit également des instructions pour tester l’application afin de vérifier que les revendications transformées sont présentées au moment de l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-108">It also provides instructions for how to test the application to verify that transformed claims are presented when the application is run.</span></span>

## <a name="contents"></a><span data-ttu-id="bbf3f-109">Sommaire</span><span class="sxs-lookup"><span data-stu-id="bbf3f-109">Contents</span></span>

- <span data-ttu-id="bbf3f-110">Objectifs</span><span class="sxs-lookup"><span data-stu-id="bbf3f-110">Objectives</span></span>

- <span data-ttu-id="bbf3f-111">Présentation</span><span class="sxs-lookup"><span data-stu-id="bbf3f-111">Overview</span></span>

- <span data-ttu-id="bbf3f-112">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="bbf3f-112">Summary of Steps</span></span>

- <span data-ttu-id="bbf3f-113">Étape 1 : Créer une application Web Forms ASP.NET simple</span><span class="sxs-lookup"><span data-stu-id="bbf3f-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="bbf3f-114">Étape 2 : Implémenter la transformation des revendications à l’aide d’un ClaimsAuthenticationManager personnalisé</span><span class="sxs-lookup"><span data-stu-id="bbf3f-114">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>

- <span data-ttu-id="bbf3f-115">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="bbf3f-115">Step 3 – Test Your Solution</span></span>

## <a name="objectives"></a><span data-ttu-id="bbf3f-116">Objectifs</span><span class="sxs-lookup"><span data-stu-id="bbf3f-116">Objectives</span></span>

- <span data-ttu-id="bbf3f-117">Configurer une application Web Forms ASP.NET pour l’authentification basée sur les revendications</span><span class="sxs-lookup"><span data-stu-id="bbf3f-117">Configure an ASP.NET Web Forms application for claims-based authentication</span></span>

- <span data-ttu-id="bbf3f-118">Transformer les revendications entrantes en ajoutant une revendication de rôle d’administrateur (Administrator)</span><span class="sxs-lookup"><span data-stu-id="bbf3f-118">Transform incoming claims by adding an Administrator role claim</span></span>

- <span data-ttu-id="bbf3f-119">Tester l’application Web Forms ASP.NET pour vérifier si elle fonctionne correctement</span><span class="sxs-lookup"><span data-stu-id="bbf3f-119">Test the ASP.NET Web Forms application to see if it is working properly</span></span>

## <a name="overview"></a><span data-ttu-id="bbf3f-120">Présentation</span><span class="sxs-lookup"><span data-stu-id="bbf3f-120">Overview</span></span>

<span data-ttu-id="bbf3f-121">WIF expose une classe nommée <xref:System.Security.Claims.ClaimsAuthenticationManager> qui permet aux utilisateurs de modifier les revendications avant leur présentation à une application par partie de confiance.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-121">WIF exposes a class named <xref:System.Security.Claims.ClaimsAuthenticationManager> that enables users to modify claims before they are presented to a relying party (RP) application.</span></span> <span data-ttu-id="bbf3f-122">La classe <xref:System.Security.Claims.ClaimsAuthenticationManager> est utile pour la séparation des responsabilités entre l’authentification et le code d’application sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-122">The <xref:System.Security.Claims.ClaimsAuthenticationManager> is useful for separation of concerns between authentication and the underlying application code.</span></span> <span data-ttu-id="bbf3f-123">L’exemple ci-dessous montre comment ajouter un rôle aux revendications dans le principal <xref:System.Security.Claims.ClaimsPrincipal> entrant quand il est requis par l’application par partie de confiance.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-123">The example below demonstrates how to add a role to the claims in the incoming <xref:System.Security.Claims.ClaimsPrincipal> that may be required by the RP.</span></span>

## <a name="summary-of-steps"></a><span data-ttu-id="bbf3f-124">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="bbf3f-124">Summary of Steps</span></span>

- <span data-ttu-id="bbf3f-125">Étape 1 : Créer une application Web Forms ASP.NET simple</span><span class="sxs-lookup"><span data-stu-id="bbf3f-125">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="bbf3f-126">Étape 2 : Implémenter la transformation des revendications à l’aide d’un ClaimsAuthenticationManager personnalisé</span><span class="sxs-lookup"><span data-stu-id="bbf3f-126">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>

- <span data-ttu-id="bbf3f-127">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="bbf3f-127">Step 3 – Test Your Solution</span></span>

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="bbf3f-128">Étape 1 : Créer une application Web Forms ASP.NET simple</span><span class="sxs-lookup"><span data-stu-id="bbf3f-128">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

<span data-ttu-id="bbf3f-129">Lors de cette étape, vous allez créer une application Web Forms ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-129">In this step, you will create a new ASP.NET Web Forms application.</span></span>

#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="bbf3f-130">Pour créer une application ASP.NET simple</span><span class="sxs-lookup"><span data-stu-id="bbf3f-130">To create a simple ASP.NET application</span></span>

1. <span data-ttu-id="bbf3f-131">Démarrez Visual Studio en mode élevé en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-131">Start Visual Studio in elevated mode as administrator.</span></span>

2. <span data-ttu-id="bbf3f-132">Dans Visual Studio, cliquez sur **Fichier**, sur **Nouveau**, puis sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-132">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="bbf3f-133">Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web Forms ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>

4. <span data-ttu-id="bbf3f-134">Dans **Nom**, entrez `TestApp` et appuyez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-134">In **Name**, enter `TestApp` and press **OK**.</span></span>

5. <span data-ttu-id="bbf3f-135">Cliquez avec le bouton droit sur le projet **TestApp** sous l’**Explorateur de solutions**, puis sélectionnez **Identity and Access** (Identity and Access Tool).</span><span class="sxs-lookup"><span data-stu-id="bbf3f-135">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>

6. <span data-ttu-id="bbf3f-136">La fenêtre **Identity and Access** (Identity and Access Tool) s’affiche.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-136">The **Identity and Access** window appears.</span></span> <span data-ttu-id="bbf3f-137">Sous **Fournisseurs**, sélectionnez **Test your application with the Local Development STS** (Tester votre application avec le service STS de développement local), puis cliquez sur **Appliquer**.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-137">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>

7. <span data-ttu-id="bbf3f-138">Dans le fichier *Default.aspx*, remplacez le balisage existant par le code suivant, puis enregistrez le fichier :</span><span class="sxs-lookup"><span data-stu-id="bbf3f-138">In the *Default.aspx* file, replace the existing markup with the following, then save the file:</span></span>

    ```aspx-csharp
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>

    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">
          <h3>Your Claims</h3>
        <p>
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">
                <AlternatingRowStyle BackColor="White" />
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />
            </asp:GridView>
        </p>
    </asp:Content>
    ```

8. <span data-ttu-id="bbf3f-139">Ouvrez le fichier code-behind nommé *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-139">Open the code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="bbf3f-140">Remplacez le code existant par celui qui suit, puis enregistrez le fichier :</span><span class="sxs-lookup"><span data-stu-id="bbf3f-140">Replace the existing code with the following, then save the file:</span></span>

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

## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="bbf3f-141">Étape 2 : Implémenter la transformation des revendications à l’aide d’un ClaimsAuthenticationManager personnalisé</span><span class="sxs-lookup"><span data-stu-id="bbf3f-141">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>

<span data-ttu-id="bbf3f-142">Dans cette étape, vous allez substituer les fonctionnalités par défaut dans la classe <xref:System.Security.Claims.ClaimsAuthenticationManager> pour ajouter un rôle d’administrateur (Administrator) au principal entrant.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-142">In this step you will override default functionality in the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to add an Administrator role to the incoming Principal.</span></span>

#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="bbf3f-143">Pour implémenter la transformation des revendications à l’aide d’un ClaimsAuthenticationManager personnalisé</span><span class="sxs-lookup"><span data-stu-id="bbf3f-143">To implement claims transformation using a custom ClaimsAuthenticationManager</span></span>

1. <span data-ttu-id="bbf3f-144">Dans Visual Studio, cliquez avec le bouton droit sur la solution, cliquez sur **Ajouter**, puis cliquez sur **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-144">In Visual Studio, right-click the on the solution, click **Add**, and then click **New Project**.</span></span>

2. <span data-ttu-id="bbf3f-145">Dans la fenêtre **Ajouter un nouveau projet**, sélectionnez **Bibliothèque de classes** dans la liste de modèles **Visual C#** , entrez `ClaimsTransformation`, puis appuyez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-145">In the **Add New Project** window, select **Class Library** from the **Visual C#** templates list, enter `ClaimsTransformation`, and then press **OK**.</span></span> <span data-ttu-id="bbf3f-146">Le nouveau projet est créé dans votre dossier de solutions.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-146">The new project will be created in your solution folder.</span></span>

3. <span data-ttu-id="bbf3f-147">Cliquez avec le bouton droit sur **Références** sous le projet **ClaimsTransformation**, puis cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-147">Right-click on **References** under the **ClaimsTransformation** project, and then click **Add Reference**.</span></span>

4. <span data-ttu-id="bbf3f-148">Dans la fenêtre **Gestionnaire de références**, sélectionnez **System.IdentityModel**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-148">In the **Reference Manager** window, select **System.IdentityModel**, and then click **OK**.</span></span>

5. <span data-ttu-id="bbf3f-149">Ouvrez **Class1.cs**. Si cette classe n’existe pas, cliquez avec le bouton droit sur **ClaimsTransformation**, cliquez sur **Ajouter** et cliquez sur **Classe...**</span><span class="sxs-lookup"><span data-stu-id="bbf3f-149">Open **Class1.cs**, or if it doesn’t exist, right-click **ClaimsTransformation**, click **Add**, then click **Class…**</span></span>

6. <span data-ttu-id="bbf3f-150">Ajoutez le code suivant à l’aide de directives dans le fichier de code :</span><span class="sxs-lookup"><span data-stu-id="bbf3f-150">Add the following using directives to the code file:</span></span>

    ```csharp
    using System.Security.Claims;
    using System.Security.Principal;
    ```

7. <span data-ttu-id="bbf3f-151">Ajoutez la classe et la méthode suivantes dans le fichier de code.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-151">Add the following class and method in the code file.</span></span>

    > [!WARNING]
    > <span data-ttu-id="bbf3f-152">Le code suivant est fourni à titre de démonstration uniquement. Vérifiez les autorisations prévues dans votre code de production.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-152">The following code is for demonstration purposes only; make sure that you verify your intended permissions in production code.</span></span>

    ```csharp
    public class ClaimsTransformationModule : ClaimsAuthenticationManager
    {
        public override ClaimsPrincipal Authenticate(string resourceName, ClaimsPrincipal incomingPrincipal)
        {
            if (incomingPrincipal != null && incomingPrincipal.Identity.IsAuthenticated == true)
            {
               ((ClaimsIdentity)incomingPrincipal.Identity).AddClaim(new Claim(ClaimTypes.Role, "Admin"));
            }

            return incomingPrincipal;
        }
    }
    ```

8. <span data-ttu-id="bbf3f-153">Enregistrez le fichier et générez le projet **ClaimsTransformation**.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-153">Save the file and build the **ClaimsTransformation** project.</span></span>

9. <span data-ttu-id="bbf3f-154">Dans votre projet **TestApp** ASP.NET, cliquez avec le bouton droit sur Références, puis cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-154">In your **TestApp** ASP.NET project, right-click on References, and then click **Add Reference**.</span></span>

10. <span data-ttu-id="bbf3f-155">Dans la fenêtre **Gestionnaire de références**, sélectionnez **Solution** dans le menu de gauche, sélectionnez **ClaimsTransformation** dans les options remplies, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-155">In the **Reference Manager** window, select **Solution** from the left menu, select **ClaimsTransformation** from the populated options, and then click **OK**.</span></span>

11. <span data-ttu-id="bbf3f-156">Dans le fichier racine **Web.config**, accédez à l’entrée **\<system.identityModel>** .</span><span class="sxs-lookup"><span data-stu-id="bbf3f-156">In the root **Web.config** file, navigate to the **\<system.identityModel>** entry.</span></span> <span data-ttu-id="bbf3f-157">Dans les éléments **\<identityConfiguration>** , ajoutez la ligne suivante, puis enregistrez le fichier :</span><span class="sxs-lookup"><span data-stu-id="bbf3f-157">Within the **\<identityConfiguration>** elements, add the following line and save the file:</span></span>

    ```xml
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />
    ```

## <a name="step-3--test-your-solution"></a><span data-ttu-id="bbf3f-158">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="bbf3f-158">Step 3 – Test Your Solution</span></span>

<span data-ttu-id="bbf3f-159">Dans cette étape, vous allez tester votre application Web Forms ASP.NET et vérifier que les revendications sont présentées à l’utilisateur qui se connecte à l’aide de l’authentification par formulaire.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-159">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>

#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="bbf3f-160">Pour tester votre application Web Forms ASP.NET pour les revendications à l’aide de l’authentification par formulaire</span><span class="sxs-lookup"><span data-stu-id="bbf3f-160">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>

1. <span data-ttu-id="bbf3f-161">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-161">Press **F5** to build and run the application.</span></span> <span data-ttu-id="bbf3f-162">La page *Default.aspx* doit s’afficher.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-162">You should be presented with *Default.aspx*.</span></span>

2. <span data-ttu-id="bbf3f-163">Dans la page *Default.aspx*, sous l’en-tête **Your Claims** (Vos revendications), vous voyez normalement un tableau qui affiche ces informations sur les revendications associées à votre compte : **Issuer**, **OriginalIssuer**, **Type**, **Value** et **ValueType**.</span><span class="sxs-lookup"><span data-stu-id="bbf3f-163">On the *Default.aspx* page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span> <span data-ttu-id="bbf3f-164">La dernière ligne doit se présenter de cette façon :</span><span class="sxs-lookup"><span data-stu-id="bbf3f-164">The last row should be presented in the following way:</span></span>

    ||||||
    |-|-|-|-|-|
    |<span data-ttu-id="bbf3f-165">LOCAL AUTHORITY</span><span class="sxs-lookup"><span data-stu-id="bbf3f-165">LOCAL AUTHORITY</span></span>|<span data-ttu-id="bbf3f-166">LOCAL AUTHORITY</span><span class="sxs-lookup"><span data-stu-id="bbf3f-166">LOCAL AUTHORITY</span></span>|`http://schemas.microsoft.com/ws/2008/06/identity/claims/role`|<span data-ttu-id="bbf3f-167">Admin</span><span class="sxs-lookup"><span data-stu-id="bbf3f-167">Admin</span></span>|<https://www.w3.org/2001/XMLSchema#string>|
