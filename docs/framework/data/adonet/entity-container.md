---
title: conteneur d'entités
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 95740fb9d8b357a4fa160af6fdafb139711283cd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795255"
---
# <a name="entity-container"></a>conteneur d'entités
Un *conteneur d’entités* est un regroupement logique de [jeux d’entités](entity-set.md), d' [ensembles d’associations](association-set.md)et d’importations de [fonctions](model-declared-function.md).  
  
 Un conteneur d'entités défini dans un modèle conceptuel doit répondre aux spécifications suivantes :  
  
- Au moins un conteneur d'entités doit être défini dans chaque modèle conceptuel.  
  
- Le conteneur d'entités doit avoir un nom unique dans chaque modèle conceptuel.  
  
 Un conteneur d'entités peut définir des jeux d'entités ou des ensembles d'associations qui utilisent des types d'entité ou des associations définis dans un ou plusieurs espaces de noms. Pour plus d’informations, [consultez Entity Data Model : Espaces de noms.](entity-data-model-namespaces.md)  
  
## <a name="example"></a>Exemples  
 Le diagramme suivant montre un modèle conceptuel avec trois types d'entités : `Book`, `Publisher` et `Author`.  Pour plus d'informations, consultez l'exemple suivant.  
  
 ![Exemple de modèle avec trois types d’entité](./media/entity-container/example-model-three-entity-types.gif)  
  
 Bien que le diagramme n'achemine pas d'informations sur le conteneur d'entités, le modèle conceptuel doit définir un conteneur d'entités. Le [Entity Framework ADO.net](./ef/index.md) utilise une DSL appelée Conceptual Schema Definition Language ([CSDL](./ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels. Le CSDL suivant définit un conteneur d'entités pour le modèle conceptuel présenté dans le diagramme ci-dessus. Notez que le nom du conteneur d'entités est défini dans un attribut XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts clés d’Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
