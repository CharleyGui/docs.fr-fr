---
title: <transport> de <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: c563339e4f854cc4e60f92dd5b8c0b39112dc000
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736118"
---
# <a name="transport-of-basichttpbinding"></a>\<transport> de \<basicHttpBinding>
Définit les propriétés qui déterminent les paramètres d'authentification pour le transport HTTP.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<basicHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="String">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|clientCredentialType|-Spécifie le type d’informations d’identification à utiliser lors de l’authentification du client à l’aide de l’authentification HTTP.  Par défaut, il s’agit de `None`. Cet attribut est de type <xref:System.ServiceModel.HttpClientCredentialType>.|  
|proxyCredentialType|-Spécifie le type d’informations d’identification à utiliser lors de l’authentification du client à partir d’un domaine à l’aide d’un proxy sur HTTP. Cet attribut est applicable uniquement lorsque l'attribut `mode` de l'élément `security` parent est `Transport` ou `TransportCredentialsOnly`. Cet attribut est de type <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|realm|Chaîne qui spécifie le domaine utilisé par la méthode d'authentification HTTP pour l'authentification Digest ou de base. La valeur par défaut est une chaîne vide.|  
|policyEnforcement|Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.<br /><br /> 1. jamais : la stratégie n’est jamais appliquée (la protection étendue est désactivée).<br />2. WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.<br />3. Always : la stratégie est toujours appliquée. Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.|  
|protectionScenario|Cette énumération spécifie le scénario de protection appliqué par la stratégie.|  
  
## <a name="clientcredentialtype-attribute"></a>Attribut clientCredentialType  
  
|Valeur|Description|  
|-----------|-----------------|  
|None|Les messages ne sont pas sécurisés pendant le transfert.|  
|De base|Spécifie l'authentification de base.|  
|Digest|Spécifie l’authentification Digest.|  
|Ntlm|Spécifie l'authentification NTLM le cas échéant et en cas d'échec d'authentification Windows.|  
|Windows|Spécifie l'authentification intégrée Windows.|  
  
## <a name="proxycredentialtype-attribute"></a>Attribut proxyCredentialType  
  
|Valeur|Description|  
|-----------|-----------------|  
|None|-Les messages ne sont pas sécurisés lors du transfert.|  
|De base|Spécifie l’authentification de base telle que définie par RFC 2617 – Authentification HTTP : Authentification de base et Digest.|  
|Digest|Spécifie l'authentification Digest telle que définie par RFC 2617 – Authentification HTTP : Authentification de base et Digest.|  
|Ntlm|Spécifie l'authentification NTLM le cas échéant et en cas d'échec d'authentification Windows.|  
|Windows|Spécifie l'authentification intégrée Windows.|  
|Certificat|Effectue l'authentification du client à l'aide d'un certificat. Cette option fonctionne uniquement si l'attribut `Mode` de l'élément `security` parent est configuré pour le transport et ne fonctionnera pas s'il a la valeur TransportCredentialOnly.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucune  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|Définit les fonctionnalités de sécurité pour [\<basicHttpBinding>](basichttpbinding.md) .|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre l'utilisation de la sécurité de transport SSL avec la liaison de base. Par défaut, la liaison de base prend en charge la communication HTTP.  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [Securing Services and Clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
