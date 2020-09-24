---
title: <iriParsing>, élément (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: ec2610e47957d5560bc7f51e0641afc9ba60c814
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158888"
---
# <a name="iriparsing-element-uri-settings"></a>\<iriParsing>, élément (paramètres d’URI)

Spécifie si l’analyse d’identificateur de ressource internationale (IRI) s’applique à un <xref:System.Uri> et si les règles d’analyse IRI doivent s’appliquer.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|**Element**|**Description**|  
|-----------------|---------------------|  
|`enabled`|Spécifie si l’analyse IRI est activée. La valeur par défaut est `false`.|  
  
### <a name="child-elements"></a>Éléments enfants  

 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Element**|**Description**|  
|-----------------|---------------------|  
|[uri](uri-element-uri-settings.md)|Contient des paramètres qui spécifient comment le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier).|  
  
## <a name="remarks"></a>Notes  

 La <xref:System.Uri> classe existante a été étendue dans .NET Framework 3,5. 3,0 SP1 et 2,0 SP1 pour assurer la prise en charge des IRI (International Resource Identifier) et des noms de domaine internationaux (IDN). Les utilisateurs actuels ne voient aucune modification du comportement .NET Framework 2,0, sauf s’ils activent spécifiquement la prise en charge des IRI et des IDN. Cela garantit la compatibilité des applications avec les versions antérieures de .NET Framework.  
  
 Pour activer la prise en charge des IRI, les deux modifications suivantes sont requises :  
  
1. Ajoutez la ligne suivante au fichier machine.config sous le répertoire .NET Framework 2,0  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. Spécifie si les règles d’analyse IRI doivent être appliquées. Cela est spécifié dans le fichier machine.config ou app.config.  
  
 L’activation de l’analyse IRI (iriParsing enabled = `true` ) effectue la normalisation et la vérification des caractères selon les dernières règles IRI de la norme RFC 3987. La valeur par défaut est et effectue la `false` normalisation et la vérification des caractères selon les spécifications rfc 2396 et rfc 3986 (pour les littéraux IPv6).  
  
### <a name="configuration-files"></a>Fichiers de configuration  

 Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  

 L’exemple suivant illustre une configuration utilisée par la <xref:System.Uri> classe pour prendre en charge l’analyse des IRI et les noms IDN.  
  
### <a name="code"></a>Code  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [Schéma des paramètres réseau](index.md)
