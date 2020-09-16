---
title: Fonctions définies par l'utilisateur (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: ab18c3ec785ca3bba9f8b67fbb82fb4bb8244f4f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540652"
---
# <a name="user-defined-functions-entity-sql"></a>Fonctions définies par l'utilisateur (Entity SQL)
Entity SQL prend en charge l'appel de fonctions définies par l'utilisateur dans une requête. Vous pouvez définir ces fonctions inline avec la requête (consultez [Comment : appeler une fonction définie par l’utilisateur](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) ou dans le cadre du modèle conceptuel (consultez Guide pratique [pour définir des fonctions personnalisées dans le modèle conceptuel](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))). Les fonctions de modèle conceptuel sont définies en tant que Entity SQL commande dans l’élément [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) d’un élément de [fonction](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) dans le modèle conceptuel.  
  
 Entity SQL permet de définir des fonctions dans la commande de requête elle-même. L’opérateur de [fonction](function-entity-sql.md) définit des fonctions inline. Vous pouvez définir plusieurs fonctions dans une même commande et ces fonctions peuvent avoir le même nom de fonction, tant que les signatures des fonctions sont uniques. Pour plus d'informations, consultez [Function Overload Resolution](function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions](functions-entity-sql.md)
