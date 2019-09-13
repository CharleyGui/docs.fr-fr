---
title: 'Tutoriel : Héberger et exécuter un service de Windows Communication Foundation de base'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 984c5e73a8efc4e9c2d487485267868ffa2f60f3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928726"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>Tutoriel : Héberger et exécuter un service de Windows Communication Foundation de base

Ce didacticiel décrit la troisième des cinq tâches requises pour créer une application de base Windows Communication Foundation (WCF). Pour obtenir une vue d’ensemble des didacticiels, consultez [didacticiel : Prise en main des applications](getting-started-tutorial.md)Windows Communication Foundation.

La tâche suivante pour créer une application WCF consiste à héberger un service WCF dans une application console. Un service WCF expose un ou plusieurs *points de terminaison*, chacun d’entre eux exposant une ou plusieurs opérations de service. Un point de terminaison de service spécifie les informations suivantes :

- Adresse à laquelle vous pouvez trouver le service.
- Liaison qui contient les informations qui décrivent comment un client doit communiquer avec le service. 
- Contrat qui définit les fonctionnalités fournies par le service à ses clients.

Ce tutoriel vous montre comment effectuer les opérations suivantes :
> [!div class="checklist"]
>
> - Créez et configurez un projet d’application console pour l’hébergement d’un service WCF.
> - Ajoutez du code pour héberger le service WCF.
> - Mettez à jour le fichier de configuration.
> - Démarrez le service WCF et vérifiez qu’il est en cours d’exécution.

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>Créer et configurer un projet d’application console pour héberger le service

1. Créez un projet d’application console dans Visual Studio : 
 
    1. Dans le menu **fichier** , sélectionnez **ouvrir** > un**projet/une solution** , puis accédez à la solution **gettingstarted** que vous avez créée précédemment (*gettingstarted. sln*). Sélectionnez **Ouvrir**.

    2. Dans le menu **affichage** , sélectionnez **Explorateur de solutions**.
    
    3. Dans la fenêtre **Explorateur de solutions** , sélectionnez la solution **gettingstarted** (nœud supérieur), puis sélectionnez **Ajouter** > **un nouveau projet** dans le menu contextuel. 

    4. Dans la fenêtre **Ajouter un nouveau projet** , sur le côté gauche, sélectionnez la catégorie **Bureau Windows** sous  **C# Visual** ou **Visual Basic**. 

    5. Sélectionnez le modèle **application console (.NET Framework)** , puis entrez *GettingStartedHost* pour le **nom**. Sélectionnez **OK**.

2. Ajoutez une référence dans le projet **GettingStartedHost** au projet **GettingStartedLib** : 

    1. Dans la fenêtre **Explorateur de solutions** , sélectionnez le dossier **références** sous le projet **GettingStartedHost** , puis sélectionnez Ajouter une **référence** dans le menu contextuel. 

    2. Dans la boîte de dialogue **Ajouter une référence** , sous **projets** sur le côté gauche de la fenêtre, sélectionnez **solution**. 
 
    3. Sélectionnez **GettingStartedLib** dans la section centrale de la fenêtre, puis sélectionnez **OK**. 

       Cette action rend les types définis dans le projet **GettingStartedLib** disponibles pour le projet **GettingStartedHost** .

3. Ajoutez une référence dans le projet **GettingStartedHost** à l' <xref:System.ServiceModel> assembly : 

    1. Dans la fenêtre **Explorateur de solutions** , sélectionnez le dossier **références** sous le projet **GettingStartedHost** , puis sélectionnez Ajouter une **référence** dans le menu contextuel.
    
    2. Dans la fenêtre **Ajouter une référence** , sous **assemblys** sur le côté gauche de la fenêtre, sélectionnez **Framework**. 

    3. Sélectionnez **System. ServiceModel**, puis cliquez sur **OK**. 
    
    4. Enregistrez la solution en sélectionnant **fichier** > **enregistrer tout**.

## <a name="add-code-to-host-the-service"></a>Ajouter du code pour héberger le service

Pour héberger le service, vous ajoutez du code pour effectuer les étapes suivantes : 

1. Créez un URI pour l’adresse de base.
2. Créez une instance de classe pour héberger le service.
3. Créez un point de terminaison de service.
4. Activer l'échange de métadonnées.
5. Ouvrez l’hôte de service pour écouter les messages entrants.
  
Apportez les modifications suivantes au code:

1. Ouvrez le fichier **Program.cs** ou **Module1. vb** dans le projet **GettingStartedHost** et remplacez son code par le code suivant :

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using GettingStartedLib;

    namespace GettingStartedHost
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Step 1: Create a URI to serve as the base address.
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

                // Step 2: Create a ServiceHost instance.
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

                try
                {
                    // Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                    // Step 4: Enable metadata exchange.
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                    smb.HttpGetEnabled = true;
                    selfHost.Description.Behaviors.Add(smb)    ;

                    // Step 5: Start the service.
                    selfHost.Open();
                    Console.WriteLine("The service is ready.");

                    // Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.");
                    Console.WriteLine();
                    Console.ReadLine();
                    selfHost.Close();
                }
                catch (CommunicationException ce)
                {
                    Console.WriteLine("An exception occurred: {0}", ce.Message);
                    selfHost.Abort();
                }
            }
        }
    }
    ```

    ```vb
    Imports System.ServiceModel
    Imports System.ServiceModel.Description
    Imports GettingStartedLib.GettingStartedLib

    Module Service

        Class Program
            Shared Sub Main()
                ' Step 1: Create a URI to serve as the base address.
                Dim baseAddress As New Uri("http://localhost:8000/GettingStarted/")

                ' Step 2: Create a ServiceHost instance.
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
               Try

                    ' Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint( _
                        GetType(ICalculator), _
                        New WSHttpBinding(), _
                        "CalculatorService")

                    ' Step 4: Enable metadata exchange.
                    Dim smb As New ServiceMetadataBehavior()
                    smb.HttpGetEnabled = True
                    selfHost.Description.Behaviors.Add(smb)

                    ' Step 5: Start the service.
                    selfHost.Open()
                    Console.WriteLine("The service is ready.")

                    ' Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.")
                    Console.WriteLine()
                    Console.ReadLine()
                    selfHost.Close()

                Catch ce As CommunicationException
                    Console.WriteLine("An exception occurred: {0}", ce.Message)
                    selfHost.Abort()
                End Try
            End Sub
        End Class

    End Module
    ```
    
    Pour plus d’informations sur le fonctionnement de ce code, consultez [étapes du programme d’hébergement de services](#service-hosting-program-steps).

2. Mettez à jour les propriétés du projet :

   1. Dans la fenêtre **Explorateur de solutions** , sélectionnez le dossier **GettingStartedHost** , puis sélectionnez **Propriétés** dans le menu contextuel.

   2. Sur la page Propriétés de **GettingStartedHost** , sélectionnez l’onglet **application** :

      - Pour C# les projets, sélectionnez **GettingStartedHost. Program** dans la liste **objet de démarrage** .

      - Pour Visual Basic projets, sélectionnez **service. Program** dans la liste **objet de démarrage** .

   3. Dans le menu **fichier** , sélectionnez **enregistrer tout**.

## <a name="verify-the-service-is-working"></a>Vérifier que le service fonctionne

1. Générez la solution, puis exécutez l’application console **GettingStartedHost** à partir de Visual Studio. 

    Le service doit être exécuté avec des privilèges d’administrateur. Étant donné que vous avez ouvert Visual Studio avec des privilèges d’administrateur, lorsque vous exécutez **GettingStartedHost** dans Visual Studio, l’application est également exécutée avec des privilèges d’administrateur. Vous pouvez également ouvrir une nouvelle invite de commandes en tant qu’administrateur (sélectionnez **plus** > **exécuter en tant qu’administrateur** dans le menu contextuel) et exécutez **GettingStartedHost. exe** dans celui-ci.

2. Ouvrez un navigateur Web et accédez à la page du service à `http://localhost:8000/GettingStarted/CalculatorService`l’adresse.
   
   > [!NOTE]
   > Les services tels que celui-ci requièrent l’autorisation appropriée pour inscrire des adresses HTTP sur l’ordinateur pour l’écoute. Les comptes Administrateur possèdent cette autorisation, mais l'autorisation pour les espaces de noms HTTP doit être accordée aux comptes qui ne sont pas administrateur. Pour plus d’informations sur la configuration des réservations d’espaces de noms, consultez [Configuration de HTTP et HTTPS](feature-details/configuring-http-and-https.md). 

## <a name="service-hosting-program-steps"></a>Étapes du programme d’hébergement de service

Les étapes du code que vous avez ajouté pour héberger le service sont décrites comme suit :

- **Étape 1** : Créez une instance de la `Uri` classe pour contenir l’adresse de base du service. Une URL qui contient une adresse de base a un URI facultatif qui identifie un service. L’adresse de base est mise en forme `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`comme suit :. L’adresse de base pour le service de calculatrice utilise le transport HTTP, localhost, le port 8000 et le segment d’URI, GettingStarted.

- **Étape 2** : Créez une instance de la <xref:System.ServiceModel.ServiceHost> classe, que vous utilisez pour héberger le service. Le constructeur prend deux paramètres : le type de la classe qui implémente le contrat de service et l’adresse de base du service.

- **Étape 3** : Créez une instance <xref:System.ServiceModel.Description.ServiceEndpoint>. Un point de terminaison de service est composé d'une adresse, d'une liaison et d'un contrat de service. Le <xref:System.ServiceModel.Description.ServiceEndpoint> constructeur est composé du type d’interface de contrat de service, d’une liaison et d’une adresse. Le contrat de service est `ICalculator`, que vous définissez et implémentez dans le type de service. La liaison de cet exemple est <xref:System.ServiceModel.WSHttpBinding>, qui est une liaison intégrée et se connecte aux points de terminaison conformes aux spécifications WS-*. Pour plus d’informations sur les liaisons WCF, consultez [vue d’ensemble des liaisons WCF](bindings-overview.md). Vous ajoutez l’adresse à l’adresse de base pour identifier le point de terminaison. Le code spécifie l’adresse comme CalculatorService et l’adresse complète du point de terminaison `http://localhost:8000/GettingStarted/CalculatorService`en tant que.

    > [!IMPORTANT]
    > Pour .NET Framework version 4 et versions ultérieures, l’ajout d’un point de terminaison de service est facultatif. Pour ces versions, si vous n’ajoutez pas votre code ou votre configuration, WCF ajoute un point de terminaison par défaut pour chaque combinaison d’adresse de base et de contrat implémentée par le service. Pour plus d’informations sur les points de terminaison par défaut, consultez [spécification d’une adresse de point de terminaison](specifying-an-endpoint-address.md). Pour plus d’informations sur les points de terminaison, les liaisons et les comportements par défaut, consultez [configuration simplifiée](simplified-configuration.md) et [configuration simplifiée pour les services WCF](samples/simplified-configuration-for-wcf-services.md).

- **Étape 4** : Activer l'échange de métadonnées. Les clients utilisent l’échange de métadonnées pour générer des proxies afin d’appeler les opérations de service. Pour activer l’échange de métadonnées <xref:System.ServiceModel.Description.ServiceMetadataBehavior> , créez une instance <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> , affectez à `true`sa propriété `ServiceMetadataBehavior` la valeur et <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> ajoutez l’objet <xref:System.ServiceModel.ServiceHost> à la collection de l’instance.

- **Étape 5** : Ouvrir <xref:System.ServiceModel.ServiceHost> pour écouter les messages entrants. L’application attend que vous appuyiez sur **entrée**. Une fois l’application instanciée <xref:System.ServiceModel.ServiceHost>, elle exécute un bloc try/catch. Pour plus d’informations sur l’interception en toute sécurité <xref:System.ServiceModel.ServiceHost>des exceptions levées par, consultez la rubrique [utilisation de Close et Abort pour libérer des ressources clientes WCF](samples/use-close-abort-release-wcf-client-resources.md).

> [!IMPORTANT]
> Lorsque vous ajoutez une bibliothèque de service WCF, Visual Studio l’héberge pour vous si vous la déboguez en démarrant un hôte de service. Pour éviter les conflits, vous pouvez empêcher Visual Studio d’héberger la bibliothèque du service WCF. 
>
> 1. Sélectionnez le projet **GettingStartedLib** dans **Explorateur de solutions** , puis choisissez **Propriétés** dans le menu contextuel.
> 2. Sélectionnez **options WCF** et désactivez **Démarrer l’hôte de service WCF lors du débogage d’un autre projet dans la même solution**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez appris à :
> [!div class="checklist"]
>
> - Créez et configurez un projet d’application console pour l’hébergement d’un service WCF.
> - Ajoutez du code pour héberger le service WCF.
> - Mettez à jour le fichier de configuration.
> - Démarrez le service WCF et vérifiez qu’il est en cours d’exécution.

Passez au didacticiel suivant pour apprendre à créer un client WCF.

> [!div class="nextstepaction"]
> [Tutoriel : Créer un client WCF](how-to-create-a-wcf-client.md)
