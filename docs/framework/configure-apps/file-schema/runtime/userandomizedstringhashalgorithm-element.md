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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153775"
---
# <a name="userandomizedstringhashalgorithm-element"></a>Élément \<UseRandomizedStringHashAlgorithm>
Détermine si le common language runtime calcule les codes de hachage pour les chaînes par domaine d’application.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**  
  
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
|`enabled`|Attribut requis.<br /><br /> Spécifie si les codes de hachage pour les chaînes sont calculés par domaine d’application.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`0`|Le common language runtime ne calcule pas les codes de hachage pour les chaînes par domaine d’application ; un seul algorithme est utilisé pour calculer les codes de hachage de chaîne. Il s'agit de la valeur par défaut.|  
|`1`|Le common language runtime calcule les codes de hachage pour les chaînes par domaine d’application. Les chaînes identiques dans différents domaines d’application et dans des processus différents auront des codes de hachage différents.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Remarques  
 Par défaut, la <xref:System.StringComparer> classe et la <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> méthode utilisent un algorithme de hachage unique qui produit un code de hachage cohérent entre les domaines d’application. Cela équivaut à affecter à l' `enabled` attribut de l' `<UseRandomizedStringHashAlgorithm>` élément la valeur `0` . Il s’agit de l’algorithme de hachage utilisé dans le .NET Framework 4.  
  
 La <xref:System.StringComparer> classe et la <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> méthode peuvent également utiliser un algorithme de hachage différent qui calcule les codes de hachage pour chaque domaine d’application. Par conséquent, les codes de hachage pour les chaînes équivalentes diffèrent entre les domaines d’application. Il s’agit d’une fonctionnalité d’abonnement. pour en tirer parti, vous devez affecter la valeur à l' `enabled` attribut de l' `<UseRandomizedStringHashAlgorithm>` élément `1` .  
  
 La recherche de chaîne dans une table de hachage est généralement une opération O (1). Toutefois, lorsqu’un grand nombre de collisions se produisent, la recherche peut devenir une opération O (n<sup>2</sup>). Vous pouvez utiliser l' `<UseRandomizedStringHashAlgorithm>` élément de configuration pour générer un algorithme de hachage aléatoire par domaine d’application, qui, à son tour, limite le nombre de collisions potentielles, en particulier lorsque les clés à partir desquelles les codes de hachage sont calculés sont basées sur les données entrées par les utilisateurs.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit une `DisplayString` classe qui comprend une constante de chaîne privée, `s` , dont la valeur est « This is a String ». Il inclut également une méthode `ShowStringHashCode` qui affiche la valeur de chaîne et son code de hachage avec le nom du domaine d'application dans lequel la méthode est exécutée.  
  
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
