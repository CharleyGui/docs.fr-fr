---
title: <httpListener>, élément (paramètres réseau)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 78526559164939667eab8848bc5fd2af6749d474
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195439"
---
# <a name="httplistener-element-network-settings"></a>\<httpListener>, élément (paramètres réseau)

Personnalise les paramètres utilisés par la <xref:System.Net.HttpListener> classe.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpListener>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a>Type  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|unescapeRequestUrl|Valeur booléenne qui indique si une <xref:System.Net.HttpListener> instance utilise l’URI brut sans séquence d’échappement plutôt que l’URI converti.|  
  
### <a name="child-elements"></a>Éléments enfants  

 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Element**|**Description**|  
|-----------------|---------------------|  
|[settings](settings-element-network-settings.md)|Configure les options réseau de base pour l’espace de noms <xref:System.Net>.|  
  
## <a name="remarks"></a>Notes  

 L’attribut **unescapeRequestUrl** indique si <xref:System.Net.HttpListener> utilise l’URI brut sans séquence d’échappement à la place de l’URI converti dans lequel toutes les valeurs encodées en pourcentage sont converties et d’autres étapes de normalisation sont effectuées.  
  
 Lorsqu’une <xref:System.Net.HttpListener> instance reçoit une demande via le `http.sys` service, elle crée une instance de la chaîne d’URI fournie par `http.sys` et l’expose en tant que <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> propriété.  
  
 Le `http.sys` service expose deux chaînes d’URI de requête :  
  
- URI brut  
  
- URI converti  
  
 L’URI brut est le <xref:System.Uri?displayProperty=nameWithType> fourni dans la ligne de demande d’une requête http :  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 L’URI brut fourni par `http.sys` pour la demande mentionnée ci-dessus est « /Path/ ». Cela représente la chaîne qui suit le verbe HTTP tel qu’il a été envoyé sur le réseau.  
  
 Le `http.sys` service crée un URI converti à partir des informations fournies dans la demande à l’aide de l’URI fourni dans la ligne de requête HTTP et de l’en-tête de l’hôte pour déterminer le serveur d’origine vers lequel la demande doit être transférée. Pour ce faire, comparez les informations de la demande avec un ensemble de préfixes URI inscrits. La documentation du kit de développement logiciel (SDK) du serveur HTTP fait référence à cet URI converti en tant que structure HTTP_COOKED_URL.  
  
 Pour pouvoir comparer la demande aux préfixes d’URI inscrits, une certaine normalisation de la demande doit être effectuée. Pour l’exemple ci-dessus, l’URI converti serait le suivant :  
  
 `http://www.contoso.com/path/`  
  
 Le `http.sys` service combine la <xref:System.Uri.Host%2A?displayProperty=nameWithType> valeur de la propriété et la chaîne dans la ligne de demande pour créer un URI converti. En outre, `http.sys` la <xref:System.Uri?displayProperty=nameWithType> classe effectue également les opérations suivantes :  
  
- Annule l’échappement de toutes les valeurs encodées en pourcentage.  
  
- Convertit des caractères non-ASCII encodés en pourcentage en une représentation de caractères UTF-16. Notez que les caractères UTF-8 et ANSI/DBCS sont pris en charge, ainsi que les caractères Unicode (encodage Unicode utilisant le format% uXXXX).  
  
- Exécute d’autres étapes de normalisation, telles que la compression de chemin.  
  
 Étant donné que la demande ne contient pas d’informations sur l’encodage utilisé pour les valeurs encodées en pourcentage, il n’est pas possible de déterminer l’encodage correct en analysant uniquement les valeurs encodées en pourcentage.  
  
 `http.sys`Fournit donc deux clés de Registre pour la modification du processus :  
  
|Clé de Registre|Valeur par défaut|Description|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|Si la valeur est égale à zéro, `http.sys` accepte uniquement les URL encodées en UTF-8.<br /><br /> Si la valeur est différente de zéro, `http.sys` accepte également les URL codées en ANSI ou DBCS dans les demandes.|  
|FavorUTF8|1|Si la valeur est différente de zéro, `http.sys` tente toujours de décoder en premier une URL au format UTF-8. Si cette conversion échoue et que EnableNonUTF8 est différent de zéro, Http.sys essaie de la décoder en ANSI ou DBCS.<br /><br /> Si la valeur zéro (et EnableNonUTF8 est différente de zéro), `http.sys` tente de la décoder en ANSI ou DBCS ; si cela ne réussit pas, elle tente une conversion UTF-8.|  
  
 Lorsque <xref:System.Net.HttpListener> reçoit une requête, il utilise l’URI converti à partir de `http.sys` comme entrée à la <xref:System.Net.HttpListenerRequest.Url%2A> propriété.  
  
 Il est nécessaire de prendre en charge des caractères autres que des caractères et des nombres dans les URI. Par exemple, l’URI suivant est utilisé pour extraire les informations client pour le numéro de client « 1/3812 » :  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Notez la barre oblique encodée en pourcentage dans l’URI (% 2F). Cela est nécessaire, car dans ce cas, la barre oblique représente des données et non un délimiteur de chemin d’accès.  
  
 Le passage de la chaîne au constructeur d’URI entraîne l’URI suivant :  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Le fractionnement du tracé en ses segments entraînerait les éléments suivants :  
  
 `Customer('1`  
  
 `3812')`  
  
 Il ne s’agit pas de l’intention de l’expéditeur de la demande.  
  
 Si l’attribut **unescapeRequestUrl** est défini sur **false**, lorsque le <xref:System.Net.HttpListener> reçoit une requête, il utilise l’URI brut au lieu de l’URI converti à partir de `http.sys` comme entrée à la <xref:System.Net.HttpListenerRequest.Url%2A> propriété.  
  
 La valeur par défaut de l’attribut **unescapeRequestUrl** est **true**.  
  
 La <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> propriété peut être utilisée pour récupérer la valeur actuelle de l’attribut **unescapeRequestUrl** à partir des fichiers de configuration applicables.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment configurer la <xref:System.Net.HttpListener> classe lorsqu’elle reçoit une demande d’utilisation de l’URI brut au lieu de l’URI converti à partir d’une `http.sys` entrée de la <xref:System.Net.HttpListenerRequest.Url%2A> propriété.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|||
|-|-|  
|Espace de noms|System.Net|  
|Nom du schéma||  
|Fichier de validation||  
|Peut être vide||  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [Schéma des paramètres réseau](index.md)
