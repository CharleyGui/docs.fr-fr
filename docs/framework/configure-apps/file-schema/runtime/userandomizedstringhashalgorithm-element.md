---
title: Élément <UseRandomizedStringHashAlgorithm>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
ms.openlocfilehash: a9afa0db516a542b74d08a4c3754a3244abbbea7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153775"
---
# <a name="userandomizedstringhashalgorithm-element"></a>\<UtilisationRandomizedStringHashAlgorithm> Element
Détermine si le temps d’exécution de langue commun calcule des codes de hachage pour les chaînes sur une base de domaine d’application.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UtilisationRandomizedStringHashAlgorithm>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Précise si les codes de hachage pour les chaînes sont calculés sur une base de domaine d’application.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`0`|L’heure courante de fonctionnement de langue ne calcule pas des codes de hachage pour des chaînes sur une base de domaine d’application ; un seul algorithme est utilisé pour calculer les codes de hachage des chaînes. Il s’agit de la valeur par défaut.|  
|`1`|Le langage courant calcule des codes de hachage pour les chaînes par domaine d’application. Les chaînes identiques dans différents domaines d’application et dans différents processus auront différents codes de hachage.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes   
 Par défaut, <xref:System.StringComparer> la <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> classe et la méthode utilisent un algorithme de hachage unique qui produit un code de hachage cohérent dans tous les domaines d’application. Cela équivaut à `enabled` définir `<UseRandomizedStringHashAlgorithm>` l’attribut de l’élément à `0`. Il s’agit de l’algorithme de hachage utilisé dans le cadre .NET 4.  
  
 La <xref:System.StringComparer> classe <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> et la méthode peuvent également utiliser un algorithme de hachage différent qui calcule les codes de hachage sur une base de domaine d’application. Par conséquent, les codes de hachage pour les chaînes équivalentes varieront d’un domaine d’application à l’autre. Il s’agit d’une fonction d’opt-in; pour en profiter, vous devez `enabled` définir `<UseRandomizedStringHashAlgorithm>` l’attribut de l’élément à `1`.  
  
 Le lookup de chaîne dans une table de hachage est typiquement une opération O(1). Cependant, lorsqu’un grand nombre de collisions se produisent, la recherche peut devenir une opération O(n<sup>2).</sup> Vous pouvez `<UseRandomizedStringHashAlgorithm>` utiliser l’élément de configuration pour générer un algorithme aléatoire de hachage par domaine d’application, ce qui limite à son tour le nombre de collisions potentielles, en particulier lorsque les clés à partir desquelles les codes de hachage sont calculés sont basées sur l’entrée de données par les utilisateurs.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant `DisplayString` définit une classe qui `s`comprend une constante de cordes privées, dont la valeur est "C’est une chaîne." Il inclut également une méthode `ShowStringHashCode` qui affiche la valeur de chaîne et son code de hachage avec le nom du domaine d'application dans lequel la méthode est exécutée.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Lorsque vous exécutez l'exemple sans fournir un fichier de configuration, il affiche une sortie similaire à la suivante. Notez que les codes de hachage pour la chaîne sont identiques dans les deux domaines d'application.  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 Toutefois, si vous ajoutez le fichier de configuration suivant au répertoire de l'exemple, puis exécutez l'exemple, les codes de hachage pour la même chaîne diffèrent par domaine d'application.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 Lorsque le fichier de configuration est présent, l'exemple affiche la sortie suivante :  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
