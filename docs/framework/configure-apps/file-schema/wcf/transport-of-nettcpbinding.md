---
title: <transport> de <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 4ef08ad73a03dea21d27217364a7bacb46a3848e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735933"
---
# <a name="transport-of-nettcpbinding"></a>\<transport> de \<netTcpBinding>
Définit le type d’exigences de sécurité au niveau du message pour un point de terminaison configuré avec le [\<NetTcpBinding](nettcpbinding.md).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<NetTcpBinding**](nettcpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< **\**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **&nbsp;&nbsp;\<** ](security-of-nettcpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netTcpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential">
      <transport clientCredentialType="None|Windows|Certificate"
                 protectionLevel="None|Sign|EncryptAndSign"
                 sslProtocols="Tls|Tls11|Tls12">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|clientCredentialType|Optionnel. Spécifie le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité de transport.<br /><br /> -La valeur par défaut est `Windows`.<br />-Cet attribut est de type <xref:System.ServiceModel.TcpClientCredentialType>.|  
|protectionLevel|Optionnel. Définit la sécurité au niveau du transport TCP. La signature des messages atténue le risque de modification par un tiers pendant le transfert. Le chiffrement garantit la confidentialité des données pendant le transport.<br /><br /> La valeur par défaut est `EncryptAndSign`.|  
|sslProtocols|Valeur d'indicateur d'énumération SslProtocols qui spécifie les protocoles SSL pris en charge. La valeur par défaut&#124;est&#124;TLS Tls11 Tls12.|  
|policyEnforcement|Cette énumération spécifie à quel moment <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> doit être appliqué.<br /><br /> 1. jamais : la stratégie n’est jamais appliquée (la protection étendue est désactivée).<br />2. WhenSupported : la stratégie est appliquée uniquement si le client prend en charge la protection étendue.<br />3. Always : la stratégie est toujours appliquée. Les clients qui ne prennent pas en charge la protection étendue ne pourront pas être authentifiés.|  
  
## <a name="clientcredentialtype-attribute"></a>Attribut clientCredentialType  
  
|valeur|Description|  
|-----------|-----------------|  
|aucune.|Le client est anonyme. Cela requiert un certificat pour le service.|  
|Windows|Spécifie l'authentification Windows du client à l'aide de la négociation SP (négociation Kerberos).|  
|Certificat|Le client est authentifié à l'aide d'un certificat. Cette valeur utilise la négociation SSL et requiert un certificat pour le service.|  
  
## <a name="protectionlevel-attribute"></a>protectionLevel, attribut  
  
|valeur|Description|  
|-----------|-----------------|  
|aucune.|Aucune protection.|  
|Sign|Les messages sont signés.|  
|EncryptAndSign|-Les messages sont chiffrés et signés.|  
  
### <a name="child-elements"></a>Éléments enfants  
 aucune.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[> de sécurité \<](security-of-nettcpbinding.md)|Spécifie les fonctionnalités de sécurité de la [\<NetTcpBinding](nettcpbinding.md).|  
  
## <a name="remarks"></a>Notes  
 Utilisez la sécurité de transport pour l'intégrité et la confidentialité du message SOAP et l'authentification mutuelle. Si ce mode de sécurité est sélectionné sur une liaison, la pile de canaux est configurée à l'aide d'un transport sécurisé et les messages SOAP sont sécurisés à l'aide d'une sécurité de transport, telle que Windows (Negotiate) ou SSL sur TCP.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [Sécurisation des services et des clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [Liaisons](../../../wcf/bindings.md)
- [Configuration des liaisons fournies par le système](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Utilisation de liaisons pour configurer des services et des clients](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [liaison de \<](bindings.md)
