---
title: fonction déclarée par modèle
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: 73e716f1c42dfbbb91dc6456212de2a331d7c4ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943924"
---
# <a name="model-declared-function"></a>fonction déclarée par modèle
Une *fonction déclarée par modèle* est une fonction qui est déclarée dans un modèle conceptuel, mais qui n’est pas définie dans ce modèle conceptuel. La fonction peut être définie dans l'environnement d'hébergement ou de stockage. Par exemple, une fonction déclarée par modèle peut être mappée à une fonction définie dans une base de données, exposant ainsi les fonctionnalités côté serveur dans le modèle conceptuel.  
  
 La déclaration d'une fonction déclarée par modèle contient les informations suivantes :  
  
- Nom de la fonction. (Requis)  
  
- Type de la valeur de retour. (facultatif)  
  
    > [!NOTE]
    > Si aucune valeur de retour n'est spécifiée, le type de retour est void.  
  
- Informations sur les paramètres, notamment le nom et le type des paramètres. (facultatif)  
  
## <a name="example"></a>Exemple  
 Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels. En CSDL, une implémentation d’une fonction déclarée par modèle est une importation de fonction (à l’aide de l' [élément FunctionImport](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)). Le CSDL suivant définit un conteneur d'entités avec une définition d'importation de fonction. Notez que le type de retour pour la fonction est void, car aucun type de retour n'est spécifié.  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts clés d’Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
