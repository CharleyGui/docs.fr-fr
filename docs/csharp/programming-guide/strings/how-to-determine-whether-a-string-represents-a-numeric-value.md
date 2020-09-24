---
title: Comment déterminer si une chaîne représente une valeur numérique-Guide de programmation C#
description: Découvrez comment déterminer si une chaîne est une représentation valide d’un type numérique spécifié. Consultez des exemples de code et affichez des ressources supplémentaires.
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: cbe0703ca39422ac0a9e7a93bf2cfc4c3f8528f8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151426"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Comment déterminer si une chaîne représente une valeur numérique (Guide de programmation C#)

Pour déterminer si une chaîne est une représentation valide d’un type numérique spécifié, utilisez la méthode statique `TryParse` implémentée par tous les types numériques primitifs et par les types tels que <xref:System.DateTime> et <xref:System.Net.IPAddress>. L’exemple suivant montre comment déterminer si « 108 » est une chaîne [int](../../language-reference/builtin-types/integral-numeric-types.md) valide.  
  
```csharp  
int i = 0;
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Si la chaîne contient des caractères non numériques ou si la valeur numérique est trop grande ou trop petite pour le type particulier que vous avez spécifié, `TryParse` retourne la valeur false et affecte la valeur zéro comme paramètre de sortie. Sinon, elle retourne la valeur true et affecte la valeur numérique de la chaîne comme paramètre de sortie.  
  
> [!NOTE]
> Une chaîne peut contenir uniquement des caractères numériques et ne pas être valide pour le type dont vous utilisez la méthode `TryParse`. Par exemple, « 256 » n’est pas une valeur valide pour `byte`, mais elle est valide pour `int`. « 98,6 » n’est pas une valeur valide pour `int`, mais elle est valide pour `decimal`.  
  
## <a name="example"></a>Exemple  

 Les exemples suivants montrent comment utiliser `TryParse` avec des représentations sous forme de chaîne de valeurs `long`, `byte` et `decimal`.  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Programmation fiable  

 Les types numériques primitifs implémentent également la méthode statique `Parse`, qui lève une exception si la chaîne n’est pas un nombre valide. `TryParse` est généralement plus efficace, car elle retourne simplement false si le nombre n’est pas valide.  
  
## <a name="net-security"></a>Sécurité .NET  

 Utilisez toujours la méthode `TryParse` ou `Parse` pour valider l’entrée utilisateur à partir de contrôles tels que des zones de texte et des zones de liste déroulante.  
  
## <a name="see-also"></a>Voir aussi

- [Comment convertir un tableau d’octets en entier](../types/how-to-convert-a-byte-array-to-an-int.md)
- [Comment convertir une chaîne en nombre](../types/how-to-convert-a-string-to-a-number.md)
- [Comment effectuer une conversion entre des chaînes hexadécimales et des types numériques](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Analyse des chaînes numériques](../../../standard/base-types/parsing-numeric.md)
- [Mise en forme des types](../../../standard/base-types/formatting-types.md)
