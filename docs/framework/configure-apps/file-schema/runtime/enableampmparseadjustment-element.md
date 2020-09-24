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
# <a name="enableampmparseadjustment-element"></a>Élément \<EnableAmPmParseAdjustment>

Détermine si les méthodes d’analyse de date et d’heure utilisent un ensemble de règles ajusté pour analyser les chaînes de date qui contiennent un jour, un mois, une heure et un indicateur AM/PM.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si les méthodes d’analyse de date et d’heure utilisent un ensemble de règles ajusté pour analyser les chaînes de date qui contiennent uniquement un jour, un mois, une heure et un indicateur AM/PM.|  
  
### <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|0|Les méthodes d’analyse de date et d’heure n’utilisent pas de règles ajustées pour analyser les chaînes de date qui contiennent uniquement un jour, un mois, une heure et un indicateur AM/PM.|  
|1|Les méthodes d’analyse de date et d’heure utilisent des règles ajustées pour analyser les chaînes de date qui contiennent uniquement un jour, un mois, une heure et un indicateur AM/PM.|  
  
### <a name="child-elements"></a>Éléments enfants  

 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes  

 L' `<EnableAmPmParseAdjustment>` élément contrôle la façon dont les méthodes suivantes analysent une chaîne de date contenant un jour et un mois numériques suivis d’une heure et d’un indicateur AM/PM (par exemple, « 4/10 6 AM ») :  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 Aucun autre modèle n’est affecté.  
  
 L' `<EnableAmPmParseAdjustment>` élément n’a aucun effet sur  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> les  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> méthodes,, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> et <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> .  
  
> [!IMPORTANT]
> Dans .NET Core et .NET Native, les règles d’analyse AM/PM ajustées sont activées par défaut.  
  
 Si la règle d’ajustement d’analyse n’est pas activée, le premier chiffre de la chaîne est interprété comme l’heure de l’horloge de 12 heures, et le reste de la chaîne, à l’exception de l’indicateur AM/PM, est ignoré. La date et l’heure retournées par la méthode d’analyse se composent de la date actuelle et de l’heure du jour extraite de la chaîne de date.  
  
 Si la règle d’ajustement de l’analyse est activée, la méthode d’analyse interprète le jour et le mois comme appartenant à l’année en cours et interprète l’heure comme l’heure de l’horloge de 12 heures.  
  
 Le tableau suivant illustre la différence de <xref:System.DateTime> valeur lorsque la <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> méthode est utilisée pour analyser la chaîne « 4/10 6 AM » avec la `<EnableAmPmParseAdjustment>` propriété de l’élément `enabled` définie sur « 0 » ou « 1 ». Elle suppose que la date du jour est le 5 janvier 2017 et affiche la date comme si elle était mise en forme à l’aide de la chaîne de format « G » de la culture spécifiée.  
  
|Nom de culture|activé = "0"|activé = "1"|  
|------------------|------------------|------------------|  
|fr-FR|1/5/2017 4:00:00|4/10/2017 6:00:00|  
|en-GB|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>Voir aussi

- [\<runtime> Appartient](runtime-element.md)
- [\<configuration> Appartient](../configuration-element.md)
