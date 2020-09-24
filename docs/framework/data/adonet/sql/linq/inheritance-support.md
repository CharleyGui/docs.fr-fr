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
# <a name="inheritance-support"></a><span data-ttu-id="b05f3-102">Prise en charge de l'héritage</span><span class="sxs-lookup"><span data-stu-id="b05f3-102">Inheritance Support</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b05f3-103">prend en charge *le mappage de table unique*.</span><span class="sxs-lookup"><span data-stu-id="b05f3-103">supports *single-table mapping*.</span></span> <span data-ttu-id="b05f3-104">En d'autres termes, une hiérarchie d'héritage complète est stockée dans une seule table de base de données.</span><span class="sxs-lookup"><span data-stu-id="b05f3-104">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="b05f3-105">La table contient l'union au format à plat de toutes les colonnes de données possibles pour l'ensemble de la hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="b05f3-105">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="b05f3-106">(Une Union est le résultat de la combinaison de deux tables en une table qui contient les lignes qui étaient présentes dans l’une des tables d’origine.) Chaque ligne a des valeurs NULL dans les colonnes qui ne s’appliquent pas au type de l’instance représentée par la ligne.</span><span class="sxs-lookup"><span data-stu-id="b05f3-106">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="b05f3-107">La stratégie de mappage de table unique est la représentation la plus simple de l'héritage. Elle fournit des caractéristiques de performances satisfaisantes pour de nombreuses catégories de requêtes.</span><span class="sxs-lookup"><span data-stu-id="b05f3-107">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="b05f3-108">Pour implémenter ce mappage dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], vous devez spécifier les attributs et les propriétés d'attribut sur la classe racine de la hiérarchie d'héritage.</span><span class="sxs-lookup"><span data-stu-id="b05f3-108">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="b05f3-109">Pour plus d’informations, consultez [Comment : mapper des hiérarchies d’héritage](how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="b05f3-109">For more information, see [How to: Map Inheritance Hierarchies](how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="b05f3-110">Les développeurs qui utilisent Visual Studio peuvent également utiliser le Concepteur Objet Relationnel pour mapper des hiérarchies d’héritage.</span><span class="sxs-lookup"><span data-stu-id="b05f3-110">Developers using Visual Studio can also use the Object Relational Designer to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b05f3-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b05f3-111">See also</span></span>

- [<span data-ttu-id="b05f3-112">Informations générales</span><span class="sxs-lookup"><span data-stu-id="b05f3-112">Background Information</span></span>](background-information.md)
