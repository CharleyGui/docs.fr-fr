---
title: 'Entity Data Model : Espaces de noms'
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: 1e5f9527ec208c5650c68fe35bb758e0850b7700
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194828"
---
# <a name="entity-data-model-namespaces"></a>Entity Data Model : Espaces de noms

Un espace de noms dans le modèle EDM (Entity Data Model) est un conteneur abstrait pour les [types d’entité](entity-type.md), les [types complexes](complex-type.md)et les [associations](association-type.md). Les espaces de noms dans le modèle EDM sont semblables aux espaces de noms dans un langage de programmation : ils fournissent le contexte pour les objets qu'ils contiennent et offrent un moyen de lever l'ambiguïté entre les objets qui portent le même nom (mais qui sont contenus dans des espaces de noms différents).  
  
## <a name="example"></a>Exemple  

 Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels. Le CSDL suivant utilise un espace de noms pour identifier un type défini dans un modèle conceptuel différent. L'exemple définit un type d'entité (`Publisher`) qui a une propriété de type complexe (`Address`) importée à partir de l'espace de noms `ExtendedBooksModel`. Notez que l'élément `Using` indique qu'un espace de noms a été importé. Notez également que le type de la propriété `Address` est défini à l'aide de son nom qualifié complet (`ExtendedBooksModel.Address`), ce qui indique que ce type est défini dans l'espace de noms `ExtendedBooksModel`.  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts clés d'Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
