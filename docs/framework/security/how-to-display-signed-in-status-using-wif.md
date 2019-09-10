---
title: 'Procédure : Afficher l’état Connecté à l’aide de WIF'
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: d2500c6ded485fca76715425b9a52258e07be08d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851566"
---
# <a name="how-to-display-signed-in-status-using-wif"></a>Procédure : Afficher l’état Connecté à l’aide de WIF
## <a name="applies-to"></a>S'applique à  
  
- Microsoft® Windows® Identity Foundation (WIF) 4.5  
  
- Web Forms ASP.NET®  
  
## <a name="summary"></a>Récapitulatif  
 Cette rubrique décrit comment afficher l’état de la connexion dans une application ASP.NET WIF. WIF fournit le mécanisme permettant à votre application de prendre en charge les revendications, ainsi que pour gérer l’authentification et l’autorisation pour les ressources d’applications.  
  
## <a name="contents"></a>Sommaire  
  
- Présentation  
  
- Résumé des étapes  
  
- Étape 1 : installer l’extension Identity and Access Tool  
  
- Étape 2 : créer une application ASP.NET par partie de confiance  
  
- Étape 3 : activer le service STS de développement local pour authentifier les utilisateurs  
  
- Étape 4 : modifier votre application ASP.NET pour afficher l’état de connexion  
  
- Étape 5 : tester l’intégration entre WIF et votre application ASP.NET  
  
## <a name="overview"></a>Présentation  
 Cette rubrique montre comment créer une simple application prenant en charge les revendications à l’aide de WIF et indiquer facilement si un utilisateur est connecté ou non. Les étapes suivantes utilisent le service STS de développement local qui est inclus avec l’extension Visual Studio Identity and Access Tool. Le service STS de développement local est conçu pour un environnement de développement et de test afin de fournir une méthode simple d’intégration des revendications dans votre application. Il ne doit jamais être utilisé dans un environnement de production, car il n’effectue pas de véritable authentification et les informations d’identification ne sont pas requises. Toutefois, le code impératif dans les étapes suivantes est le même pour une application prête pour la production qui utilise l’authentification réelle.  
  
## <a name="summary-of-steps"></a>Résumé des étapes  
  
- Étape 1 : installer l’extension Identity and Access Tool  
  
- Étape 2 : créer une application ASP.NET par partie de confiance  
  
- Étape 3 : activer le service STS de développement local pour authentifier les utilisateurs  
  
- Étape 4 : modifier votre application ASP.NET pour afficher l’état de connexion  
  
- Étape 5 : tester l’intégration entre WIF et votre application ASP.NET  
  
## <a name="step-1--install-the-identity-and-access-extension"></a>Étape 1 : installer l’extension Identity and Access Tool  
 Cette étape explique comment configurer l’extension Identity and Access Tool pour Visual Studio 2012. Cette extension automatise le processus de configuration de votre application afin de communiquer avec les points de terminaison STS.  
  
### <a name="to-install-the-identity-and-access-extension"></a>Pour installer l’extension Identity and Access Tool  
  
1. Démarrez Visual Studio en mode élevé en tant qu’administrateur.  
  
2. Dans Visual Studio, cliquez sur **Outils**, puis sur **Gestionnaire d’extensions**. La fenêtre **Gestionnaire d’extensions** s’affiche.  
  
3. Dans le **Gestionnaire d’extensions**, cliquez sur **Online Extensions** (Extensions en ligne) dans le menu de gauche, puis sélectionnez **Galerie Visual Studio**.  
  
4. Dans l’angle supérieur droit du **Gestionnaire d’extensions**, recherchez *Identity and Access* (Identity and Access Tool).  
  
5. L’élément **Identity and Access** (Identity and Access Tool) apparaît dans les résultats de la recherche. Cliquez dessus, puis sur **Télécharger**.  
  
6. La boîte de dialogue **Télécharger et installer** s’affiche. Si vous êtes d’accord avec les termes du contrat de licence, cliquez sur **Installer**.  
  
7. Quand l’installation de l’extension **Identity and Access** (Identity and Access Tool) est terminée, redémarrez Visual Studio en mode administrateur.  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a>Étape 2 : créer une application ASP.NET par partie de confiance  
 Cette étape décrit comment créer une application Web Forms ASP.NET par partie de confiance qui s’intègre avec WIF.  
  
### <a name="to-create-a-simple-aspnet-application"></a>Pour créer une application ASP.NET simple  
  
1. Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.  
  
2. Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web Forms ASP.NET**.  
  
3. Dans **Nom**, entrez `TestApp` et appuyez sur **OK**.  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a>Étape 3 : activer le service STS de développement local pour authentifier les utilisateurs  
 Cette étape décrit comment activer le service STS de développement local dans votre application. Le service STS de développement local est activé à l’aide de l’extension Identity and Access Tool pour Visual Studio.  
  
### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a>Pour activer le service STS de développement local dans votre application ASP.NET  
  
1. Dans Visual Studio, cliquez avec le bouton droit sur le projet **TestApp** sous l’**Explorateur de solutions**, puis sélectionnez **Identity and Access** (Identity and Access Tool).  
  
2. La fenêtre **Identity and Access** (Identity and Access Tool) s’affiche. Sous **Fournisseurs**, sélectionnez **Test your application with the Local Development STS** (Tester votre application avec le service STS de développement local), puis cliquez sur **Appliquer**.  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a>Étape 4 : modifier votre application ASP.NET pour afficher l’état de connexion  
 Cette étape explique comment modifier votre application ASP.NET afin d’indiquer dynamiquement si l’utilisateur actuel est connecté. Une fois que votre fournisseur STS a été configuré, WIF traite les revendications entrantes. Vous devez maintenant configurer le code de votre application pour afficher le résultat de l’authentification.  
  
### <a name="to-display-sign-in-status"></a>Pour afficher l’état de connexion  
  
1. Dans Visual Studio, ouvrez le fichier **Default.aspx** sous le projet **TestApp**.  
  
2. Remplacez le balisage existant dans le fichier **Default.aspx** par le balisage suivant :  
  
    ```aspx-csharp  
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
  
3. Enregistrez **Default.aspx**, puis ouvrez son fichier code-behind nommé **Default.aspx.cs**.  
  
    > [!NOTE]
    > **Default.aspx.cs** peut être masqué sous **Default.aspx** dans l’Explorateur de solutions. Si **Default.aspx.cs** n’est pas visible, développez **Default.aspx** en cliquant sur le triangle en regard de celui-ci.  
  
4. Remplacez le code existant dans **Default.aspx.cs** par le code suivant :  
  
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
  
5. Enregistrez **Default.aspx.cs** et générez l’application.  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a>Étape 5 : tester l’intégration entre WIF et votre application ASP.NET  
 Cette étape explique comment tester l’intégration entre WIF et votre application ASP.NET.  
  
### <a name="to-test-the-integration-between-wif-and-aspnet"></a>Pour tester l’intégration entre WIF et ASP.NET  
  
1. Dans Visual Studio, appuyez sur **F5** pour démarrer le débogage de l’application. Si aucune erreur n’est trouvée, une nouvelle fenêtre de navigateur s’ouvre.  
  
2. Vous pouvez remarquer que le navigateur redirige en mode silencieux votre demande vers le service STS, puis ouvre la page Default.aspx. Si WIF est correctement configuré, le site doit afficher le texte suivant : **« Vous êtes connecté »** .
