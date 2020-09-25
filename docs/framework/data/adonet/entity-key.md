---
title: clé d'entité
ms.date: 03/30/2017
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
ms.openlocfilehash: b2692faf2f8bea27c8a5d6cdc52689ca186d3194
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200782"
---
# <a name="entity-key"></a>clé d'entité

Une *clé d’entité* est une [propriété](property.md) ou un ensemble de propriétés d’un [type d’entité](entity-type.md) qui sont utilisées pour déterminer l’identité. Les propriétés qui composent une clé d'entité sont choisies au moment du design. Les valeurs des propriétés de clé d’entité doivent identifier de manière unique une instance de type d’entité dans un [jeu d’entités](entity-set.md) au moment de l’exécution. Les propriétés qui composent une clé d'entité doivent être choisies pour garantir l'unicité des instances dans un jeu d'entités.  
  
 Pour être une clé d’entité, un jeu de propriétés doit répondre aux exigences suivantes :  
  
- Il ne peut pas y avoir deux clés d'entité identiques dans un même jeu d'entités. Autrement dit, pour deux entités quelconques dans un jeu d'entités, les valeurs de toutes les propriétés qui constituent une clé ne peuvent pas être les mêmes. Toutefois, quelques-unes des valeurs (mais pas toutes) qui composent une clé d'entité peuvent être les mêmes.  
  
- Une clé d’entité doit se composer d’un jeu de [Propriétés de type primitif](entity-data-model-primitive-data-types.md), non Nullable, immuables.  
  
- Les propriétés qui composent une clé d'entité pour un type d'entité donné ne peuvent pas être modifiées. Vous ne pouvez pas autoriser plusieurs clés d'entité possibles pour un type d'entité donné ; les clés de substitution ne sont pas prises en charge.  
  
- Lorsqu'une entité est impliquée dans une hiérarchie d'héritage, l'entité racine doit contenir toutes les propriétés qui composent la clé d'entité, et la clé d'entité doit être définie sur le type d'entité racine. Pour plus d’informations, consultez [Entity Data Model : héritage](entity-data-model-inheritance.md).  
  
## <a name="example"></a>Exemple  

 Le diagramme suivant montre un modèle conceptuel avec trois types d'entités : `Book`, `Publisher` et `Author`. Les propriétés de chaque type d'entité qui composent sa clé d'entité sont signalées par « (Key) ». Notez que le type d'entité `Author` possède une clé d'entité composée de deux propriétés : `Name` et `Address`.  
  
 ![Exemple de modèle avec trois types d’entité](./media/entity-key/example-model-three-entity-types.gif)  
  
 Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels. Le CSDL suivant définit le type d'entité `Book` présenté dans le diagramme ci-dessus. Notez que la clé d'entité est définie en référençant la propriété `ISBN` du type d'entité.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 La propriété `ISBN` est un bon choix pour la clé d'entité, car un numéro ISBN (International Standard Book Number) identifie un livre de façon unique.  
  
 Le CSDL suivant définit le type d'entité `Author` présenté dans le diagramme ci-dessus. Notez que la clé d'entité comprend deux propriétés : `Name` et `Address`.  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 L'utilisation de `Name` et d'`Address` pour la clé d'entité est un choix raisonnable, car il est improbable que deux auteurs du même nom habitent à la même adresse. Toutefois, ce choix pour une clé d'entité ne garantit pas vraiment l'unicité des clés d'entité dans un jeu d'entités. Il est recommandé dans ce cas d'ajouter une propriété, telle qu'`AuthorId`, qui peut être utilisée pour identifier un auteur de façon unique.  
  
## <a name="see-also"></a>Voir aussi

- [Concepts clés d'Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
