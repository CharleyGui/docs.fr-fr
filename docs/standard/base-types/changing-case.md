---
title: Changement de casse dans .NET
description: Apprenez à changer la casse des chaînes dans .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], case
- case sensitivity
- ToUpper method
- ToLower method
- uppercase
- lowercase
ms.assetid: 6805f81b-e9ad-4387-9f4c-b9bdb21b87c0
ms.openlocfilehash: 77b879bcc36886a8f457610e6c406bcd121dcfe7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820551"
---
# <a name="change-case-in-net"></a>Modifier la casse dans .NET

Si vous écrivez une application qui accepte l’entrée d’un utilisateur, vous ne pouvez jamais être sûr de la casse (supérieure ou inférieure) qu’elle utilisera pour entrer les données. Souvent, vous voulez que les chaînes aient une casse cohérente, en particulier si vous les affichez dans l'interface utilisateur. Le tableau suivant décrit trois méthodes de changement de la casse : Les deux premières méthodes fournissent une surcharge qui accepte une culture.  
  
|Nom de la méthode|Utilisation|  
|-----------------|---------|  
|<xref:System.String.ToUpper%2A?displayProperty=nameWithType>|Convertit tous les caractères d'une chaîne en majuscules.|  
|<xref:System.String.ToLower%2A?displayProperty=nameWithType>|Convertit tous les caractères d'une chaîne en minuscules.|  
|<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>|Convertit une chaîne en une casse avec la première lettre des mots en majuscule.|  
  
> [!WARNING]
> Notez que les méthodes <xref:System.String.ToUpper%2A?displayProperty=nameWithType> et <xref:System.String.ToLower%2A?displayProperty=nameWithType> ne doivent pas être utilisées pour convertir des chaînes pour les comparer ou pour tester leur égalité. Pour plus d'informations, consultez la section [Comparaison de chaînes de casse mixte](#Comparing).  
  
<a name="Comparing"></a>
## <a name="compare-strings-of-mixed-case"></a>Comparer des chaînes de casse mixte  

 Pour comparer des chaînes de casse mixte et déterminer leur classement, appelez une des surcharges de la méthode <xref:System.String.CompareTo%2A?displayProperty=nameWithType> avec un paramètre `comparisonType` et spécifiez une valeur <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> ou <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pour l’argument `comparisonType`. Pour une comparaison en utilisant une culture spécifique autre que la culture actuelle, appelez une surcharge de la méthode <xref:System.String.CompareTo%2A?displayProperty=nameWithType> avec les paramètres `culture` et `options`, et spécifiez une valeur <xref:System.Globalization.CompareOptions.IgnoreCase?displayProperty=nameWithType> pour l'argument `options`.  
  
 Pour comparer des chaînes de casse mixte et déterminer si elles sont égales, appelez une des surcharges de la méthode <xref:System.String.Equals%2A?displayProperty=nameWithType> avec un paramètre `comparisonType` et spécifiez une valeur <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> ou <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pour l’argument `comparisonType`.  
  
 Pour plus d’informations, consultez [Bonnes pratiques l’utilisation de chaînes](best-practices-strings.md).  
  
## <a name="toupper"></a>ToUpper  
 La méthode <xref:System.String.ToUpper%2A?displayProperty=nameWithType> change tous les caractères d'une chaîne en majuscules. L’exemple suivant convertit la chaîne « Hello World! » d’une casse mixte en majuscules.  
  
 [!code-csharp[Strings.ChangingCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#1)]
 [!code-vb[Strings.ChangingCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#1)]  
  
 L'exemple précédent est par défaut dépendant de la culture. Il applique les conventions de casse de la culture actuelle. Pour effectuer un changement de casse indépendant de la culture ou appliquer les conventions de casse d'une culture particulière, utilisez la surcharge de la méthode <xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> et spécifiez une valeur <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> ou un objet <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> qui représente la culture spécifiée pour le paramètre *culture*. Pour un exemple montrant comment utiliser la méthode <xref:System.String.ToUpper%2A> pour effectuer un changement de casse indépendant de la culture, consultez [Réalisation de changements de casse indépendants de la culture](../globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="tolower"></a>ToLower  
 La méthode <xref:System.String.ToLower%2A?displayProperty=nameWithType> est similaire à la méthode précédente, mais elle convertit tous les caractères d'une chaîne en minuscules. L’exemple suivant convertit la chaîne « Hello World! » en minuscules.  
  
 [!code-csharp[Strings.ChangingCase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#2)]
 [!code-vb[Strings.ChangingCase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#2)]  
  
 L'exemple précédent est par défaut dépendant de la culture. Il applique les conventions de casse de la culture actuelle. Pour effectuer un changement de casse indépendant de la culture ou appliquer les conventions de casse d'une culture particulière, utilisez la surcharge de la méthode <xref:System.String.ToLower%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> et spécifiez une valeur <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> ou un objet <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> qui représente la culture spécifiée pour le paramètre *culture*. Pour un exemple montrant comment utiliser la méthode <xref:System.String.ToLower%28System.Globalization.CultureInfo%29> pour effectuer un changement de casse indépendant de la culture, consultez [Réalisation de changements de casse indépendants de la culture](../globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="totitlecase"></a>ToTitleCase  
 La méthode <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> convertit le premier caractère de chaque mot en majuscules et les autres caractères en minuscules. Cependant, les mots qui sont entièrement en majuscules sont supposés être des acronymes et ne sont pas convertis.  
  
 La méthode <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> est dépendante de la culture ; autrement dit, elle utilise les conventions de casse d'une culture particulière. Pour pouvoir appeler la méthode, vous récupérez d'abord l'objet <xref:System.Globalization.TextInfo> qui représente les conventions de casse de la culture spécifique auprès de la propriété <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> d'une culture particulière.  
  
 L'exemple suivant passe chaque chaîne d'un tableau à la méthode <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>.  Les chaînes incluent des chaînes de titre appropriées, ainsi que des acronymes. Les chaînes sont converties en casse avec la première lettre des mots en majuscules en utilisant les conventions de casse de la culture Anglais (États-Unis).  
  
 [!code-csharp[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/cs/totitlecase2.cs#1)]
 [!code-vb[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/vb/totitlecase2.vb#1)]  
  
 Notez que bien qu'elle soit dépendante de la culture, la méthode <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> ne fournit pas de règles de casse correctes d'un point de vue linguistique. Par exemple, dans l'exemple précédent, la méthode convertit "a tale of two cities" en "A Tale Of Two Cities". Cependant, la casse linguistiquement correcte de ce titre pour la culture en-US est "A Tale of Two Cities".  
  
## <a name="see-also"></a>Voir aussi

- [Opérations de chaînes de base](basic-string-operations.md)
- [Exécution d'opérations de chaînes indépendantes de la culture](../globalization-localization/performing-culture-insensitive-string-operations.md)
