---
title: <httpWebRequest>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: fa00aed2cd1e96ec788d4bc9c1c63f20561d8d1c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698183"
---
# <a name="httpwebrequest-element-network-settings"></a>\<httpWebRequest >, élément (paramètres réseau)
Personnalise les paramètres de la demande Web.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<httpWebRequest >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|**Attribut**|**Description**|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|Spécifie la longueur maximale d’un en-tête de réponse, en kilo-octets. La valeur par défaut est 64. La valeur-1 indique qu’aucune limite de taille n’est imposée sur les en-têtes de réponse.|  
|`maximumErrorResponseLength`|Spécifie la longueur maximale d’une réponse d’erreur, en kilo-octets. La valeur par défaut est 64. La valeur-1 indique qu’aucune limite de taille n’est imposée à la réponse d’erreur.|  
|`maximumUnauthorizedUploadLength`|Spécifie la longueur maximale d’un téléchargement en réponse à un code d’erreur non autorisé, en octets. La valeur par défaut est -1. La valeur-1 indique qu’aucune limite de taille n’est imposée au chargement.|  
|`useUnsafeHeaderParsing`|Spécifie si l’analyse d’en-tête non sécurisé est activée. La valeur par défaut est `false`.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[settings](settings-element-network-settings.md)|Configure les options réseau de base pour l’espace de noms <xref:System.Net>.|  
  
## <a name="remarks"></a>Notes  
 Par défaut, le .NET Framework applique strictement la norme RFC 2616 pour l’analyse d’URI. Certaines réponses du serveur peuvent inclure des caractères de contrôle dans les champs interdits, ce qui entraîne la levée d’une <xref:System.Net.WebException> par la méthode <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType>. Si **UseUnsafeHeaderParsing** a la valeur **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> ne lève pas d’exception dans ce cas ; Toutefois, votre application est vulnérable à plusieurs formes d’attaques d’analyse d’URI. La meilleure solution consiste à modifier le serveur afin que la réponse n’inclue pas les caractères de contrôle.  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier une longueur d’en-tête maximale supérieure à la normale.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [Schéma des paramètres réseau](index.md)
