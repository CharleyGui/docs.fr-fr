---
title: Conversion de chaînes en types de données .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
ms.openlocfilehash: 28c84b04bde045643158d8d2b9fed44b74334e77
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92688007"
---
# <a name="convert-strings-to-net-data-types"></a><span data-ttu-id="c3511-102">Convertir des chaînes en types de données .NET</span><span class="sxs-lookup"><span data-stu-id="c3511-102">Convert strings to .NET data types</span></span>

<span data-ttu-id="c3511-103">Si vous souhaitez convertir une chaîne en type de données .NET, utilisez la méthode **XmlConvert** conforme aux exigences de l’application.</span><span class="sxs-lookup"><span data-stu-id="c3511-103">If you want to convert a string to a .NET data type, use the **XmlConvert** method that fits the application requirements.</span></span> <span data-ttu-id="c3511-104">Pour une liste de toutes les méthodes de conversion disponibles dans la classe **XmlConvert** , consultez <xref:System.Xml.XmlConvert>.</span><span class="sxs-lookup"><span data-stu-id="c3511-104">For a list of all conversion methods available in the **XmlConvert** class, see <xref:System.Xml.XmlConvert>.</span></span>  
  
 <span data-ttu-id="c3511-105">La chaîne retournée par la méthode **ToString** est une version de la chaîne des données qui lui sont passées.</span><span class="sxs-lookup"><span data-stu-id="c3511-105">The string returned from the **ToString** method is a string version of the data that is passed in.</span></span> <span data-ttu-id="c3511-106">En outre, il existe plusieurs types .NET qui sont convertis à l’aide de la classe **XmlConvert** , mais ils n’utilisent pas les méthodes de la classe **System. Convert** .</span><span class="sxs-lookup"><span data-stu-id="c3511-106">Additionally, there are several .NET types that convert using the **XmlConvert** class yet they do not use the methods in the **System.Convert** class.</span></span> <span data-ttu-id="c3511-107">La classe **XmlConvert** est conforme à la spécification des types de données XSD (XML Schema Definition) et possède un type de données auquel **XmlConvert** peut être mappé.</span><span class="sxs-lookup"><span data-stu-id="c3511-107">The **XmlConvert** class follows the XML Schema (XSD) data type specification and has a data type that the **XmlConvert** can map to.</span></span>  
  
 <span data-ttu-id="c3511-108">Le tableau suivant répertorie les types de données .NET et les types de chaîne retournés à l’aide du mappage de type de données XSD (XML Schema).</span><span class="sxs-lookup"><span data-stu-id="c3511-108">The following table lists .NET data types and the string types that are returned using XML Schema (XSD) data type mapping.</span></span> <span data-ttu-id="c3511-109">Ces types .NET ne peuvent pas être traités à l’aide de **System. Convert** .</span><span class="sxs-lookup"><span data-stu-id="c3511-109">These .NET types cannot be processed using **System.Convert** .</span></span>  
  
|<span data-ttu-id="c3511-110">Type .NET</span><span class="sxs-lookup"><span data-stu-id="c3511-110">.NET type</span></span>|<span data-ttu-id="c3511-111">Chaîne retournée</span><span class="sxs-lookup"><span data-stu-id="c3511-111">String returned</span></span>|  
|-------------------------|---------------------|  
|<span data-ttu-id="c3511-112">Boolean</span><span class="sxs-lookup"><span data-stu-id="c3511-112">Boolean</span></span>|<span data-ttu-id="c3511-113">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="c3511-113">"true", "false"</span></span>|  
|<span data-ttu-id="c3511-114">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="c3511-114">Single.PositiveInfinity</span></span>|<span data-ttu-id="c3511-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="c3511-115">"INF"</span></span>|  
|<span data-ttu-id="c3511-116">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="c3511-116">Single.NegativeInfinity</span></span>|<span data-ttu-id="c3511-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="c3511-117">"-INF"</span></span>|  
|<span data-ttu-id="c3511-118">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="c3511-118">Double.PositiveInfinity</span></span>|<span data-ttu-id="c3511-119">"INF"</span><span class="sxs-lookup"><span data-stu-id="c3511-119">"INF"</span></span>|  
|<span data-ttu-id="c3511-120">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="c3511-120">Double.NegativeInfinity</span></span>|<span data-ttu-id="c3511-121">"-INF"</span><span class="sxs-lookup"><span data-stu-id="c3511-121">"-INF"</span></span>|  
|<span data-ttu-id="c3511-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="c3511-122">DateTime</span></span>|<span data-ttu-id="c3511-123">Le format est « yyyy-MM-ddTHH:mm:sszzzzzz » et ses sous-ensembles.</span><span class="sxs-lookup"><span data-stu-id="c3511-123">Format is "yyyy-MM-ddTHH:mm:sszzzzzz" and its subsets.</span></span>|  
|<span data-ttu-id="c3511-124">Timespan</span><span class="sxs-lookup"><span data-stu-id="c3511-124">Timespan</span></span>|<span data-ttu-id="c3511-125">Le format est PnYnMnTnHnMnS, c'est-à-dire que `P2Y10M15DT10H30M20S` indique une durée de 2 années, 10 mois, 15 jours, 10 heures, 30 minutes et 20 secondes.</span><span class="sxs-lookup"><span data-stu-id="c3511-125">Format is PnYnMnTnHnMnS that is, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10 hours, 30 minutes, and 20 seconds.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="c3511-126">Si vous convertissez l’un des types .NET figurant dans le tableau en une chaîne à l’aide de la méthode **ToString** , la chaîne retournée n’est pas le type de base, mais le type de chaîne XSD (XML Schema).</span><span class="sxs-lookup"><span data-stu-id="c3511-126">If converting any of the .NET types listed in the table to a string using the **ToString** method, the returned string is not the base type, but the XML Schema (XSD) string type.</span></span>  
  
 <span data-ttu-id="c3511-127">Le type des valeurs **DateTime** et **Timespan** diffère en ce sens que **DateTime** représente un moment donné dans le temps, alors que **TimeSpan** représente un intervalle de temps.</span><span class="sxs-lookup"><span data-stu-id="c3511-127">The **DateTime** and **Timespan** value type differs in that a **DateTime** represents an instant in time, whereas a **TimeSpan** represents a time interval.</span></span> <span data-ttu-id="c3511-128">Les formats **DateTime** et **Timespan** sont spécifiés dans la spécification des types de données XSD (XML Schema Definition).</span><span class="sxs-lookup"><span data-stu-id="c3511-128">The **DateTime** and **Timespan** formats are specified in the XML Schema (XSD) data types specification.</span></span> <span data-ttu-id="c3511-129">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c3511-129">For example:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim [date] As New DateTime(2001, 8, 4)  
writer.WriteElementString("Date", XmlConvert.ToString([date]))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
DateTime date = new DateTime (2001, 08, 04);  
writer.WriteElementString("Date", XmlConvert.ToString(date));  
```  
  
 <span data-ttu-id="c3511-130">**Sortie**</span><span class="sxs-lookup"><span data-stu-id="c3511-130">**Output**</span></span>  
  
 <span data-ttu-id="c3511-131">`<Date>2001-08-04T00:00:00</Date>`.</span><span class="sxs-lookup"><span data-stu-id="c3511-131">`<Date>2001-08-04T00:00:00</Date>`.</span></span>  
  
 <span data-ttu-id="c3511-132">Le code suivant convertit un entier en chaîne :</span><span class="sxs-lookup"><span data-stu-id="c3511-132">The following code converts an integer to a string:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim value As Int32 = 200  
writer.WriteElementString("Number", XmlConvert.ToString(value))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
Int32 value = 200;  
writer.WriteElementString("Number", XmlConvert.ToString(value));  
```  
  
 <span data-ttu-id="c3511-133">**Sortie**</span><span class="sxs-lookup"><span data-stu-id="c3511-133">**Output**</span></span>  
  
 `<Number>200</Number>`  
  
 <span data-ttu-id="c3511-134">Toutefois, si vous convertissez une chaîne en type **Boolean** , **Single** ou **double** , le type .net retourné n’est pas le même que le type retourné lors de l’utilisation de la classe **System. Convert** .</span><span class="sxs-lookup"><span data-stu-id="c3511-134">However, if you are converting a string to **Boolean** , **Single** , or **Double** , the .NET type that's returned is not the same as the type returned when using the **System.Convert** class.</span></span>  
  
## <a name="string-to-boolean"></a><span data-ttu-id="c3511-135">String vers Boolean</span><span class="sxs-lookup"><span data-stu-id="c3511-135">String to Boolean</span></span>  
 <span data-ttu-id="c3511-136">Le tableau suivant indique le type généré pour une chaîne d'entrée donnée durant la conversion d'une chaîne en type **Boolean** à l'aide de la méthode **ToBoolean** .</span><span class="sxs-lookup"><span data-stu-id="c3511-136">The following table shows what type is generated for the given input strings, when converting a string to **Boolean** using the **ToBoolean** method.</span></span>  
  
|<span data-ttu-id="c3511-137">Paramètre d'entrée de chaîne valide</span><span class="sxs-lookup"><span data-stu-id="c3511-137">Valid string input parameter</span></span>|<span data-ttu-id="c3511-138">Type de sortie .NET</span><span class="sxs-lookup"><span data-stu-id="c3511-138">.NET output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="c3511-139">"true"</span><span class="sxs-lookup"><span data-stu-id="c3511-139">"true"</span></span>|<span data-ttu-id="c3511-140">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="c3511-140">Boolean.True</span></span>|  
|<span data-ttu-id="c3511-141">"1"</span><span class="sxs-lookup"><span data-stu-id="c3511-141">"1"</span></span>|<span data-ttu-id="c3511-142">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="c3511-142">Boolean.True</span></span>|  
|<span data-ttu-id="c3511-143">"false"</span><span class="sxs-lookup"><span data-stu-id="c3511-143">"false"</span></span>|<span data-ttu-id="c3511-144">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="c3511-144">Boolean.False</span></span>|  
|<span data-ttu-id="c3511-145">"0"</span><span class="sxs-lookup"><span data-stu-id="c3511-145">"0"</span></span>|<span data-ttu-id="c3511-146">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="c3511-146">Boolean.False</span></span>|  
  
 <span data-ttu-id="c3511-147">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="c3511-147">For example, given the following XML:</span></span>  
  
 <span data-ttu-id="c3511-148">**Entrée**</span><span class="sxs-lookup"><span data-stu-id="c3511-148">**Input**</span></span>  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>
```  
  
 <span data-ttu-id="c3511-149">Tous deux peuvent être reconnus par le code suivant, et **bvalue** est **System.Boolean.True** :</span><span class="sxs-lookup"><span data-stu-id="c3511-149">Both can be understood by the following code, and **bvalue** is **System.Boolean.True** :</span></span>  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a><span data-ttu-id="c3511-150">String vers Single</span><span class="sxs-lookup"><span data-stu-id="c3511-150">String to Single</span></span>  
 <span data-ttu-id="c3511-151">Le tableau suivant indique le type généré pour une chaîne d'entrée donnée durant la conversion d'une chaîne en type **Single** à l'aide de la méthode **ToSingle** .</span><span class="sxs-lookup"><span data-stu-id="c3511-151">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToSingle** method.</span></span>  
  
|<span data-ttu-id="c3511-152">Paramètre d'entrée de chaîne valide</span><span class="sxs-lookup"><span data-stu-id="c3511-152">Valid string input parameter</span></span>|<span data-ttu-id="c3511-153">Type de sortie .NET</span><span class="sxs-lookup"><span data-stu-id="c3511-153">.NET output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="c3511-154">"INF"</span><span class="sxs-lookup"><span data-stu-id="c3511-154">"INF"</span></span>|<span data-ttu-id="c3511-155">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="c3511-155">Single.PositiveInfinity</span></span>|  
|<span data-ttu-id="c3511-156">"-INF"</span><span class="sxs-lookup"><span data-stu-id="c3511-156">"-INF"</span></span>|<span data-ttu-id="c3511-157">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="c3511-157">Single.NegativeInfinity</span></span>|  
  
## <a name="string-to-double"></a><span data-ttu-id="c3511-158">String vers Double</span><span class="sxs-lookup"><span data-stu-id="c3511-158">String to Double</span></span>  
 <span data-ttu-id="c3511-159">Le tableau suivant indique le type généré pour une chaîne d'entrée donnée durant la conversion d'une chaîne en type **Single** à l'aide de la méthode **ToDouble** .</span><span class="sxs-lookup"><span data-stu-id="c3511-159">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToDouble** method.</span></span>  
  
|<span data-ttu-id="c3511-160">Paramètre d'entrée de chaîne valide</span><span class="sxs-lookup"><span data-stu-id="c3511-160">Valid string input parameter</span></span>|<span data-ttu-id="c3511-161">Type de sortie .NET</span><span class="sxs-lookup"><span data-stu-id="c3511-161">.NET output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="c3511-162">"INF"</span><span class="sxs-lookup"><span data-stu-id="c3511-162">"INF"</span></span>|<span data-ttu-id="c3511-163">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="c3511-163">Double.PositiveInfinity</span></span>|  
|<span data-ttu-id="c3511-164">"-INF"</span><span class="sxs-lookup"><span data-stu-id="c3511-164">"-INF"</span></span>|<span data-ttu-id="c3511-165">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="c3511-165">Double.NegativeInfinity</span></span>|  
  
 <span data-ttu-id="c3511-166">Le code suivant écrit `<Infinity>INF</Infinity>` :</span><span class="sxs-lookup"><span data-stu-id="c3511-166">The following code writes `<Infinity>INF</Infinity>`:</span></span>  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3511-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3511-167">See also</span></span>

- [<span data-ttu-id="c3511-168">Conversion des types de données XML</span><span class="sxs-lookup"><span data-stu-id="c3511-168">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)
- [<span data-ttu-id="c3511-169">Conversion de types .NET en chaînes</span><span class="sxs-lookup"><span data-stu-id="c3511-169">Converting .NET Types to Strings</span></span>](converting-dotnet-types-to-strings.md)
