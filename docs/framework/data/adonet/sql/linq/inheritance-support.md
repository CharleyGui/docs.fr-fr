---
title: Prise en charge de l'héritage
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 7673e69458d5c1af854747c43ba463332a9cd588
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158251"
---
# <a name="inheritance-support"></a>Prise en charge de l'héritage

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge *le mappage de table unique*. En d'autres termes, une hiérarchie d'héritage complète est stockée dans une seule table de base de données. La table contient l'union au format à plat de toutes les colonnes de données possibles pour l'ensemble de la hiérarchie. (Une Union est le résultat de la combinaison de deux tables en une table qui contient les lignes qui étaient présentes dans l’une des tables d’origine.) Chaque ligne a des valeurs NULL dans les colonnes qui ne s’appliquent pas au type de l’instance représentée par la ligne.  
  
 La stratégie de mappage de table unique est la représentation la plus simple de l'héritage. Elle fournit des caractéristiques de performances satisfaisantes pour de nombreuses catégories de requêtes.  
  
 Pour implémenter ce mappage dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], vous devez spécifier les attributs et les propriétés d'attribut sur la classe racine de la hiérarchie d'héritage. Pour plus d’informations, consultez [Comment : mapper des hiérarchies d’héritage](how-to-map-inheritance-hierarchies.md).  
  
 Les développeurs qui utilisent Visual Studio peuvent également utiliser le Concepteur Objet Relationnel pour mapper des hiérarchies d’héritage.  
  
## <a name="see-also"></a>Voir aussi

- [Informations générales](background-information.md)
