---
title: Appel de fonctions dans les requêtes LINQ to Entities
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 267bb393d9e75c66eb18139e8897da34bd86e159
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251262"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>Appel de fonctions dans les requêtes LINQ to Entities
Les rubriques de cette section expliquent comment appeler des fonctions dans les requêtes LINQ to Entities.  
  
 Les classes <xref:System.Data.Objects.EntityFunctions> et <xref:System.Data.Objects.SqlClient.SqlFunctions> donnent accès à des fonctions canoniques et de base de données dans le cadre d'Entity Framework. Pour plus d'informations, voir [Procédure : Appeler des fonctions](how-to-call-canonical-functions.md) canoniques et [Comment : Appeler des fonctions](how-to-call-database-functions.md)de base de données.  
  
 L'appel d'une fonction personnalisée passe par trois étapes de base obligatoires :  
  
1. Définissez une fonction dans votre modèle conceptuel ou déclarez-la dans votre modèle de stockage.  
  
2. Ajoutez une méthode à votre application et mappez-la à la fonction du modèle avec un objet <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  
  
3. Appelez la fonction dans une requête LINQ to Entities.  
  
 Pour plus d'informations, consultez les rubriques de cette section.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique : Appeler des fonctions canoniques](how-to-call-canonical-functions.md)  
  
 [Guide pratique pour Appeler des fonctions de base de données](how-to-call-database-functions.md)  
  
 [Guide pratique pour Appeler des fonctions de base de données personnalisées](how-to-call-custom-database-functions.md)  
  
 [Guide pratique pour Appeler des fonctions définies par modèle dans les requêtes](how-to-call-model-defined-functions-in-queries.md)  
  
 [Guide pratique pour Appeler des fonctions définies par modèle comme méthodes d’objet](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Voir aussi

- [Requêtes dans LINQ to Entities](queries-in-linq-to-entities.md)
- [Fonctions canoniques](canonical-functions.md)
- [Vue d’ensemble du fichier. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Guide pratique pour Définir des fonctions personnalisées dans le modèle conceptuel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))
