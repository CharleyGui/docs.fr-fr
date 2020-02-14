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
ms.openlocfilehash: 2fdace8a9c7bcc090fd801be3bd717e4a2b34a87
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217550"
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat (MDA)
L’Assistant Débogage managé (MDA, Managed Debugging Assistant) `dateTimeInvalidLocalFormat` est activé quand une instance de <xref:System.DateTime> stockée en temps universel (UTC, Universal Coordinated Time) est mise en forme à l’aide d’un format conçu uniquement pour des instances de <xref:System.DateTime> locales. Cet Assistant Débogage managé n’est pas activé pour les instances de <xref:System.DateTime> par défaut ou non spécifiées.  
  
## <a name="symptom"></a>Symptôme  
 Une application sérialise manuellement une instance de <xref:System.DateTime> en temps universel à l’aide d’un format local :  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>Cause :  
 Le format « z » pour la méthode <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> inclut l’offset de fuseau horaire local, par exemple, « +10:00 » pour l’heure de Sydney. Comme tel, il ne produit un résultat significatif que si <xref:System.DateTime> a une valeur locale. S’il s’agit d’une valeur en heure UTC, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> inclut l’offset de fuseau horaire local, mais il n’affiche pas et n’ajuste pas le spécificateur de fuseau horaire.  
  
### <a name="resolution"></a>Résolution  
 Les instances de <xref:System.DateTime> en temps universel doivent être mises en forme d’une façon qui indique qu’elles sont au format UTC. Le format recommandé consiste à utiliser un « Z » pour désigner l’heure UTC :  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 Il existe également un format « o » qui sérialise <xref:System.DateTime> en utilisant la propriété <xref:System.DateTime.Kind%2A>, qui effectue une sérialisation correcte qu’il s’agisse d’une instance locale, en temps universel ou non spécifiée :  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Cet Assistant Débogage managé n’affecte pas le runtime.  
  
## <a name="output"></a>Output  
 Il n’y a aucune sortie spéciale résultant de l’activation de cet Assistant Débogage managé. Toutefois, la pile des appels peut être utilisée pour déterminer l’emplacement de l’appel à <xref:System.DateTime.ToString%2A> qui a activé l’Assistant Débogage managé.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Exemple  
 Prenons l’exemple d’une application qui sérialise indirectement une valeur <xref:System.DateTime> en temps universel en utilisant la classe <xref:System.Xml.XmlConvert> ou <xref:System.Data.DataSet> de la manière suivante.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 Les sérialisations de <xref:System.Xml.XmlConvert> et <xref:System.Data.DataSet> utilisent par défaut des formats locaux pour la sérialisation. Des options supplémentaires sont nécessaires pour sérialiser d’autres types de valeurs <xref:System.DateTime>, tels que le temps universel.  
  
 Pour cet exemple précis, passez `XmlDateTimeSerializationMode.RoundtripKind` à l’appel `ToString` sur `XmlConvert`. Les données sont sérialisées en heure UTC.  
  
 Si vous utilisez un <xref:System.Data.DataSet>, affectez la valeur <xref:System.Data.DataColumn.DateTimeMode%2A> à la propriété <xref:System.Data.DataColumn> sur l’objet <xref:System.Data.DataSetDateTime.Utc>.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Globalization.DateTimeFormatInfo>
- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
