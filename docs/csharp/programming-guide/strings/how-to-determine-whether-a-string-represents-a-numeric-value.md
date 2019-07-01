---
title: 'Procédure : Déterminer si une chaîne représente une valeur numérique - Guide de programmation C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 626fce590ba08bbdabf27ac33287a0b46b592f9c
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423612"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Procédure : Déterminer si une chaîne représente une valeur numérique (Guide de programmation C#)
Pour déterminer si une chaîne est une représentation valide d’un type numérique spécifié, utilisez la méthode statique `TryParse` implémentée par tous les types numériques primitifs et par les types tels que <xref:System.DateTime> et <xref:System.Net.IPAddress>. L’exemple suivant montre comment déterminer si « 108 » est une chaîne [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) valide.  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Si la chaîne contient des caractères non numériques ou si la valeur numérique est trop grande ou trop petite pour le type particulier que vous avez spécifié, `TryParse` retourne la valeur false et affecte la valeur zéro comme paramètre de sortie. Sinon, elle retourne la valeur true et affecte la valeur numérique de la chaîne comme paramètre de sortie.  
  
> [!NOTE]
>  Une chaîne peut contenir uniquement des caractères numériques et ne pas être valide pour le type dont vous utilisez la méthode `TryParse`. Par exemple, « 256 » n’est pas une valeur valide pour `byte`, mais elle est valide pour `int`. « 98,6 » n’est pas une valeur valide pour `int`, mais elle est valide pour `decimal`.  
  
## <a name="example"></a>Exemples  
 Les exemples suivants montrent comment utiliser `TryParse` avec des représentations sous forme de chaîne de valeurs `long`, `byte` et `decimal`.  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les types numériques primitifs implémentent également la méthode statique `Parse`, qui lève une exception si la chaîne n’est pas un nombre valide. `TryParse` est généralement plus efficace, car elle retourne simplement false si le nombre n’est pas valide.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Utilisez toujours la méthode `TryParse` ou `Parse` pour valider l’entrée utilisateur à partir de contrôles tels que des zones de texte et des zones de liste déroulante.  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour convertir un tableau d’octets en int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)
- [Guide pratique pour convertir une chaîne en nombre](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
- [Guide pratique pour effectuer une conversion entre des chaînes hexadécimales et des types numériques](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Analyse de chaînes numériques](../../../standard/base-types/parsing-numeric.md)
- [Mise en forme des types](../../../standard/base-types/formatting-types.md)
