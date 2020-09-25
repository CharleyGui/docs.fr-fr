---
title: propriété
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: 6aeb29c5aa608987466ec858416a4ac141ff1da3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180918"
---
# <a name="property"></a>propriété

Les *Propriétés* sont les blocs de construction fondamentaux des [types d’entité](entity-type.md) et des [types complexes](complex-type.md). Les propriétés définissent la forme et les caractéristiques des données qui sont contenues dans une instance de type d'entité ou une instance de type complexe. Les propriétés dans un modèle conceptuel sont analogues aux propriétés définies sur une classe. De même que les propriétés sur une classe définissent la forme de la classe et acheminent des informations sur les objets, les propriétés dans un modèle conceptuel définissent la forme d'un type d'entité et acheminent des informations sur les instances de type d'entité.  
  
> [!NOTE]
> Les propriétés, comme décrit dans cette rubrique, sont différentes des propriétés de navigation. Pour plus d’informations, consultez [Propriétés de navigation](navigation-property.md).  
  
 Une définition de propriété contient les informations suivantes :  
  
- Nom de la propriété. (Obligatoire)  
  
- Type de propriété. (Obligatoire)  
  
- Ensemble de [facettes](facet.md). (facultatif)  
  
 Une propriété peut contenir des données de type primitif (comme une chaîne, un entier ou une valeur booléenne) ou des données structurées (comme un type complexe). Les propriétés de type primitif sont également appelées des propriétés scalaires. Pour plus d’informations, consultez [Entity Data Model : types de données primitifs](entity-data-model-primitive-data-types.md).  
  
> [!NOTE]
> Un type complexe peut lui-même avoir des propriétés qui sont des types complexes.  
  
## <a name="example"></a>Exemple  

 Le diagramme suivant montre un modèle conceptuel avec trois types d'entités : `Book`, `Publisher` et `Author`. Chaque type d'entité possède plusieurs propriétés, bien que les informations de type pour chaque propriété ne soient pas représentées dans le diagramme. Les propriétés qui sont des [clés d’entité](entity-key.md) sont signalées par (Key).  
  
 ![Exemple de modèle avec trois types d’entité](./media/property/example-model-three-entity-types.gif)  
  
 Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels. Le CSDL suivant définit le type d'entité `Book` (tel que présenté dans le diagramme ci-dessus) et indique le type et le nom de chaque propriété à l'aide d'attributs XML. Une facette facultative, `Nullable`, est également définie à l'aide d'un attribut XML.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 Il est possible que l'une des propriétés présentées dans le diagramme soit une propriété de type complexe. Par exemple, la propriété `Address` sur le type d'entité `Publisher` peut être une propriété de type complexe composée de plusieurs propriétés scalaires, telles que `StreetAddress`, `City`, `StateOrProvince`, `Country` et `PostalCode`. Voici la représentation CSDL d'un tel type complexe :  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts clés d'Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
