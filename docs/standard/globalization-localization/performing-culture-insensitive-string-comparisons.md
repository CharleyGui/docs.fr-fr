---
title: Exécution de comparaisons de chaînes indépendantes de la culture
ms.date: 08/22/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.CompareTo method
- String.Compare method
- string comparison [.NET], culture-insensitive
- strings [.NET], comparing
- culture-insensitive string operations, comparisons
- culture parameter
ms.assetid: abae50ef-32f7-4a50-a540-fd256fd1aed0
ms.openlocfilehash: 3f933121d3c878dd8eee4812fa6669a915c22356
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696490"
---
# <a name="performing-culture-insensitive-string-comparisons"></a>Exécution de comparaisons de chaînes indépendantes de la culture

Par défaut, la méthode <xref:System.String.Compare%2A?displayProperty=nameWithType> effectue des comparaisons dépendantes de la culture et qui respectent la casse. Cette méthode inclut également plusieurs surcharges qui fournissent un paramètre `culture` qui vous permet de spécifier la culture à utiliser et un paramètre `comparisonType` qui vous sert à spécifier les règles de comparaison à utiliser. L'appel de ces méthodes au lieu de la surcharge par défaut supprime toute ambiguïté à propos des règles utilisées dans un appel de méthode particulier et indique si une comparaison donnée est dépendante ou indépendante de la culture.  
  
> [!NOTE]
> Les surcharges de la méthode <xref:System.String.CompareTo%2A?displayProperty=nameWithType> effectuent des comparaisons dépendantes de la culture et sensibles à la casse ; vous ne pouvez pas utiliser cette méthode pour effectuer des comparaisons indépendantes de la culture. Pour des raisons de clarté du code, nous recommandons d'utiliser la méthode <xref:System.String.Compare%2A?displayProperty=nameWithType> à la place.  
  
 Pour les opérations dépendantes de la culture, spécifiez la valeur d'énumération <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> ou <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> comme paramètre `comparisonType`. Si vous souhaitez effectuer une comparaison dépendante de la culture à l'aide d'une culture désignée autre que la culture actuelle, spécifiez l'objet <xref:System.Globalization.CultureInfo> qui représente cette culture comme paramètre `culture`.  
  
 Les comparaisons de chaînes indépendantes de la culture prises en charge par la méthode <xref:System.String.Compare%2A?displayProperty=nameWithType> sont linguistiques (selon les conventions de tri de la culture indifférente) ou non linguistiques (selon la valeur ordinale des caractères dans la chaîne). La plupart des comparaisons de chaînes indépendantes de la culture sont non linguistiques. Pour ces comparaisons, spécifiez la valeur d'énumération <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> ou <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> comme paramètre `comparisonType`. Par exemple, si une décision de sécurité (telle qu'une comparaison de nom d'utilisateur ou de mot de passe) est basée sur le résultat d'une comparaison de chaînes, l'opération doit être indépendante de la culture et non linguistique pour garantir que le résultat n'est pas affecté par les conventions d'une culture ou d'une langue particulière.  
  
 Utilisez la comparaison de chaînes linguistique indépendante de la culture si vous souhaitez gérer de manière cohérente des chaînes linguistiquement pertinentes de cultures multiples. Par exemple, si votre application affiche des mots qui utilisent plusieurs jeux de caractères dans une zone de liste, vous pouvez afficher des mots dans le même ordre indépendamment de la culture actuelle. Pour les comparaisons linguistiques indépendantes de la culture, .NET définit une culture dite indifférente basée sur les conventions linguistiques de l’anglais. Pour effectuer une comparaison linguistique indépendante de la culture, spécifiez <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> ou <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> comme paramètre `comparisonType`.  
  
 L'exemple suivant exécute deux comparaisons de chaînes indépendantes de la culture, non linguistiques. La première respecte la casse, mais pas la seconde.  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  

Vous pouvez télécharger les [Sorting Weight Tables](https://www.microsoft.com/download/details.aspx?id=10921), un ensemble de fichiers texte qui contiennent des informations sur les poids des caractères utilisés dans les opérations de tri et de comparaison pour les systèmes d’exploitation Windows et la [Default Unicode Collation Element Table](https://www.unicode.org/Public/UCA/latest/allkeys.txt), la table de pondération de tri pour Linux et macOS.

## <a name="see-also"></a>Voir aussi

- <xref:System.String.Compare%2A?displayProperty=nameWithType>
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- [Exécution d'opérations de chaînes indépendantes de la culture](performing-culture-insensitive-string-operations.md)
- [Meilleures pratiques pour l’utilisation de chaînes](../base-types/best-practices-strings.md)
