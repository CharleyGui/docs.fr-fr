---
title: contrainte d'intégrité référentielle
description: Découvrez les contraintes d’intégrité référentielle dans le Entity Data Model, qui garantissent que les associations valides existent toujours entre les types d’entités.
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: 65c811b2a12a64870107ff771d5acc64e86f2c1f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286622"
---
# <a name="referential-integrity-constraint"></a>contrainte d'intégrité référentielle
Une *contrainte d’intégrité référentielle* dans le Entity Data Model (EDM) est similaire à une contrainte d’intégrité référentielle dans une base de données relationnelle. De la même façon qu’une colonne (ou des colonnes) d’une table de base de données peut faire référence à la clé primaire d’une autre table [, une ou plusieurs propriétés d'](property.md) un [type d’entité](entity-type.md) peuvent référencer la [clé d’entité](entity-key.md) d’un autre type d’entité. Le type d’entité référencé est appelé *terminaison principale* de la contrainte. Le type d’entité qui référence la terminaison principale est appelé *terminaison dépendante* de la contrainte.  
  
 Une contrainte d’intégrité référentielle est définie dans le cadre d’une [Association](association-type.md) entre deux types d’entités. La définition d'une contrainte d'intégrité référentielle spécifie les informations suivantes :  
  
- Terminaison principale de la contrainte. (Type d'entité dont la clé d'entité est référencée par la terminaison dépendante.)  
  
- Clé d'entité de la terminaison principale.  
  
- Terminaison dépendante de la contrainte. (Type d'entité dont une ou plusieurs propriétés référencent la clé d'entité de la terminaison principale.)  
  
- Propriété ou propriétés de référence de la terminaison dépendante.  
  
 Les contraintes d'intégrité référentielle dans le modèle EDM ont pour objectif de vérifier que des associations valides existent toujours. Pour plus d’informations, consultez [propriété de clé étrangère](foreign-key-property.md).  
  
## <a name="example"></a>Exemple  
 Le diagramme suivant montre un modèle conceptuel avec deux associations : `WrittenBy` et `PublishedBy`. Le type d'entité `Book` a une propriété, `PublisherId`, qui référence la clé d'entité du type d'entité `Publisher` lorsque vous définissez une contrainte d'intégrité référentielle sur l'association `PublishedBy`.  
  
 ![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "Exemple de modèle de contrainte référentielle")  
  
 Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels. Le CSDL suivant définit une contrainte d'intégrité référentielle sur l'association `PublishedBy` présentée dans le modèle conceptuel ci-dessus.  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts clés d’Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
