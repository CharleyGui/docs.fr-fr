---
title: Exécution de changements de casse indépendants de la culture
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
ms.openlocfilehash: 6baef7b0a5bbdacd33d84df01b1aa943897a9e3d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276814"
---
# <a name="performing-culture-insensitive-case-changes"></a>Exécution de changements de casse indépendants de la culture
Les méthodes <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> et <xref:System.Char.ToLower%2A?displayProperty=nameWithType> fournissent des surcharges qui n’acceptent pas de paramètres. Par défaut, ces surcharges sans paramètres effectuent des changements de casse basés sur la valeur de la <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>. Cela produit des résultats de la casse qui peuvent varier selon la culture. Pour indiquer clairement si vous souhaitez que les changements de casse soient ou non dépendants de la culture, vous devez utiliser les surcharges de ces méthodes qui vous demandent de spécifier explicitement un paramètre `culture`. Pour les changements de casse dépendants de la culture, spécifiez `CultureInfo.CurrentCulture` pour le paramètre `culture`. Pour les changements de casse indépendants de la culture, spécifiez `CultureInfo.InvariantCulture` pour le paramètre `culture`.  
  
 Souvent, les chaînes sont converties en casse standard pour faciliter des recherches ultérieures. Lorsque des chaînes sont utilisées de cette manière, vous devriez spécifier `CultureInfo.InvariantCulture` pour le paramètre `culture`, car la valeur de <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> peut changer entre le moment où la casse est modifiée et le moment de la recherche.  
  
 Si une décision de sécurité est basée sur une opération de changement de casse, cette opération doit être indépendante de la culture pour garantir que le résultat n'est pas affecté par la valeur de `CultureInfo.CurrentCulture`. Consultez la section « Comparaisons de chaînes qui utilisent la culture actuelle » de l’article [Meilleures pratiques d’utilisation des chaînes](../base-types/best-practices-strings.md) pour voir un exemple montrant comment les opérations de chaînes dépendantes de la culture peuvent produire des résultats incohérents.  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>Utilisation des méthodes String.ToUpper et String.ToLower  
 Pour la clarté du code, il est recommandé de toujours utiliser des surcharges des méthodes `String.ToUpper` et `String.ToLower` vous permettant de spécifier explicitement un paramètre `culture`. Par exemple, le code suivant effectue une recherche d’identificateur. L’opération `key.ToLower` est dépendante de la culture par défaut, mais ce comportement ne ressort pas clairement de la lecture du code.  
  
### <a name="example"></a>Exemple  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 Si vous souhaitez que l’opération `key.ToLower` soit indépendante de la culture, vous devez modifier l’exemple précédent comme suit pour utiliser explicitement le `CultureInfo.InvariantCulture` lors de la modification de la casse.  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a>Utilisation des méthodes Char.ToUpper et Char.ToLower  
 Bien que les méthodes `Char.ToUpper` et `Char.ToLower` aient les mêmes caractéristiques que les méthodes `String.ToUpper` et `String.ToLower`, les seules cultures affectées sont le turc (Turquie) et l’azéri (latin, Azerbaïdjan). Ce sont les deux seules cultures avec des différences de casse de caractère unique. Pour plus d’informations sur ce mappage de casse unique, consultez la section « Casse » dans la rubrique de la classe <xref:System.String>. Pour la clarté du code et pour garantir des résultats cohérents, il est recommandé de toujours utiliser les surcharges de ces méthodes qui vous permettent de spécifier explicitement un paramètre `culture`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [Exécution d’opérations de chaînes indépendantes de la culture](performing-culture-insensitive-string-operations.md)
