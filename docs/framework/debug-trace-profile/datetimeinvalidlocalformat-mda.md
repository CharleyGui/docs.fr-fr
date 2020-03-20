---
title: dateTimeInvalidLocalFormat (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- dates [.NET Framework], formatting
- invalid date time local format
- invalid local formats
- MDAs (managed debugging assistants), invalid local formats
- managed debugging assistants (MDAs), invalid local formats
- dateTimeInvalidLocalFormat MDA
- date formatting
- time formatting
- UTC formatting
ms.assetid: c4a942bb-2651-4b65-8718-809f892a0659
ms.openlocfilehash: b01f030c474e426cb87fb907f99f241eeb76a7fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174756"
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="13f82-102">dateTimeInvalidLocalFormat (MDA)</span><span class="sxs-lookup"><span data-stu-id="13f82-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="13f82-103">L’Assistant Débogage managé (MDA, Managed Debugging Assistant) `dateTimeInvalidLocalFormat` est activé quand une instance de <xref:System.DateTime> stockée en temps universel (UTC, Universal Coordinated Time) est mise en forme à l’aide d’un format conçu uniquement pour des instances de <xref:System.DateTime> locales.</span><span class="sxs-lookup"><span data-stu-id="13f82-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="13f82-104">Cet Assistant Débogage managé n’est pas activé pour les instances de <xref:System.DateTime> par défaut ou non spécifiées.</span><span class="sxs-lookup"><span data-stu-id="13f82-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="13f82-105">Symptôme</span><span class="sxs-lookup"><span data-stu-id="13f82-105">Symptom</span></span>  
 <span data-ttu-id="13f82-106">Une application sérialise manuellement une instance de <xref:System.DateTime> en temps universel à l’aide d’un format local :</span><span class="sxs-lookup"><span data-stu-id="13f82-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="13f82-107">Cause :</span><span class="sxs-lookup"><span data-stu-id="13f82-107">Cause</span></span>  
 <span data-ttu-id="13f82-108">Le format « z » pour la méthode <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> inclut l’offset de fuseau horaire local, par exemple, « +10:00 » pour l’heure de Sydney.</span><span class="sxs-lookup"><span data-stu-id="13f82-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="13f82-109">Comme tel, il ne produit un résultat significatif que si <xref:System.DateTime> a une valeur locale.</span><span class="sxs-lookup"><span data-stu-id="13f82-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="13f82-110">S’il s’agit d’une valeur en heure UTC, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> inclut l’offset de fuseau horaire local, mais il n’affiche pas et n’ajuste pas le spécificateur de fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="13f82-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="13f82-111">Résolution</span><span class="sxs-lookup"><span data-stu-id="13f82-111">Resolution</span></span>  
 <span data-ttu-id="13f82-112">Les instances de <xref:System.DateTime> en temps universel doivent être mises en forme d’une façon qui indique qu’elles sont au format UTC.</span><span class="sxs-lookup"><span data-stu-id="13f82-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="13f82-113">Le format recommandé consiste à utiliser un « Z » pour désigner l’heure UTC :</span><span class="sxs-lookup"><span data-stu-id="13f82-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="13f82-114">Il existe également un format « o » qui sérialise <xref:System.DateTime> en utilisant la propriété <xref:System.DateTime.Kind%2A>, qui effectue une sérialisation correcte qu’il s’agisse d’une instance locale, en temps universel ou non spécifiée :</span><span class="sxs-lookup"><span data-stu-id="13f82-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="13f82-115">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="13f82-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="13f82-116">Cet Assistant Débogage managé n’affecte pas le runtime.</span><span class="sxs-lookup"><span data-stu-id="13f82-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="13f82-117">Output</span><span class="sxs-lookup"><span data-stu-id="13f82-117">Output</span></span>  
 <span data-ttu-id="13f82-118">Il n’y a aucune sortie spéciale résultant de l’activation de cet Assistant Débogage managé. Toutefois, la pile des appels peut être utilisée pour déterminer l’emplacement de l’appel à <xref:System.DateTime.ToString%2A> qui a activé l’Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="13f82-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="13f82-119">Configuration</span><span class="sxs-lookup"><span data-stu-id="13f82-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="13f82-120"> Exemple</span><span class="sxs-lookup"><span data-stu-id="13f82-120">Example</span></span>  
 <span data-ttu-id="13f82-121">Prenons l’exemple d’une application qui sérialise indirectement une valeur <xref:System.DateTime> en temps universel en utilisant la classe <xref:System.Xml.XmlConvert> ou <xref:System.Data.DataSet> de la manière suivante.</span><span class="sxs-lookup"><span data-stu-id="13f82-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="13f82-122">Les sérialisations de <xref:System.Xml.XmlConvert> et <xref:System.Data.DataSet> utilisent par défaut des formats locaux pour la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="13f82-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="13f82-123">Des options supplémentaires sont nécessaires pour sérialiser d’autres types de valeurs <xref:System.DateTime>, tels que le temps universel.</span><span class="sxs-lookup"><span data-stu-id="13f82-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="13f82-124">Pour cet exemple précis, passez `XmlDateTimeSerializationMode.RoundtripKind` à l’appel `ToString` sur `XmlConvert`.</span><span class="sxs-lookup"><span data-stu-id="13f82-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="13f82-125">Les données sont sérialisées en heure UTC.</span><span class="sxs-lookup"><span data-stu-id="13f82-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="13f82-126">Si vous utilisez un <xref:System.Data.DataSet>, affectez la valeur <xref:System.Data.DataSetDateTime.Utc> à la propriété <xref:System.Data.DataColumn.DateTimeMode%2A> sur l’objet <xref:System.Data.DataColumn>.</span><span class="sxs-lookup"><span data-stu-id="13f82-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="13f82-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13f82-127">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="13f82-128">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="13f82-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
