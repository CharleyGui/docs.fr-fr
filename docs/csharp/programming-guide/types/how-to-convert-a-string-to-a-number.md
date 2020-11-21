---
title: Comment convertir une chaîne en un nombre-guide de programmation C#
description: Découvrez comment convertir une chaîne en nombre en C# en appelant les méthodes de classe Parse, TryParse ou Convert.
ms.date: 11/20/2020
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 0a9585d05a817d09308e06558352f78a5347a8f1
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099170"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Comment convertir une chaîne en nombre (Guide de programmation C#)

Vous pouvez convertir une [chaîne](../../language-reference/builtin-types/reference-types.md) en nombre en appelant la `Parse` méthode ou `TryParse` trouvée sur les différents types numériques ( `int` , `long` , `double` , etc.), ou en utilisant des méthodes de la <xref:System.Convert?displayProperty=nameWithType> classe.  
  
 Il est légèrement plus efficace et simple d’appeler une `TryParse` méthode (par exemple, [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A) ) ou une `Parse` méthode (par exemple, [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A) ).  L'utilisation d'une méthode <xref:System.Convert> s'avère plus utile pour les objets généraux qui implémentent <xref:System.IConvertible>.  
  
 Vous utilisez `Parse` les `TryParse` méthodes ou sur le type numérique que la chaîne contient, comme le <xref:System.Int32?displayProperty=nameWithType> type.  La méthode <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> utilise <xref:System.Int32.Parse%2A> en interne.  La `Parse` méthode retourne le nombre converti ; la `TryParse` méthode retourne une <xref:System.Boolean> valeur qui indique si la conversion a réussi, et retourne le nombre converti dans un [ `out` paramètre](../../language-reference/keywords/out.md). Si la chaîne n’est pas dans un format valide, `Parse` lève une exception, mais `TryParse` retourne `false` . Lorsque vous appelez une méthode `Parse`, vous devez toujours utiliser la gestion des exceptions pour intercepter une <xref:System.FormatException> si l’opération d’analyse échoue.  
  
## <a name="calling-the-parse-and-tryparse-methods"></a>Appel des méthodes Parse et TryParse

Les `Parse` `TryParse` méthodes et ignorent les espaces blancs au début et à la fin de la chaîne, mais tous les autres caractères doivent être des caractères qui forment le type numérique approprié ( `int` ,,,,, etc `long` `ulong` `float` `decimal` .).  La présence d’un espace blanc dans la chaîne qui forme le nombre génère une erreur.  Par exemple, vous pouvez utiliser `decimal.TryParse` pour analyser « 10 », « 10,3 » ou « 10 », mais vous ne pouvez pas utiliser cette méthode pour analyser 10 à partir de « 10x », « 1 0 » (Notez l’espace incorporé), « 10.3 » (Notez l’espace incorporé), « 10E1 » ( `float.TryParse` fonctionne ici), et ainsi de suite. Chaîne dont la valeur est `null` ou <xref:System.String.Empty?displayProperty=nameWithType> ne parvient pas à être analysée correctement. Vous pouvez rechercher une chaîne Null ou vide avant de tenter de l’analyser en appelant la méthode <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType>.

L’exemple suivant illustre des appels à `Parse` et à `TryParse` qui ont réussi ou échoué.  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

L’exemple suivant illustre une approche pour analyser une chaîne supposée inclure des caractères numériques de début (y compris des caractères hexadécimaux) et des caractères non numériques de fin. Il attribue dès le début des caractères valides à une nouvelle chaîne avant d’appeler la méthode <xref:System.Int32.TryParse%2A>. Étant donné que les chaînes à analyser contiennent un petit nombre de caractères, l’exemple appelle la méthode <xref:System.String.Concat%2A?displayProperty=nameWithType> pour attribuer des caractères valides à une nouvelle chaîne. Pour une chaîne plus grande, la classe <xref:System.Text.StringBuilder> peut être utilisée à la place.
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a>Appel des méthodes de conversion

Le tableau suivant répertorie quelques unes des méthodes de la classe <xref:System.Convert> que vous pouvez utiliser pour convertir une chaîne en nombre.  
  
|Type numérique|Méthode|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 L’exemple suivant appelle la <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> méthode pour convertir une chaîne d’entrée en [int](../../language-reference/builtin-types/integral-numeric-types.md). L’exemple intercepte les deux exceptions les plus courantes qui peuvent être levées par cette méthode, <xref:System.FormatException> et <xref:System.OverflowException> . Si le nombre obtenu peut être incrémenté sans dépasser <xref:System.Int32.MaxValue?displayProperty=nameWithType>, l’exemple ajoute 1 au résultat et affiche la sortie.  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a>Voir aussi

- [Types](./index.md)
- [Comment déterminer si une chaîne représente une valeur numérique](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [Exemple : utilitaire de mise en forme .NET Core WinForms (C#)](/samples/dotnet/samples/windowsforms-formatting-utility-cs)
