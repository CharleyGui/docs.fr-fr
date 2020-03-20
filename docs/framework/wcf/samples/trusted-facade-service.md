---
title: Trusted Facade Service
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 17901b7a68d4701287d02bc7ee3174683e777fd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143744"
---
# <a name="trusted-facade-service"></a>Trusted Facade Service
Cet échantillon de scénario montre comment faire circuler les informations d’identité de l’appelant d’un service à l’autre en utilisant l’infrastructure de sécurité de la Windows Communication Foundation (WCF).  
  
 Exposer les fonctionnalités fournies par un service au réseau public à l'aide d'un service de façade correspond à un modèle de conception standard. Le service de façade, qui se trouve en principe dans le réseau de périmètre (également appelé sous-réseau filtré), communique avec le service principal, lequel implémente la logique métier et l'accès aux données internes. Le canal de communication entre ces deux services traverse un pare-feu et est habituellement utilisé à une seule fin.  
  
 Cet exemple comporte les composants suivants :  
  
- Client de calculatrice  
  
- Service de façade de calculatrice  
  
- Service principal de calculatrice  
  
 Le service de façade est chargé de valider la demande et d'authentifier l'appelant. Après authentification de l'appelant et validation de la demande, il transfert celle-ci au service principal à l'aide du canal de communication contrôlé depuis le réseau de périmètre vers le réseau interne. Le service de façade ajoute à la demande transférée des informations relatives à l'identité de l'appelant que le service principal pourra utiliser à des fins de traitement. L'identité de l'appelant est transmise à l'aide d'un jeton de sécurité `Username` figurant dans l'en-tête `Security` du message. L’échantillon utilise l’infrastructure de sécurité WCF `Security` pour transmettre et extraire ces informations de l’en-tête.  
  
> [!IMPORTANT]
> Le service principal approuve le service de façade pour authentifier l'appelant. C'est pourquoi le service principal n'authentifie pas à nouveau l'appelant. Il utilise, en revanche, les informations d'identité fournies par le service de façade dans la demande transférée. Dans le cadre de cette relation de confiance, il est essentiel que le service principal authentifie le service de façade afin de garantir la provenance depuis une source fiable (dans ce cas, le service de façade) du message transféré.  
  
## <a name="implementation"></a>Implémentation  
 Dans cet exemple, deux voies de communication sont utilisées. La première entre le client et le service de façade, la seconde entre le service de façade et le service principal.  
  
### <a name="communication-path-between-client-and-faade-service"></a>Voie de communication entre le client et le service de façade  
 La voie de communication entre le client et le service de façade utilise `wsHttpBinding` avec un type d'informations d'identification de client `UserName` . Cela signifie que le client s'authentifie auprès du service de façade à l'aide d'un nom d'utilisateur et d'un mot de passe et que le service de façade s'authentifie auprès du client à l'aide d'un certificat X.509. La configuration de la liaison ressemble à l'exemple suivant.  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="Binding1">  
      <security mode="Message">  
        <message clientCredentialType="UserName"/>  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 Le service de façade authentifie l'appelant à l'aide de l'implémentation `UserNamePasswordValidator` personnalisée. Dans le cadre de cet exemple, le processus d'authentification se contente seulement de vérifier que le nom d'utilisateur de l'appelant correspond au mot de passe présenté. Dans la réalité, il y a de grandes chances que l'utilisateur soit authentifié à l'aide d'Active Directory ou d'un fournisseur d'appartenances ASP.NET personnalisé. L'implémentation du validateur réside dans le fichier `FacadeService.cs` .  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // check that username matches password  
        if (null == userName || userName != password)  
        {  
            Console.WriteLine("Invalid username or password");  
            throw new SecurityTokenValidationException(  
                       "Invalid username or password");  
        }  
    }  
}  
```  
  
 Le validateur personnalisé est configuré pour être utilisé à l'intérieur du comportement `serviceCredentials` , dans le fichier de configuration du service de façade. Ce comportement est également utilisé pour configurer le certificat X.509 du service.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="FacadeServiceBehavior">  
      <!--The serviceCredentials behavior allows you to define -->  
      <!--a service certificate. -->  
      <!--A service certificate is used by the service to  -->  
      <!--authenticate itself to its clients and to provide  -->  
      <!--message protection. -->  
      <!--This configuration references the "localhost"  -->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate
               findValue="localhost"
               storeLocation="LocalMachine"
               storeName="My"
               x509FindType="FindBySubjectName" />  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
            customUserNamePasswordValidatorType=  
           "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,  
            FacadeService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
### <a name="communication-path-between-faade-service-and-backend-service"></a>Voie de communication entre le service de façade et le service principal  
 La voie de communication entre le service de façade et le service principal utilise une liaison `customBinding` qui se compose de plusieurs éléments de liaison. Cette liaison remplit deux fonctions. Elle authentifie le service de façade et le service principal afin de garantir que la communication est sécurisée et qu'elle provient d'une source fiable. En outre, elle transmet l'identité de l'appelant initial à l'intérieur du jeton de sécurité `Username` . Dans ce cas, seul le nom d'utilisateur de l'appelant initial est transmis au service principal, son mot de passe ne figure pas dans le message. La raison en est que le service principal approuve le service de façade pour authentifier l'appelant avant que la demande de ce dernier de ne lui soit transféré. Le service de façade s'authentifiant auprès du service principal, ce dernier peut se fier aux informations contenues dans la demande transférée.  
  
 Le code suivant contient la configuration de liaison utilisée par cette voie de communication.  
  
```xml  
<bindings>  
  <customBinding>  
    <binding name="ClientBinding">  
      <security authenticationMode="UserNameOverTransport"/>  
      <windowsStreamSecurity/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 [ \<L’élément de liaison>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) de sécurité s’occupe de la transmission et de l’extraction du nom d’utilisateur initial de l’appelant. Les [ \<fenêtresStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) et [ \<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) s’occuper de l’authentification des services de façade et de backend et de la protection des messages.  
  
 Pour transmettre la demande, la mise en œuvre du service de façade doit fournir le nom d’utilisateur initial de l’appelant afin que l’infrastructure de sécurité WCF puisse placer cela dans le message transmis. Pour que l'implémentation du service de façade puisse fournir ce nom d'utilisateur, ce dernier doit être défini dans la propriété `ClientCredentials` de l'instance de proxy de client utilisée par ce service pour communiquer avec le service principal.  
  
 Le code suivant illustre la manière dont la méthode `GetCallerIdentity` est implémentée sur le service de façade. Ce même modèle est utilisé par d'autres méthodes.  
  
```csharp  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 Comme illustré dans le code précédent, le mot de passe n'est pas défini dans la propriété' `ClientCredentials` , seul le nom d'utilisateur est défini. L’infrastructure de sécurité WCF crée un jeton de sécurité de nom d’utilisateur sans mot de passe dans ce cas, ce qui est exactement ce qui est nécessaire dans ce scénario.  
  
 Sur le service principal, les informations contenues dans le jeton de sécurité de nom d'utilisateur doivent être authentifiées. Par défaut, la sécurité WCF tente de cartographier l’utilisateur vers un compte Windows à l’aide du mot de passe fourni. Dans ce cas, aucun mot de passe n'est communiqué et le service principal n'est pas obligé d'authentifier le nom d'utilisateur, le service de façade ayant déjà procédé à cette authentification. Pour implémenter cette fonctionnalité `UserNamePasswordValidator` dans WCF, une coutume est fournie qui applique uniquement qu’un nom d’utilisateur est spécifié dans le jeton et n’effectue aucune authentification supplémentaire.  
  
```csharp  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // Ignore the password because it is empty,
        // we trust the facade service to authenticate the client.  
        // Accept the username information here so that the
        // application gets access to it.  
        if (null == userName)  
        {  
            Console.WriteLine("Invalid username");  
            throw new
             SecurityTokenValidationException("Invalid username");  
        }  
    }  
}  
```  
  
 Le validateur personnalisé est configuré pour être utilisé à l'intérieur du comportement `serviceCredentials` , dans le fichier de configuration du service de façade.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="BackendServiceBehavior">  
      <serviceCredentials>  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
           customUserNamePasswordValidatorType=  
          "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,
           BackendService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Pour extraire les informations de nom d'utilisateur et les informations concernant le compte du service de façade approuvé, l'implémentation de service principal utilise la classe `ServiceSecurityContext` . L'exemple de code suivant illustre la manière dont la méthode `GetCallerIdentity` est implémentée.  
  
```csharp  
public string GetCallerIdentity()  
{  
    // Facade service is authenticated using Windows authentication.  
    //Its identity is accessible.  
    // On ServiceSecurityContext.Current.WindowsIdentity.  
    string facadeServiceIdentityName =
          ServiceSecurityContext.Current.WindowsIdentity.Name;  
  
    // The client name is transmitted using Username authentication on
    //the message level without the password  
    // using a supporting encrypted UserNameToken.  
    // Claims extracted from this supporting token are available in
    // ServiceSecurityContext.Current.AuthorizationContext.ClaimSets
    // collection.  
    string clientName = null;  
    foreach (ClaimSet claimSet in
        ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)  
    {  
        foreach (Claim claim in claimSet)  
        {  
            if (claim.ClaimType == ClaimTypes.Name &&
                                   claim.Right == Rights.Identity)  
            {  
                clientName = (string)claim.Resource;  
                break;  
            }  
        }  
    }  
    if (clientName == null)  
    {  
        // In case there was no UserNameToken attached to the request.  
        // In the real world implementation the service should reject
        // this request.  
        return "Anonymous caller via " + facadeServiceIdentityName;  
    }  
  
    return clientName + " via " + facadeServiceIdentityName;  
}  
```  
  
 Les informations relatives au compte du service de façade sont extraites à l'aide de la propriété `ServiceSecurityContext.Current.WindowsIdentity` . Pour accéder aux informations de l'appelant initial, le service principal utilise la propriété `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` . Le service recherche une revendication `Identity` ayant le type `Name`. Cette allégation est automatiquement générée par l’infrastructure `Username` de sécurité WCF à partir des informations contenues dans le jeton de sécurité.  
  
## <a name="running-the-sample"></a>Exécution de l’exemple  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter. Vous pouvez appuyer sur le bouton ENTER de la fenêtre du service de façade ou de la fenêtre du service principal pour arrêter ces derniers.  
  
```console  
Username authentication required.  
Provide a valid machine or domain ac  
   Enter username:  
user  
   Enter password:  
****  
user via MyMachine\testaccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Le fichier de commandes Setup.bat contenu dans cet exemple de scénario vous permet de configurer le serveur en utilisant le certificat requis pour permettre au service de façade exigeant la sécurité basée sur les certificats de s'authentifier auprès du client. Pour plus d'informations, consultez la procédure d'installation figurant en fin de rubrique.  
  
 Les éléments suivants fournissent une vue d'ensemble des différentes sections des fichiers de commandes.  
  
- Création du certificat de serveur  
  
     Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser.  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     La variable `%SERVER_NAME%` spécifie le nom du serveur, sa valeur par défaut est localhost. Le certificat est stocké dans le magasin LocalMachine.  
  
- Installation du certificat du service de façade dans le magasin de certificats approuvés du client.  
  
     La ligne suivante copie le certificat du service de façade dans le magasin de personnes de confiance du client. Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client. Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple d'un certificat émis par Microsoft, il n'est pas nécessaire d'ajouter le certificat du serveur au magasin de certificats du client.  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Pour exécuter l'exemple sur le même ordinateur  
  
1. Assurez-vous que le chemin d'accès pointe vers le dossier dans lequel Makecert.exe se trouve.  
  
2. Exécutez Setup.bat à partir du dossier d'installation de l'exemple. Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.  
  
3. Lancez le fichier BackendService.exe figurant dans le répertoire \BackendService\bin dans une fenêtre de console distincte.  
  
4. Lancez le fichier FacadeService.exe figurant dans le répertoire \FacadeService\bin dans une fenêtre de console distincte.  
  
5. Lancez Client.exe à partir de \client\bin. L'activité du client s'affiche sur son application de console.  
  
6. Si le client et le service ne sont pas en mesure de communiquer, voir [Conseils de dépannage pour les échantillons WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
1. Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
