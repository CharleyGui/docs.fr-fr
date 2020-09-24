---
title: Élément <EnableAmPmParseAdjustment>
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
ms.openlocfilehash: f935f213e1bca8dac7a5401970bc6183575e2301
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167227"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="54ac4-102">Élément \<EnableAmPmParseAdjustment></span><span class="sxs-lookup"><span data-stu-id="54ac4-102">\<EnableAmPmParseAdjustment> Element</span></span>

<span data-ttu-id="54ac4-103">Détermine si les méthodes d’analyse de date et d’heure utilisent un ensemble de règles ajusté pour analyser les chaînes de date qui contiennent un jour, un mois, une heure et un indicateur AM/PM.</span><span class="sxs-lookup"><span data-stu-id="54ac4-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**  
  
## <a name="syntax"></a><span data-ttu-id="54ac4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54ac4-104">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54ac4-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="54ac4-105">Attributes and Elements</span></span>  

 <span data-ttu-id="54ac4-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="54ac4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54ac4-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="54ac4-107">Attributes</span></span>  
  
|<span data-ttu-id="54ac4-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="54ac4-108">Attribute</span></span>|<span data-ttu-id="54ac4-109">Description</span><span class="sxs-lookup"><span data-stu-id="54ac4-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="54ac4-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="54ac4-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="54ac4-111">Spécifie si les méthodes d’analyse de date et d’heure utilisent un ensemble de règles ajusté pour analyser les chaînes de date qui contiennent uniquement un jour, un mois, une heure et un indicateur AM/PM.</span><span class="sxs-lookup"><span data-stu-id="54ac4-111">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="54ac4-112">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="54ac4-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="54ac4-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="54ac4-113">Value</span></span>|<span data-ttu-id="54ac4-114">Description</span><span class="sxs-lookup"><span data-stu-id="54ac4-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="54ac4-115">0</span><span class="sxs-lookup"><span data-stu-id="54ac4-115">0</span></span>|<span data-ttu-id="54ac4-116">Les méthodes d’analyse de date et d’heure n’utilisent pas de règles ajustées pour analyser les chaînes de date qui contiennent uniquement un jour, un mois, une heure et un indicateur AM/PM.</span><span class="sxs-lookup"><span data-stu-id="54ac4-116">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="54ac4-117">1</span><span class="sxs-lookup"><span data-stu-id="54ac4-117">1</span></span>|<span data-ttu-id="54ac4-118">Les méthodes d’analyse de date et d’heure utilisent des règles ajustées pour analyser les chaînes de date qui contiennent uniquement un jour, un mois, une heure et un indicateur AM/PM.</span><span class="sxs-lookup"><span data-stu-id="54ac4-118">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54ac4-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="54ac4-119">Child Elements</span></span>  

 <span data-ttu-id="54ac4-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="54ac4-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54ac4-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="54ac4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="54ac4-122">Élément</span><span class="sxs-lookup"><span data-stu-id="54ac4-122">Element</span></span>|<span data-ttu-id="54ac4-123">Description</span><span class="sxs-lookup"><span data-stu-id="54ac4-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="54ac4-124">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54ac4-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="54ac4-125">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="54ac4-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54ac4-126">Notes</span><span class="sxs-lookup"><span data-stu-id="54ac4-126">Remarks</span></span>  

 <span data-ttu-id="54ac4-127">L' `<EnableAmPmParseAdjustment>` élément contrôle la façon dont les méthodes suivantes analysent une chaîne de date contenant un jour et un mois numériques suivis d’une heure et d’un indicateur AM/PM (par exemple, « 4/10 6 AM ») :</span><span class="sxs-lookup"><span data-stu-id="54ac4-127">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="54ac4-128">Aucun autre modèle n’est affecté.</span><span class="sxs-lookup"><span data-stu-id="54ac4-128">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="54ac4-129">L' `<EnableAmPmParseAdjustment>` élément n’a aucun effet sur  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> les  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> méthodes,, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> et <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="54ac4-129">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="54ac4-130">Dans .NET Core et .NET Native, les règles d’analyse AM/PM ajustées sont activées par défaut.</span><span class="sxs-lookup"><span data-stu-id="54ac4-130">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="54ac4-131">Si la règle d’ajustement d’analyse n’est pas activée, le premier chiffre de la chaîne est interprété comme l’heure de l’horloge de 12 heures, et le reste de la chaîne, à l’exception de l’indicateur AM/PM, est ignoré.</span><span class="sxs-lookup"><span data-stu-id="54ac4-131">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="54ac4-132">La date et l’heure retournées par la méthode d’analyse se composent de la date actuelle et de l’heure du jour extraite de la chaîne de date.</span><span class="sxs-lookup"><span data-stu-id="54ac4-132">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="54ac4-133">Si la règle d’ajustement de l’analyse est activée, la méthode d’analyse interprète le jour et le mois comme appartenant à l’année en cours et interprète l’heure comme l’heure de l’horloge de 12 heures.</span><span class="sxs-lookup"><span data-stu-id="54ac4-133">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="54ac4-134">Le tableau suivant illustre la différence de <xref:System.DateTime> valeur lorsque la <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> méthode est utilisée pour analyser la chaîne « 4/10 6 AM » avec la `<EnableAmPmParseAdjustment>` propriété de l’élément `enabled` définie sur « 0 » ou « 1 ».</span><span class="sxs-lookup"><span data-stu-id="54ac4-134">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="54ac4-135">Elle suppose que la date du jour est le 5 janvier 2017 et affiche la date comme si elle était mise en forme à l’aide de la chaîne de format « G » de la culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="54ac4-135">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="54ac4-136">Nom de culture</span><span class="sxs-lookup"><span data-stu-id="54ac4-136">Culture name</span></span>|<span data-ttu-id="54ac4-137">activé = "0"</span><span class="sxs-lookup"><span data-stu-id="54ac4-137">enabled="0"</span></span>|<span data-ttu-id="54ac4-138">activé = "1"</span><span class="sxs-lookup"><span data-stu-id="54ac4-138">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="54ac4-139">fr-FR</span><span class="sxs-lookup"><span data-stu-id="54ac4-139">en-US</span></span>|<span data-ttu-id="54ac4-140">1/5/2017 4:00:00</span><span class="sxs-lookup"><span data-stu-id="54ac4-140">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="54ac4-141">4/10/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="54ac4-141">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="54ac4-142">en-GB</span><span class="sxs-lookup"><span data-stu-id="54ac4-142">en-GB</span></span>|<span data-ttu-id="54ac4-143">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="54ac4-143">5/1/2017 6:00:00</span></span>|<span data-ttu-id="54ac4-144">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="54ac4-144">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54ac4-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54ac4-145">See also</span></span>

- [<span data-ttu-id="54ac4-146">\<runtime> Appartient</span><span class="sxs-lookup"><span data-stu-id="54ac4-146">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="54ac4-147">\<configuration> Appartient</span><span class="sxs-lookup"><span data-stu-id="54ac4-147">\<configuration> Element</span></span>](../configuration-element.md)
