---
title: 'Procédure : Activer WIF pour une application de service web WCF'
ms.date: 03/30/2017
ms.assetid: bfc64b3d-64e9-4093-a6a4-72e933917af7
author: BrucePerlerMS
ms.openlocfilehash: b9fa1f815a962adc0b3c91177021788734b92bb6
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041456"
---
# <a name="how-to-enable-wif-for-a-wcf-web-service-application"></a>Procédure : Activer WIF pour une application de service web WCF
## <a name="applies-to"></a>S'applique à

- Microsoft® Windows® Identity Foundation (WIF)

- Microsoft® Windows® Communication Foundation (WCF)

## <a name="summary"></a>Récapitulatif

Cette procédure fournit des informations détaillées pour activer WIF dans un service Web WCF. Elle fournit également des instructions décrivant comment tester l'application pour vérifier que le service Web répertorie correctement les revendications lorsque l'application est exécutée. Cette procédure ne fournit pas d'instructions détaillées pour créer un service d'émission de jeton de sécurité (STS, Security Token Service), et utilise à la place le développement STS fourni avec l'outil Identité et accès. Le développement STS n'exécute de véritable authentification et est destiné à des fins de test uniquement. Vous devez installer l'outil Identité et accès pour exécuter cette procédure. Il peut être téléchargé à partir de l’emplacement suivant: [Outil identité et accès](https://go.microsoft.com/fwlink/?LinkID=245849)

## <a name="contents"></a>Sommaire

- Objectifs

- Présentation

- Résumé des étapes

- Étape 1 : créer un service WCF simple

- Étape 2 : créer une application cliente pour le service WCF

- Étape 3 : tester votre solution

## <a name="objectives"></a>Objectifs

- Créer un service WCF qui requiert des jetons émis

- Créer un client WCF qui demande un jeton à partir de STS et le transmet au service WCF

## <a name="overview"></a>Présentation

Cette procédure est destinée à montrer comment un développeur peut utiliser l'authentification fédérée lors du développement des services WCF. Parmi les avantages de l'utilisation de la fédération dans des services WCF, on trouve :

1. Factoriser la logique d'identification hors du code de service WCF

2. Réutiliser des solutions existantes de gestion des identités

3. Interopérabilité avec d'autres solutions d'identité

4. Souplesse et résilience des futures modifications

WIF associé à l'outil Identité et accès facilite le développement et le test d'un service WCF à l'aide de l'authentification fédérée, comme illustré dans les étapes suivantes.

## <a name="summary-of-steps"></a>Résumé des étapes

- Étape 1 : créer un service WCF simple

- Étape 2 : créer une application cliente pour le service WCF

- Étape 3 : tester votre solution

## <a name="step-1--create-a-simple-wcf-service"></a>Étape 1 : créer un service WCF simple

Dans cette étape, vous allez créer un service WCF qui utilise le développement STS inclus avec l'outil Identité et accès.

#### <a name="to-create-a-simple-wcf-service"></a>Pour créer un service WCF simple

1. Démarrez Visual Studio en mode élevé en tant qu’administrateur.

2. Dans Visual Studio, cliquez sur **Fichier**, sur **Nouveau**, puis sur **Projet**.

3. Dans la fenêtre **Nouveau projet**, cliquez sur **Application de service WCF**.

4. Dans **Nom**, entrez `TestService` et appuyez sur **OK**.

5. Cliquez avec le bouton droit sur le projet **TestService** sous l’**Explorateur de solutions**, puis sélectionnez **Identity and Access** (Identity and Access Tool).

6. La fenêtre **Identity and Access** (Identity and Access Tool) s’affiche. Sous **Fournisseurs**, sélectionnez **Test your application with the Local Development STS** (Tester votre application avec le service STS de développement local), puis cliquez sur **Appliquer**. L’outil Identity and Access Tool configure le service pour utiliser WIF et pour externaliser l’authentification vers le service STS de développement local (**LocalSTS**) en ajoutant des éléments de configuration au fichier *Web.config*.

7. Dans le fichier *Service1.svc.cs*, ajoutez une directive `using` pour l’espace de noms **System.Security.Claims** et remplacez le code existant par le texte suivant, puis enregistrez le fichier :

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

    La méthode `ComputeResponse` affiche les propriétés des revendications émises par **LocalSTS**.

8. Dans le fichier *IService1.cs*, remplacez le code existant par celui qui suit, puis enregistrez le fichier :

    ```csharp
    [ServiceContract]
    public interface IService1
    {
        [OperationContract]
        string ComputeResponse(string input);
    }
    ```

9. Générez le projet.

10. Appuyez sur **Ctrl+F5** pour exécuter le service sans démarrer le débogueur. Une page web doit s’ouvrir pour le service et vous pouvez vérifier que **LocalSTS** s’exécute en regardant dans la zone de notification (barre d’état système).

    > [!IMPORTANT]
    > **TestService** et **LocalSTS** doivent s’exécuter quand vous ajoutez la référence de service à l’application cliente à l’étape suivante.

## <a name="step-2--create-a-client-application-for-the-wcf-service"></a>Étape 2 : créer une application cliente pour le service WCF

Dans cette étape, vous allez créer une application console qui utilise le développement STS pour s'authentifier auprès du service WCF créé à l'étape précédente.

#### <a name="to-create-a-client-application"></a>Pour créer une application cliente

1. Dans Visual Studio, cliquez avec le bouton droit sur la solution, cliquez sur **Ajouter**, puis sur **Nouveau projet**.

2. Dans la fenêtre **Ajouter un nouveau projet**, sélectionnez **Application console** dans la liste de modèles **Visual C#** , entrez `Client`, puis appuyez sur **OK**. Le nouveau projet est créé dans votre dossier de solutions.

3. Cliquez avec le bouton droit sur **Références** sous le projet **Client**, puis cliquez sur **Ajouter une référence de service**.

4. Dans la fenêtre **Ajouter une référence de service**, cliquez sur la flèche déroulante du bouton **Découvrir**, puis cliquez sur **Services dans la solution**. Le champ **Adresse** est automatiquement rempli avec le service WCF que vous avez créé précédemment, et le champ **Espace de noms** a la valeur **ServiceReference1**. Cliquez sur **OK**.

    > [!IMPORTANT]
    > **TestService** et **LocalSTS** doivent s’exécuter quand vous ajoutez la référence de service au client.

5. Visual Studio génère des classes proxy pour le service WCF, et ajoute toutes les informations de référence nécessaires. Il ajoute également des éléments au fichier *App.config* pour configurer le client afin d’obtenir un jeton du service STS pour s’authentifier auprès du service. Quand ce processus est terminé, le fichier **Program.cs** s’ouvre. Ajoutez une directive `using` pour **System.ServiceModel** et une autre pour **Client.ServiceReference1**, remplacez la méthode **Main** par le code suivant, puis enregistrez le fichier :

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

6. Ouvrez le fichier *App.config* et ajoutez le code XML suivant comme premier élément enfant sous l’élément `<system.serviceModel>`, puis enregistrez le fichier :

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

    Cela désactive la validation de certificat.

7. Cliquez avec le bouton droit sur la solution **TestService** et cliquez sur **Définir les projets de démarrage**. La page de propriétés de **Projet de démarrage** s’ouvre. Dans la page de propriétés de **Projet de démarrage**, sélectionnez **Plusieurs projets de démarrage**, cliquez dans le champ **Action** pour chaque projet et sélectionnez **Démarrer** dans le menu déroulant. Cliquez sur **OK** pour enregistrer les paramètres.

8. Générez la solution.

## <a name="step-3--test-your-solution"></a>Étape 3 : tester votre solution

Dans cette étape, vous allez tester votre application WCF activée pour WIF et vérifier que les revendications sont présentées.

#### <a name="to-test-your-wif-enabled-wcf-application-for-claims"></a>Pour tester votre application WCF activée pour WIF pour les revendications

1. Appuyez sur **F5** pour générer et exécuter l’application. Une fenêtre de console et le texte suivant doivent s’affichent: **Appuyez sur la touche entrée pour appeler le service, toute autre clé pour quitter l’application:**

2. Appuyez sur **Entrée** et les informations sur les revendications suivantes doivent apparaître dans la console :

    ```
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
    > **TestService** et **LocalSTS** doivent s’exécuter avant que vous n’appuyiez sur **Entrée**. Une page web doit s’ouvrir pour le service et vous pouvez vérifier que **LocalSTS** s’exécute en regardant dans la zone de notification (barre d’état système).

3. Si les revendications apparaissent dans la console, vous vous êtes correctement authentifié avec STS pour afficher les revendications du service WCF.
