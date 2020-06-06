---
title: <idn>, élément (paramètres d’URI)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 533b2562f6e5c8d6c2bf452e56dff9a8bf8ab376
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698170"
---
# <a name="idn-element-uri-settings"></a>\<idn>, élément (paramètres d’URI)

Spécifie si l’analyse des IDN (Internationalized Domain Name) est appliquée à un nom de domaine.
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<idn>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<idn
  enabled="All|AllExceptIntranet|None"
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  

|**Appartient**|**Description**|  
|-----------------|---------------------|  
|`enabled`|Spécifie si l’analyse des IDN (Internationalized Domain Name) est appliquée à un nom de domaine. la valeur par défaut est None.|  

### <a name="child-elements"></a>Éléments enfants

Aucune
  
### <a name="parent-elements"></a>Éléments parents

|**Appartient**|**Description**|  
|-----------------|---------------------|  
|[uri](uri-element-uri-settings.md)|Contient des paramètres qui spécifient comment le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier).|  

## <a name="remarks"></a>Remarques

La <xref:System.Uri> classe existante a été étendue dans .NET Framework 3,5. 3,0 SP1 et 2,0 SP1 avec prise en charge des IRI (International Resource Identifiers) et des noms de domaine internationaux (IDN). Les utilisateurs actuels ne voient aucune modification du comportement .NET Framework 2,0, sauf s’ils activent spécifiquement la prise en charge des IRI et des IDN. Cela garantit la compatibilité des applications avec les versions antérieures de .NET Framework.

Pour activer la prise en charge des IRI, les deux modifications suivantes sont requises :

1. Ajoutez la ligne suivante au fichier machine. config dans le répertoire .NET Framework 2,0 :
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. Spécifiez si vous souhaitez appliquer l’analyse des IDN (Internationalized Domain Name) au nom de domaine et si les règles d’analyse IRI doivent être appliquées. Cela est spécifié dans le fichier machine.config ou app.config.

 Il existe trois valeurs possibles pour l’IDN selon les serveurs DNS utilisés :

- IDN activé = tous  

     Cette valeur convertit tous les noms de domaine Unicode en leurs équivalents Punycode (noms IDN).

- IDN activé = AllExceptIntranet

     Cette valeur convertit tous les noms de domaine Unicode qui ne se trouvent pas sur l’intranet local pour utiliser les équivalents Punycode (noms IDN). Dans ce cas, pour gérer les noms internationaux sur l’intranet local, les serveurs DNS utilisés pour l’intranet doivent prendre en charge la résolution de noms Unicode.

- IDN activé = aucun

     Cette valeur ne convertit aucun nom de domaine Unicode pour utiliser Punycode. Il s'agit de la valeur par défaut cohérente avec le comportement du .NET Framework 2.0.

 L’activation des IDN entraîne la conversion de toutes les étiquettes Unicode d’un nom de domaine en leurs équivalents Punycode. Les noms Punycode contiennent uniquement des caractères ASCII et commencent toujours par le préfixe xn--. Cela permet de garantir la prise en charge des serveurs DNS existants sur Internet, la plupart d’entre eux prenant uniquement en charge les caractères ASCII (consultez la norme RFC 3940).

### <a name="configuration-files"></a>Fichiers de configuration

Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).

## <a name="example"></a>Exemple

L’exemple suivant illustre une configuration utilisée par la <xref:System.Uri> classe pour prendre en charge l’analyse des IRI et les noms IDN :

```xml
<configuration>
  <uri>
    <idn enabled="All" />
    <iriParsing enabled="true" />
  </uri>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [Schéma des paramètres réseau](index.md)
