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
ms.openlocfilehash: 3a1de120f5f97ba93939f332f121d70cd3091216
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392972"
---
# <a name="value-types-and-reference-types"></a>Types valeur et types référence
Il existe deux genres de types dans Visual Basic : les types référence et les types valeur. Les variables des types référence font référence à leurs données (objets), tandis que les variables des types valeur contiennent directement leurs données. Avec les types référence, deux variables peuvent faire référence au même objet ; par conséquent, les opérations sur une variable peuvent affecter le même objet référencé par l'autre variable. Avec les types valeur, chaque variable possède sa propre copie des données, et il n’est pas possible pour les opérations sur une variable d’affecter l’autre (sauf dans le cas du [modificateur ByRef sur les paramètres](../../../language-reference/modifiers/byref.md)).
  
## <a name="value-types"></a>Types valeur  
 Un type de données est un *type valeur* s’il contient les données dans sa propre allocation de mémoire. Les types valeur sont les suivants :  
  
- Tous les types de données numériques  
  
- `Boolean`, `Char` et `Date`  
  
- Toutes les structures, même si leurs membres sont des types référence  
  
- Les énumérations, étant donné que leur type sous-jacent est toujours `SByte` , `Short` , `Integer` , `Long` , `Byte` , `UShort` , `UInteger` ou`ULong`  
  
 Chaque structure est un type valeur, même s’il contient des membres de type référence. Pour cette raison, les types de valeur tels que `Char` et `Integer` sont implémentés par les structures de .NET Framework.  
  
 Vous pouvez déclarer un type valeur à l’aide du mot clé réservé, par exemple, `Decimal` . Vous pouvez également utiliser le `New` mot clé pour initialiser un type valeur. Cela s’avère particulièrement utile si le type a un constructeur qui accepte des paramètres. Par exemple <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> , le constructeur, qui génère une nouvelle `Decimal` valeur à partir des parties fournies.  
  
## <a name="reference-types"></a>Types référence  
 Un *type référence* stocke une référence à ses données. Les types de référence incluent les éléments suivants :  
  
- `String`  
  
- Tous les tableaux, même si leurs éléments sont des types valeur  
  
- Les types de classe, tels que<xref:System.Windows.Forms.Form>  
  
- Délégués  
  
 Une classe est un *type référence*. Notez que chaque tableau est un type référence, même si ses membres sont des types valeur.  
  
 Étant donné que chaque type référence représente une classe .NET Framework sous-jacente, vous devez utiliser le mot clé [New Operator](../../../language-reference/operators/new-operator.md) quand vous l’initialisez. L’instruction suivante initialise un tableau.  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Éléments qui ne sont pas des types  
 Les éléments de programmation suivants ne sont pas qualifiés de types, car vous ne pouvez pas en spécifier un comme type de données pour un élément déclaré :  
  
- Espaces de noms  
  
- Modules  
  
- Événements  
  
- Propriétés et procédures  
  
- Variables, constantes et champs  
  
## <a name="working-with-the-object-data-type"></a>Utilisation du type de données Object  
 Vous pouvez assigner un type référence ou un type valeur à une variable du `Object` type de données. Une `Object` variable contient toujours une référence aux données, jamais les données elles-mêmes. Toutefois, si vous assignez un type valeur à une `Object` variable, il se comporte comme s’il contenait ses propres données. Pour plus d’informations, consultez [Object Data type](../../../language-reference/data-types/object-data-type.md).  
  
 Vous pouvez déterminer si une `Object` variable agit comme un type référence ou un type valeur en la passant à la <xref:Microsoft.VisualBasic.Information.IsReference%2A> méthode dans la <xref:Microsoft.VisualBasic.Information> classe de l’espace de <xref:Microsoft.VisualBasic?displayProperty=nameWithType> noms. <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType>retourne `True` si le contenu de la `Object` variable représente un type référence.  
  
## <a name="see-also"></a>Voir aussi

- [Types valeur Nullable](nullable-value-types.md)
- [Conversions de type en Visual Basic](type-conversions.md)
- [Structure, instruction](../../../language-reference/statements/structure-statement.md)
- [Utilisation efficace des types de données](efficient-use-of-data-types.md)
- [Object Data Type](../../../language-reference/data-types/object-data-type.md)
- [Types de données](index.md)
