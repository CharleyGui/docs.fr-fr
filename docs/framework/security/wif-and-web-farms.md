---
title: WIF et batteries de serveurs web
ms.date: 03/30/2017
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
author: BrucePerlerMS
ms.openlocfilehash: 09d5f3f745f170439a7fbf160b78439c103623b9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851524"
---
# <a name="wif-and-web-farms"></a>WIF et batteries de serveurs web
Si vous utilisez WIF (Windows Identity Foundation) pour sécuriser les ressources d’une application par partie de confiance déployée dans une batterie de serveurs web, vous devez définir des paramètres spécifiques pour vous assurer que WIF peut traiter les jetons provenant d’instances de l’application par partie de confiance qui sont exécutées sur les différents ordinateurs de la batterie de serveurs. Ces paramètres incluent la validation des signatures de jetons de session, le chiffrement et le déchiffrement des jetons de session, la mise en cache des jetons de session et la détection des jetons de sécurité relus.  
  
 En règle générale, quand WIF est utilisé pour sécuriser les ressources d’une application par partie de confiance (que cette application soit exécutée sur un seul ordinateur ou sur plusieurs ordinateurs dans une batterie de serveurs web), une session est établie avec le client sur la base du jeton de sécurité qui a été obtenu auprès du service d’émission de jeton de sécurité (STS). De cette manière, le client n’a pas à s’authentifier auprès du service STS pour chaque ressource d’application sécurisée à l’aide de WIF. Pour plus d’informations sur la façon dont WIF gère les sessions, consultez [Gestion des sessions par WIF](../../../docs/framework/security/wif-session-management.md).  
  
 Quand les paramètres par défaut sont utilisés, WIF procède comme suit :  
  
- Il utilise une instance de la classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> pour lire et écrire un jeton de session (une instance de la classe <xref:System.IdentityModel.Tokens.SessionSecurityToken>) qui contient les revendications et d’autres informations sur le jeton de sécurité ayant servi pour l’authentification, ainsi que des informations sur la session elle-même. Le jeton de session est empaqueté et stocké dans un cookie de session. Par défaut, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> utilise la classe <xref:System.IdentityModel.ProtectedDataCookieTransform>, qui utilise l’API de protection des données (DPAPI), pour protéger le jeton de session. L’interface DPAPI assure cette protection par le biais des informations d’identification de l’utilisateur ou de la machine, et stocke les données de clés dans le profil utilisateur.  
  
- Il utilise une implémentation en mémoire par défaut de la classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> pour stocker et traiter le jeton de session.  
  
 Ces paramètres par défaut sont appropriés pour les scénarios où l’application par partie de confiance est déployée sur un seul ordinateur. Toutefois, si l’application par partie de confiance est déployée dans une batterie de serveurs web, chaque demande HTTP peut être envoyée pour traitement à une autre instance de l’application exécutée sur un autre ordinateur. Dans ce scénario, les paramètres WIF par défaut décrits ci-dessus ne sont pas adaptés, car la protection des jetons et la mise en cache des jetons sont des processus dépendants de l’ordinateur.  
  
 Si vous déployez une application par partie de confiance dans une batterie de serveurs web, vous devez vous assurer que le traitement des jetons de session (et des jetons relus) n’est pas dépendant de l’application exécutée sur un ordinateur spécifique. Pour garantir cela, une technique possible est d’implémenter votre application par partie de confiance pour qu’elle utilise les fonctionnalités fournies par l’élément de configuration `<machineKey>` ASP.NET et qu’elle autorise la mise en cache distribuée pour le traitement des jetons de session et des jetons relus. Avec l’élément `<machineKey>`, vous pouvez spécifier les clés nécessaires pour valider, chiffrer et déchiffrer les jetons dans un fichier de configuration, ce qui vous permet de spécifier les mêmes clés sur différents ordinateurs dans la batterie de serveurs web. WIF fournit un gestionnaire de jetons de session spécifique, <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, qui protège les jetons à l’aide des clés spécifiées dans l’élément `<machineKey>`. Pour implémenter cette stratégie, suivez les conseils ci-dessous :  
  
- Utilisez l’élément de configuration `<machineKey>` ASP.NET pour spécifier explicitement les clés de chiffrement et de signature qui peuvent être utilisées sur les différents ordinateurs de la batterie de serveurs. L’exemple de code XML suivant montre comment spécifier l’élément `<machineKey>` sous l’élément `<system.web>` dans un fichier de configuration.  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
- Configurez l’application pour qu’elle utilise le gestionnaire <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> en l’ajoutant à la collection de gestionnaires de jetons. Si la collection contient le gestionnaire <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (ou un gestionnaire dérivé de la classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>), vous devez d’abord supprimer ce gestionnaire. <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> utilise la classe <xref:System.IdentityModel.Services.MachineKeyTransform>, qui protège les données de cookie de session à l’aide des informations de chiffrement spécifiées dans l’élément `<machineKey>`. Le code XML suivant montre comment ajouter <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> à une collection de gestionnaires de jetons.  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
- Implémentez une mise en cache distribuée dérivée de la classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>, autrement dit, un cache qui est accessible à partir de tous les ordinateurs de la batterie de serveurs sur lesquels l’application par partie de confiance est susceptible d’être exécutée. Configurez l’application par partie de confiance pour qu’elle utilise votre cache distribué en spécifiant l’élément [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) dans le fichier de configuration. Vous pouvez substituer la méthode <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> dans votre classe dérivée pour implémenter les éléments enfants de l’élément `<sessionSecurityTokenCache>` qui sont nécessaires.  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!--optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     Un moyen d’implémenter la mise en cache distribuée est de spécifier un serveur frontal WCF pour votre cache personnalisé. Pour plus d’informations sur l’implémentation d’un service caching WCF, consultez [Service caching WCF](#BKMK_TheWCFCachingService). Pour plus d’informations sur l’implémentation d’un client WCF que l’application par partie de confiance peut utiliser pour appeler le service caching, consultez [Client caching WCF](#BKMK_TheWCFClient).  
  
- Si votre application détecte la présence de jetons relus, vous devez appliquer une stratégie de mise en cache distribuée similaire pour le cache de relecture de jetons. Pour cela, le cache doit être dérivé de <xref:System.IdentityModel.Tokens.TokenReplayCache> et pointer vers votre service caching de relecture de jetons dans l’élément de configuration [\<tokenReplayCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md).  
  
> [!IMPORTANT]
> Tous les exemples de code XML et de code figurant dans cette rubrique proviennent de l’exemple [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) .  
  
> [!IMPORTANT]
> Les exemples de cette rubrique sont fournis en l’état et ne sont pas destinés à être utilisés tels quels dans du code de production.  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a>Service caching WCF  
 L’interface suivante définit le contrat entre le service caching WCF et le client WCF utilisé par l’application par partie de confiance pour communiquer avec lui. Elle expose essentiellement les méthodes de la classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> comme des opérations de service.  
  
```csharp
[ServiceContract()]  
public interface ISessionSecurityTokenCacheService  
{  
    [OperationContract]  
    void AddOrUpdate(string endpointId, string contextId, string keyGeneration, SessionSecurityToken value, DateTime expiryTime);  
  
    [OperationContract]  
    IEnumerable<SessionSecurityToken> GetAll(string endpointId, string contextId);  
  
    [OperationContract]  
    SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration);  
  
    [OperationContract(Name = "RemoveAll")]  
    void RemoveAll(string endpointId, string contextId);  
  
    [OperationContract(Name = "RemoveAllByEndpointId")]  
    void RemoveAll(string endpointId);  
  
    [OperationContract]  
    void Remove(string endpointId, string contextId, string keyGeneration);  
}  
```  
  
 Le code suivant illustre l’implémentation du service caching WCF. Cet exemple utilise le cache de jetons de session en mémoire par défaut qui est implémenté par WIF. Vous pouvez également implémenter un cache durable associé à une base de données. `ISessionSecurityTokenCacheService` définit l’interface présentée ci-dessus. Par souci de concision, cet exemple ne montre pas toutes les méthodes devant être utilisées pour implémenter l’interface.  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace WcfSessionSecurityTokenCacheService  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    public class SessionSecurityTokenCacheService : ISessionSecurityTokenCacheService  
    {  
        SessionSecurityTokenCache internalCache;  
  
        // sets the internal cache used by the service to the default WIF in-memory cache.  
        public SessionSecurityTokenCacheService()  
        {  
            internalCache = new IdentityModelCaches().SessionSecurityTokenCache;  
        }  
  
        ...  
  
        public SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration)  
        {  
            // Delegates to the default, in-memory MruSessionSecurityTokenCache used by WIF  
            SessionSecurityToken token = internalCache.Get(new SessionSecurityTokenCacheKey(endpointId, GetContextId(contextId), GetKeyGeneration(keyGeneration)));  
            return token;  
        }  
  
        ...  
  
        private static UniqueId GetContextId(string contextIdString)  
        {  
            return contextIdString == null ? null : new UniqueId(contextIdString);  
        }  
  
        private static UniqueId GetKeyGeneration(string keyGenerationString)  
        {  
            return keyGenerationString == null ? null : new UniqueId(keyGenerationString);  
        }  
    }  
}  
```  
  
<a name="BKMK_TheWCFClient"></a>   
## <a name="the-wcf-caching-client"></a>Client caching WCF  
 Cette section montre l’implémentation d’une classe dérivée de <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> qui délègue les appels au service caching. Vous devez configurer l’application par partie de confiance pour qu’elle utilise cette classe à l’aide de l’élément [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md), comme dans le code XML suivant :  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 La classe substitue la méthode <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> pour obtenir le point de terminaison du service à partir de l’élément enfant `<cacheServiceAddress>` personnalisé de l’élément `<sessionSecurityTokenCache>`. Elle utilise ensuite ce point de terminaison pour initialiser un canal `ISessionSecurityTokenCacheService` via lequel elle peut communiquer avec le service.  Par souci de concision, cet exemple ne montre pas toutes les méthodes devant être utilisées pour implémenter la classe <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>.  
  
```csharp
using System;  
using System.Configuration;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace CacheLibrary  
{  
    /// <summary>  
    /// This class acts as a proxy to the WcfSessionSecurityTokenCacheService.  
    /// </summary>  
    public class SharedSessionSecurityTokenCache : SessionSecurityTokenCache, ICustomIdentityConfiguration  
    {  
        private ISessionSecurityTokenCacheService WcfSessionSecurityTokenCacheServiceClient;  
  
        internal SharedSessionSecurityTokenCache()  
        {  
        }  
  
        /// <summary>  
        /// Creates a client channel to call the service host.  
        /// </summary>  
        protected void Initialize(string cacheServiceAddress)  
        {  
            if (this.WcfSessionSecurityTokenCacheServiceClient != null)  
            {  
                return;  
            }  
  
            ChannelFactory<ISessionSecurityTokenCacheService> cf = new ChannelFactory<ISessionSecurityTokenCacheService>(  
                new WS2007HttpBinding(SecurityMode.None),  
                new EndpointAddress(cacheServiceAddress));  
            this.WcfSessionSecurityTokenCacheServiceClient = cf.CreateChannel();  
        }  
  
        #region SessionSecurityTokenCache Members  
        // Delegates the following operations to the centralized session security token cache service in the web farm.  
  
        ...  
  
        public override SessionSecurityToken Get(SessionSecurityTokenCacheKey key)  
        {  
            return this.WcfSessionSecurityTokenCacheServiceClient.Get(key.EndpointId, GetContextIdString(key), GetKeyGenerationString(key));  
        }  
  
        ...  
  
        #endregion  
  
        #region ICustomIdentityConfiguration Members  
        // Called from configuration infrastructure to load custom elements  
        public void LoadCustomConfiguration(XmlNodeList nodeList)  
        {  
            // Retrieve the endpoint address of the centralized session security token cache service running in the web farm  
            if (nodeList.Count == 0)  
            {  
                throw new ConfigurationException("No child config element found under <sessionSecurityTokenCache>.");  
            }  
  
            XmlElement cacheServiceAddressElement = nodeList.Item(0) as XmlElement;  
            if (cacheServiceAddressElement.LocalName != "cacheServiceAddress")  
            {  
                throw new ConfigurationException("First child config element under <sessionSecurityTokenCache> is expected to be <cacheServiceAddress>.");  
            }  
  
            string cacheServiceAddress = null;  
            if (cacheServiceAddressElement.Attributes["url"] != null)  
            {  
                cacheServiceAddress = cacheServiceAddressElement.Attributes["url"].Value;  
            }  
            else  
            {  
                throw new ConfigurationException("<cacheServiceAddress> is expected to contain a 'url' attribute.");  
            }  
  
            // Initialize the proxy to the WebFarmSessionSecurityTokenCacheService  
            this.Initialize(cacheServiceAddress);  
        }  
        #endregion  
  
        private static string GetKeyGenerationString(SessionSecurityTokenCacheKey key)  
        {  
            return key.KeyGeneration == null ? null : key.KeyGeneration.ToString();  
        }  
  
        private static string GetContextIdString(SessionSecurityTokenCacheKey key)  
        {  
            return GetContextIdString(key.ContextId);  
        }  
  
        private static string GetContextIdString(UniqueId contextId)  
        {  
            return contextId == null ? null : contextId.ToString();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>
- <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>
- [Gestion de session WIF](../../../docs/framework/security/wif-session-management.md)
