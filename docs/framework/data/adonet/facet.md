---
title: facet
ms.date: 03/30/2017
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
ms.openlocfilehash: b9ef2276f988923fe83cefce910e8c3685cb9da9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156444"
---
# <a name="facet"></a>facet

Une *facette* est utilisée pour ajouter des détails à une définition de propriété de type primitif. Une définition de [propriété](property.md) contient des informations sur le type de propriété, mais elle est souvent plus détaillée. Par exemple, un type d'entité dans un modèle conceptuel peut avoir une propriété de type `String` dont la valeur ne peut pas être null. Les facettes vous permettent de spécifier ce niveau de détail.  
  
 Le tableau suivant décrit les facettes prises en charge dans le modèle EDM.  
  
> [!NOTE]
> Les valeurs et comportements exacts des facettes sont déterminés par l'environnement d'exécution qui utilise une implémentation EDM.  
  
|Facette|Description|S’applique à|  
|-----------|-----------------|----------------|  
|`Collation`|Spécifie la table de classement ou ordre de tri à utiliser lors de l'exécution d'opérations de comparaison et de tri sur des valeurs de la propriété.|`String`|  
|`ConcurrencyMode`|Indique que la valeur de la propriété doit être utilisée pour des contrôles d'accès concurrentiel optimiste.|Toutes les propriétés de type primitif|  
|`Default`|Spécifie la valeur par défaut de la propriété si aucune valeur n'est fournie en cas d'instanciation.|Toutes les propriétés de type primitif|  
|`FixedLength`|Spécifie si la longueur de la valeur de propriété peut varier.|`Binary`, `String`|  
|`MaxLength`|Spécifie la longueur maximale de la valeur de propriété.|`Binary`, `String`|  
|`Nullable`|Spécifie si la propriété peut avoir une valeur null.|Toutes les propriétés de type primitif|  
|`Precision`|Pour les propriétés de type `Decimal`, spécifie le nombre de chiffres qu'une valeur de propriété peut avoir. Pour les propriétés de type `Time`, `DateTime` et `DateTimeOffset`, spécifie le nombre de chiffres de la partie fractionnaire des secondes de la valeur de propriété.|`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,|  
|`Scale`|Spécifie le nombre de chiffres à droite de la virgule décimale pour la valeur de propriété.|Decimal|  
|`Unicode`|Indique si la valeur de propriété est stockée au format Unicode.|`String`|  
  
## <a name="example"></a>Exemple  

 Le [Entity Framework ADO.net](./ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) pour définir des modèles conceptuels. Le CSDL suivant définit un type d'entité `Book`. Notez que les facettes sont implémentées en tant qu'attributs XML. Les valeurs de facette indiquent qu'aucune propriété ne peut avoir la valeur null, et que les facettes `Scale` et `Precision` de la propriété `Revision` ont la valeur 29.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts clés d'Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
