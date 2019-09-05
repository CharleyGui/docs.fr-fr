---
title: Fonctions définies par l'utilisateur (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 9ddafb18a10ff2313fd27eab453907054a35218a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248769"
---
# <a name="user-defined-functions-entity-sql"></a>Fonctions définies par l'utilisateur (Entity SQL)
Entity SQL prend en charge l'appel de fonctions définies par l'utilisateur dans une requête. Vous pouvez définir ces fonctions en ligne avec la requête (consultez [procédure : Appeler une fonction](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))définie par l’utilisateur) ou dans le cadre du modèle conceptuel ( [consultez Procédure : Définir des fonctions personnalisées dans le](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))modèle conceptuel). Les fonctions de modèle conceptuel sont définies en tant que Entity SQL commande dans l’élément [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) d’un élément de [fonction](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) dans le modèle conceptuel.  
  
 Entity SQL permet de définir des fonctions dans la commande de requête elle-même. L’opérateur de [fonction](function-entity-sql.md) définit des fonctions inline. Vous pouvez définir plusieurs fonctions dans une même commande et ces fonctions peuvent avoir le même nom de fonction, tant que les signatures des fonctions sont uniques. Pour plus d'informations, consultez [Function Overload Resolution](function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions](functions-entity-sql.md)
