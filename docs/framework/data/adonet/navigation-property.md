---
title: Propriété de navigation
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: b6c286e63322a66be0407c864295a20685df2b7f
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980156"
---
# <a name="navigation-property"></a>Propriété de navigation

Une *propriété de navigation* est une propriété facultative sur [un type d’entité](entity-type.md) qui permet de naviguer d’une [terminaison](association-end.md) d’une [Association](association-type.md) à l’autre terminaison. Contrairement aux autres [Propriétés](property.md), les propriétés de navigation ne transmettent pas de données.

Une définition de propriété de navigation comprend les éléments suivants :

- Nom. (Requis)

- Association faisant l'objet de la navigation. (Requis)

- Terminaisons de l'association faisant l'objet de la navigation. (Requis)

Notez que les propriétés de navigation sont facultatives sur les deux types d'entités au niveau des terminaisons d'une association. Si vous définissez une propriété de navigation sur un type d'entité au niveau de la terminaison d'une association, il n'est pas nécessaire de définir une propriété de navigation sur le type d'entité à l'autre terminaison de l'association.

Le type de données d’une propriété de navigation est déterminé par la [multiplicité](association-end-multiplicity.md) de sa [terminaison d’association](association-end.md)distante. Par exemple, considérez une propriété de navigation, `OrdersNavProp`, qui existe sur un type d'entité `Customer` et qui navigue dans une association un-à-plusieurs entre `Customer` et `Order`. Étant donné que la terminaison d’association distante pour la propriété de navigation a une multiplicité de plusieurs (\*), son type de données est une collection (de `Order`). De même, si une propriété de navigation, `CustomerNavProp`, existe sur le type d'entité `Order`, son type de données est `Customer`, car la multiplicité de la terminaison distante est un (1).

## <a name="example"></a>Exemple

Le diagramme suivant montre un modèle conceptuel avec trois types d'entités : `Book`, `Publisher` et `Author`. Les propriétés de navigation, `Publisher` et `Authors`, sont définies sur le type d'entité Book. La propriété de navigation `Books` est définie sur le type d'entité Publisher et le type d'entité `Author`.

 ![Diagramme montrant un modèle conceptuel avec trois types d’entité.](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels. Le CSDL suivant définit le type d'entité `Book` présenté dans le diagramme ci-dessus :

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

Notez que des attributs XML sont utilisés pour communiquer les informations nécessaires pour définir une propriété de navigation. L'attribut `Name` contient le nom de la propriété, `Relationship` contient le nom de l'association faisant l'objet de la navigation, et `FromRole` et `ToRole` contiennent les terminaisons de l'association.

## <a name="see-also"></a>Voir aussi

- [Concepts clés d’Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
- [Relations, propriétés de navigation et clés étrangères](/ef/ef6/fundamentals/relationships)
