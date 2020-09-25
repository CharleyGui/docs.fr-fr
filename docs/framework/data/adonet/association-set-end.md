---
title: terminaison d'ensemble d'associations
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: bd104ffb46cbd02a886ce87822ddc37159961174
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198793"
---
# <a name="association-set-end"></a>terminaison d'ensemble d'associations

Une *terminaison d’ensemble d’associations* identifie le [type d’entité](entity-type.md) et le [jeu d’entités](entity-set.md) à la fin d’un [ensemble d’associations](association-set.md). Les terminaisons d'ensemble d'associations sont définies dans le cadre d'un ensemble d'associations ; un ensemble d'associations doit avoir exactement deux terminaisons d'ensemble d'associations.  
  
 Une définition de terminaison d'ensemble d'associations contient les informations suivantes :  
  
- Un des types d'entité impliqués dans l'ensemble d'associations. (Obligatoire)  
  
- Jeu d'entités pour le type d'entité impliqué dans l'ensemble d'associations. (Obligatoire)  
  
## <a name="example"></a>Exemple  

 Le diagramme suivant montre un modèle conceptuel avec deux associations : `WrittenBy` et `PublishedBy`.  
  
 ![Exemple de modèle avec trois types d’entité](./media/association-set-end/example-model-three-entity-types.gif)  
  
 Le diagramme suivant montre un ensemble d'associations (`PublishedBy`) et deux jeux d'entités (`Books` et `Publishers`) selon le modèle conceptuel présenté ci-dessus. Les terminaisons d'ensemble d'associations sont les jeux d'entités `Books` et `Publishers`. Bi dans le `Books` jeu d’entités représente une instance du `Book` type d’entité au moment de l’exécution. De même, PJ représente une `Publisher` instance dans le `Publishers` jeu d’entités. BiPj représente une instance de l' `PublishedBy` Association dans l' `PublishedBy` ensemble d’associations.  
  
 ![Capture d’écran montrant un exemple de jeu.](./media/association-set-end/sets-example-association.gif)  
  
 Le [Entity Framework ADO.net](./ef/index.md) utilise une DSL appelée Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels. Le CSDL suivant définit un conteneur d'entités avec un ensemble d'associations pour chaque association dans le diagramme ci-dessus. Notez que les terminaisons d'ensemble d'associations sont définies dans le cadre de chaque définition d'ensemble d'associations.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts clés d'Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
