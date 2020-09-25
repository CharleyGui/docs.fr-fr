---
title: Fonctions définies par l'utilisateur (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 9e5ad1f6edb0e719733edd2518c5d62a7fc6bdf7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180970"
---
# <a name="user-defined-functions-entity-sql"></a>Fonctions définies par l'utilisateur (Entity SQL)

Entity SQL prend en charge l'appel de fonctions définies par l'utilisateur dans une requête. Vous pouvez définir ces fonctions inline avec la requête (consultez [Comment : appeler une fonction définie par l’utilisateur](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) ou dans le cadre du modèle conceptuel (consultez Guide pratique [pour définir des fonctions personnalisées dans le modèle conceptuel](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))). Les fonctions de modèle conceptuel sont définies en tant que Entity SQL commande dans l’élément [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) d’un élément de [fonction](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) dans le modèle conceptuel.  
  
 Entity SQL permet de définir des fonctions dans la commande de requête elle-même. L’opérateur de [fonction](function-entity-sql.md) définit des fonctions inline. Vous pouvez définir plusieurs fonctions dans une même commande et ces fonctions peuvent avoir le même nom de fonction, tant que les signatures des fonctions sont uniques. Pour plus d'informations, consultez [Function Overload Resolution](function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions](functions-entity-sql.md)
