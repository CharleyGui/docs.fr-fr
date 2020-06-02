---
title: Appel de fonctions dans les requêtes LINQ to Entities
description: Utilisez ces articles pour voir comment les classes EntityFunctions et SqlFunctions fournissent l’accès aux fonctions canoniques et de base de données dans le cadre de la Entity Framework.
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: faa6406713592f10e5e7371cd73f29bec4b03b7b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286855"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>Appel de fonctions dans les requêtes LINQ to Entities
Les rubriques de cette section expliquent comment appeler des fonctions dans les requêtes LINQ to Entities.  
  
 Les classes <xref:System.Data.Objects.EntityFunctions> et <xref:System.Data.Objects.SqlClient.SqlFunctions> donnent accès à des fonctions canoniques et de base de données dans le cadre d'Entity Framework. Pour plus d’informations, consultez [Comment : appeler des fonctions canoniques](how-to-call-canonical-functions.md) et [Comment : appeler des fonctions de base de données](how-to-call-database-functions.md).  
  
 L'appel d'une fonction personnalisée passe par trois étapes de base obligatoires :  
  
1. Définissez une fonction dans votre modèle conceptuel ou déclarez-la dans votre modèle de stockage.  
  
2. Ajoutez une méthode à votre application et mappez-la à la fonction du modèle avec un objet <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  
  
3. Appelez la fonction dans une requête LINQ to Entities.  
  
 Pour plus d'informations, consultez les rubriques de cette section.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Comment : appeler des fonctions de chaînes canoniques](how-to-call-canonical-functions.md)  
  
 [Comment : appeler des fonctions de base de données](how-to-call-database-functions.md)  
  
 [Comment : appeler des fonctions de base de données personnalisées](how-to-call-custom-database-functions.md)  
  
 [Comment : appeler des fonctions définies par modèle dans les requêtes](how-to-call-model-defined-functions-in-queries.md)  
  
 [Comment : appeler des fonctions définies par modèle comme méthodes d'objet](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Voir aussi

- [Requêtes dans LINQ to Entities](queries-in-linq-to-entities.md)
- [Fonctions canoniques](canonical-functions.md)
- [Présentation d'un fichier .edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Procédure : définir des fonctions personnalisées dans le modèle conceptuel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))
