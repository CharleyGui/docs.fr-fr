---
title: Comment effectuer une conversion entre des chaînes hexadécimales et des types numériques (Guide de programmation C#)
description: Découvrez comment effectuer une conversion entre des chaînes hexadécimales et des types numériques. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 35cf1af661071c70b8d68de2e47ce555be7b9fef
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025405"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Comment effectuer une conversion entre des chaînes hexadécimales et des types numériques (Guide de programmation C#)

Ces exemples montrent comment effectuer les tâches suivantes :  
  
- Obtenir la valeur hexadécimale de chaque caractère dans une chaîne ([string](../../language-reference/builtin-types/reference-types.md)).  
  
- Obtenir la valeur [char](../../language-reference/builtin-types/char.md) qui correspond à chaque valeur d’une chaîne hexadécimale.  
  
- Convertir une `string` hexadécimale en [int](../../language-reference/builtin-types/integral-numeric-types.md).  
  
- Convertir une `string` hexadécimale en [float](../../language-reference/builtin-types/floating-point-numeric-types.md).  
  
- Convertir un tableau d’[octets](../../language-reference/builtin-types/integral-numeric-types.md) en `string` hexadécimale.  
  
## <a name="example"></a>Exemple  

 Cet exemple génère la valeur hexadécimale de chaque caractère dans une `string`. Il convertit d’abord la `string` en un tableau de caractères. Ensuite, il appelle <xref:System.Convert.ToInt32%28System.Char%29> sur chaque caractère afin d’obtenir sa valeur numérique. Pour finir, il représente le nombre sous forme hexadécimale dans une `string`.  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a>Exemple  

 Cet exemple analyse une `string` de valeurs hexadécimales et génère le caractère correspondant à chacune d’elles. Tout d’abord, elle appelle la méthode [Split (char \[ \] )](xref:System.String.Split(System.Char[])) pour obtenir chaque valeur hexadécimale en tant qu’individu `string` dans un tableau. Il appelle ensuite <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> pour convertir la valeur hexadécimale en valeur décimale représentée sous la forme d’un [entier](../../language-reference/builtin-types/integral-numeric-types.md). Il montre deux façons différentes d’obtenir le caractère correspondant à ce code de caractère. La première technique utilise `string`, qui retourne le caractère correspondant à l’argument entier sous forme de <xref:System.Char.ConvertFromUtf32%28System.Int32%29>. La deuxième technique effectue un cast explicite de l’`int` en [char](../../language-reference/builtin-types/char.md).  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a>Exemple  

 Cet exemple montre une autre façon de convertir un `string` hexadécimal en entier, en appelant la méthode <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29>.  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment convertir un `string` hexadécimal en [float](../../language-reference/builtin-types/floating-point-numeric-types.md) à l’aide de la classe <xref:System.BitConverter?displayProperty=nameWithType> et de la méthode <xref:System.UInt32.Parse%2A?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment convertir un tableau d’[octets](../../language-reference/builtin-types/integral-numeric-types.md) en chaîne hexadécimale à l’aide de la classe <xref:System.BitConverter?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment convertir un tableau d' [octets](../../language-reference/builtin-types/integral-numeric-types.md) en une chaîne hexadécimale en appelant la <xref:System.Convert.ToHexString%2A?displayProperty=nameWithType> méthode introduite dans .net 5,0.
  
 [!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]  
  
## <a name="see-also"></a>Voir aussi

- [Chaînes de format numériques standard](../../../standard/base-types/standard-numeric-format-strings.md)
- [Types](./index.md)
- [Comment déterminer si une chaîne représente une valeur numérique](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
