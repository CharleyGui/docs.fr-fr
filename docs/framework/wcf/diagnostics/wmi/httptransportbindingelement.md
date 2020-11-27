---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 2be32591c4844cc6d5d0f02916dd1563bb15dc2a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288786"
---
# <a name="httptransportbindingelement"></a>HttpTransportBindingElement

HttpTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class HttpTransportBindingElement : TransportBindingElement  
{  
  boolean AllowCookies;  
  string AuthenticationScheme;  
  boolean BypassProxyOnLocal;  
  string HostNameComparisonMode;  
  boolean KeepAliveEnabled;  
  sint32 MaxBufferSize;  
  string ProxyAddress;  
  string ProxyAuthenticationScheme;  
  string Realm;  
  string TransferMode;  
  boolean UnsafeConnectionNtlmAuthentication;  
  boolean UseDefaultWebProxy;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe HttpTransportBindingElement ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  

 La classe HttpTransportBindingElement a les propriétés suivantes :  
  
### <a name="allowcookies"></a>AllowCookies  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Valeur qui indique si le client accepte les cookies et les propage aux demandes suivantes.  
  
### <a name="authenticationscheme"></a>AuthenticationScheme  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Schéma d'authentification utilisé pour authentifier les demandes d'un client traitées par un écouteur HTTP.  
  
### <a name="bypassproxyonlocal"></a>BypassProxyOnLocal  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Valeur qui indique si les proxys sont ignorés pour les adresses locales.  
  
### <a name="hostnamecomparisonmode"></a>HostNameComparisonMode  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Valeur qui indique si le nom d'hôte est utilisé pour atteindre le service lors de la correspondance avec l'URI.  
  
### <a name="keepaliveenabled"></a>KeepAliveEnabled  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 En cas d'activation, les connexions HTTP sont maintenues indépendamment du niveau d'activité.  
  
### <a name="maxbuffersize"></a>MaxBufferSize  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 La taille maximale du pool de mémoires tampons.  
  
### <a name="proxyaddress"></a>ProxyAddress  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 URI qui contient l'adresse du proxy à utiliser pour les requêtes HTTP.  
  
### <a name="proxyauthenticationscheme"></a>ProxyAuthenticationScheme  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Schéma d'authentification utilisé pour authentifier les demandes d'un client traitées par un proxy HTTP.  
  
### <a name="realm"></a>Realm  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Domaine d'authentification.  
  
### <a name="transfermode"></a>TransferMode  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Valeur qui spécifie si les messages sont mis en mémoire tampon ou transmis en continu ou s'il s'agit d'une demande ou d'une réponse.  
  
### <a name="unsafeconnectionntlmauthentication"></a>UnsafeConnectionNtlmAuthentication  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Valeur qui indique si le partage de connexion non sécurisé est activé sur le serveur.  
  
### <a name="usedefaultwebproxy"></a>UseDefaultWebProxy  

 Type de données : booléen  
  
 Type d'accès : Lecture seule  
  
 Valeur qui indique si les paramètres de proxy à l'échelle de l'ordinateur sont utilisés à la place des paramètres propres à l'utilisateur.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
