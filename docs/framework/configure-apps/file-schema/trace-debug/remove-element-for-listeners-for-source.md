---
title: <remove>, Élément de <listeners> pour<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 657e6db2af9b99b3bbf03afc6aab02c58a830f2d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153333"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="b8d6d-102">\<remove>, Élément de \<listeners> pour\<source></span><span class="sxs-lookup"><span data-stu-id="b8d6d-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="b8d6d-103">Supprime un écouteur de la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="b8d6d-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="b8d6d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8d6d-104">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8d6d-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b8d6d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b8d6d-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b8d6d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8d6d-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="b8d6d-107">Attributes</span></span>  
  
|<span data-ttu-id="b8d6d-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="b8d6d-108">Attribute</span></span>|<span data-ttu-id="b8d6d-109">Description</span><span class="sxs-lookup"><span data-stu-id="b8d6d-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="b8d6d-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="b8d6d-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="b8d6d-111">Nom de l’écouteur à supprimer de la `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="b8d6d-111">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8d6d-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b8d6d-112">Child Elements</span></span>  
 <span data-ttu-id="b8d6d-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b8d6d-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8d6d-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b8d6d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="b8d6d-115">Élément</span><span class="sxs-lookup"><span data-stu-id="b8d6d-115">Element</span></span>|<span data-ttu-id="b8d6d-116">Description</span><span class="sxs-lookup"><span data-stu-id="b8d6d-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b8d6d-117">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8d6d-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b8d6d-118">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="b8d6d-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="b8d6d-119">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="b8d6d-119">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="b8d6d-120">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="b8d6d-120">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="b8d6d-121">Spécifie les écouteurs qui collectent, stockent et acheminent les messages.</span><span class="sxs-lookup"><span data-stu-id="b8d6d-121">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8d6d-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="b8d6d-122">Remarks</span></span>  
 <span data-ttu-id="b8d6d-123">L' `<remove>` élément supprime un écouteur spécifié de la `Listeners` collection pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="b8d6d-123">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="b8d6d-124">Vous pouvez supprimer un élément de la `Listeners` collection pour une source de suivi par programmation en appelant la <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> méthode sur la <xref:System.Diagnostics.TraceSource.Listeners%2A> propriété de l' <xref:System.Diagnostics.TraceSource> instance.</span><span class="sxs-lookup"><span data-stu-id="b8d6d-124">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="b8d6d-125">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="b8d6d-125">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8d6d-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="b8d6d-126">Example</span></span>  
 <span data-ttu-id="b8d6d-127">L’exemple suivant montre comment utiliser l' `<remove>` élément avant d’utiliser l' `<add>` élément pour ajouter l’écouteur `console` à la `Listeners` collection pour la source de trace `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="b8d6d-127">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="b8d6d-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8d6d-128">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="b8d6d-129">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="b8d6d-129">Trace and Debug Settings Schema</span></span>](index.md)
- [\<clear>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="b8d6d-130">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="b8d6d-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
