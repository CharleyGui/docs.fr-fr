---
title: 'Procédure : Activer WIF pour une application de service web WCF'
ms.date: 03/30/2017
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
author: BrucePerlerMS
ms.openlocfilehash: 809009642caf743f4f067591adfa63ccb154a577
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851532"
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a><span data-ttu-id="c3ea5-102">Procédure : Activer WIF pour une application de service web WCF</span><span class="sxs-lookup"><span data-stu-id="c3ea5-102">How To: Enable WIF for a WCF Web Service Application</span></span>
## <a name="applies-to"></a><span data-ttu-id="c3ea5-103">S'applique à</span><span class="sxs-lookup"><span data-stu-id="c3ea5-103">Applies To</span></span>

- <span data-ttu-id="c3ea5-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="c3ea5-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>

- <span data-ttu-id="c3ea5-105">Microsoft® Windows® Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="c3ea5-105">Microsoft® Windows® Communication Foundation (WCF)</span></span>

## <a name="summary"></a><span data-ttu-id="c3ea5-106">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="c3ea5-106">Summary</span></span>

<span data-ttu-id="c3ea5-107">Cette procédure fournit des informations détaillées pour activer WIF dans un service Web WCF.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-107">This How-To provides detailed step-by-step procedures for enabling WIF in a WCF web service.</span></span> <span data-ttu-id="c3ea5-108">Elle fournit également des instructions décrivant comment tester l'application pour vérifier que le service Web répertorie correctement les revendications lorsque l'application est exécutée.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-108">It also provides instructions for how to test the application to verify that the web service is correctly presenting claims when the application is run.</span></span> <span data-ttu-id="c3ea5-109">Cette procédure ne fournit pas d'instructions détaillées pour créer un service d'émission de jeton de sécurité (STS, Security Token Service), et utilise à la place le développement STS fourni avec l'outil Identité et accès.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="c3ea5-110">Le développement STS n'exécute de véritable authentification et est destiné à des fins de test uniquement.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="c3ea5-111">Vous devez installer l'outil Identité et accès pour exécuter cette procédure.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="c3ea5-112">Il peut être téléchargé à partir de l’emplacement suivant : [Outil identité et accès](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="c3ea5-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>

## <a name="contents"></a><span data-ttu-id="c3ea5-113">Sommaire</span><span class="sxs-lookup"><span data-stu-id="c3ea5-113">Contents</span></span>

- <span data-ttu-id="c3ea5-114">Objectifs</span><span class="sxs-lookup"><span data-stu-id="c3ea5-114">Objectives</span></span>

- <span data-ttu-id="c3ea5-115">Présentation</span><span class="sxs-lookup"><span data-stu-id="c3ea5-115">Overview</span></span>

- <span data-ttu-id="c3ea5-116">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="c3ea5-116">Summary of Steps</span></span>

- <span data-ttu-id="c3ea5-117">Étape 1 : créer un service WCF simple</span><span class="sxs-lookup"><span data-stu-id="c3ea5-117">Step 1 – Create a Simple WCF Service</span></span>

- <span data-ttu-id="c3ea5-118">Étape 2 : créer une application cliente pour le service WCF</span><span class="sxs-lookup"><span data-stu-id="c3ea5-118">Step 2 – Create a Client Application for the WCF Service</span></span>

- <span data-ttu-id="c3ea5-119">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="c3ea5-119">Step 3 – Test Your Solution</span></span>

## <a name="objectives"></a><span data-ttu-id="c3ea5-120">Objectifs</span><span class="sxs-lookup"><span data-stu-id="c3ea5-120">Objectives</span></span>

- <span data-ttu-id="c3ea5-121">Créer un service WCF qui requiert des jetons émis</span><span class="sxs-lookup"><span data-stu-id="c3ea5-121">Create a WCF service that requires issued tokens</span></span>

- <span data-ttu-id="c3ea5-122">Créer un client WCF qui demande un jeton à partir de STS et le transmet au service WCF</span><span class="sxs-lookup"><span data-stu-id="c3ea5-122">Create a WCF client that requests a token from an STS and passes it to the WCF service</span></span>

## <a name="overview"></a><span data-ttu-id="c3ea5-123">Présentation</span><span class="sxs-lookup"><span data-stu-id="c3ea5-123">Overview</span></span>

<span data-ttu-id="c3ea5-124">Cette procédure est destinée à montrer comment un développeur peut utiliser l'authentification fédérée lors du développement des services WCF.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-124">This How-To is intended to demonstrate how a developer can use federated authentication when developing WCF services.</span></span> <span data-ttu-id="c3ea5-125">Parmi les avantages de l'utilisation de la fédération dans des services WCF, on trouve :</span><span class="sxs-lookup"><span data-stu-id="c3ea5-125">Some of the benefits of using federation in WCF services include:</span></span>

1. <span data-ttu-id="c3ea5-126">Factoriser la logique d'identification hors du code de service WCF</span><span class="sxs-lookup"><span data-stu-id="c3ea5-126">Factoring authentication logic out of WCF service code</span></span>

2. <span data-ttu-id="c3ea5-127">Réutiliser des solutions existantes de gestion des identités</span><span class="sxs-lookup"><span data-stu-id="c3ea5-127">Re-using existing identity management solutions</span></span>

3. <span data-ttu-id="c3ea5-128">Interopérabilité avec d'autres solutions d'identité</span><span class="sxs-lookup"><span data-stu-id="c3ea5-128">Interoperability with other identity solutions</span></span>

4. <span data-ttu-id="c3ea5-129">Souplesse et résilience des futures modifications</span><span class="sxs-lookup"><span data-stu-id="c3ea5-129">Flexibility and resilience to future changes</span></span>

<span data-ttu-id="c3ea5-130">WIF associé à l'outil Identité et accès facilite le développement et le test d'un service WCF à l'aide de l'authentification fédérée, comme illustré dans les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-130">WIF and the associated Identity and Access tool make it easier to develop and test a WCF service using federated authentication, as the following steps demonstrate.</span></span>

## <a name="summary-of-steps"></a><span data-ttu-id="c3ea5-131">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="c3ea5-131">Summary of Steps</span></span>

- <span data-ttu-id="c3ea5-132">Étape 1 : créer un service WCF simple</span><span class="sxs-lookup"><span data-stu-id="c3ea5-132">Step 1 – Create a Simple WCF Service</span></span>

- <span data-ttu-id="c3ea5-133">Étape 2 : créer une application cliente pour le service WCF</span><span class="sxs-lookup"><span data-stu-id="c3ea5-133">Step 2 – Create a Client Application for the WCF Service</span></span>

- <span data-ttu-id="c3ea5-134">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="c3ea5-134">Step 3 – Test Your Solution</span></span>

## <a name="step-1--create-a-simple-wcf-service"></a><span data-ttu-id="c3ea5-135">Étape 1 : créer un service WCF simple</span><span class="sxs-lookup"><span data-stu-id="c3ea5-135">Step 1 – Create a Simple WCF Service</span></span>

<span data-ttu-id="c3ea5-136">Dans cette étape, vous allez créer un service WCF qui utilise le développement STS inclus avec l'outil Identité et accès.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-136">In this step, you will create a new WCF service that uses the Development STS that is included with the Identity and Access tool.</span></span>

#### <a name="to-create-a-simple-wcf-service"></a><span data-ttu-id="c3ea5-137">Pour créer un service WCF simple</span><span class="sxs-lookup"><span data-stu-id="c3ea5-137">To create a simple WCF service</span></span>

1. <span data-ttu-id="c3ea5-138">Démarrez Visual Studio en mode élevé en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-138">Start Visual Studio in elevated mode as administrator.</span></span>

2. <span data-ttu-id="c3ea5-139">Dans Visual Studio, cliquez sur **Fichier**, sur **Nouveau**, puis sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-139">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="c3ea5-140">Dans la fenêtre **Nouveau projet**, cliquez sur **Application de service WCF**.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-140">In the **New Project** window, click **WCF Service Application**.</span></span>

4. <span data-ttu-id="c3ea5-141">Dans **Nom**, entrez `TestService` et appuyez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-141">In **Name**, enter `TestService` and press **OK**.</span></span>

5. <span data-ttu-id="c3ea5-142">Cliquez avec le bouton droit sur le projet **TestService** sous l’**Explorateur de solutions**, puis sélectionnez **Identity and Access** (Identity and Access Tool).</span><span class="sxs-lookup"><span data-stu-id="c3ea5-142">Right-click the **TestService** project under **Solution Explorer**, then select **Identity and Access**.</span></span>

6. <span data-ttu-id="c3ea5-143">La fenêtre **Identity and Access** (Identity and Access Tool) s’affiche.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-143">The **Identity and Access** window appears.</span></span> <span data-ttu-id="c3ea5-144">Sous **Fournisseurs**, sélectionnez **Test your application with the Local Development STS** (Tester votre application avec le service STS de développement local), puis cliquez sur **Appliquer**.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-144">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span> <span data-ttu-id="c3ea5-145">L’outil Identity and Access Tool configure le service pour utiliser WIF et pour externaliser l’authentification vers le service STS de développement local (**LocalSTS**) en ajoutant des éléments de configuration au fichier *Web.config*.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-145">The Identity and Access Tool configures the service to use WIF and to outsource authentication to the local development STS (**LocalSTS**) by adding configuration elements to the *Web.config* file.</span></span>

7. <span data-ttu-id="c3ea5-146">Dans le fichier *Service1.svc.cs*, ajoutez une directive `using` pour l’espace de noms **System.Security.Claims** et remplacez le code existant par le texte suivant, puis enregistrez le fichier :</span><span class="sxs-lookup"><span data-stu-id="c3ea5-146">In the *Service1.svc.cs* file, add a `using` directive for the **System.Security.Claims** namespace and replace the existing code with the following, then save the file:</span></span>

    ```csharp
    public class Service1 : IService1
    {
        public string ComputeResponse(string input)
        {
            // Get the caller's identity from ClaimsPrincipal.Current
            ClaimsPrincipal claimsPrincipal = OperationContext.Current.ClaimsPrincipal;

            // Start generating the output
            StringBuilder builder = new StringBuilder();
            builder.AppendLine("Computed by ClaimsAwareWebService");
            builder.AppendLine("Input received from client:" + input);

            if (claimsPrincipal != null)
            {
                // Display the claims from the caller. Do not use this code in a production application.
                ClaimsIdentity identity = claimsPrincipal.Identity as ClaimsIdentity;
                builder.AppendLine("Client Name:" + identity.Name);
                builder.AppendLine("IsAuthenticated:" + identity.IsAuthenticated);
                builder.AppendLine("The service received the following issued claims of the client:");

                // Iterate over the caller’s claims and append to the output
                foreach (Claim claim in claimsPrincipal.Claims)
                {
                    builder.AppendLine("ClaimType :" + claim.Type + "   ClaimValue:" + claim.Value);
                }
            }

            return builder.ToString();
        }
    }
    ```

    <span data-ttu-id="c3ea5-147">La méthode `ComputeResponse` affiche les propriétés des revendications émises par **LocalSTS**.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-147">The `ComputeResponse` method displays the properties of various claims that are issued by **LocalSTS**.</span></span>

8. <span data-ttu-id="c3ea5-148">Dans le fichier *IService1.cs*, remplacez le code existant par celui qui suit, puis enregistrez le fichier :</span><span class="sxs-lookup"><span data-stu-id="c3ea5-148">In the *IService1.cs* file, replace the existing code with the following, then save the file:</span></span>

    ```csharp
    [ServiceContract]
    public interface IService1
    {
        [OperationContract]
        string ComputeResponse(string input);
    }
    ```

9. <span data-ttu-id="c3ea5-149">Générez le projet.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-149">Build the project.</span></span>

10. <span data-ttu-id="c3ea5-150">Appuyez sur **Ctrl+F5** pour exécuter le service sans démarrer le débogueur.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-150">Press **Ctrl-F5** to run the service without starting the debugger.</span></span> <span data-ttu-id="c3ea5-151">Une page web doit s’ouvrir pour le service et vous pouvez vérifier que **LocalSTS** s’exécute en regardant dans la zone de notification (barre d’état système).</span><span class="sxs-lookup"><span data-stu-id="c3ea5-151">A Web page should open for the service and you can verify that **LocalSTS** is running by looking in the notification area (system tray).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="c3ea5-152">**TestService** et **LocalSTS** doivent s’exécuter quand vous ajoutez la référence de service à l’application cliente à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-152">Both **TestService** and **LocalSTS** must be running when you add the service reference to the client application in the next step.</span></span>

## <a name="step-2--create-a-client-application-for-the-wcf-service"></a><span data-ttu-id="c3ea5-153">Étape 2 : créer une application cliente pour le service WCF</span><span class="sxs-lookup"><span data-stu-id="c3ea5-153">Step 2 – Create a Client Application for the WCF Service</span></span>

<span data-ttu-id="c3ea5-154">Dans cette étape, vous allez créer une application console qui utilise le développement STS pour s'authentifier auprès du service WCF créé à l'étape précédente.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-154">In this step, you will create a console application that uses the Development STS to authenticate with the WCF service you created in the previous step.</span></span>

#### <a name="to-create-a-client-application"></a><span data-ttu-id="c3ea5-155">Pour créer une application cliente</span><span class="sxs-lookup"><span data-stu-id="c3ea5-155">To create a client application</span></span>

1. <span data-ttu-id="c3ea5-156">Dans Visual Studio, cliquez avec le bouton droit sur la solution, cliquez sur **Ajouter**, puis sur **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-156">In Visual Studio, right-click on the solution, click **Add**, and then click **New Project**.</span></span>

2. <span data-ttu-id="c3ea5-157">Dans la fenêtre **Ajouter un nouveau projet**, sélectionnez **Application console** dans la liste de modèles **Visual C#** , entrez `Client`, puis appuyez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-157">In the **Add New Project** window, select **Console Application** from the **Visual C#** templates list, enter `Client`, and then press **OK**.</span></span> <span data-ttu-id="c3ea5-158">Le nouveau projet est créé dans votre dossier de solutions.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-158">The new project will be created in your solution folder.</span></span>

3. <span data-ttu-id="c3ea5-159">Cliquez avec le bouton droit sur **Références** sous le projet **Client**, puis cliquez sur **Ajouter une référence de service**.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-159">Right-click on **References** under the **Client** project, and then click **Add Service Reference**.</span></span>

4. <span data-ttu-id="c3ea5-160">Dans la fenêtre **Ajouter une référence de service**, cliquez sur la flèche déroulante du bouton **Découvrir**, puis cliquez sur **Services dans la solution**.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-160">In the **Add Service Reference** window, click the drop-down arrow on the **Discover** button and click **Services in Solution**.</span></span> <span data-ttu-id="c3ea5-161">Le champ **Adresse** est automatiquement rempli avec le service WCF que vous avez créé précédemment, et le champ **Espace de noms** a la valeur **ServiceReference1**.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-161">The **Address** will automatically populate with the WCF service you created earlier, and the **Namespace** will be set to **ServiceReference1**.</span></span> <span data-ttu-id="c3ea5-162">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-162">Click **OK**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="c3ea5-163">**TestService** et **LocalSTS** doivent s’exécuter quand vous ajoutez la référence de service au client.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-163">Both **TestService** and **LocalSTS** must be running when you add the service reference to the client.</span></span>

5. <span data-ttu-id="c3ea5-164">Visual Studio génère des classes proxy pour le service WCF, et ajoute toutes les informations de référence nécessaires.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-164">Visual Studio will generate proxy classes for the WCF service, and add all of the necessary reference information.</span></span> <span data-ttu-id="c3ea5-165">Il ajoute également des éléments au fichier *App.config* pour configurer le client afin d’obtenir un jeton du service STS pour s’authentifier auprès du service.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-165">It will also add elements to the *App.config* file to configure the client to get a token from the STS to authenticate with the service.</span></span> <span data-ttu-id="c3ea5-166">Quand ce processus est terminé, le fichier **Program.cs** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-166">When this process is finished, the **Program.cs** file will open.</span></span> <span data-ttu-id="c3ea5-167">Ajoutez une directive `using` pour **System.ServiceModel** et une autre pour **Client.ServiceReference1**, remplacez la méthode **Main** par le code suivant, puis enregistrez le fichier :</span><span class="sxs-lookup"><span data-stu-id="c3ea5-167">Add a `using` directive for **System.ServiceModel** and another for **Client.ServiceReference1**, replace the **Main** method with the following code, then save the file:</span></span>

    ```csharp
    static void Main(string[] args)
    {
        // Create the client for the service
        Service1Client client = new Service1Client();
        Console.WriteLine("-------------WCF Client Application--------------\n");

        while (!ShouldQuitApplication())
        {
            try
            {
                Console.WriteLine(client.ComputeResponse("Hello World"));
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
                Console.WriteLine(e.StackTrace);
                Exception ex = e.InnerException;
                while (ex != null)
                {
                    Console.WriteLine("===========================");
                    Console.WriteLine(ex.Message);
                    Console.WriteLine(ex.StackTrace);
                    ex = ex.InnerException;
                }
            }
            catch (TimeoutException)
            {
                Console.WriteLine("Timed out...");
            }
            catch (Exception e)
            {
                Console.WriteLine("An unexpected exception occurred.");
                Console.WriteLine(e.StackTrace);
            }
        }

        client.Close();

        if (client != null)
        {
            client.Abort();
        }
    }

    static bool ShouldQuitApplication()
    {
        Console.WriteLine("---------------------------------------------------------------------");
        Console.WriteLine("Press Enter key to invoke service, any other key to quit application:");
        Console.WriteLine("----------------------------------------------------------------------");

        ConsoleKeyInfo keyInfo = Console.ReadKey();
        if (keyInfo.Key == ConsoleKey.Enter)
            return false;
        return true;
    }
    ```

6. <span data-ttu-id="c3ea5-168">Ouvrez le fichier *App.config* et ajoutez le code XML suivant comme premier élément enfant sous l’élément `<system.serviceModel>`, puis enregistrez le fichier :</span><span class="sxs-lookup"><span data-stu-id="c3ea5-168">Open the *App.config* file and add the following XML as the first child element under the `<system.serviceModel>` element, then save the file:</span></span>

    ```xml
    <behaviors>
       <endpointBehaviors>
         <behavior>
           <clientCredentials>
             <serviceCertificate>
               <authentication certificateValidationMode="None"/>
             </serviceCertificate>
           </clientCredentials>
         </behavior>
       </endpointBehaviors>
     </behaviors>
    ```

    <span data-ttu-id="c3ea5-169">Cela désactive la validation de certificat.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-169">This disables certificate validation.</span></span>

7. <span data-ttu-id="c3ea5-170">Cliquez avec le bouton droit sur la solution **TestService** et cliquez sur **Définir les projets de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-170">Right-click the **TestService** solution and click on **Set StartUp Projects**.</span></span> <span data-ttu-id="c3ea5-171">La page de propriétés de **Projet de démarrage** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-171">The **Startup Project** property page opens.</span></span> <span data-ttu-id="c3ea5-172">Dans la page de propriétés de **Projet de démarrage**, sélectionnez **Plusieurs projets de démarrage**, cliquez dans le champ **Action** pour chaque projet et sélectionnez **Démarrer** dans le menu déroulant.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-172">In the **Startup Project** property page, select **Multiple startup projects** then click in the **Action** field for each project and select **Start** from the drop-down menu.</span></span> <span data-ttu-id="c3ea5-173">Cliquez sur **OK** pour enregistrer les paramètres.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-173">Click **OK** to save the settings.</span></span>

8. <span data-ttu-id="c3ea5-174">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-174">Build the solution.</span></span>

## <a name="step-3--test-your-solution"></a><span data-ttu-id="c3ea5-175">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="c3ea5-175">Step 3 – Test Your Solution</span></span>

<span data-ttu-id="c3ea5-176">Dans cette étape, vous allez tester votre application WCF activée pour WIF et vérifier que les revendications sont présentées.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-176">In this step you will test your WIF-enabled WCF application and verify that claims are presented.</span></span>

#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a><span data-ttu-id="c3ea5-177">Pour tester votre application WCF activée pour WIF pour les revendications</span><span class="sxs-lookup"><span data-stu-id="c3ea5-177">To test your WIF-enabled WCF application for claims</span></span>

1. <span data-ttu-id="c3ea5-178">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-178">Press **F5** to build and run the application.</span></span> <span data-ttu-id="c3ea5-179">Une fenêtre de console et le texte suivant doivent s’affichent : **Appuyez sur la touche entrée pour appeler le service, toute autre clé pour quitter l’application :**</span><span class="sxs-lookup"><span data-stu-id="c3ea5-179">You should be presented with a console window, and the following text: **Press Enter key to invoke service, any other key to quit application:**</span></span>

2. <span data-ttu-id="c3ea5-180">Appuyez sur **Entrée** et les informations sur les revendications suivantes doivent apparaître dans la console :</span><span class="sxs-lookup"><span data-stu-id="c3ea5-180">Press **Enter**, and the following claims information should appear in the console:</span></span>

    ```output
    Computed by Service1
    Input received from client: Hello World
    Client Name: Terry
    IsAuthenticated: True
    The service received the following issued claims of the client:
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name    ClaimValue:Terry
    ClaimType :http://schema.xmlsoap.org/ws/2005/05/identity/claims/surname    ClaimValue:Adams
    ClaimType :http://schemas.microsoft.com/ws/2008/06/identity/claims/role    ClaimValue:developer
    ClaimType :http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress    ClaimValue:terry@contoso.com
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="c3ea5-181">**TestService** et **LocalSTS** doivent s’exécuter avant que vous n’appuyiez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-181">Both **TestService** and **LocalSTS** must be running before you press **Enter**.</span></span> <span data-ttu-id="c3ea5-182">Une page web doit s’ouvrir pour le service et vous pouvez vérifier que **LocalSTS** s’exécute en regardant dans la zone de notification (barre d’état système).</span><span class="sxs-lookup"><span data-stu-id="c3ea5-182">A Web page should open for the service and you can verify that **LocalSTS** is running by looking in the notification area (system tray).</span></span>

3. <span data-ttu-id="c3ea5-183">Si les revendications apparaissent dans la console, vous vous êtes correctement authentifié avec STS pour afficher les revendications du service WCF.</span><span class="sxs-lookup"><span data-stu-id="c3ea5-183">If these claims appear in the console, you have successfully authenticated with the STS to display claims from the WCF service.</span></span>
