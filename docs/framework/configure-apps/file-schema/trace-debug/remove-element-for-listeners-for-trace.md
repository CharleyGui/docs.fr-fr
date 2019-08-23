---
title: <remove>, Élément <listeners> de pour<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: 0c5c9efb8a22d26ea5d4467f9628af5935d6dbad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920476"
---
# <a name="remove-element-for-listeners-for-trace"></a>\<supprimer > élément pour \<les écouteurs > pour \<la trace >
Supprime un écouteur de la collection d' **écouteurs** .  
  
 \<configuration>  
\<system.diagnostics>  
\<> de trace  
\<listeners>  
\<remove>  
  
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
|`trace`|Configure le service de trace ASP.NET.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> La suppression <xref:System.Diagnostics.DefaultTraceListener> du de `Listeners` la <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>collection altère <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>le <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> comportement des méthodes, ,et.<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> L’appel `Assert` d' `Fail` une méthode ou entraîne normalement l’affichage d’une boîte de message, mais la boîte de message ne s' <xref:System.Diagnostics.DefaultTraceListener> affiche pas si le `Listeners` n’est pas dans la collection.  
  
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
- [Schéma des paramètres de trace et de débogage](index.md)
