---
title: <TimeSpan_LegacyFormatMode>, élément
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31e2a075f9202439cd62c81a06528b20c4971656
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489336"
---
# <a name="timespanlegacyformatmode-element"></a>\<TimeSpan_LegacyFormatMode > élément
Détermine si le runtime conserve le comportement hérité dans les opérations avec la mise en forme <xref:System.TimeSpan?displayProperty=nameWithType> valeurs.  
  
 \<configuration>  
\<runtime>  
<TimeSpan_LegacyFormatMode>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime utilise le comportement de mise en forme hérité avec <xref:System.TimeSpan?displayProperty=nameWithType> valeurs.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Value|Description|  
|-----------|-----------------|  
|`false`|Le runtime ne restaure pas le comportement de mise en forme hérité.|  
|`true`|Le runtime restaure le comportement de mise en forme hérité.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes  
 En commençant par le .NET Framework 4, le <xref:System.TimeSpan?displayProperty=nameWithType> structure implémente le <xref:System.IFormattable> interface et prend en charge la mise en forme des opérations avec des chaînes de format standard et personnalisées. Si une méthode d’analyse rencontre un spécificateur de format non pris en charge ou de la chaîne de format, elle lève une <xref:System.FormatException>.  
  
 Dans les versions précédentes du .NET Framework, le <xref:System.TimeSpan> structure n’a pas implémenté <xref:System.IFormattable> et ne prenait pas en charge des chaînes de format. Toutefois, de nombreux développeurs supposé par erreur que <xref:System.TimeSpan> prenaient en charge un ensemble de chaînes de format et utilisé dans [opérations de mise en forme composite](../../../../../docs/standard/base-types/composite-formatting.md) avec des méthodes telles que <xref:System.String.Format%2A?displayProperty=nameWithType>. En règle générale, si un type implémente <xref:System.IFormattable> et prend en charge les chaînes, appels aux méthodes de formatage avec un format non pris en charge lèvent habituellement des chaînes de format un <xref:System.FormatException>. Toutefois, étant donné que <xref:System.TimeSpan> n’a pas implémenté <xref:System.IFormattable>, le runtime ignoré la chaîne de format et appelé à la place le <xref:System.TimeSpan.ToString?displayProperty=nameWithType> (méthode). Cela signifie que, bien que les chaînes de format n’avaient aucun effet sur l’opération de mise en forme, leur présence n’ont pas généré un <xref:System.FormatException>.  
  
 Pour les cas dans lesquels le code hérité passe un composite mise en forme de méthode et une chaîne de format non valide, et ce code ne peut pas être recompilé, vous pouvez utiliser la `<TimeSpan_LegacyFormatMode>` élément à restaurer les anciennes <xref:System.TimeSpan> comportement. Lorsque vous définissez la `enabled` attribut de l’élément `true`, la mise en forme des résultats de la méthode dans un appel à composite <xref:System.TimeSpan.ToString?displayProperty=nameWithType> plutôt que <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>et un <xref:System.FormatException> n’est pas levée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant instancie un <xref:System.TimeSpan> objet et tente de mettre en forme avec la <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> méthode en utilisant une chaîne de format standard non pris en charge.  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 Lorsque vous exécutez l’exemple sur le [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] ou sur une version antérieure, il affiche la sortie suivante :  
  
```  
12:30:45  
```  
  
 Cela diffère sensiblement de la sortie si vous exécutez l’exemple sur le .NET Framework 4 ou version ultérieure :  
  
```  
Invalid Format  
```  
  
 Toutefois, si vous ajoutez le fichier de configuration suivant au répertoire de l’exemple et puis exécutez l’exemple sur le .NET Framework 4 ou version ultérieure, la sortie est identique à celle produite par l’exemple lorsqu’il est exécuté sur [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
