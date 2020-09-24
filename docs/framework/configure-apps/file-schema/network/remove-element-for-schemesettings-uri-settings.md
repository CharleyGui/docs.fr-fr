---
title: <remove>, élément de schemeSettings (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: 018a08693a39bb297bdaa468ba59d4bf097f6922
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151387"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a>\<remove>, élément de schemeSettings (paramètres d’URI)

Supprime un paramètre de schéma pour un nom de schéma.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Nom du schéma auquel ce paramètre s’applique. Les seules valeurs prises en charge sont Name = "http" et Name = "https".|  
  
### <a name="child-elements"></a>Éléments enfants  

 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<schemeSettings> , Élément (paramètres d’URI)](schemesettings-element-uri-settings.md)|Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.|  
  
## <a name="remarks"></a>Notes  

 Par défaut, la <xref:System.Uri?displayProperty=nameWithType> classe annule l’échappement des délimiteurs de chemin d’accès encodés en pourcentage avant d’exécuter la compression de chemin d’accès. Cela a été implémenté comme un mécanisme de sécurité contre les attaques telles que les suivantes :  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Si cet URI est passé aux modules qui ne gèrent pas correctement les caractères encodés en pourcentage, cela peut entraîner l’exécution de la commande suivante par le serveur :  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Pour cette raison, la <xref:System.Uri?displayProperty=nameWithType> classe First annule les délimiteurs de chemin d’accès, puis applique la compression de chemin d’accès. Le résultat de la transmission de l’URL malveillante ci-dessus au <xref:System.Uri?displayProperty=nameWithType> constructeur de classe génère l’URI suivant :  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Ce comportement par défaut peut être modifié pour éviter les délimiteurs de chemin d’accès encodés de pourcentage à l’aide de l’option de configuration schemeSettings pour un schéma spécifique.  
  
## <a name="configuration-files"></a>Fichiers de configuration  

 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant illustre une configuration utilisée par la <xref:System.Uri> classe qui supprime tous les paramètres de schéma pour le schéma http.  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [Schéma des paramètres réseau](index.md)
