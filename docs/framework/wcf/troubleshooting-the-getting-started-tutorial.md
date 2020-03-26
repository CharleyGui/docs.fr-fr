---
title: Dépannage de la Get a commencé avec Windows Communication Foundation tutoriels
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 73aa0f5784784cb788a7532f8e22cbe925429c41
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249615"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Dépannage de la Get a commencé avec Windows Communication Foundation tutoriels

Cet article fournit des solutions pour les problèmes les plus courants et les erreurs que vous pourriez faire face lorsque vous suivez les étapes du [tutorial: Démarrer avec les applications Windows Communication Foundation](getting-started-tutorial.md).
  
## <a name="common-problems"></a>Problèmes courants

**Je ne trouve pas les fichiers du projet sur mon disque dur.**

 Visual Studio enregistre les fichiers de projet dans *C : nom\\&lt;&gt;d’utilisateur d’utilisateurs .*  

**Je ne peux pas trouver le fichier *App.config* généré par *Svcutil.exe*.**

 Dans Visual Studio, la fenêtre **Add Existing Item** n’affiche les fichiers qu’avec les extensions suivantes par défaut :

- *.cs*
- *.resx*
- *.paramètres*
- *.xsd (en)*
- *.wsdl*

Pour afficher tous les types de fichiers, sélectionnez **tous les fichiers (.\*\*)** dans la liste des dépôts dans le coin inférieur droit de la fenêtre Ajouter **l’élément existant.**  
  
## <a name="common-errors"></a>Erreurs courantes

### <a name="compile-the-service-application"></a>Compiler l’application de service

**Erreur BC30420 'Sub Main' n’a pas été trouvé dans 'GettingStartedHost.Module1'.**

Le point d’entrée est incorrect pour l’application Visual Basic. Effectuer le changement suivant:

   1. Dans la fenêtre **Solution Explorer,** sélectionnez le dossier **GettingStartedHost,** puis sélectionnez **les propriétés** du menu raccourci.
    a. Dans la fenêtre **GettingStartedHost,** pour **l’objet Startup**, sélectionnez **Service.Program** (ou le point d’entrée de votre application particulière) de la liste.
    b. Dans le menu principal, sélectionnez **Fichier** > **Enregistrer tous**.

### <a name="run-the-service-application"></a>Exécuter l’application de service

**HTTP ne pouvait pas\/enregistrer URL 'http: /':8000/GettingStarted/CalculatorService'. Votre processus n’a pas de droits d’accès à cet espace de nom.**

 Pour un accès adéquat, commencez le processus d’hébergement du service de la Windows Communication Foundation (WCF) avec des privilèges administratifs :

- Pour Visual Studio: Sélectionnez le programme Visual Studio dans le menu **Démarrer,** puis sélectionnez **More** > **Run en tant qu’administrateur** du menu raccourci.
- Pour une fenêtre console : Sélectionnez **l’invite de commande** dans le menu **Démarrer,** puis sélectionnez **More** > **Run As administrator** dans le menu raccourci.
- Pour Windows Explorer : Sélectionnez l’exécutable, puis **sélectionnez Run comme administrateur** dans le menu raccourci.

### <a name="compile-the-client-application"></a>Compiler l’application client

**'CalculatorClient', ne contient pas\<de définition pour 'nom de méthode\<>' et aucune méthode de prolongation 'nom de méthode>' acceptant un premier argument de type 'CalculatorClient' pourrait être trouvé (manquez-vous une directive utilisant ou une référence d’assemblage?)**  

Seules les méthodes que `ServiceOperationAttribute` vous marquez avec l’attribut sont exposées publiquement. Si vous ometez `ServiceOperationAttribute` l’attribut `ICalculator` à partir d’une méthode de l’interface, vous recevez ce message d’erreur lors de la compilation.  

**Le nom type ou namespace 'CalculatorClient' n’a pas pu être trouvé (manquez-vous une directive utilisant ou une référence d’assemblage?)**

 Vous recevez cette erreur si vous n’ajoutez pas le *fichier generatedProxy.cs* (ou *généréProxy.vb)* à votre projet client lorsque vous les avez générées avec *l’outil Svcutil.exe.*  

### <a name="run-the-client-application"></a>Exécuter l’application client

**Exception non gérée: System.ServiceModel.EndpointNotFoundException: Impossible de\/se connecter à 'http: /localhost:8000/GettingStarted/CalculatorService'. Code d’erreur TCP 10061 : Aucune connexion n’a pu être faite parce que la machine cible l’a activement refusée.**

Cette erreur se produit si vous exécutez l’application client sans commencer d’abord le service. Tout d’abord, exécutez l’application hôte pour démarrer le service, puis exécutez l’application client.

### <a name="use-the-svcutilexe-tool"></a>Utilisez l’outil Svcutil.exe

**'Svcutil' n’est pas reconnu comme un commandement interne ou externe, un programme opérable ou un fichier par lots.**

 *Svcutil.exe* doit être dans la voie du système. La solution la plus simple est d’utiliser l’invite de commande Visual Studio. À partir du menu **Démarrer,** sélectionnez la **version Visual Studio \<>** répertoire, puis sélectionnez Developer Command Prompt pour la version VS ** \<>**. Cette commande invite définit le chemin du système vers les emplacements corrects pour tous les outils expédiés dans le cadre de Visual Studio.  
  
### <a name="run-the-service-and-client-applications"></a>Exécuter le service et les applications client

**System.ServiceModel.Security.SecurityNegotiationException: SOAP security negotiation\/with 'http: /localhost:8000/GettingStarted/CalculatorService' for target 'http:\//localhost:8000/GettingStarted/CalculatorService' failed**  

Cette erreur se produit sur un ordinateur connecté au domaine qui n’a pas de connectivité réseau. Connectez votre ordinateur au réseau ou éteignez la sécurité du service et du client.

Pour désactiver la sécurité :

- Pour le service, remplacez `WSHttpBinding` le code qui crée le code suivant :  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- Pour le client, dans le fichier de configuration, mettre à jour ** \<l’élément de sécurité>** sous l’élément ** \<de liaison>** comme suit :  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator">
      <security mode="None" />
    </binding
    ```  

## <a name="see-also"></a>Voir aussi  
 [Démarrer avec les applications WCF](getting-started-tutorial.md)  
 [WCF dépannage quickstart](wcf-troubleshooting-quickstart.md)  
 [Problèmes de configuration de dépannage](troubleshooting-setup-issues.md)
