---
title: Création de nouvelles chaînes dans .NET
description: Apprenez à créer des chaînes à l’aide d’affectations, de constructeurs de classe ou de méthodes System. String qui combinent plusieurs chaînes, tableaux de chaînes ou objets dans .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
ms.openlocfilehash: 7dedaf61f56f19343299c841bb4cee70fb9c767a
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889437"
---
# <a name="creating-new-strings-in-net"></a>Création de nouvelles chaînes dans .NET

.NET permet de créer des chaînes à l’aide d’une assignation simple, et surcharge un constructeur de classe pour prendre en charge la création de chaînes à l’aide de plusieurs paramètres différents. .NET fournit également plusieurs méthodes dans la <xref:System.String?displayProperty=nameWithType> classe qui créent des objets String en combinant plusieurs chaînes, tableaux de chaînes ou objets.  
  
## <a name="creating-strings-using-assignment"></a>Création de chaînes à l’aide d’une affectation  
 Le moyen le plus simple de créer un objet <xref:System.String> consiste à assigner un littéral de chaîne à un objet <xref:System.String>.  
  
## <a name="creating-strings-using-a-class-constructor"></a>Création de chaînes à l’aide d’un constructeur de classe  
 Vous pouvez utiliser des surcharges du constructeur de classe <xref:System.String> pour créer des chaînes à partir de tableaux de caractères. Vous pouvez également créer une chaîne en dupliquant un caractère spécifique un nombre spécifié de fois.  
  
## <a name="methods-that-return-strings"></a>Méthodes retournant des chaînes  
 Le tableau suivant présente plusieurs méthodes utiles qui retournent de nouveaux objets String.  
  
|Nom de la méthode|Utilisation|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|Génère une chaîne mise en forme à partir d’un ensemble d’objets en entrée.|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|Génère des chaînes à partir de deux ou de plusieurs chaînes.|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|Génère une nouvelle chaîne en combinant un tableau de chaînes.|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|Génère une nouvelle chaîne en insérant une chaîne dans l’index spécifié d’une chaîne existante.|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|Copie des caractères spécifiés dans une chaîne à une position spécifiée dans un tableau de caractères.|  
  
### <a name="format"></a>Format  
 Vous pouvez utiliser la méthode **String.Format** pour créer des chaînes mises en forme et concaténer des chaînes représentant plusieurs objets. Cette méthode convertit automatiquement tout objet passé en une chaîne. Par exemple, si votre application doit afficher une valeur **Int32** et une valeur **DateTime** à l’utilisateur, vous pouvez aisément construire une chaîne représentant ces valeurs à l’aide de la méthode **Format** . Pour plus d’informations sur les conventions de mise en forme utilisées avec cette méthode, consultez la section relative à la [mise en forme composite](composite-formatting.md).  
  
 L’exemple suivant utilise la méthode **Format** pour créer une chaîne utilisant une variable de type integer.  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 Dans cet exemple, <xref:System.DateTime.Now%2A?displayProperty=nameWithType> affiche la date et l’heure actuelles de la manière spécifiée par la culture associée au thread actuel.  
  
### <a name="concat"></a>Concat  
 La méthode **String.Concat** peut être utilisée pour créer facilement un objet chaîne à partir de deux ou de plusieurs objets existants. Elle offre un moyen de concaténer des chaînes indépendamment du langage. Cette méthode accepte toute classe qui dérive de **System.Object** . L’exemple suivant crée une chaîne à partir de deux objets String existants et d’un caractère à utiliser comme séparateur.  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Join  
 La méthode **String.Join** crée une chaîne à partir d’un tableau de chaînes et d’une chaîne de séparation. Cette méthode est utile si vous voulez concaténer plusieurs chaînes et en faire une liste éventuellement séparée par une virgule.  
  
 L’exemple suivant utilise un espace pour lier un tableau de chaînes.  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>Insérer  
 La méthode **String.Insert** crée une chaîne en insérant une chaîne à une position spécifiée dans une autre chaîne. Cette méthode utilise un index de base zéro. L’exemple suivant insère une chaîne à la cinquième position d’index de `MyString` et crée une chaîne avec cette valeur.  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>CopyTo  
 La méthode **String.CopyTo** copie des fragments d’une chaîne dans un tableau de caractères. Vous pouvez spécifier l’index de début de la chaîne et le nombre de caractères à copier. Cette méthode utilise l’index source, un tableau de caractères, l’index de destination et le nombre de caractères à copier. Tous les index sont de base zéro.  
  
 L’exemple suivant utilise la méthode **CopyTo** pour copier les caractères du mot « Hello » d’un objet String vers la première position d’un tableau de caractères.  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>Voir aussi

- [Opérations de chaînes de base](basic-string-operations.md)
- [Mise en forme composite](composite-formatting.md)
