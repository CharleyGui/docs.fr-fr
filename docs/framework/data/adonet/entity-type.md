---
title: type d'entité
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: efd3ea0972148e885d4b22b49040640539bb28cd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795122"
---
# <a name="entity-type"></a>type d'entité
Le *type d’entité* est le bloc de construction fondamental pour la description de la structure des données avec le Entity Data Model (EDM). Dans un modèle conceptuel, un type d'entité représente la structure des concepts de niveau supérieur, comme les clients ou les commandes. Un type d'entité est un modèle pour les instances de type d'entité. Chaque modèle contient les informations suivantes :  
  
- Nom unique. (Obligatoire.)  
  
- [Clé d’entité](entity-key.md) définie par une ou plusieurs propriétés. (Obligatoire.)  
  
- Données sous la forme de [Propriétés](property.md). (Facultatif)  
  
- [Propriétés de navigation](navigation-property.md) qui permettent de naviguer d’une [terminaison](association-end.md) d’une [Association](association-type.md) à l’autre extrémité. (facultatif)  
  
 Dans une application, une instance d'un type d'entité représente un objet spécifique (tel qu'un client ou une commande spécifique). Chaque instance d’un type d’entité doit avoir une [clé d’entité](entity-key.md) unique dans un [jeu d’entités](entity-set.md).  
  
 Deux instances de type d'entité sont considérées égales seulement si elles sont du même type et si les valeurs de leurs clés d'entité sont identiques.  
  
## <a name="example"></a>Exemple  
 Le diagramme suivant montre un modèle conceptuel avec trois types d'entité : `Book`, `Publisher` et `Author`.  
  
 ![Exemple de modèle avec trois types d’entité](./media/entity-type/example-model-three-entity-types.gif)  
  
 Notez que les propriétés de chaque type d'entité qui composent sa clé d'entité sont signalées par « (Key) ».  
  
 Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](./ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels. Le CSDL suivant définit le type d'entité `Book` présenté dans le diagramme ci-dessus :  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts clés d’Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
- [facet](facet.md)
