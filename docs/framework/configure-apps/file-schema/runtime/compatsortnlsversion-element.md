---
title: Élément <CompatSortNLSVersion>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
ms.openlocfilehash: 30afeb2ab9380db75cbeb723ea15a23e4313c9e8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154268"
---
# <a name="compatsortnlsversion-element"></a>Élément \<CompatSortNLSVersion>
Spécifie que le runtime doit utiliser des ordres de tri hérités lors de l'exécution de comparaisons de chaînes.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<CompatSortNLSVersion>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<CompatSortNLSVersion
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie l'ID de paramètres régionaux dont l'ordre de tri doit être utilisé.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|4096|ID de paramètres régionaux qui représente un ordre de tri secondaire. Dans ce cas, 4096 représente l’ordre de tri des .NET Framework 3,5 et des versions antérieures.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Remarques  
 Étant donné que les opérations de comparaison de chaînes, de tri et de respect de la casse effectuées par la <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> classe dans le .NET Framework 4 sont conformes à la norme Unicode 5,1, les résultats des méthodes de comparaison de chaînes telles que <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> et <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> peuvent différer des versions précédentes du .NET Framework. Si votre application dépend d’un comportement hérité, vous pouvez restaurer la comparaison de chaînes et les règles de tri utilisées dans le .NET Framework 3,5 et les versions antérieures en incluant l' `<CompatSortNLSVersion>` élément dans le fichier de configuration de votre application.  
  
> [!IMPORTANT]
> La restauration de la comparaison de chaînes héritées et des règles de tri requiert également que la bibliothèque de liens dynamiques sort00001000.dll soit disponible sur le système local.  
  
 Vous pouvez également utiliser des règles de tri et de comparaison de chaîne héritées dans un domaine d'application spécifique en passant la chaîne « NetFx40_Legacy20SortingBehavior » à la méthode <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> lorsque vous créez le domaine d'application.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant instancie deux objets <xref:System.String> et appelle la méthode <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> pour les comparer en utilisant les conventions de la culture actuelle.  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 Lorsque vous exécutez l’exemple sur le .NET Framework 4, la sortie suivante s’affiche :
  
```console
sta follows a in the sort order.  
```  
  
 Cela est complètement différent de la sortie qui s’affiche lorsque vous exécutez l’exemple sur la .NET Framework 3,5 :
  
```console
sta equals a in the sort order.  
```  
  
 Toutefois, si vous ajoutez le fichier de configuration suivant au répertoire de l’exemple, puis exécutez l’exemple sur le .NET Framework 4, la sortie est identique à celle produite par l’exemple lorsqu’elle est exécutée sur le .NET Framework 3,5.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma du fichier de configuration](../index.md)
