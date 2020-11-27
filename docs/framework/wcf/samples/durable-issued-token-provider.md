---
title: Durable Issued Token Provider
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 7e0025eb4bc4918b977d9d8c4e2b1435b0425973
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291672"
---
# <a name="durable-issued-token-provider"></a>Durable Issued Token Provider

Cet exemple montre comment implémenter un fournisseur de jetons émis client personnalisé.  
  
## <a name="discussion"></a>Discussions  

 Un fournisseur de jetons dans Windows Communication Foundation (WCF) est utilisé pour fournir des informations d’identification à l’infrastructure de sécurité. En général, le fournisseur de jetons examine la cible et publie des informations d'identification appropriées afin que l'infrastructure de sécurité puisse sécuriser le message. WCF est fourni avec un fournisseur de jetons CardSpace. Les fournisseurs de jetons personnalisés sont utiles dans les cas suivants :  
  
- Si vous disposez d'un magasin d'informations d'identification avec lequel le fournisseur de jetons intégré ne peut pas fonctionner.  
  
- Si vous souhaitez fournir votre propre mécanisme personnalisé pour transformer les informations d’identification à partir du moment où l’utilisateur fournit les détails lorsque le client WCF utilise les informations d’identification.  
  
- si vous générez un jeton personnalisé.  
  
 Cet exemple montre comment générer un fournisseur de jetons personnalisé qui met en cache des jetons émis par un service d'émission de jeton de sécurité (STS, Security Token Service).  
  
 En résumé, cet exemple montre :  
  
- la façon dont un client peut être configuré avec un fournisseur de jetons personnalisé ;  
  
- Comment les jetons émis peuvent être mis en cache et fournis au client WCF.  
  
- la façon dont le serveur est authentifié auprès du client à l'aide du certificat X.509 du serveur.  
  
 Cet exemple comporte un programme de console client (Client.exe), un programme de console de service d'émission de jeton de sécurité (Securitytokenservice.exe) et un programme de console de service (Service.exe). Le service implémente un contrat qui définit un modèle de communication demande-réponse. Le contrat est défini par l'interface `ICalculator`, laquelle expose les opérations mathématiques suivantes : addition, soustraction, multiplication et division. Le client obtient un jeton de sécurité du STS et effectue des demandes synchrones au service pour une opération mathématique donnée, puis le service répond avec le résultat. L'activité du client est affichée dans la fenêtre de console.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
 Cet exemple expose le contrat ICalculator à l’aide de [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) . La configuration de cette liaison sur le client est présentée dans le code suivant.  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey"
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuer address="http://localhost:8000/sts/windows"
                  binding="wsHttpBinding" />
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 Sur l'élément `security` de `wsFederationHttpBinding`, la valeur `mode` configure le mode de sécurité à utiliser. Dans cet exemple, la sécurité de niveau message est utilisée ; c'est pourquoi l'élément `message` de `wsFederationHttpBinding` est spécifié dans l'élément `security` de `wsFederationHttpBinding`. L’élément `issuer` de `wsFederationHttpBinding` dans l’élément `message` de `wsFederationHttpBinding` spécifie l’adresse et la liaison du STS qui publie un jeton de sécurité pour le client afin de permettre à ce dernier de s’authentifier auprès du service Calculator.  
  
 La configuration de cette liaison sur le service est présentée dans le code suivant.  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey"
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuerMetadata address="http://localhost:8000/sts/mex">
            <identity>
              <certificateReference storeLocation="CurrentUser"
                                    storeName="TrustedPeople"
                                    x509FindType="FindBySubjectDistinguishedName"
                                    findValue="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 Sur l'élément `security` de `wsFederationHttpBinding`, la valeur `mode` configure le mode de sécurité à utiliser. Dans cet exemple, la sécurité de niveau message est utilisée ; c'est pourquoi l'élément `message` de `wsFederationHttpBinding` est spécifié dans l'élément `security` de `wsFederationHttpBinding`. L'élément `issuerMetadata` de `wsFederationHttpBinding` dans l'élément `message` de `wsFederationHttpBinding` spécifie l'adresse et l'identité du point de terminaison qui peut être utilisé afin de récupérer les métadonnées destinées au STS.  
  
 Le comportement du service est présenté dans le code suivant.  
  
```xml  
<behavior name="ServiceBehavior">
  <serviceDebug includeExceptionDetailInFaults="true" />
  <serviceMetadata httpGetEnabled="true" />
  <serviceCredentials>
    <issuedTokenAuthentication>
      <knownCertificates>
        <add storeLocation="LocalMachine"
              storeName="TrustedPeople"
              x509FindType="FindBySubjectDistinguishedName"
              findValue="CN=STS" />
      </knownCertificates>
    </issuedTokenAuthentication>
    <serviceCertificate storeLocation="LocalMachine"
                        storeName="My"
                        x509FindType="FindBySubjectDistinguishedName"
                        findValue="CN=localhost" />
  </serviceCredentials>
</behavior>  
```  
  
 L'élément `issuedTokenAuthentication` dans l'élément `serviceCredentials` permet au service de spécifier des contraintes sur les jetons que les clients sont autorisés à présenter pendant l'authentification. Cette configuration spécifie que les jetons signés par un certificat ayant CN=STS comme nom du sujet sont acceptés par le service.  
  
 Le service d'émission de jeton de sécurité expose un point de terminaison unique à l'aide du wsHttpBinding standard. Le service d'émission de jeton de sécurité répond pour demander des jetons aux clients et, à la condition que le client s'authentifie à l'aide d'un compte Windows, il émet un jeton qui contient le nom d'utilisateur du client comme revendication dans le jeton émis. Dans le cadre de la création du jeton, le service d'émission de jeton de sécurité le signe à l'aide de la clé privée associée au certificat CN=STS. Par ailleurs, il crée une clé symétrique et la chiffre à l'aide de la clé publique associée au certificat CN=localhost. Lors du retour du jeton au client, le service d'émission de jeton de sécurité retourne également la clé symétrique. Le client présente le jeton émis au service de calculatrice et prouve qu'il connaît la clé symétrique en signant le message à l'aide de celle-ci.  
  
## <a name="custom-client-credentials-and-token-provider"></a>Informations d'identification client personnalisées et fournisseur de jetons personnalisé  

 Les étapes suivantes indiquent comment développer un fournisseur de jetons personnalisé qui met en cache les jetons émis et les intègre à WCF : Security.  
  
### <a name="to-develop-a-custom-token-provider"></a>Pour développer un fournisseur de jetons personnalisé  
  
1. Écrivez un fournisseur de jetons personnalisé.  
  
     L'exemple implémente un fournisseur de jetons personnalisé qui retourne un jeton de sécurité récupéré d'un cache.  
  
     Pour effectuer cette tâche, le fournisseur de jetons personnalisé dérive la classe <xref:System.IdentityModel.Selectors.SecurityTokenProvider> et substitue la méthode <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A>. Cette méthode tente d'obtenir un jeton provenant du cache, ou si aucun jeton n'est trouvé dans le cache, elle en récupère un du fournisseur sous-jacent, puis le met en cache. Dans les deux cas, la méthode retourne un `SecurityToken`.  
  
    ```csharp  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
      GenericXmlSecurityToken token;  
      if (!this.cache.TryGetToken(target, issuer, out token))  
      {  
        token = (GenericXmlSecurityToken) this.innerTokenProvider.GetToken(timeout);  
        this.cache.AddToken(token, target, issuer);  
      }  
      return token;  
    }  
    ```  
  
2. Écrivez un gestionnaire de jetons de sécurité personnalisé.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> permet de créer un <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pour un <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> spécifique qui lui est passé dans la méthode `CreateSecurityTokenProvider`. Le gestionnaire de jetons de sécurité permet également de créer des authentificateurs et des sérialiseurs de jeton, mais ceux-là ne sont pas traités dans cet exemple. Dans cet exemple, le gestionnaire de jetons de sécurité personnalisé hérite de la classe <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> et substitue la méthode `CreateSecurityTokenProvider` pour retourner le fournisseur de jetons personnalisé lorsque les exigences du jeton passé indiquent qu’un jeton émis est demandé.  
  
    ```csharp
    class DurableIssuedTokenClientCredentialsTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentialsTokenManager ( DurableIssuedTokenClientCredentials creds ): base(creds)  
      {  
        this.cache = creds.IssuedTokenCache;  
      }  
  
      public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
      {  
        if (IsIssuedSecurityTokenRequirement(tokenRequirement))  
        {  
          return new DurableIssuedSecurityTokenProvider ((IssuedSecurityTokenProvider)base.CreateSecurityTokenProvider( tokenRequirement), this.cache);  
        }  
        else
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3. Écrivez une information d'identification client personnalisée.  
  
     Une classe d'informations d'identification client permet de représenter les informations d'identification qui sont configurées pour le proxy client et crée le gestionnaire de jetons de sécurité utilisé pour obtenir des authentificateurs, des fournisseurs et des sérialiseurs de jeton.  
  
    ```csharp
    public class DurableIssuedTokenClientCredentials : ClientCredentials  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentials() : base()  
      {  
      }  
  
      DurableIssuedTokenClientCredentials ( DurableIssuedTokenClientCredentials other) : base(other)  
      {  
        this.cache = other.cache;  
      }  
  
      public IssuedTokenCache IssuedTokenCache  
      {  
        get  
        {  
          return this.cache;  
        }  
        set  
        {  
          this.cache = value;  
        }  
      }  
  
      protected override ClientCredentials CloneCore()  
      {  
        return new DurableIssuedTokenClientCredentials(this);  
      }  
  
      public override SecurityTokenManager CreateSecurityTokenManager()  
      {  
        return new DurableIssuedTokenClientCredentialsTokenManager ((DurableIssuedTokenClientCredentials)this.Clone());  
      }  
    }  
    ```  
  
4. Implémentez le cache du jeton. L'exemple d'implémentation utilise une classe de base abstraite par l'intermédiaire de laquelle les consommateurs d'un cache de jeton donné interagissent avec le cache.  
  
    ```csharp
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    // Configure the client to use the custom client credential.  
    ```  
  
     Pour que le client puisse utiliser l'information d'identification client personnalisée, l'exemple supprime la classe d'informations d'identification client par défaut et fournit la nouvelle.  
  
    ```csharp
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a>Exécution de l’exemple  

 Consultez les instructions suivantes pour exécuter l'exemple. Lorsque vous exécutez l'exemple, la demande de jeton de sécurité s'affiche dans la fenêtre de console du service d'émission de jeton de sécurité. Les demandes et réponses d'opération s'affichent dans les fenêtres de console du client et du service. Appuyez sur ENTER dans l'une ou l'autre de ces fenêtres pour arrêter l'application leur correspondant.  
  
## <a name="the-setupcmd-batch-file"></a>Fichier de commandes Setup.cmd  

 Le fichier de commandes Setup.cmd inclus avec cet exemple vous permet de configurer le serveur et le service d'émission de jeton de sécurité avec les certificats appropriés pour exécuter une application auto-hébergée. Il crée deux certificats dans le magasin de certificats CurrentUser/TrustedPeople. Le nom du sujet du premier certificat est CN=STS. Ce certificat est utilisé par le service d'émission de jeton de sécurité pour signer les jetons de sécurité qu'il émet au client. Le deuxième a le nom du sujet CN=localhost et est utilisé par le service d'émission de jeton de sécurité pour chiffrer un secret de sorte que le service puisse le déchiffrer.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Exécutez le fichier Setup.cmd pour créer les certificats requis.  
  
2. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md). Assurez-vous que tous les projets de la solution sont générés (Shared, RSTRSTR, Service, SecurityTokenService et Client).  
  
3. Veillez à ce que Service.exe et SecurityTokenService.exe s'exécutent tous deux avec des privilèges d'administrateur.  
  
4. Exécutez client.exe.  
  
### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
1. Exécutez Cleanup.cmd dans le dossier d’exemples après avoir exécuté l’exemple.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
