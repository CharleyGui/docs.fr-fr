---
title: <remove>, Élément de <listeners> pour<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: f06973ec30d5061e4a200d6bf7e68adcf6302018
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088843"
---
# <a name="remove-element-for-listeners-for-trace"></a>\<remove>, Élément de \<listeners> pour\<trace>
Supprime un écouteur de la collection d' **écouteurs** .  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**name**|Attribut requis.<br /><br /> Nom de l’écouteur à supprimer de la collection d' **écouteurs** .|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`listeners`|Spécifie un écouteur qui collecte, stocke et achemine des messages. Les écouteurs dirigent la sortie de suivi vers une cible appropriée.|  
|`system.diagnostics`|Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.|  
|`trace`|Configuration du service de trace ASP.NET.|  
  
## <a name="remarks"></a>Remarques  
  
> [!NOTE]
> La suppression du <xref:System.Diagnostics.DefaultTraceListener> de la `Listeners` collection altère le comportement des <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> méthodes,, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> et <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> . L’appel d’une `Assert` `Fail` méthode ou entraîne normalement l’affichage d’une boîte de message, mais la boîte de message ne s’affiche pas si le <xref:System.Diagnostics.DefaultTraceListener> n’est pas dans la `Listeners` collection.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment supprimer l’écouteur de suivi par défaut de la collection d' **écouteurs** de trace.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [Schéma des paramètres de traçage et de débogage](index.md)
