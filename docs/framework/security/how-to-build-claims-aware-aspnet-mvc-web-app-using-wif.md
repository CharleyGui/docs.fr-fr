---
title: 'Procédure : Générer une application web ASP.NET MVC prenant en charge les revendications à l’aide de WIF'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: 4d245288b04d8ed3d997bc5572b40c7f8a9334e5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045446"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a>Procédure : Générer une application web ASP.NET MVC prenant en charge les revendications à l’aide de WIF
## <a name="applies-to"></a>S'applique à  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- ASP.NET® MVC  
  
## <a name="summary"></a>Récapitulatif  
 Cette procédure fournit des procédures pas à pas détaillées pour la création d’une simple application web ASP.NET MVC prenant en charge les revendications. Elle fournit également des instructions afin de tester cette simple application web ASP.NET MVC prenant en charge les revendications pour une implémentation réussie de l’authentification basée sur les revendications. Cette procédure ne comprend pas d’instructions détaillées pour créer un service d’émission de jeton de sécurité (STS) et suppose que vous en avez déjà configuré un.  
  
## <a name="contents"></a>Sommaire  
  
- Objectifs  
  
- Résumé des étapes  
  
- Étape 1 : créer une simple application ASP.NET MVC  
  
- Étape 2 : configurer l’application ASP.NET MVC pour l’authentification basée sur les revendications  
  
- Étape 3 : tester votre solution  
  
- Éléments associés  
  
## <a name="objectives"></a>Objectifs  
  
- Configurer l’application web ASP.NET MVC pour l’authentification basée sur les revendications  
  
- Tester le bon fonctionnement de l’application web ASP.NET MVC prenant en charge les revendications  
  
## <a name="summary-of-steps"></a>Résumé des étapes  
  
- Étape 1 : créer une simple application ASP.NET MVC  
  
- Étape 2 : configurer l’application ASP.NET MVC pour l’authentification basée sur les revendications  
  
- Étape 3 : tester votre solution  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a>Étape 1 : créer une simple application ASP.NET MVC  
 Dans cette étape, vous allez créer une application ASP.NET MVC.  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a>Pour créer une simple application ASP.NET MVC  
  
1. Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.  
  
2. Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web ASP.NET MVC 3**.  
  
3. Dans **Nom**, entrez `TestApp` et appuyez sur **OK**.  
  
4. Dans la boîte de dialogue **Nouveau projet ASP.NET MVC 3**, sélectionnez **Application Internet** dans les modèles disponibles, vérifiez que **Moteur de vue** a la valeur **Razor**, puis cliquez sur **OK**.  
  
5. Quand le nouveau projet s’ouvre, cliquez avec le bouton droit sur le projet **TestApp** dans l’**Explorateur de solutions** et sélectionnez l’option **Propriétés**.  
  
6. Dans la page de propriétés du projet, cliquez sur l’onglet **Web** sur la gauche et vérifiez que l’option **Utiliser le serveur Web IIS local** est sélectionnée.  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a>Étape 2 : configurer l’application ASP.NET MVC pour l’authentification basée sur les revendications  
 Dans cette étape, vous allez ajouter des entrées de configuration au fichier de configuration *Web.config* de votre application web ASP.NET MVC pour qu’elle prenne en charge les revendications.  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a>Pour configurer une application ASP.NET MVC pour l’authentification basée sur les revendications  
  
1. Ajoutez les définitions des sections de configuration suivantes au fichier de configuration *Web.config*. Elles définissent les sections de configuration requises par Windows Identity Foundation. Ajoutez les définitions immédiatement après l’élément d’ouverture **\<configuration>**  :  
  
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
  
4. Ajoutez les entrées de configuration liées à Windows Identity Foundation suivantes et vérifiez que l’URL et le numéro de port de votre application ASP.NET correspondent aux valeurs dans l’entrée **\<audienceUris>** , l’attribut **realm** de l’élément **\<wsFederation>** et l’attribut **reply** de l’élément **\<wsFederation>** . Vérifiez également que la valeur **issuer** correspond à l’URL de votre service d’émission de jeton de sécurité (STS).  
  
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
            <cookieHandler requireSsl="false" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="false" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
5. Ajoutez une référence à l’assembly <xref:System.IdentityModel>.  
  
6. Compilez la solution pour vérifier la présence d’erreurs.  
  
## <a name="step-3--test-your-solution"></a>Étape 3 : tester votre solution  
 Dans cette étape, vous allez tester votre application web ASP.NET MVC configurée pour l’authentification basée sur les revendications. Pour effectuer un test de base, vous allez ajouter un code simple qui affiche les revendications dans le jeton émis par le service d’émission de jeton de sécurité (STS).  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a>Pour tester votre application ASP.NET MVC pour l’authentification basée sur les revendications  
  
1. Dans l’**Explorateur de solutions**, développez le dossier **Contrôleurs** et ouvrez le fichier *HomeController.cs* dans l’éditeur. Ajoutez le code suivant à la méthode **Index** :  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2. Dans l’**Explorateur de solutions**, développez les dossiers **Vues**, puis **Accueil**, et ouvrez le fichier *Index.cshtml* dans l’éditeur. Supprimez son contenu et ajoutez le balisage suivant :  
  
    ```html  
    @{  
        ViewBag.Title = "Home Page";  
    }  
  
    <h2>Welcome: @ViewBag.ClaimsIdentity.Name</h2>  
    <h3>Values from Identity</h3>  
    <table>  
        <tr>  
            <th>  
                IsAuthenticated   
            </th>  
            <td>  
                @ViewBag.ClaimsIdentity.IsAuthenticated   
            </td>  
        </tr>  
        <tr>  
            <th>  
                Name   
            </th>          
            <td>  
                @ViewBag.ClaimsIdentity.Name  
            </td>          
        </tr>  
    </table>  
    <h3>Claims from ClaimsIdentity</h3>  
    <table>  
        <tr>  
            <th>  
                Claim Type  
            </th>  
            <th>  
                Claim Value  
            </th>  
            <th>  
                Value Type  
            </th>  
            <th>  
                Subject Name  
            </th>          
            <th>  
                Issuer Name  
            </th>          
        </tr>  
            @foreach (System.Security.Claims.Claim claim in ViewBag.ClaimsIdentity.Claims ) {  
        <tr>  
            <td>  
                @claim.Type  
            </td>  
            <td>  
                @claim.Value  
            </td>  
            <td>  
                @claim.ValueType  
            </td>  
            <td>  
                @claim.Subject.Name  
            </td>  
            <td>  
                @claim.Issuer  
            </td>  
        </tr>  
    }  
    </table>  
    ```  
  
3. Exécutez la solution en appuyant sur la touche **F5**.  
  
4. La page qui affiche les revendications dans le jeton émis par le service d’émission de jeton de sécurité doit s’afficher.  
  
## <a name="related-items"></a>Éléments associés  
  
- [Guide pratique pour Générer des ASP.NET Web Forms application prenant en charge les revendications à l’aide de WIF](how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
