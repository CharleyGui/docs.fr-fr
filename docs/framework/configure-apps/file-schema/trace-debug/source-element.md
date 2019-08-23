---
title: Élément <source>
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 55120e292ac2a2c822c5510563d1aa167ca921e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920454"
---
# <a name="source-element"></a>\<Élément > source
Spécifie une source de trace qui lance des messages de traçage.  
  
 \<configuration>  
\<system.diagnostics>  
\<sources>  
\<> source  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`name`|Attribut facultatif.<br /><br /> Spécifie le nom de la source de suivi.|  
|`switchName`|Attribut facultatif.<br /><br /> Spécifie le nom d’une instance de commutateur de trace dans l’application. Si le commutateur n’est pas identifié dans `<switches>` un élément, la valeur spécifie le niveau du commutateur.|  
|`switchType`|Attribut facultatif.<br /><br /> Spécifie le type du commutateur de trace. S’il est présent, le type doit être un nom de classe valide et ne peut pas être une chaîne vide.|  
|`extraAttribute`|Attribut facultatif.<br /><br /> Spécifie la valeur d’un attribut spécifique à la source de trace <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> identifié par la méthode pour cette source de suivi.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-source.md)|Contient des écouteurs qui collectent, stockent et acheminent des messages.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
|`sources`|Contient les sources de trace qui lancent des messages de traçage.|  
  
## <a name="remarks"></a>Notes  
 Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant montre comment utiliser l' `<source>` élément pour ajouter la source `mySource` de suivi et définir le niveau du commutateur source nommé `sourceSwitch`. Un écouteur de suivi de console est ajouté pour écrire des informations de traçage dans la console.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>    
  </system.diagnostics>   
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres de trace et de débogage](index.md)
- [Commutateurs de suivi](../../../debug-trace-profile/trace-switches.md)
