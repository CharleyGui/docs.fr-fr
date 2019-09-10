---
title: 'Procédure : Générer une application Web Forms ASP.NET prenant en charge les revendications à l’aide de WIF'
ms.date: 03/30/2017
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
author: BrucePerlerMS
ms.openlocfilehash: 45ad084013cbcafdf0d7c4ac3e0fd952305232c4
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851562"
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a>Procédure : Générer une application Web Forms ASP.NET prenant en charge les revendications à l’aide de WIF
## <a name="applies-to"></a>S'applique à  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- Web Forms ASP.NET®  
  
## <a name="summary"></a>Récapitulatif  
 Cette procédure fournit des procédures pas à pas détaillées pour la création d’une simple application Web Forms ASP.NET prenant en charge les revendications. Elle fournit également des instructions afin de tester cette simple application Web Forms ASP.NET prenant en charge les revendications pour une implémentation réussie de l’authentification fédérée. Cette procédure ne comprend pas d’instructions détaillées pour créer un service d’émission de jeton de sécurité (STS) et suppose que vous en avez déjà configuré un.  
  
## <a name="contents"></a>Sommaire  
  
- Objectifs  
  
- Résumé des étapes  
  
- Étape 1 : Créer une application Web Forms ASP.NET simple  
  
- Étape 2 : configurer l’application Web Forms ASP.NET pour l’authentification basée sur les revendications  
  
- Étape 3 : tester votre solution  
  
## <a name="objectives"></a>Objectifs  
  
- Configurer l’application Web Forms ASP.NET pour l’authentification basée sur les revendications  
  
- Tester le bon fonctionnement de l’application Web Forms ASP.NET prenant en charge les revendications  
  
## <a name="summary-of-steps"></a>Résumé des étapes  
  
- Étape 1 : créer une simple application Web Forms ASP.NET  
  
- Étape 2 : configurer l’application Web Forms ASP.NET pour l’authentification fédérée  
  
- Étape 3 : tester votre solution  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Étape 1 : Créer une application Web Forms ASP.NET simple  
 Lors de cette étape, vous allez créer une application Web Forms ASP.NET.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Pour créer une simple application ASP.NET  
  
1. Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.  
  
2. Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web Forms ASP.NET**.  
  
3. Dans **Nom**, entrez `TestApp` et appuyez sur **OK**.  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a>Étape 2 : configurer l’application Web Forms ASP.NET pour l’authentification basée sur les revendications  
 Dans cette étape, vous allez ajouter des entrées de configuration au fichier de configuration *Web.config* de votre application Web Forms ASP.NET pour qu’elle prenne en charge les revendications.  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a>Pour configurer une application ASP.NET pour l’authentification basée sur les revendications  
  
1. Ajoutez les entrées des sections de configuration suivantes au fichier de configuration *Web.config* immédiatement après l’élément d’ouverture **\<configuration>**  :  
  
    ```xml  
    <configSections>  
      <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
      <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. Ajoutez un élément **\<location>** qui permet d’accéder aux métadonnées de fédération de l’application :  
  
    ```xml  
    <location path="FederationMetadata">  
      <system.web>  
        <authorization>  
          <allow users="*" />  
        </authorization>  
      </system.web>  
    </location>  
    ```  
  
3. Ajoutez les entrées de configuration suivantes dans les éléments **\<system.web>** pour refuser des utilisateurs, désactiver l’authentification native et activer WIF afin de gérer l’authentification.  
  
    ```xml  
    <authorization>  
      <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. Ajoutez un élément **\<system.webServer>** qui définit les modules pour l’authentification fédérée. Notez que l’attribut*PublicKeyToken* doit être le même que l’attribut *PublicKeyToken* pour les entrées **\<configSections>** ajoutées précédemment :  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5. Ajoutez les entrées de configuration liées à Windows Identity Foundation suivantes et vérifiez que l’URL et le numéro de port de votre application ASP.NET correspondent aux valeurs dans l’entrée **\<audienceUris>** , l’attribut **realm** de l’élément **\<wsFederation>** et l’attribut **reply** de l’élément **\<wsFederation>** . Vérifiez également que la valeur **issuer** correspond à l’URL de votre service d’émission de jeton de sécurité (STS).  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <audienceUris>  
                <add value="http://localhost:28503/" />  
            </audienceUris>  
            <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
                <trustedIssuers>  
                    <add thumbprint="1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ1234" name="YourSTSName" />  
                </trustedIssuers>   
            </issuerNameRegistry>  
            <certificateValidation certificateValidationMode="None" />  
        </identityConfiguration>  
    </system.identityModel>  
    <system.identityModel.services>  
        <federationConfiguration>  
            <cookieHandler requireSsl="true" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="true" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
6. Ajoutez une référence à l’assembly <xref:System.IdentityModel>.  
  
7. Compilez la solution pour vérifier l’absence d’erreurs.  
  
## <a name="step-3--test-your-solution"></a>Étape 3 : tester votre solution  
 Dans cette étape, vous allez tester votre application Web Forms ASP.NET configurée pour l’authentification basée sur les revendications. Pour effectuer un test de base, vous allez ajouter le code qui affiche les revendications dans le jeton émis par le service d’émission de jeton de sécurité (STS).  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a>Pour tester votre application Web Forms ASP.NET pour l’authentification basée sur les revendications  
  
1. Ouvrez le fichier **Default.aspx** sous le projet **TestApp** et remplacez le balisage existant par le suivant :  
  
    ```aspx-csharp
    <%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head id="Head1" runat="server">  
        <title></title>  
    </head>  
    <body>  
        <h1><asp:label ID="signedIn" runat="server" /></h1>  
        <asp:label ID="claimType" runat="server" />  
        <asp:label ID="claimValue" runat="server" />  
        <asp:label ID="claimValueType" runat="server" />  
        <asp:label ID="claimSubjectName" runat="server" />  
        <asp:label ID="claimIssuer" runat="server" />  
    </body>  
    </html>  
    ```  
  
2. Enregistrez **Default.aspx**, puis ouvrez son fichier code-behind nommé **Default.aspx.cs**.  
  
    > [!NOTE]
    > **Default.aspx.cs** peut être masqué sous **Default.aspx** dans l’Explorateur de solutions. Si **Default.aspx.cs** n’est pas visible, développez **Default.aspx** en cliquant sur le triangle en regard de celui-ci.  
  
3. Remplacez le code existant dans la méthode **Page_Load** de **Default.aspx.cs** par le code suivant :  
  
    ```csharp  
    using System;  
    using System.IdentityModel;  
    using System.Security.Claims;  
    using System.Threading;  
    using System.Web.UI;  
  
    namespace TestApp  
    {  
        public partial class _Default : System.Web.UI.Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
                if (claimsPrincipal != null)  
                {  
                    signedIn.Text = "You are signed in.";  
  
                    foreach (Claim claim in claimsPrincipal.Claims)  
                    {  
                        claimType.Text = claim.Type;  
                        claimValue.Text = claim.Value;  
                        claimValueType.Text = claim.ValueType;  
                        claimSubjectName.Text = claim.Subject.Name;  
                        claimIssuer.Text = claim.Issuer;  
                    }  
                }  
                else  
                {  
                    signedIn.Text = "You are not signed in.";  
                }  
            }  
        }  
    }  
    ```  
  
4. Enregistrez **Default.aspx.cs** et générez la solution.  
  
5. Exécutez la solution en appuyant sur la touche **F5**.  
  
6. La page qui affiche les revendications dans le jeton émis par le service d’émission de jeton de sécurité doit s’afficher.
