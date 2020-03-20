---
title: <network>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: f7cfcc3b9d5a717c23175cd15aa48ae97c828e57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154814"
---
# <a name="network-element-network-settings"></a>\<> element réseau (Paramètres réseau)
Configure les options réseau pour un serveur externe Simple Mail Transport Protocol (SMTP).  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>smtp**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>réseau**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<network  
  clientDomain="string"
  defaultCredentials="true|false"  
  enableSsl="true|false"  
  host="string"
  password="string"  
  port="integer"
  targetName="string"  
  userName="string"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`clientDomain`|Spécifie le nom de domaine client à utiliser dans la demande initiale de protocole SMTP pour se connecter au serveur de messagerie SMTP. La valeur par défaut est le nom localhost de l’ordinateur local d’envoi de la demande.|  
|`defaultCredentials`|Précise si les informations d’identification des utilisateurs par défaut doivent être utilisées pour accéder au serveur de messagerie SMTP pour les transactions SMTP. La valeur par défaut est `false`.|  
|`enableSsl`|Précise si SSL est utilisé pour accéder à un serveur de messagerie SMTP. La valeur par défaut est `false`.|  
|`host`|Spécifie le nom d’hôte du serveur de messagerie SMTP à utiliser pour les transactions SMTP. Cet attribut n’a aucune valeur par défaut.|  
|`password`|Spécifie le mot de passe à utiliser pour l’authentification du serveur de messagerie SMTP. Cet attribut n’a aucune valeur par défaut.|  
|`port`|Spécifie le numéro de port à utiliser pour se connecter au serveur de messagerie SMTP. La valeur par défaut est 25.|  
|`targetName`|Spécifie le nom du fournisseur de services (SPN) à utiliser pour l’authentification lors de l’utilisation d’une protection étendue pour les transactions SMTP. Cet attribut n’a aucune valeur par défaut.|  
|`userName`|Spécifie le nom d’utilisateur à utiliser pour l’authentification du serveur de messagerie SMTP. Cet attribut n’a aucune valeur par défaut.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<smtp> Element (Paramètres réseau)](smtp-element-network-settings.md)|Configure les options d’envoi de courrier simple par protocole de transport de courrier (SMTP).|  
  
## <a name="remarks"></a>Notes   
 Certains serveurs SMTP exigent que vous vous authentifiiez au serveur avant utilisation. Si vous souhaitez vous authentifier à l’aide `defaultCredentials` des `true`informations d’identification réseau par défaut de votre hôte, définissez l’attribut à . La <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> propriété peut être utilisée pour `defaultCredentials` obtenir la valeur actuelle de l’attribut à partir de fichiers de configuration applicables.  
  
 Vous pouvez également utiliser l’authentification de base (nom d’utilisateur et mot de passe) pour vous authentifier au serveur SMTP. Pour utiliser cette option, vous devez spécifier un nom d’utilisateur et un mot de passe valides pour le serveur SMTP spécifié.  
  
> [!NOTE]
> L’authentification `password` de base envoie le et les `userName` valeurs au serveur non chiffré. Toute personne surveillant le trafic réseau peut afficher vos informations d’identification et les utiliser pour se connecter au serveur. Vous devriez envisager d’utiliser un mécanisme d’authentification plus sécurisé, comme Kerberos ou NT LAN Manager (NTLM.) Si `defaultCredentials` `true`c’est , Kerberos ou NTLM sera utilisé si le serveur prend en charge ces protocoles.  
  
 Les options d’authentification de base et d’informations d’identification par défaut du réseau s’excluent mutuellement ; si vous `defaultCredentials` `true` définissez et spécifiez un nom d’utilisateur et un mot de passe, l’identifiant réseau par défaut est utilisé, et les données d’authentification de base sont ignorées.  
  
 Pour l’authentification `userName`de base si `password` vous spécifiez un , vous devez également spécifier un pour vous authentifier au serveur de messagerie.  
  
 La <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> propriété peut être utilisée pour `userName` obtenir la valeur actuelle de l’attribut à partir de fichiers de configuration applicables. La <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> propriété peut être utilisée pour `password` obtenir la valeur actuelle de l’attribut à partir de fichiers de configuration applicables. Un `password` attribut ne serait normalement pas entré dans les fichiers de configuration pour des raisons de sécurité.  
  
 L’attribut `clientDomain` modifie le nom de domaine du client utilisé dans la demande initiale de protocole SMTP à un serveur SMTP. L’attribut `clientDomain` peut être défini au nom de domaine entièrement qualifié de la machine locale, plutôt qu’au nom local d’host qui est utilisé par défaut. Cela permet une plus grande conformité aux normes du protocole SMTP. La valeur par défaut est le nom localhost de l’ordinateur local d’envoi de la demande. La <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> propriété peut être utilisée pour `clientDomain` obtenir la valeur actuelle de l’attribut à partir de fichiers de configuration applicables.  
  
 L’attribut `targetName` est utilisé pour l’authentification lors de l’utilisation d’une protection étendue. La valeur par défaut est du formulaire\<"SMTPSVC/ \<host>" où l’hôte> est le nom hôte du serveur de messagerie SMTP. La <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> propriété peut être utilisée pour `targetName` obtenir la valeur actuelle de l’attribut à partir de fichiers de configuration applicables.  
  
 L’attribut `enableSsl` précise si SSL est utilisé pour accéder à un serveur de messagerie SMTP. La <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> classe ne prend en charge que l’extension de service SMTP pour secure SMTP sur la sécurité des couches de transport telle que définie dans RFC 3207. Dans ce mode, la session SMTP commence sur un canal non crypté, puis une commande STARTTLS est délivrée par le client au serveur pour passer à la communication sécurisée à l’aide de SSL. Voir RFC 3207 publié par l’Internet Engineering Task Force (IETF) pour plus d’informations.  
  
 Une autre méthode de connexion est l’endroit où une session SSL est établie à l’avance avant que des commandes de protocole soient envoyées. Cette méthode de connexion est parfois appelée SMTPS et utilise par défaut le port 465. Cette méthode de connexion alternative utilisant SSL n’est pas actuellement prise en charge.  
  
 La <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> propriété peut être utilisée pour `enableSsl` obtenir la valeur actuelle de l’attribut à partir de fichiers de configuration applicables.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant spécifie les paramètres SMTP appropriés pour envoyer des e-mails à l’aide des informations d’identification réseau par défaut.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          clientDomain="www.contoso.com"  
          defaultCredentials="true"  
          enableSsl="false"  
          host="mail.contoso.com"  
          port="25"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [Paramètres réseau Schema](index.md)
