---
title: fonction définie par modèle
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 973d7ff9f7b76650782d62dcdcab60c8cedde18f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735578"
---
# <a name="model-defined-function"></a>fonction définie par modèle
Une *fonction définie par modèle* est une fonction définie dans un modèle conceptuel. Le corps d’une fonction définie par modèle est exprimé en [Entity SQL](./ef/language-reference/entity-sql-language.md), ce qui permet d’exprimer la fonction indépendamment des règles ou des langages pris en charge dans la source de données.  
  
 Une définition pour une fonction définie par modèle contient les informations suivantes :  
  
- Nom de la fonction. (Requis)  
  
- Type de la valeur de retour. (Facultatif)  
  
    > [!NOTE]
    > Si aucun type de retour n’est spécifié, la valeur de retour est void.  
  
- Informations sur les paramètres. (Facultatif)  
  
- Expression [Entity SQL](./ef/language-reference/entity-sql-language.md) qui définit le corps de la fonction.  
  
 Notez que les fonctions définies par modèle ne prennent pas en charge les paramètres de sortie. Cette restriction est en place de manière à ce que des fonctions définies par modèle puissent être composées.  
  
## <a name="example"></a>Exemple  
 Le diagramme suivant montre un modèle conceptuel avec trois types d'entités : `Book`, `Publisher` et `Author`.  
  
 ![Capture d’écran montrant un modèle avec la date de publication.](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels. Le CSDL suivant définit une fonction dans le modèle conceptuel qui retourne le nombre d'années écoulées depuis la publication d'une instance de `Book` (dans le diagramme ci-dessus).  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts clés d’Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
- [Entity Data Model : types de données primitifs](entity-data-model-primitive-data-types.md)
