---
title: Analyse d’autres chaînes dans .NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
ms.openlocfilehash: 352bd426c889996daa5f420ccc384947896dc118
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683743"
---
# <a name="parsing-other-strings-in-net"></a>Analyse d’autres chaînes dans .NET

Outre des chaînes numériques et <xref:System.DateTime>, vous pouvez analyser des chaînes qui représentent les types <xref:System.Char>, <xref:System.Boolean> et <xref:System.Enum> dans des types de données.  
  
## <a name="char"></a>Char  

 La méthode d’analyse statique associée au type de données **Char** est utile pour la conversion d’une chaîne qui contient un caractère unique en une valeur Unicode. L’exemple de code suivant analyse une chaîne en un caractère Unicode.  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>Boolean  

 Le type de données **Boolean** contient une méthode **Parse** que vous pouvez utiliser pour convertir une chaîne représentant une valeur Boolean en type **Boolean** réel. Cette méthode ne respecte pas la casse et peut analyser une chaîne contenant « True » ou « False ». La méthode **Parse** associée au type **Boolean** peut aussi analyser des chaînes entourées d’espaces blancs. Si une autre chaîne est passée, une exception <xref:System.FormatException> est levée.  
  
 L’exemple de code suivant utilise la méthode **Parse** pour convertir une chaîne en valeur Boolean.  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>Énumération  

 Vous pouvez utiliser la méthode **Parse** statique pour initialiser un type d’énumération avec la valeur d’une chaîne. Cette méthode accepte le type d’énumération que vous analysez, la chaîne à analyser et un indicateur Boolean facultatif indiquant si l’analyse respecte la casse. La chaîne que vous analysez peut contenir plusieurs valeurs séparées par des virgules, lesquelles peuvent être précédées ou suivies d’un ou plusieurs espaces vides (aussi appelés espaces blancs). Quand la chaîne contient plusieurs valeurs, celle de l’objet retourné est la valeur de toutes les valeurs spécifiées, combinées avec une opération OR au niveau du bit.  
  
 L’exemple suivant utilise la méthode **Parse** pour convertir une représentation sous forme de chaîne en valeur d’énumération. L’énumération <xref:System.DayOfWeek> est initialisée à **Thursday** à partir d’une chaîne.  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Analyse de chaînes](parsing-strings.md)
- [Mise en forme des types](formatting-types.md)
- [Conversion de type dans .NET](type-conversion.md)
