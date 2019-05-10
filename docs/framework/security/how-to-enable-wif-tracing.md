---
title: 'Procédure : Activer le suivi WIF'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
ms.openlocfilehash: 72e22fb5e0358c5f216bfe59d16ad030ce02e0eb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626062"
---
# <a name="how-to-enable-wif-tracing"></a>Procédure : Activer le suivi WIF
## <a name="applies-to"></a>S'applique à  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- Web Forms ASP.NET®  
  
## <a name="summary"></a>Récapitulatif  
 Cette procédure fournit des procédures pas à pas détaillées pour l’activation du suivi WIF dans une application ASP.NET. Elle fournit également des instructions pour tester l’application afin de vérifier que l’écouteur de suivi et le journal fonctionnent correctement. Cette procédure ne fournit pas d'instructions détaillées pour créer un service d'émission de jeton de sécurité (STS, Security Token Service), et utilise à la place le développement STS fourni avec l'outil Identité et accès. Le développement STS n'exécute de véritable authentification et est destiné à des fins de test uniquement. Vous devez installer l'outil Identité et accès pour exécuter cette procédure. Il peut être téléchargé à partir de l’emplacement suivant : [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)  
  
> [!IMPORTANT]
>  L’activation du suivi WIF pour les applications passives, autrement dit les applications qui utilisent le protocole WS-Federation, peut potentiellement exposer l’application à des attaques par déni de service ou une divulgation d’informations à une personne malveillante. Cela inclut à la fois les parties de confiance et les services STS passifs. Pour cette raison, nous vous recommandons de ne pas activer le suivi WIF pour les parties de confiance ou les services STS passifs dans un environnement de production.  
  
## <a name="contents"></a>Sommaire  
  
- Objectifs  
  
- Vue d'ensemble  
  
- Résumé des étapes  
  
- Étape 1 : créer une simple application Web Forms ASP.NET et activer le suivi  
  
- Étape 2 : tester votre solution  
  
## <a name="objectives"></a>Objectifs  
  
- Créer une simple application ASP.NET qui utilise WIF et le service STS de développement à partir de l’outil Identity and Access Tool  
  
- Activer le suivi et vérifier son fonctionnement  
  
## <a name="overview"></a>Vue d'ensemble  
 Le suivi vous permet de déboguer et résoudre de nombreux types de problèmes liés à WIF, notamment les jetons, les cookies, les revendications, les messages de protocole et bien plus encore. Le suivi WIF est semblable au suivi WCF ; par exemple, vous pouvez choisir le niveau de détail des suivis pour tout afficher, des messages critiques à l’ensemble des messages. Les suivis WIF peuvent être générés dans des fichiers **.xml** ou **.svclog** qui sont visibles à l’aide de l’outil Service Trace Viewer. Cet outil se trouve dans le **bin** répertoire du SDK Windows chemin d’installation sur votre ordinateur, par exemple : **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.  
  
## <a name="summary-of-steps"></a>Résumé des étapes  
  
- Étape 1 : créer une simple application Web Forms ASP.NET et activer le suivi  
  
- Étape 2 : tester votre solution  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a>Étape 1 : créer une simple application Web Forms ASP.NET et activer le suivi  
 Dans cette étape, vous allez créer une application Web Forms ASP.NET et modifier le fichier *Web.config* pour activer le suivi.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Pour créer une application ASP.NET simple  
  
1. Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.  
  
2. Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web Forms ASP.NET**.  
  
3. Dans **Nom**, entrez `TestApp` et appuyez sur **OK**.  
  
4. Cliquez avec le bouton droit sur le projet **TestApp** sous l’**Explorateur de solutions**, puis sélectionnez **Identity and Access** (Identity and Access Tool).  
  
5. La fenêtre **Identity and Access** (Identity and Access Tool) s’affiche. Sous **Fournisseurs**, sélectionnez **Test your application with the Local Development STS** (Tester votre application avec le service STS de développement local), puis cliquez sur **Appliquer**.  
  
6. Créez un dossier nommé **journaux** à la racine de la **C:** lecteur, comme indiqué : **C:\logs**  
  
7. Ajoutez l’élément **\<system.diagnostics>** suivant au fichier de configuration *Web.config* immédiatement après l’élément de fermeture **\</configSections>**, comme illustré ci-dessous :  
  
    ```xml  
    <configuration>  
        <configSections>  
            ...
        </configSections>  
        <system.diagnostics>  
            <sources>  
                <source name="System.IdentityModel" switchValue="Verbose">  
                    <listeners>  
                        <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="C:\logs\WIF.xml" />  
                    </listeners>  
                </source>  
            </sources>  
            <trace autoflush="true" />  
        </system.diagnostics>  
    ```  
  
    > [!NOTE]
    >  L’emplacement du répertoire spécifié dans l’attribut **initializeData** doit exister avant de commencer la journalisation. Si l’emplacement n’existe pas, aucun journal n’est créé.  
  
     Les paramètres de configuration ci-dessus activent le suivi **détaillé** pour WIF et enregistrent le journal obtenu dans le fichier **C:logsWIF.xml**.  
  
## <a name="step-2--test-your-solution"></a>Étape 2 : tester votre solution  
 Dans cette étape, vous allez tester votre application ASP.NET WIF pour vérifier que les journaux sont enregistrés.  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a>Pour tester votre application ASP.NET WIF pour un suivi réussi  
  
1. Exécutez la solution en appuyant sur la touche **F5**. La page d’accueil ASP.NET par défaut doit s’afficher et vous devez être automatiquement authentifié avec le nom d’utilisateur *Terry*, qui est l’utilisateur par défaut retourné par le service STS de développement.  
  
2. Fermez la fenêtre du navigateur et accédez au dossier **C:\logs**. Ouvrez le fichier **C:\logs\WIF.xml** à l’aide d’un éditeur de texte.  
  
3. Examinez le fichier **WIF.xml** et vérifiez qu’il contient des entrées commençant par **\<E2ETraceEvent>**. Ces suivis contiennent des éléments **\<TraceRecord>** avec des descriptions de l’activité suivie, par exemple **Validation du SecurityToken**.
