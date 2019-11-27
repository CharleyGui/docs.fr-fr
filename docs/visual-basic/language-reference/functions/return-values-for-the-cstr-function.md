---
title: Valeurs de retour pour la fonction CStr
ms.date: 07/20/2015
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
ms.openlocfilehash: 4a40777c7290ec6d8c0d032f2edca5d889e20f04
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349988"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>Valeurs de retour pour la fonction CStr (Visual Basic)
Le tableau suivant décrit les valeurs renvoyées pour `CStr` pour différents types de données de `expression`.  
  
|Si le type de `expression` est|Retours `CStr`|  
|-----------------------------|--------------------|  
|[Booléen (type de données)](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Chaîne contenant « true » ou « false ».|  
|[Date (type de données)](../../../visual-basic/language-reference/data-types/date-data-type.md)|Chaîne contenant une valeur `Date` (date et heure) au format de date abrégée de votre système.|  
|[Types de données numériques](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Chaîne représentant le nombre.|  
  
## <a name="cstr-and-date"></a>CStr et date  
 Le type de `Date` contient toujours des informations de date et d’heure. À des fins de conversion de type, Visual Basic considère que 1/1/0001 (1er janvier de l’année 1) comme étant une *valeur neutre* pour la date, et 00:00:00 (minuit) comme valeur neutre pour le moment. `CStr` n’inclut pas de valeurs neutres dans la chaîne résultante. Par exemple, si vous convertissez `#January 1, 0001 9:30:00#` en chaîne, le résultat est « 9:30:00 AM ». les informations de date sont supprimées. Toutefois, les informations de date sont toujours présentes dans la valeur `Date` d’origine et peuvent être récupérées avec des fonctions telles que <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.  
  
> [!NOTE]
> La fonction `CStr` effectue sa conversion en fonction des paramètres de culture actuels de l’application. Pour obtenir la représentation sous forme de chaîne d’un nombre dans une culture particulière, utilisez la méthode `ToString(IFormatProvider)` du nombre. Par exemple, utilisez <xref:System.Double.ToString%2A?displayProperty=nameWithType> lors de la conversion d’une valeur de type `Double` en `String`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Booléen (type de données)](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Date (type de données)](../../../visual-basic/language-reference/data-types/date-data-type.md)
