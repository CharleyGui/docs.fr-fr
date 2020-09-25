---
title: 'Entity Data Model : Héritage'
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: 057040eee411988c46adc9c4cabcfe5f5a185e1b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175458"
---
# <a name="entity-data-model-inheritance"></a>Entity Data Model : Héritage

Le Entity Data Model (EDM) prend en charge l’héritage pour les [types d’entités](entity-type.md). L'héritage dans le modèle EDM est semblable à l'héritage pour les classes dans les langages de programmation orientés objet. Comme pour les classes dans les langages orientés objet, dans un modèle conceptuel, vous pouvez définir un type d’entité ( *type dérivé*) qui hérite d’un autre type d’entité ( *type de base*). Toutefois, contrairement aux classes dans la programmation orientée objet, dans un modèle conceptuel, le type dérivé hérite toujours de toutes les [Propriétés](property.md) et [Propriétés de navigation](navigation-property.md) du type de base. Vous ne pouvez pas remplacer les propriétés héritées dans un type dérivé.  
  
 Dans un modèle conceptuel, vous pouvez générer des hiérarchies d'héritage dans lesquelles un type dérivé hérite d'un autre type dérivé. Le type situé en haut de la hiérarchie (celui de la hiérarchie qui n’est pas un type dérivé) est appelé *type racine*. Dans une hiérarchie d’héritage, la [clé d’entité](entity-key.md) doit être définie sur le type racine.  
  
 Vous ne pouvez pas générer de hiérarchies d'héritage dans lesquelles un type dérivé hérite de plusieurs types. Par exemple, dans un modèle conceptuel avec un type d'entité `Book`, vous pouvez définir les types dérivés `FictionBook` et `NonFictionBook` qui héritent de `Book`. Toutefois, vous ne pouvez pas ensuite définir un type qui hérite à la fois du type `FictionBook` et du type `NonFictionBook`.  
  
## <a name="example"></a>Exemple  

Le diagramme suivant montre un modèle conceptuel avec quatre types d’entités : `Book` , `FictionBook` , `Publisher` et `Author` . Le type d'entité `FictionBook` est un type dérivé qui hérite du type d'entité `Book`. Le type `FictionBook` hérite les propriétés `ISBN (Key)`, `Title` et `Revision`, et définit une propriété supplémentaire appelée `Genre`.  
  
 ![Diagramme qui montre un modèle conceptuel avec quatre types d’entités.](./media/entity-data-model-inheritance/entity-type-inheritance.gif)  
  
 Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels. Le CSDL suivant définit un type d'entité, `FictionBook`, qui hérite du type `Book` (comme dans le diagramme ci-dessus) :  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts clés d'Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
