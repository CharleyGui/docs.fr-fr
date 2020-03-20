---
title: 'Tutorial: Hébergez et exécutez un service de base de la Fondation De communication Windows'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 30eb86987b83427b94c6fff22755cde3d73dd9f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184082"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>Tutorial: Hébergez et exécutez un service de base de la Fondation De communication Windows

Ce tutoriel décrit la troisième des cinq tâches requises pour créer une application de base de la Windows Communication Foundation (WCF). Pour un aperçu des tutoriels, voir [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).

La prochaine tâche pour créer une application WCF est d’héberger un service WCF dans une application console. Un service WCF expose un ou plusieurs critères de *terminaison,* chacun d’eux qui expose une ou plusieurs opérations de service. Un critère de service spécifie les informations suivantes :

- Une adresse où vous pouvez trouver le service.
- Une liaison qui contient l’information qui décrit comment un client doit communiquer avec le service.
- Un contrat qui définit la fonctionnalité que le service fournit à ses clients.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> - Créez et configurez un projet d’application console pour l’hébergement d’un service WCF.
> - Ajoutez du code pour accueillir le service WCF.
> - Mettre à jour le fichier de configuration.
> - Démarrez le service WCF et vérifiez qu’il est en cours d’exécution.

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>Créer et configurer un projet d’application console pour l’hébergement du service

1. Créez un projet d’application console dans Visual Studio :

    1. Du menu **Fichier,** sélectionnez **Open** > **Project/Solution** et naviguez vers la solution **GettingStarted** que vous avez déjà créée (*GettingStarted.sln*). Sélectionnez **uvrir**.

    2. Du menu **View,** sélectionnez **Solution Explorer**.

    3. Dans la fenêtre **Solution Explorer,** sélectionnez la solution **GettingStarted** (nœud supérieur), puis **sélectionnez Ajouter** > **un nouveau projet** dans le menu raccourci.

    4. Dans la fenêtre **Add New Project,** sur le côté gauche, sélectionnez la catégorie **Windows Desktop** sous Visual **C ou** **Visual Basic**.

    5. Sélectionnez le modèle **Console App (.NET Framework)** et *entrez GettingStartedHost* pour le **nom**. Sélectionnez **OK**.

2. Ajoutez une référence dans le projet **GettingStartedHost** au projet **GettingStartedLib** :

    1. Dans la fenêtre **Solution Explorer,** sélectionnez le dossier **Références** dans le cadre du projet **GettingStartedHost,** puis **sélectionnez Ajouter la référence** dans le menu raccourci.

    2. Dans le dialogue **Add Reference,** dans le cadre **de Projets** sur le côté gauche de la fenêtre, sélectionnez **Solution**.

    3. Sélectionnez **GettingStartedLib** dans la section centrale de la fenêtre, puis sélectionnez **OK**.

       Cette action met les types définis dans le projet **GettingStartedLib** à la disposition du projet **GettingStartedHost.**

3. Ajoutez une référence dans le projet **GettingStartedHost** à l’assemblage <xref:System.ServiceModel> :

    1. Dans la fenêtre **Solution Explorer,** sélectionnez le dossier **Références** dans le cadre du projet **GettingStartedHost,** puis **sélectionnez Ajouter la référence** dans le menu raccourci.

    2. Dans la fenêtre **Add Reference,** sous **les assemblées** sur le côté gauche de la fenêtre, sélectionnez **Cadre**.

    3. Sélectionnez **System.ServiceModel**, puis sélectionnez **OK**.

    4. Enregistrer la solution en sélectionnant **File** > **Save All**.

## <a name="add-code-to-host-the-service"></a>Ajouter du code pour héberger le service

Pour accueillir le service, vous ajoutez du code pour faire les étapes suivantes :

1. Créez un URI pour l’adresse de base.
2. Créez un exemple de classe pour l’hébergement du service.
3. Créez un critère de service.
4. Activer l'échange de métadonnées.
5. Ouvrez l’hôte du service pour écouter les messages entrants.
  
Apportez les modifications suivantes au code :

1. Ouvrez le fichier **Program.cs** ou **Module1.vb** dans le projet **GettingStartedHost** et remplacez son code par le code suivant :

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

    Pour plus d’informations sur le fonctionnement de ce code, voir [les étapes du programme d’hébergement service](#service-hosting-program-steps).

2. Mettre à jour les propriétés du projet :

   1. Dans la fenêtre **Solution Explorer,** sélectionnez le dossier **GettingStartedHost,** puis sélectionnez **les propriétés** du menu raccourci.

   2. Sur la page des propriétés **GettingStartedHost,** sélectionnez **l’onglet Application** :

      - Pour les projets C, **sélectionnez GettingStartedHost.Program** dans la liste **d’objets Startup.**

      - Pour les projets Visual Basic, sélectionnez **Service.Program** de la liste **d’objets Startup.**

   3. Dans le menu **Fichier,** sélectionnez **Enregistrer tous**.

## <a name="verify-the-service-is-working"></a>Vérifier le fonctionnement du service

1. Construisez la solution, puis exécutez l’application de console **GettingStartedHost** depuis Visual Studio.

    Le service doit être exécuté avec les privilèges de l’administrateur. Parce que vous avez ouvert Visual Studio avec des privilèges d’administrateur, lorsque vous **exécutez GettingStartedHost** dans Visual Studio, l’application est gérée avec des privilèges d’administrateur ainsi. Comme alternative, vous pouvez ouvrir une nouvelle invite de commande en tant qu’administrateur (sélectionnez **More** > **Run comme administrateur** du menu raccourci) et exécuter **GettingStartedHost.exe** en elle.

2. Ouvrez un navigateur Web et naviguez `http://localhost:8000/GettingStarted/CalculatorService`sur la page du service à .

   > [!NOTE]
   > Des services comme celui-ci nécessitent la permission appropriée d’enregistrer les adresses HTTP sur la machine pour l’écoute. Les comptes Administrateur possèdent cette autorisation, mais l'autorisation pour les espaces de noms HTTP doit être accordée aux comptes qui ne sont pas administrateur. Pour plus d’informations sur la configuration des réservations d’espaces de noms, consultez [Configuration de HTTP et HTTPS](feature-details/configuring-http-and-https.md).

## <a name="service-hosting-program-steps"></a>Étapes du programme d’hébergement de services

Les étapes du code que vous avez ajoutée pour héberger le service sont décrites comme suit :

- **Étape 1**: Créez `Uri` une instance de la classe pour tenir l’adresse de base du service. Une URL qui contient une adresse de base dispose d’une URI facultative qui identifie un service. L’adresse de base est `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`formatée comme suit: . L’adresse de base pour le service de calculatrice utilise le transport HTTP, localhost, port 8000, et le segment URI, GettingStarted.

- **Étape 2**: Créez <xref:System.ServiceModel.ServiceHost> une instance de la classe, que vous utilisez pour accueillir le service. Le constructeur prend deux paramètres : le type de classe qui met en œuvre le contrat de service et l’adresse de base du service.

- **Étape 3**: <xref:System.ServiceModel.Description.ServiceEndpoint> Créer une instance. Un point de terminaison de service est composé d'une adresse, d'une liaison et d'un contrat de service. Le <xref:System.ServiceModel.Description.ServiceEndpoint> constructeur est composé du type d’interface de contrat de service, d’une liaison et d’une adresse. Le contrat de service est `ICalculator`, que vous définissez et implémentez dans le type de service. La liaison pour <xref:System.ServiceModel.WSHttpBinding>cet échantillon est , qui est une liaison intégrée et se connecte à des points de terminaison qui se conforment aux spécifications WS-MD. Pour plus d’informations sur les liaisons WCF, voir [aperçu des liaisons WCF](bindings-overview.md). Vous appendicez l’adresse à l’adresse de base pour identifier le point de terminaison. Le code spécifie l’adresse en tant que `http://localhost:8000/GettingStarted/CalculatorService`CalculatorService et l’adresse entièrement qualifiée pour le point de terminaison comme .

    > [!IMPORTANT]
    > Pour .NET Framework Version 4 et plus tard, l’ajout d’un critère de service est facultatif. Pour ces versions, si vous n’ajoutez pas votre code ou configuration, WCF ajoute un point de terminaison par défaut pour chaque combinaison d’adresse de base et de contrat implémenté par le service. Pour plus d’informations sur les paramètres par défaut, voir [Spécifier une adresse de point final](specifying-an-endpoint-address.md). Pour plus d’informations sur les paramètres, les liaisons et les comportements par défaut, voir [configuration simplifiée](simplified-configuration.md) et [configuration simplifiée pour les services WCF](samples/simplified-configuration-for-wcf-services.md).

- **Étape 4**: Activez l’échange de métadonnées. Les clients utilisent l’échange de métadonnées pour générer des procurations pour appeler les opérations de service. Pour permettre l’échange de <xref:System.ServiceModel.Description.ServiceMetadataBehavior> métadonnées, `true`créez une `ServiceMetadataBehavior` instance, <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> définissez <xref:System.ServiceModel.ServiceHost> sa <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> propriété et ajoutez l’objet à la collection de l’instance.

- **Étape 5** <xref:System.ServiceModel.ServiceHost> : Ouvert pour écouter les messages entrants. L’application vous attend pour appuyer **sur Enter**. Après l’application <xref:System.ServiceModel.ServiceHost>instantiates , il exécute un bloc d’essai/ capture. Pour plus d’informations sur <xref:System.ServiceModel.ServiceHost>la capture en toute sécurité des exceptions jetées par , voir [Use Close et Abort pour libérer les ressources des clients WCF](samples/use-close-abort-release-wcf-client-resources.md).

> [!IMPORTANT]
> Lorsque vous ajoutez une bibliothèque de service WCF, Visual Studio l’héberge pour vous si vous la déboçonnez en lançant un hôte de service. Pour éviter les conflits, vous pouvez empêcher Visual Studio d’accueillir la bibliothèque de services WCF.
>
> 1. Sélectionnez le projet **GettingStartedLib** dans **Solution Explorer** et choisissez **les propriétés** dans le menu raccourci.
> 2. Sélectionnez **WCF Options** et décocher **Démarrer WCF Service Host lors de débogage d’un autre projet dans la même solution**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> - Créez et configurez un projet d’application console pour l’hébergement d’un service WCF.
> - Ajoutez du code pour accueillir le service WCF.
> - Mettre à jour le fichier de configuration.
> - Démarrez le service WCF et vérifiez qu’il est en cours d’exécution.

Avancez au tutoriel suivant pour apprendre à créer un client WCF.

> [!div class="nextstepaction"]
> [Tutorial: Créer un client WCF](how-to-create-a-wcf-client.md)
