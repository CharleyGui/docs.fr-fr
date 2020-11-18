---
title: Conversion de chaînes en types de données .NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
ms.openlocfilehash: 2eee3ff905473d8fd520929c0fe5abfb5d5c42da
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830959"
---
# <a name="convert-strings-to-net-data-types"></a>Convertir des chaînes en types de données .NET

Si vous souhaitez convertir une chaîne en type de données .NET, utilisez la méthode **XmlConvert** conforme aux exigences de l’application. Pour une liste de toutes les méthodes de conversion disponibles dans la classe **XmlConvert**, consultez <xref:System.Xml.XmlConvert>.  
  
 La chaîne retournée par la méthode **ToString** est une version de la chaîne des données qui lui sont passées. En outre, il existe plusieurs types .NET qui sont convertis à l’aide de la classe **XmlConvert** , mais ils n’utilisent pas les méthodes de la classe **System. Convert** . La classe **XmlConvert** est conforme à la spécification des types de données XSD (XML Schema Definition) et possède un type de données auquel **XmlConvert** peut être mappé.  
  
 Le tableau suivant répertorie les types de données .NET et les types de chaîne retournés à l’aide du mappage de type de données XSD (XML Schema). Ces types .NET ne peuvent pas être traités à l’aide de **System. Convert**.  
  
|Type .NET|Chaîne retournée|  
|-------------------------|---------------------|  
|Booléen|"true", "false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|Le format est « yyyy-MM-ddTHH:mm:sszzzzzz » et ses sous-ensembles.|  
|Timespan|Le format est PnYnMnTnHnMnS, c'est-à-dire que `P2Y10M15DT10H30M20S` indique une durée de 2 années, 10 mois, 15 jours, 10 heures, 30 minutes et 20 secondes.|  
  
> [!NOTE]
> Si vous convertissez l’un des types .NET figurant dans le tableau en une chaîne à l’aide de la méthode **ToString** , la chaîne retournée n’est pas le type de base, mais le type de chaîne XSD (XML Schema).  
  
 Le type des valeurs **DateTime** et **Timespan** diffère en ce sens que **DateTime** représente un moment donné dans le temps, alors que **TimeSpan** représente un intervalle de temps. Les formats **DateTime** et **Timespan** sont spécifiés dans la spécification des types de données XSD (XML Schema Definition). Par exemple :  
  
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
  
 **Sortie**  
  
 `<Date>2001-08-04T00:00:00</Date>`.  
  
 Le code suivant convertit un entier en chaîne :  
  
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
  
 **Sortie**  
  
 `<Number>200</Number>`  
  
 Toutefois, si vous convertissez une chaîne en type **Boolean**, **Single** ou **double**, le type .net retourné n’est pas le même que le type retourné lors de l’utilisation de la classe **System. Convert** .  
  
## <a name="string-to-boolean"></a>String vers Boolean  
 Le tableau suivant indique le type généré pour une chaîne d'entrée donnée durant la conversion d'une chaîne en type **Boolean** à l'aide de la méthode **ToBoolean**.  
  
|Paramètre d'entrée de chaîne valide|Type de sortie .NET|  
|----------------------------------|--------------------------------|  
|"true"|Boolean.True|  
|"1"|Boolean.True|  
|"false"|Boolean.False|  
|"0"|Boolean.False|  
  
 Examinons, par exemple, le code XML suivant :  
  
 **Entrée**  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>
```  
  
 Tous deux peuvent être reconnus par le code suivant, et **bvalue** est **System.Boolean.True** :  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a>String vers Single  
 Le tableau suivant indique le type généré pour une chaîne d'entrée donnée durant la conversion d'une chaîne en type **Single** à l'aide de la méthode **ToSingle**.  
  
|Paramètre d'entrée de chaîne valide|Type de sortie .NET|  
|----------------------------------|--------------------------------|  
|"INF"|Single.PositiveInfinity|  
|"-INF"|Single.NegativeInfinity|  
  
## <a name="string-to-double"></a>String vers Double  
 Le tableau suivant indique le type généré pour une chaîne d'entrée donnée durant la conversion d'une chaîne en type **Single** à l'aide de la méthode **ToDouble**.  
  
|Paramètre d'entrée de chaîne valide|Type de sortie .NET|  
|----------------------------------|--------------------------------|  
|"INF"|Double.PositiveInfinity|  
|"-INF"|Double.NegativeInfinity|  
  
 Le code suivant écrit `<Infinity>INF</Infinity>` :  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a>Voir aussi

- [Conversion des types de données XML](conversion-of-xml-data-types.md)
- [Conversion de types .NET en chaînes](converting-dotnet-types-to-strings.md)
