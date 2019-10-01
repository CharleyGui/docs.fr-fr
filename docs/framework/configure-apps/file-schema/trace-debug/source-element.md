---
title: Élément <source>
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: c4f7e31422ccd8129599db1120f9b0cb327d9319
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697208"
---
# <a name="source-element"></a><span data-ttu-id="e29d7-102">Élément @no__t 0source ></span><span class="sxs-lookup"><span data-stu-id="e29d7-102">\<source> Element</span></span>
<span data-ttu-id="e29d7-103">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="e29d7-103">Specifies a trace source that initiates tracing messages.</span></span>  
  
[<span data-ttu-id="e29d7-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="e29d7-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="e29d7-105">&nbsp; @ no__t-1[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="e29d7-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="e29d7-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="e29d7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="e29d7-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<source >**</span><span class="sxs-lookup"><span data-stu-id="e29d7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e29d7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e29d7-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e29d7-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e29d7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e29d7-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e29d7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e29d7-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="e29d7-111">Attributes</span></span>  
  
|<span data-ttu-id="e29d7-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="e29d7-112">Attribute</span></span>|<span data-ttu-id="e29d7-113">Description</span><span class="sxs-lookup"><span data-stu-id="e29d7-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="e29d7-114">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e29d7-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e29d7-115">Spécifie le nom de la source de suivi.</span><span class="sxs-lookup"><span data-stu-id="e29d7-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="e29d7-116">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e29d7-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e29d7-117">Spécifie le nom d’une instance de commutateur de trace dans l’application.</span><span class="sxs-lookup"><span data-stu-id="e29d7-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="e29d7-118">Si le commutateur n’est pas identifié dans un élément `<switches>`, la valeur spécifie le niveau du commutateur.</span><span class="sxs-lookup"><span data-stu-id="e29d7-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="e29d7-119">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e29d7-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e29d7-120">Spécifie le type du commutateur de trace.</span><span class="sxs-lookup"><span data-stu-id="e29d7-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="e29d7-121">S’il est présent, le type doit être un nom de classe valide et ne peut pas être une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="e29d7-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="e29d7-122">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e29d7-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e29d7-123">Spécifie la valeur d’un attribut spécifique à la source de trace identifié par la méthode <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> pour cette source de suivi.</span><span class="sxs-lookup"><span data-stu-id="e29d7-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e29d7-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e29d7-124">Child Elements</span></span>  
  
|<span data-ttu-id="e29d7-125">Élément</span><span class="sxs-lookup"><span data-stu-id="e29d7-125">Element</span></span>|<span data-ttu-id="e29d7-126">Description</span><span class="sxs-lookup"><span data-stu-id="e29d7-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e29d7-127">\<listeners></span><span class="sxs-lookup"><span data-stu-id="e29d7-127">\<listeners></span></span>](listeners-element-for-source.md)|<span data-ttu-id="e29d7-128">Contient des écouteurs qui collectent, stockent et acheminent des messages.</span><span class="sxs-lookup"><span data-stu-id="e29d7-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e29d7-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e29d7-129">Parent Elements</span></span>  
  
|<span data-ttu-id="e29d7-130">Élément</span><span class="sxs-lookup"><span data-stu-id="e29d7-130">Element</span></span>|<span data-ttu-id="e29d7-131">Description</span><span class="sxs-lookup"><span data-stu-id="e29d7-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e29d7-132">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e29d7-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e29d7-133">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="e29d7-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="e29d7-134">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="e29d7-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e29d7-135">Notes</span><span class="sxs-lookup"><span data-stu-id="e29d7-135">Remarks</span></span>  
 <span data-ttu-id="e29d7-136">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (machine. config) et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="e29d7-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e29d7-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="e29d7-137">Example</span></span>  
 <span data-ttu-id="e29d7-138">L’exemple suivant montre comment utiliser l’élément `<source>` pour ajouter la source de suivi `mySource` et pour définir le niveau du commutateur source nommé `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="e29d7-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="e29d7-139">Un écouteur de suivi de console est ajouté pour écrire des informations de traçage dans la console.</span><span class="sxs-lookup"><span data-stu-id="e29d7-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e29d7-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e29d7-140">See also</span></span>

- [<span data-ttu-id="e29d7-141">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="e29d7-141">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e29d7-142">Commutateurs de suivi</span><span class="sxs-lookup"><span data-stu-id="e29d7-142">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
