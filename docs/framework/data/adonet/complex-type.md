---
title: type complexe
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: ef20de6a9e72d3123d745ef5501ecdb7fa63967d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203785"
---
# <a name="complex-type"></a>type complexe

Un *type complexe* est un modèle permettant de définir des propriétés riches et structurées sur des [types d’entités](entity-type.md) ou sur d’autres types complexes. Chaque modèle contient les informations suivantes :  
  
- Nom unique. (Obligatoire)  
  
    > [!NOTE]
    > Le nom d'un type complexe ne peut pas être le même qu'un nom de type d'entité dans le même espace de noms.  
  
- Données sous la forme d’une ou de plusieurs [Propriétés](property.md). (Facultatif.)  
  
    > [!NOTE]
    > Une propriété d'un type complexe peut être un autre type complexe.  
  
 Un type complexe est semblable à un type d'entité en ce sens qu'il peut acheminer une charge utile de données sous la forme de propriétés de type primitif ou d'autres types complexes. Toutefois, il existe des différences clés entre les types complexes et les types d'entités :  
  
- Les types complexes n'ont pas d'identité et, par conséquent, ne peuvent pas exister indépendamment. Les types complexes peuvent uniquement exister en tant que propriétés sur des types d'entités ou d'autres types complexes.  
  
- Les types complexes ne peuvent pas participer aux [associations](association-type.md). Aucune des terminaisons d’une association ne peut être un type complexe ; par conséquent, les [Propriétés de navigation](navigation-property.md) ne peuvent pas être définies sur des types complexes.  
  
## <a name="example"></a>Exemple  

 Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels. Le CSDL suivant définit un type complexe, Address, avec les propriétés de type primitif `StreetAddress`, `City`, `StateOrProvince`, `Country` et `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Pour définir le type complexe `Address` (ci-dessus) en tant que propriété sur un type d'entité, vous devez déclarer le type de propriété dans la définition de type d'entité. Le CSDL suivant déclare la propriété `Address` en tant que type complexe sur un type d'entité (Publisher) :  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts clés d'Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
