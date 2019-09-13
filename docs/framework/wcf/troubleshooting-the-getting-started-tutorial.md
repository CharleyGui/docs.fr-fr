---
title: Résoudre les problèmes liés aux didacticiels prise en main de Windows Communication Foundation
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 10a2f8f718d802a7aab067b882f0d5cf3dc28dca
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928578"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Résoudre les problèmes liés aux didacticiels prise en main de Windows Communication Foundation

Cet article fournit des solutions aux problèmes et erreurs les plus courants que vous pouvez rencontrer lorsque vous suivez les étapes [du didacticiel : Prise en main des applications](getting-started-tutorial.md)Windows Communication Foundation. 
  
## <a name="common-problems"></a>Problèmes courants

**Je ne trouve pas les fichiers projet sur mon disque dur.**

 Visual Studio enregistre les fichiers projet *dans\\C:\Users&lt;nom&gt;d’utilisateur \source\repos*.  

**Impossible de trouver le fichier *app. config* généré par *Svcutil. exe*.**

 Dans Visual Studio, la fenêtre **Ajouter un élément existant** affiche uniquement les fichiers avec les extensions suivantes par défaut : 

- *.cs* 
- *. resx* 
- *.settings*
- *. xsd* 
- *.wsdl*

Pour afficher tous les types de fichiers, sélectionnez **tous\*les\*fichiers (.)** dans la liste déroulante dans le coin inférieur droit de la fenêtre **Ajouter un élément existant** .  
  
## <a name="common-errors"></a>Erreurs courantes

### <a name="compile-the-service-application"></a>Compiler l’application de service 

**L’erreur BC30420 'Sub Main’est introuvable dans’GettingStartedHost. Module1 '.**

Le point d’entrée est incorrect pour l’application Visual Basic. Apportez les modifications suivantes :

   1. Dans la fenêtre **Explorateur de solutions** , sélectionnez le dossier **GettingStartedHost** , puis sélectionnez **Propriétés** dans le menu contextuel.
    a. Dans la fenêtre **GettingStartedHost** , pour **objet de démarrage**, sélectionnez **service. Program** (ou le point d’entrée pour votre application spécifique) dans la liste. 
    b. Dans le menu principal, sélectionnez **fichier** > **enregistrer tout**.

### <a name="run-the-service-application"></a>Exécuter l’application de service 

**Http n’a pas pu inscrire l’URL\/« http:/+ : 8000/gettingstarted/CalculatorService ». Le processus n'a pas de droits d'accès à cet espace de noms.** 

 Pour un accès approprié, démarrez le processus hébergeant le service Windows Communication Foundation (WCF) avec des privilèges d’administrateur :

- Pour Visual Studio : Sélectionnez le programme Visual Studio dans le menu **Démarrer** , puis sélectionnez **plus** > **exécuter en tant qu’administrateur** dans le menu contextuel.
- Pour une fenêtre de console : Sélectionnez **invite de commandes** dans le menu **Démarrer** , puis sélectionnez **plus** > **exécuter en tant qu’administrateur** dans le menu contextuel.
- Pour l’Explorateur Windows : Sélectionnez le fichier exécutable, puis sélectionnez **exécuter en tant qu’administrateur** dans le menu contextuel.

### <a name="compile-the-client-application"></a>Compiler l’application cliente

**'CalculatorClient', ne contient pas de définition pour'\<method Name > 'et aucune méthode d’extension\<'method Name > 'acceptant un premier argument de type’CalculatorClient’n’a été trouvée (vous manque-t-il une directive using ou un référence d’assembly ?)**  

Seules les méthodes que vous marquez avec `ServiceOperationAttribute` l’attribut sont exposées publiquement. Si vous omettez l' `ServiceOperationAttribute` attribut d’une méthode dans l' `ICalculator` interface, vous recevez ce message d’erreur lors de la compilation.  

**Le nom de type ou d’espace de noms’CalculatorClient’est introuvable (une directive using ou une référence d’assembly est-elle manquante ?)**

 Vous recevez cette erreur si vous n’ajoutez pas le fichier *GeneratedProxy.cs* (ou *GeneratedProxy. vb*) à votre projet client quand vous l’avez généré avec l’outil *Svcutil. exe* .  

### <a name="run-the-client-application"></a>Exécuter l’application cliente

**Exception non gérée : System.ServiceModel.EndpointNotFoundException: Impossible de se connecter à « http\/:/localhost : 8000/gettingstarted/CalculatorService ». Code d’erreur TCP 10061 : Aucune connexion n’a pu être établie car l’ordinateur cible l’a refusé activement.**

Cette erreur se produit si vous exécutez l’application cliente sans démarrer le service pour la première fois. Tout d’abord, exécutez l’application hôte pour démarrer le service, puis exécutez l’application cliente.

### <a name="use-the-svcutilexe-tool"></a>Utiliser l’outil Svcutil. exe
   
**« Svcutil » n’est pas reconnu en tant que commande interne ou externe, programme exécutable ou fichier de commandes.**

 *Svcutil. exe* doit se trouver dans le chemin d’accès système. La solution la plus simple consiste à utiliser l’invite de commandes de Visual Studio. Dans le menu **Démarrer** , sélectionnez le répertoire **version \<de Visual Studio >**  **\<** , puis sélectionnez invite de commandes développeur pour Visual Studio version >. Cette invite de commandes affecte au chemin d’accès système les emplacements corrects pour tous les outils fournis dans le cadre de Visual Studio.  
  
### <a name="run-the-service-and-client-applications"></a>Exécuter le service et les applications clientes

**System. ServiceModel. Security. SecurityNegotiationException : Échec de la négociation de sécurité SOAP\/avec « http:/localhost : 8000/gettingstarted/CalculatorService » pour\/la cible « http:/localhost : 8000/gettingstarted/CalculatorService »**  

Cette erreur se produit sur un ordinateur joint à un domaine qui n’a pas de connectivité réseau. Connectez votre ordinateur au réseau ou désactivez la sécurité à la fois pour le service et le client. 

Pour désactiver la sécurité :

- Pour le service, remplacez le code qui crée le `WSHttpBinding` par le code suivant :  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- Pour le client, dans le fichier de configuration, mettez  **\<** à jour l’élément de > de sécurité sous l'  **\<élément Binding >** comme suit :  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator" security mode="None" />
    ```  

## <a name="see-also"></a>Voir aussi  
 [Prise en main des applications WCF](getting-started-tutorial.md)  
 [Démarrage rapide de WCF Troubleshooting](wcf-troubleshooting-quickstart.md)  
 [Résolution des problèmes d’installation](troubleshooting-setup-issues.md)
