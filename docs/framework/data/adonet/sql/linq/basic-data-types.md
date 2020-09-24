---
title: Types de données de base
ms.date: 03/30/2017
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
ms.openlocfilehash: ae561bad3315977ba12dd0e12abda1da163ca456
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156015"
---
# <a name="basic-data-types"></a>Types de données de base

Les requêtes LINQ to SQL sont traduites en données Transact-SQL avant d'être exécutées sur Microsoft SQL Server. LINQ to SQL prend en charge une grande partie des fonctionnalités intégrées que SQL Server prend en charge pour les types de données de base.  
  
## <a name="casting"></a>Transtypage  

 Les casts implicites ou explicites sont activés d'un type CLR source en un type CLR cible s'il existe une conversion valide semblable dans SQL Server. Pour plus d’informations sur le cast CLR, consultez [fonction CType](../../../../../visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) et [opérateurs de test de type et de cast](../../../../../csharp/language-reference/operators/type-testing-and-cast.md). Après la conversion, les casts modifient le comportement d'opérations effectuées sur une expression CLR pour correspondre au comportement d'autres expressions CLR qui mappent naturellement au type de destination. Les casts sont également traduisibles dans le contexte de mappage d'héritage. Les objets peuvent être castés à des sous-types d'entité plus spécifiques afin que les données spécifiques à leur sous-type soient accessibles.  
  
## <a name="equality-operators"></a>Opérateurs d'égalité  

 LINQ to SQL prend en charge les opérateurs d'égalité suivants sur les types de données de base à l'intérieur des requêtes LINQ to SQL :  
  
- Opérateur d’égalité et d’inégalité : les opérateurs d’égalité et d’inégalité sont pris en charge pour les types numériques, <xref:System.Boolean> , <xref:System.DateTime> et <xref:System.TimeSpan> . Pour plus d’informations sur les opérateurs Visual Basic `=` et `<>` , consultez [opérateurs de comparaison](../../../../../visual-basic/language-reference/operators/comparison-operators.md). Pour plus d’informations sur les opérateurs de comparaison C# `==` et `!=` , consultez [opérateurs d’égalité](../../../../../csharp/language-reference/operators/equality-operators.md).
  
- Opérateur Is : l'opérateur `IS` a une traduction prise en charge lorsque le mappage d'héritage est utilisé. Il peut être utilisé à la place du test direct de la colonne de discriminateur afin de déterminer si un objet correspond à un type d'entité spécifique et se traduit en un contrôle sur la colonne de discriminateur. Pour plus d’informations sur les opérateurs Visual Basic et C#, consultez [opérateur is](../../../../../visual-basic/language-reference/operators/is-operator.md) et [is](../../../../../csharp/language-reference/operators/type-testing-and-cast.md#is-operator).  
  
## <a name="see-also"></a>Voir aussi

- [Mappage de type SQL-CLR](sql-clr-type-mapping.md)
- [Fonctions et types de données](data-types-and-functions.md)
