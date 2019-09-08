---
title: Propriété de clé étrangère
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: e2f41c2db9aea26c7954a99ebf3f40b03e8df735
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795026"
---
# <a name="foreign-key-property"></a>Propriété de clé étrangère
Une *propriété de clé étrangère* dans le Entity Data Model (EDM) est une [propriété](property.md) de type primitif (ou un ensemble de propriétés de type primitif) sur un [type d’entité](entity-type.md) qui contient la clé d' [entité](entity-key.md) d’un autre type d’entité.  
  
 Une propriété de clé étrangère est analogue à une colonne clé étrangère dans une base de données relationnelle. De la même façon que les colonnes clés étrangères sont utilisées dans une base de données relationnelle pour créer des relations entre les lignes dans les tables, les propriétés de clé étrangère dans un modèle conceptuel sont utilisées pour établir des [associations](association-type.md) entre les types d’entités. Une [contrainte d’intégrité référentielle](referential-integrity-constraint.md) est utilisée pour définir une association entre deux types d’entité lorsque l’un des types a une propriété de clé étrangère.  
  
## <a name="example"></a>Exemples  
 Le diagramme suivant montre un modèle conceptuel avec trois types d'entités : `Book`, `Publisher` et `Author`. Le type d'entité `Book` a une propriété, `PublisherId`, qui référence la clé d'entité du type d'entité `Publisher` lorsque vous définissez une contrainte d'intégrité référentielle sur l'association `PublishedBy`.  
  
 ![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Exemple de modèle de contrainte référentielle")  
  
 Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](./ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels. Le CSDL suivant utilise la propriété de clé étrangère `PublisherId` pour définir une contrainte d'intégrité référentielle sur l'association `PublishedBy` présentée dans le modèle conceptuel ci-dessus.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts clés d’Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
