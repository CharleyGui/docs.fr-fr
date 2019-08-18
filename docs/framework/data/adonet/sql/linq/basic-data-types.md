---
title: Types de données de base
ms.date: 03/30/2017
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
ms.openlocfilehash: 249155e185986504a85451c367c5b41cc5e68d96
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567386"
---
# <a name="basic-data-types"></a>Types de données de base
Les requêtes LINQ to SQL sont traduites en données Transact-SQL avant d'être exécutées sur Microsoft SQL Server. LINQ to SQL prend en charge une grande partie des fonctionnalités intégrées que SQL Server prend en charge pour les types de données de base.  
  
## <a name="casting"></a>Cast  
 Les casts implicites ou explicites sont activés d'un type CLR source en un type CLR cible s'il existe une conversion valide semblable dans SQL Server. Pour plus d’informations sur le cast CLR, consultez [fonction CType](~/docs/visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) et [opérateurs de test de type et de cast](~/docs/csharp/language-reference/operators/type-testing-and-cast.md). Après la conversion, les casts modifient le comportement d'opérations effectuées sur une expression CLR pour correspondre au comportement d'autres expressions CLR qui mappent naturellement au type de destination. Les casts sont également traduisibles dans le contexte de mappage d'héritage. Les objets peuvent être castés à des sous-types d'entité plus spécifiques afin que les données spécifiques à leur sous-type soient accessibles.  
  
## <a name="equality-operators"></a>Opérateurs d'égalité  
 LINQ to SQL prend en charge les opérateurs d'égalité suivants sur les types de données de base à l'intérieur des requêtes LINQ to SQL :  
  
- Opérateur d’égalité et d’inégalité: Les opérateurs d’égalité et d’inégalité sont pris <xref:System.Boolean>en <xref:System.DateTime>charge pour <xref:System.TimeSpan> les types numériques,, et. Pour plus d’informations sur `=` les `<>`opérateurs Visual Basic et, consultez [opérateurs de comparaison](~/docs/visual-basic/language-reference/operators/comparison-operators.md). Pour plus d’informations C# sur les `==` opérateurs `!=`de comparaison et, consultez [opérateurs d’égalité](~/docs/csharp/language-reference/operators/equality-operators.md).
  
- Opérateur is: L' `IS` opérateur a une traduction prise en charge lorsque le mappage d’héritage est utilisé. Il peut être utilisé à la place du test direct de la colonne de discriminateur afin de déterminer si un objet correspond à un type d'entité spécifique et se traduit en un contrôle sur la colonne de discriminateur. Pour plus d’informations sur les opérateurs C# Visual Basic et is, consultez [opérateur is](~/docs/visual-basic/language-reference/operators/is-operator.md) et [is](~/docs/csharp/language-reference/operators/type-testing-and-cast.md#is-operator).  
  
## <a name="see-also"></a>Voir aussi

- [Mappage de type SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Fonctions et types de données](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
