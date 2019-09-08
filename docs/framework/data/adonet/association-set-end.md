---
title: terminaison d'ensemble d'associations
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 48ba84d46e380462405551cc2d826d84368b351a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786933"
---
# <a name="association-set-end"></a>terminaison d'ensemble d'associations
Une *terminaison d’ensemble d’associations* identifie le [type d’entité](entity-type.md) et le [jeu d’entités](entity-set.md) à la fin d’un [ensemble d’associations](association-set.md). Les terminaisons d'ensemble d'associations sont définies dans le cadre d'un ensemble d'associations ; un ensemble d'associations doit avoir exactement deux terminaisons d'ensemble d'associations.  
  
 Une définition de terminaison d'ensemble d'associations contient les informations suivantes :  
  
- Un des types d'entité impliqués dans l'ensemble d'associations. (Requis)  
  
- Jeu d'entités pour le type d'entité impliqué dans l'ensemble d'associations. (Requis)  
  
## <a name="example"></a>Exemple  
 Le diagramme suivant montre un modèle conceptuel avec deux associations : `WrittenBy` et `PublishedBy`.  
  
 ![Exemple de modèle avec trois types d’entité](./media/association-set-end/example-model-three-entity-types.gif)  
  
 Le diagramme suivant montre un ensemble d'associations (`PublishedBy`) et deux jeux d'entités (`Books` et `Publishers`) selon le modèle conceptuel présenté ci-dessus. Les terminaisons d'ensemble d'associations sont les jeux d'entités `Books` et `Publishers`. Bi dans le `Books` jeu `Book` d’entités représente une instance du type d’entité au moment de l’exécution. De même, PJ représente une `Publisher` instance dans le `Publishers` jeu d’entités. BiPj représente une instance de l' `PublishedBy` Association dans l' `PublishedBy` ensemble d’associations.  
  
 ![Capture d’écran montrant un exemple de jeu.](./media/association-set-end/sets-example-association.gif)  
  
 Le [Entity Framework ADO.net](./ef/index.md) utilise une DSL appelée Conceptual Schema Definition Language ([CSDL](./ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels. Le CSDL suivant définit un conteneur d'entités avec un ensemble d'associations pour chaque association dans le diagramme ci-dessus. Notez que les terminaisons d'ensemble d'associations sont définies dans le cadre de chaque définition d'ensemble d'associations.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts clés d’Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
