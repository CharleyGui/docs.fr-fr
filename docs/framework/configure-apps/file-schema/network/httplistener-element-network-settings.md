---
title: <httpListener>, élément (paramètres réseau)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 3f75096681ab07dd6d4788fbded5ca5c4a024aef
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698192"
---
# <a name="httplistener-element-network-settings"></a>\<httpListener >, élément (paramètres réseau)
Personnalise les paramètres utilisés par la classe <xref:System.Net.HttpListener>.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<httpListener >**  
  
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
|unescapeRequestUrl|Valeur booléenne qui indique si une instance <xref:System.Net.HttpListener> utilise l’URI brut sans séquence d’échappement plutôt que l’URI converti.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[settings](settings-element-network-settings.md)|Configure les options réseau de base pour l’espace de noms <xref:System.Net>.|  
  
## <a name="remarks"></a>Notes  
 L’attribut **unescapeRequestUrl** indique si <xref:System.Net.HttpListener> utilise l’URI brut sans séquence d’échappement au lieu de l’URI converti dans lequel les valeurs encodées en pourcentage sont converties et d’autres étapes de normalisation sont effectuées.  
  
 Lorsqu’une instance de <xref:System.Net.HttpListener> reçoit une demande via le service `http.sys`, elle crée une instance de la chaîne d’URI fournie par `http.sys` et l’expose en tant que propriété <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType>.  
  
 Le service `http.sys` expose deux chaînes d’URI de requête :  
  
- URI brut  
  
- URI converti  
  
 L’URI brut est le <xref:System.Uri?displayProperty=nameWithType> fourni dans la ligne de demande d’une requête HTTP :  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 L’URI brut fourni par `http.sys` pour la demande mentionnée ci-dessus est « /Path/ ». Cela représente la chaîne qui suit le verbe HTTP tel qu’il a été envoyé sur le réseau.  
  
 Le service `http.sys` crée un URI converti à partir des informations fournies dans la demande à l’aide de l’URI fourni dans la ligne de requête HTTP et de l’en-tête de l’hôte pour déterminer le serveur d’origine vers lequel la demande doit être transférée. Pour ce faire, comparez les informations de la demande avec un ensemble de préfixes URI inscrits. La documentation du kit de développement logiciel (SDK) du serveur HTTP fait référence à cet URI converti comme structure HTTP_COOKED_URL.  
  
 Pour pouvoir comparer la demande aux préfixes d’URI inscrits, une certaine normalisation de la demande doit être effectuée. Pour l’exemple ci-dessus, l’URI converti serait le suivant :  
  
 `http://www.contoso.com/path/`  
  
 Le service `http.sys` combine la valeur de la propriété <xref:System.Uri.Host%2A?displayProperty=nameWithType> et la chaîne dans la ligne de demande pour créer un URI converti. En outre, `http.sys` et la classe <xref:System.Uri?displayProperty=nameWithType> effectuent également les opérations suivantes :  
  
- Annule l’échappement de toutes les valeurs encodées en pourcentage.  
  
- Convertit des caractères non-ASCII encodés en pourcentage en une représentation de caractères UTF-16. Notez que les caractères UTF-8 et ANSI/DBCS sont pris en charge, ainsi que les caractères Unicode (encodage Unicode utilisant le format% uXXXX).  
  
- Exécute d’autres étapes de normalisation, telles que la compression de chemin.  
  
 Étant donné que la demande ne contient pas d’informations sur l’encodage utilisé pour les valeurs encodées en pourcentage, il n’est pas possible de déterminer l’encodage correct en analysant uniquement les valeurs encodées en pourcentage.  
  
 Par conséquent `http.sys` fournit deux clés de Registre pour modifier le processus :  
  
|Clé de Registre|Valeur par défaut|Description|  
|------------------|-------------------|-----------------|  
|EnableNonUTF8|1|Si la valeur est zéro, `http.sys` accepte uniquement les URL encodées en UTF-8.<br /><br /> Si la valeur est différente de zéro, `http.sys` accepte également les URL encodées en ANSI ou DBCS dans les demandes.|  
|FavorUTF8|1|Si la valeur est différente de zéro, `http.sys` tente toujours de décoder une URL au format UTF-8 en premier ; Si cette conversion échoue et que EnableNonUTF8 est différent de zéro, http. sys essaie ensuite de le décoder en ANSI ou DBCS.<br /><br /> Si zéro (et EnableNonUTF8 est différent de zéro), `http.sys` essaie de le décoder en ANSI ou DBCS ; Si ce n’est pas le cas, il tente une conversion UTF-8.|  
  
 Lorsque <xref:System.Net.HttpListener> reçoit une requête, il utilise l’URI converti à partir de `http.sys` comme entrée de la propriété <xref:System.Net.HttpListenerRequest.Url%2A>.  
  
 Il est nécessaire de prendre en charge des caractères autres que des caractères et des nombres dans les URI. Par exemple, l’URI suivant est utilisé pour extraire les informations client pour le numéro de client « 1/3812 » :  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 Notez la barre oblique encodée en pourcentage dans l’URI (% 2F). Cela est nécessaire, car dans ce cas, la barre oblique représente des données et non un délimiteur de chemin d’accès.  
  
 Le passage de la chaîne au constructeur d’URI entraîne l’URI suivant :  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 Le fractionnement du tracé en ses segments entraînerait les éléments suivants :  
  
 `Customer('1`  
  
 `3812')`  
  
 Il ne s’agit pas de l’intention de l’expéditeur de la demande.  
  
 Si l’attribut **unescapeRequestUrl** est défini sur **false**, lorsque le <xref:System.Net.HttpListener> reçoit une requête, il utilise l’URI brut au lieu de l’URI converti à partir de `http.sys` comme entrée de la propriété <xref:System.Net.HttpListenerRequest.Url%2A>.  
  
 La valeur par défaut de l’attribut **unescapeRequestUrl** est **true**.  
  
 La propriété <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> peut être utilisée pour récupérer la valeur actuelle de l’attribut **unescapeRequestUrl** à partir des fichiers de configuration applicables.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment configurer la classe <xref:System.Net.HttpListener> lorsqu’elle reçoit une demande d’utilisation de l’URI brut au lieu de l’URI converti à partir de `http.sys` comme entrée de la propriété <xref:System.Net.HttpListenerRequest.Url%2A>.  
  
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
