---
title: Types valeur et types référence
ms.date: 07/20/2015
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
ms.openlocfilehash: 466bb5386235917705344d35c5141c8bf779218d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582643"
---
# <a name="value-types-and-reference-types"></a>Types valeur et types référence
Il existe deux genres de types dans Visual Basic : les types référence et les types valeur. Les variables des types référence font référence à leurs données (objets), tandis que les variables des types valeur contiennent directement leurs données. Avec les types référence, deux variables peuvent faire référence au même objet ; par conséquent, les opérations sur une variable peuvent affecter le même objet référencé par l'autre variable. Avec les types valeur, chaque variable possède sa propre copie des données, et il n’est pas possible pour les opérations sur une variable d’affecter l’autre (sauf dans le cas du [modificateur ByRef sur les paramètres](../../../language-reference/modifiers/byref.md)).
  
## <a name="value-types"></a>Types valeur  
 Un type de données est un *type valeur* s’il contient les données dans sa propre allocation de mémoire. Les types valeur sont les suivants :  
  
- Tous les types de données numériques  
  
- `Boolean`, `Char`et `Date`  
  
- Toutes les structures, même si leurs membres sont des types référence  
  
- Les énumérations, puisque leur type sous-jacent est toujours `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger` ou `ULong`  
  
 Chaque structure est un type valeur, même s’il contient des membres de type référence. Pour cette raison, les types de valeur tels que `Char` et `Integer` sont implémentés par les structures de .NET Framework.  
  
 Vous pouvez déclarer un type valeur à l’aide du mot clé réservé, par exemple, `Decimal`. Vous pouvez également utiliser le mot clé `New` pour initialiser un type valeur. Cela s’avère particulièrement utile si le type a un constructeur qui accepte des paramètres. Par exemple, le constructeur <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>, qui génère une nouvelle valeur `Decimal` à partir des parties fournies.  
  
## <a name="reference-types"></a>Types référence  
 Un *type référence* stocke une référence à ses données. Les types de référence incluent les éléments suivants :  
  
- `String`  
  
- Tous les tableaux, même si leurs éléments sont des types valeur  
  
- Les types de classe, tels que <xref:System.Windows.Forms.Form>  
  
- Délégués  
  
 Une classe est un *type référence*. Notez que chaque tableau est un type référence, même si ses membres sont des types valeur.  
  
 Étant donné que chaque type référence représente une classe .NET Framework sous-jacente, vous devez utiliser le mot clé [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) quand vous l’initialisez. L’instruction suivante initialise un tableau.  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Éléments qui ne sont pas des types  
 Les éléments de programmation suivants ne sont pas qualifiés de types, car vous ne pouvez pas en spécifier un comme type de données pour un élément déclaré :  
  
- Espaces de noms  
  
- Modules  
  
- événements  
  
- Propriétés et procédures  
  
- Variables, constantes et champs  
  
## <a name="working-with-the-object-data-type"></a>Utilisation du type de données Object  
 Vous pouvez assigner un type référence ou un type valeur à une variable du type de données `Object`. Une variable `Object` contient toujours une référence aux données, jamais les données elles-mêmes. Toutefois, si vous assignez un type valeur à une variable `Object`, il se comporte comme s’il contenait ses propres données. Pour plus d’informations, consultez [Object Data type](../../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Vous pouvez déterminer si une variable `Object` agit comme un type référence ou un type valeur en la passant à la méthode <xref:Microsoft.VisualBasic.Information.IsReference%2A> dans la classe <xref:Microsoft.VisualBasic.Information> de l’espace de noms <xref:Microsoft.VisualBasic?displayProperty=nameWithType>. <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> retourne `True` si le contenu de la variable `Object` représente un type référence.  
  
## <a name="see-also"></a>Voir aussi

- [Types valeur Nullable](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Structure (instruction)](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Utilisation efficace des types de données](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Object (type de données)](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
