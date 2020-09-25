---
title: Entity Data Model
description: Le Entity Data Model décrit la structure des données, indépendamment de son formulaire stocké, qui résout les problèmes résultant du stockage de données dans de nombreuses formes.
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: 9323f652d1cfa27d442d45bd01e546f3b81d7e80
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200769"
---
# <a name="entity-data-model"></a>Entity Data Model

Le modèle EDM (Entity Data Model) est un jeu de concepts qui décrivent la structure des données, indépendamment de la forme sous laquelle elles sont stockées. Inspiré du modèle entité-relation décrit par Peter Chen en 1976, le modèle EDM le complète et étend ses utilisations traditionnelles.  
  
 Le modèle EDM aborde les difficultés qui se présentent lors du stockage de données sous plusieurs formes. Par exemple, prenons une entreprise qui stocke des données dans des bases de données relationnelles, des fichiers texte, des fichiers XML, des feuilles de calcul et des rapports. Cette diversité pose des problèmes importants en termes de modélisation des données, de conception d'application et d'accès aux données. Lors de la conception d'une application orientée données, l'écriture de code efficace et gérable sans nuire à l'efficacité de l'accès aux données, du stockage et de l'évolutivité relève du défi. Lorsque les données ont une structure relationnelle, l'accès aux données, le stockage et l'évolutivité sont très efficaces, mais l'écriture de code efficace et gérable devient plus difficile. Lorsque les données ont une structure objet, la tendance est inversée : l'écriture de code efficace et gérable vient au détriment de l'efficacité de l'accès aux données, du stockage et de l'évolutivité. Même s'il est possible de trouver un juste équilibre entre ces deux aspects, de nouvelles difficultés se présentent lorsque des données passent d'une forme à une autre. Le modèle Entity Data Model aborde ces difficultés en décrivant la structure des données en termes d'entités et de relations qui sont indépendantes de tout schéma de stockage. La forme sous laquelle les données sont stockées n'a alors plus aucune incidence sur la conception et le développement de l'application. Par ailleurs, comme les entités et les relations décrivent la structure des données telles qu'elles sont utilisées dans une application (et non la forme sous laquelle elles sont stockées), elles peuvent évoluer parallèlement à une application.  
  
 Un `conceptual model` est une représentation spécifique de la structure des données sous forme d'entités et de relations. Il est en général défini dans un langage spécifique à un domaine (DSL) qui implémente les concepts du modèle EDM. Le [langage CSDL (Conceptual Schema Definition Language)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec) est un exemple de ce langage spécifique à un domaine. Les entités et les relations décrites dans un modèle conceptuel peuvent être considérées comme des abstractions d'objets et d'associations dans une application. Cela permet aux développeurs de se concentrer sur le modèle conceptuel sans se soucier du schéma de stockage, et d'écrire du code en favorisant son efficacité et sa maintenabilité. Pendant ce temps, les concepteurs de schémas de stockage peuvent se concentrer sur l'efficacité de l'accès aux données, du stockage et de l'évolutivité.  
  
## <a name="in-this-section"></a>Dans cette section  

 Les rubriques de cette section décrivent les concepts du modèle EDM. Tout langage DSL qui implémente le modèle EDM doit inclure les concepts décrits ici. Notez que le [Entity Framework ADO.net](./ef/index.md) utilise le langage CSDL pour définir des modèles conceptuels. Pour plus d'informations, consultez [CSDL Specification](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).  
  
 [Concepts clés d'Entity Data Model](entity-data-model-key-concepts.md)  
  
 [Entity Data Model : Espaces de noms](entity-data-model-namespaces.md)  
  
 [Entity Data Model : types de données primitifs](entity-data-model-primitive-data-types.md)  
  
 [Entity Data Model : Héritage](entity-data-model-inheritance.md)  
  
 [terminaison d'association](association-end.md)  
  
 [multiplicité de terminaison d'association](association-end-multiplicity.md)  
  
 [jeu d'associations](association-set.md)  
  
 [terminaison d'ensemble d'associations](association-set-end.md)  
  
 [type d'association](association-type.md)  
  
 [type complexe](complex-type.md)  
  
 [conteneur d'entités](entity-container.md)  
  
 [clé d'entité](entity-key.md)  
  
 [jeu d'entités](entity-set.md)  
  
 [type d’entité](entity-type.md)  
  
 [articulaire](facet.md)  
  
 [Propriété de clé étrangère](foreign-key-property.md)  
  
 [fonction déclarée par modèle](model-declared-function.md)  
  
 [fonction définie par modèle](model-defined-function.md)  
  
 [propriété de navigation](navigation-property.md)  
  
 [property](property.md)  
  
 [contrainte d'intégrité référentielle](referential-integrity-constraint.md)  
  
## <a name="see-also"></a>Voir aussi

- [Outils de Entity Data Model ADO.NET](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Présentation d'un fichier .edmx](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Spécification CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
