---
title: Élément <EnableAmPmParseAdjustment>
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f132ce0a114a6fc904d86ca3ce893c447366523f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252628"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="eb344-102">\<EnableAmPmParseAdjustment >, élément</span><span class="sxs-lookup"><span data-stu-id="eb344-102">\<EnableAmPmParseAdjustment> Element</span></span>
<span data-ttu-id="eb344-103">Détermine si les méthodes d’analyse de date et d’heure utilisent un ensemble de règles ajusté pour analyser les chaînes de date qui contiennent un jour, un mois, une heure et un indicateur AM/PM.</span><span class="sxs-lookup"><span data-stu-id="eb344-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
<span data-ttu-id="eb344-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="eb344-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="eb344-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="eb344-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="eb344-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<EnableAmPmParseAdjustment>**</span><span class="sxs-lookup"><span data-stu-id="eb344-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb344-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb344-107">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb344-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="eb344-108">Attributes and Elements</span></span>  
 <span data-ttu-id="eb344-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="eb344-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb344-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="eb344-110">Attributes</span></span>  
  
|<span data-ttu-id="eb344-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="eb344-111">Attribute</span></span>|<span data-ttu-id="eb344-112">Description</span><span class="sxs-lookup"><span data-stu-id="eb344-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="eb344-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="eb344-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="eb344-114">Spécifie si les méthodes d’analyse de date et d’heure utilisent un ensemble de règles ajusté pour analyser les chaînes de date qui contiennent uniquement un jour, un mois, une heure et un indicateur AM/PM.</span><span class="sxs-lookup"><span data-stu-id="eb344-114">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="eb344-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="eb344-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="eb344-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="eb344-116">Value</span></span>|<span data-ttu-id="eb344-117">Description</span><span class="sxs-lookup"><span data-stu-id="eb344-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="eb344-118">0</span><span class="sxs-lookup"><span data-stu-id="eb344-118">0</span></span>|<span data-ttu-id="eb344-119">Les méthodes d’analyse de date et d’heure n’utilisent pas de règles ajustées pour analyser les chaînes de date qui contiennent uniquement un jour, un mois, une heure et un indicateur AM/PM.</span><span class="sxs-lookup"><span data-stu-id="eb344-119">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="eb344-120">1</span><span class="sxs-lookup"><span data-stu-id="eb344-120">1</span></span>|<span data-ttu-id="eb344-121">Les méthodes d’analyse de date et d’heure utilisent des règles ajustées pour analyser les chaînes de date qui contiennent uniquement un jour, un mois, une heure et un indicateur AM/PM.</span><span class="sxs-lookup"><span data-stu-id="eb344-121">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb344-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="eb344-122">Child Elements</span></span>  
 <span data-ttu-id="eb344-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="eb344-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb344-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="eb344-124">Parent Elements</span></span>  
  
|<span data-ttu-id="eb344-125">Élément</span><span class="sxs-lookup"><span data-stu-id="eb344-125">Element</span></span>|<span data-ttu-id="eb344-126">Description</span><span class="sxs-lookup"><span data-stu-id="eb344-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="eb344-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eb344-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="eb344-128">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="eb344-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb344-129">Notes</span><span class="sxs-lookup"><span data-stu-id="eb344-129">Remarks</span></span>  
 <span data-ttu-id="eb344-130">L' `<EnableAmPmParseAdjustment>` élément contrôle la façon dont les méthodes suivantes analysent une chaîne de date contenant un jour et un mois numériques suivis d’une heure et d’un indicateur AM/PM (par exemple, « 4/10 6 AM ») :</span><span class="sxs-lookup"><span data-stu-id="eb344-130">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="eb344-131">Aucun autre modèle n’est affecté.</span><span class="sxs-lookup"><span data-stu-id="eb344-131">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="eb344-132">L' `<EnableAmPmParseAdjustment>` élément n’a aucun effet sur <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>les <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>méthodes <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>,, <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> et.</span><span class="sxs-lookup"><span data-stu-id="eb344-132">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="eb344-133">Dans .NET Core et .NET Native, les règles d’analyse AM/PM ajustées sont activées par défaut.</span><span class="sxs-lookup"><span data-stu-id="eb344-133">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="eb344-134">Si la règle d’ajustement d’analyse n’est pas activée, le premier chiffre de la chaîne est interprété comme l’heure de l’horloge de 12 heures, et le reste de la chaîne, à l’exception de l’indicateur AM/PM, est ignoré.</span><span class="sxs-lookup"><span data-stu-id="eb344-134">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="eb344-135">La date et l’heure retournées par la méthode d’analyse se composent de la date actuelle et de l’heure du jour extraite de la chaîne de date.</span><span class="sxs-lookup"><span data-stu-id="eb344-135">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="eb344-136">Si la règle d’ajustement de l’analyse est activée, la méthode d’analyse interprète le jour et le mois comme appartenant à l’année en cours et interprète l’heure comme l’heure de l’horloge de 12 heures.</span><span class="sxs-lookup"><span data-stu-id="eb344-136">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="eb344-137">Le tableau suivant <xref:System.DateTime> illustre la différence de valeur lorsque la <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> méthode est utilisée pour analyser la chaîne « 4/10 6 AM » avec la propriété de `enabled` l' `<EnableAmPmParseAdjustment>` élément définie sur « 0 » ou « 1 ».</span><span class="sxs-lookup"><span data-stu-id="eb344-137">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="eb344-138">Elle suppose que la date du jour est le 5 janvier 2017 et affiche la date comme si elle était mise en forme à l’aide de la chaîne de format « G » de la culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="eb344-138">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="eb344-139">Nom de la culture</span><span class="sxs-lookup"><span data-stu-id="eb344-139">Culture name</span></span>|<span data-ttu-id="eb344-140">enabled="0"</span><span class="sxs-lookup"><span data-stu-id="eb344-140">enabled="0"</span></span>|<span data-ttu-id="eb344-141">enabled="1"</span><span class="sxs-lookup"><span data-stu-id="eb344-141">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="eb344-142">en-US</span><span class="sxs-lookup"><span data-stu-id="eb344-142">en-US</span></span>|<span data-ttu-id="eb344-143">1/5/2017 4:00:00</span><span class="sxs-lookup"><span data-stu-id="eb344-143">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="eb344-144">4/10/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="eb344-144">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="eb344-145">en-GB</span><span class="sxs-lookup"><span data-stu-id="eb344-145">en-GB</span></span>|<span data-ttu-id="eb344-146">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="eb344-146">5/1/2017 6:00:00</span></span>|<span data-ttu-id="eb344-147">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="eb344-147">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eb344-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb344-148">See also</span></span>

- [<span data-ttu-id="eb344-149">\<Élément > du Runtime</span><span class="sxs-lookup"><span data-stu-id="eb344-149">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="eb344-150">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="eb344-150">\<configuration> Element</span></span>](../configuration-element.md)
