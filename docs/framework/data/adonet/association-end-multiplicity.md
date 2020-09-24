---
title: multiplicité de terminaison d'association
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: cf9e6b5af0dc6a33af364901c631b4ce66fe0480
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153506"
---
# <a name="association-end-multiplicity"></a>multiplicité de terminaison d'association

La *multiplicité de terminaison d’association* définit le nombre d’instances de type d' [entité](entity-type.md) qui peuvent être à une terminaison d’une [Association](association-type.md).  
  
 La multiplicité de terminaison d'association peut avoir l'une des valeurs suivantes :  
  
- Un (1) : indique qu'il existe exactement une instance de type d'entité au niveau de la terminaison d'association.  
  
- Zéro ou un (0..1) : indique qu'il existe zéro ou une instance de type d'entité au niveau de la terminaison d'association.  
  
- Many ( \* ) : indique qu’il existe zéro, une ou plusieurs instances de type d’entité au niveau de la terminaison d’association.  
  
 Une association est souvent caractérisée par ses multiplicités de terminaison d'association. Par exemple, si les terminaisons d’une association ont des multiplicités un (1) et plusieurs ( \* ), l’Association est appelée Association un-à-plusieurs. Dans l'exemple ci-dessous, l'association `PublishedBy` est une association un-à-plusieurs (un éditeur publie de nombreux livres, et un livre est publié par un seul éditeur). L'association `WrittenBy` est une association plusieurs-à-plusieurs (un livre peut avoir plusieurs auteurs, et un auteur peut écrire plusieurs livres).  
  
## <a name="example"></a>Exemple  

 Le diagramme suivant montre un modèle conceptuel avec deux associations : `PublishedBy` et `WrittenBy`. Les terminaisons d'association pour l'association `PublishedBy` sont les types d'entité `Book` et `Publisher`. La multiplicité de la `Publisher` terminaison est un (1) et la multiplicité de la `Book` terminaison est plusieurs ( \* ).  
  
 ![Exemple de modèle avec trois types d’entité](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 Le Entity Framework ADO.NET utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels. Le CSDL suivant définit l'association `PublishedBy` présentée dans le diagramme ci-dessus :  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts clés d'Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
