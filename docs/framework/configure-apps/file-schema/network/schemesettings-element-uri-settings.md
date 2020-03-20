---
title: <schemeSettings>, élément (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154645"
---
# <a name="schemesettings-element-uri-settings"></a>\<schemeSettings, élément (paramètres d’Uri)
Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<schémasSettings>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 None  
  
### <a name="child-elements"></a>Éléments enfants  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[ajouter](add-element-for-schemesettings-uri-settings.md)|Ajoute un paramètre de régime pour un nom de régime.|  
|[Clair](clear-element-for-schemesettings-uri-settings.md)|Efface tous les paramètres de schéma existants.|  
|[retirer](remove-element-for-schemesettings-uri-settings.md)|Supprime un paramètre de régime pour un nom de régime.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[Uri](uri-element-uri-settings.md)|Contient des paramètres qui spécifient comment le cadre .NET gère les adresses Web exprimées à l’aide d’identifiants de ressources uniformes (IER).|  
  
## <a name="remarks"></a>Notes   
 Par défaut, <xref:System.Uri?displayProperty=nameWithType> la classe n’échappe pas pour cent encodé les délimitations de chemin avant d’exécuter la compression de chemin. Ceci a été mis en œuvre comme un mécanisme de sécurité contre des attaques comme les suivantes:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Si cette URI est transmise à des modules ne manipulant pas les pourcentage de caractères codés correctement, cela pourrait entraîner l’exécution de la commande suivante par le serveur :  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Pour cette <xref:System.Uri?displayProperty=nameWithType> raison, la classe d’abord délimiters chemin d’évacuation et applique ensuite la compression de chemin. Le résultat de la transmission <xref:System.Uri?displayProperty=nameWithType> de l’URL malveillante ci-dessus au constructeur de classe se traduit par l’URI suivante:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Ce comportement par défaut peut être modifié pour ne pas délimiters chemin décodé pour un moyen d’évasion encodé en utilisant l’option de configuration schemeSettings pour un schéma spécifique.  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre une <xref:System.Uri> configuration utilisée par la classe pour soutenir ne pas échapper à des délimitations de chemin encodé pour le système http.  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|||
|-|-|  
|Espace de noms|Système|  
|Nom du schéma||  
|Fichier de validation||  
|Peut être vide||  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [Paramètres réseau Schema](index.md)
