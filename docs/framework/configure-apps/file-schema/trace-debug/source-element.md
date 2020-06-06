---
title: Élément <source>
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 417722ce2f3865350158413307495e3ab435d386
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153293"
---
# <a name="source-element"></a><span data-ttu-id="6d11a-102">Élément \<source></span><span class="sxs-lookup"><span data-stu-id="6d11a-102">\<source> Element</span></span>
<span data-ttu-id="6d11a-103">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="6d11a-103">Specifies a trace source that initiates tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**

## <a name="syntax"></a><span data-ttu-id="6d11a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d11a-104">Syntax</span></span>  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d11a-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6d11a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6d11a-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6d11a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d11a-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="6d11a-107">Attributes</span></span>  
  
|<span data-ttu-id="6d11a-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="6d11a-108">Attribute</span></span>|<span data-ttu-id="6d11a-109">Description</span><span class="sxs-lookup"><span data-stu-id="6d11a-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="6d11a-110">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="6d11a-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6d11a-111">Spécifie le nom de la source de suivi.</span><span class="sxs-lookup"><span data-stu-id="6d11a-111">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="6d11a-112">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="6d11a-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6d11a-113">Spécifie le nom d’une instance de commutateur de trace dans l’application.</span><span class="sxs-lookup"><span data-stu-id="6d11a-113">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="6d11a-114">Si le commutateur n’est pas identifié dans un `<switches>` élément, la valeur spécifie le niveau du commutateur.</span><span class="sxs-lookup"><span data-stu-id="6d11a-114">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="6d11a-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="6d11a-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6d11a-116">Spécifie le type du commutateur de trace.</span><span class="sxs-lookup"><span data-stu-id="6d11a-116">Specifies the type of the trace switch.</span></span> <span data-ttu-id="6d11a-117">S’il est présent, le type doit être un nom de classe valide et ne peut pas être une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="6d11a-117">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="6d11a-118">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="6d11a-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6d11a-119">Spécifie la valeur d’un attribut spécifique à la source de trace identifié par la <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> méthode pour cette source de suivi.</span><span class="sxs-lookup"><span data-stu-id="6d11a-119">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d11a-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6d11a-120">Child Elements</span></span>  
  
|<span data-ttu-id="6d11a-121">Élément</span><span class="sxs-lookup"><span data-stu-id="6d11a-121">Element</span></span>|<span data-ttu-id="6d11a-122">Description</span><span class="sxs-lookup"><span data-stu-id="6d11a-122">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-source.md)|<span data-ttu-id="6d11a-123">Contient des écouteurs qui collectent, stockent et acheminent des messages.</span><span class="sxs-lookup"><span data-stu-id="6d11a-123">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6d11a-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6d11a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="6d11a-125">Élément</span><span class="sxs-lookup"><span data-stu-id="6d11a-125">Element</span></span>|<span data-ttu-id="6d11a-126">Description</span><span class="sxs-lookup"><span data-stu-id="6d11a-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6d11a-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6d11a-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6d11a-128">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="6d11a-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="6d11a-129">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="6d11a-129">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d11a-130">Remarques</span><span class="sxs-lookup"><span data-stu-id="6d11a-130">Remarks</span></span>  
 <span data-ttu-id="6d11a-131">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="6d11a-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d11a-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="6d11a-132">Example</span></span>  
 <span data-ttu-id="6d11a-133">L’exemple suivant montre comment utiliser l' `<source>` élément pour ajouter la source de suivi `mySource` et définir le niveau du commutateur source nommé `sourceSwitch` .</span><span class="sxs-lookup"><span data-stu-id="6d11a-133">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="6d11a-134">Un écouteur de suivi de console est ajouté pour écrire des informations de traçage dans la console.</span><span class="sxs-lookup"><span data-stu-id="6d11a-134">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6d11a-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d11a-135">See also</span></span>

- [<span data-ttu-id="6d11a-136">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="6d11a-136">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6d11a-137">Commutateurs de traçage</span><span class="sxs-lookup"><span data-stu-id="6d11a-137">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
