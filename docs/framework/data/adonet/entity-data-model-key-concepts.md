---
title: Concepts clés d'Entity Data Model
ms.date: 03/30/2017
ms.assetid: c635a16d-6674-45aa-9344-dcb7df992bab
ms.openlocfilehash: d020de65ff64d93c0ea925b71e5f1546eb4402aa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191760"
---
# <a name="entity-data-model-key-concepts"></a>Concepts clés d'Entity Data Model

Le Entity Data Model (EDM) utilise trois concepts clés pour décrire la structure des données : le *type d’entité*, le type d' *Association*et la *propriété*. Il s'agit des concepts les plus importants pour décrire la structure des données dans n'importe quelle implémentation du modèle EDM.  
  
## <a name="entity-type"></a>Type d’entité  

 Le [type d’entité](entity-type.md) est le bloc de construction fondamental pour la description de la structure des données avec le Entity Data Model. Dans un modèle conceptuel, les types d’entités sont construits à partir de [Propriétés](property.md) et décrivent la structure des concepts de niveau supérieur, tels que les clients et les commandes dans une application métier. De la même manière qu'une définition de classe dans un logiciel est un modèle pour les instances de la classe, un type d'entité est un modèle pour les entités. Une entité représente un objet spécifique (tel qu'un client ou une commande spécifique). Chaque entité doit avoir une [clé d’entité](entity-key.md) unique dans un [jeu d’entités](entity-set.md).  Un jeu d'entités est une collection d'instances d'un type d'entité spécifique. Les jeux d’entités (et [ensembles d’associations](association-set.md)) sont regroupés logiquement dans un [conteneur d’entités](entity-container.md).  
  
 Les types d'entité prennent en charge l'héritage ; autrement dit, un type d'entité peut être dérivé d'un autre. Pour plus d’informations, consultez [Entity Data Model : héritage](entity-data-model-inheritance.md).  
  
## <a name="association-type"></a>Type d'association  

 Un [type d’association](association-type.md) (également appelé Association) est le bloc de construction fondamental pour la description des relations dans le Entity Data Model. Dans un modèle conceptuel, une association représente une relation entre deux types d'entité (tels que Customer et Order). Chaque association a deux [terminaisons d’association](association-end.md) qui spécifient les types d’entité impliqués dans l’Association. Chaque terminaison d’association spécifie également une [multiplicité de terminaison d’association](association-end-multiplicity.md) qui indique le nombre d’entités qui peuvent être à cette terminaison de l’Association. Une multiplicité de terminaison d’association peut avoir la valeur un (1), zéro ou un (0.. 1), ou plusieurs ( \* ). Les entités situées à l’extrémité d’une association sont accessibles par le biais des [Propriétés de navigation](navigation-property.md)ou via des clés étrangères si elles sont exposées sur un type d’entité. Pour plus d’informations, consultez [propriété de clé étrangère](foreign-key-property.md).  
  
 Dans une application, une instance d'une association représente une association spécifique (par exemple une association entre une instance de Customer et des instances d'Order). Les instances d’association sont regroupées logiquement dans un [ensemble d’associations](association-set.md). Les ensembles d’associations (et les [jeux d’entités](entity-set.md)) sont regroupés logiquement dans un [conteneur d’entités](entity-container.md).  
  
## <a name="property"></a>Propriété  

 Les [types d’entités](entity-type.md) contiennent des [Propriétés](property.md) qui définissent leur structure et leurs caractéristiques. Par exemple, un type d'entité Customer peut avoir des propriétés telles que CustomerId, Name et Address.  
  
 Les propriétés dans un modèle conceptuel sont analogues à celles définies sur une classe dans un logiciel. De même que les propriétés sur une classe définissent la forme de la classe et acheminent des informations sur les objets, les propriétés dans un modèle conceptuel définissent la forme d'un type d'entité et acheminent des informations sur les instances de type d'entité.  
  
 Une propriété peut contenir des données de type primitif (comme une chaîne, un entier ou une valeur booléenne) ou des données structurées (comme un type complexe). Pour plus d’informations, consultez [Entity Data Model : types de données primitifs](entity-data-model-primitive-data-types.md).  
  
## <a name="representations-of-a-conceptual-model"></a>Représentations d'un modèle conceptuel  

 Un *modèle conceptuel* est une représentation spécifique de la structure de certaines données sous forme d’entités et de relations. Un diagramme est une façon de représenter un modèle conceptuel. Le diagramme suivant représente un modèle conceptuel avec trois types d'entité (`Book`, `Publisher` et `Author`) et deux associations (`PublishedBy` et `WrittenBy`) :  
  
 ![Diagramme montrant un modèle conceptuel avec trois types d’entité.](./media/entity-data-model-key-concepts/conceptual-model-entity-types-associations.gif)  
  
 Toutefois, cette représentation présente des défauts en matière de transmission de détails sur le modèle. Par exemple, les informations sur le type de propriété et le jeu d'entités ne sont pas représentées sur le diagramme. La richesse d’un modèle conceptuel peut être transmise plus clairement dans un langage spécifique à un domaine (DSL). Le [Entity Framework ADO.net](./ef/index.md) utilise un DSL basé sur XML appelé *Conceptual Schema Definition Language* ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels. Voici la définition CSDL du modèle conceptuel dans le diagramme ci-dessus :  
  
 [!code-xml[EDM_Example_Model#EDMExampleCSDL](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#edmexamplecsdl)]  
  
## <a name="see-also"></a>Voir aussi

- [Entity Data Model](entity-data-model.md)
