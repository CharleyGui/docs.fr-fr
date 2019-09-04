---
title: 'Procédure : Appeler des fonctions définies par modèle dans les requêtes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: 33f26896dd0d4ff08beb4a011fa6bd468cba7207
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250757"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>Procédure : Appeler des fonctions définies par modèle dans les requêtes
Cette rubrique explique comment appeler des fonctions définies dans le modèle conceptuel à partir d’LINQ to Entities requêtes.  
  
 La procédure ci-dessous fournit un plan de haut niveau pour l’appel d’une fonction définie par modèle à partir d’une requête de LINQ to Entities. L'exemple qui suit fournit plus de détails sur les étapes de la procédure. La procédure suppose que vous avez défini une fonction dans le modèle conceptuel. Pour plus d’informations, consultez [Guide pratique pour Définir des fonctions personnalisées dans le](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))modèle conceptuel.  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>Pour appeler une fonction définie dans le modèle conceptuel  
  
1. Ajoutez une méthode CLR (Common Language Runtime) à votre application qui se mappe à la fonction définie dans le modèle conceptuel. Pour mapper la méthode, vous devez lui appliquer un attribut <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Notez que les paramètres <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> et <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de l'attribut correspondent respectivement au nom de l'espace de noms du modèle conceptuel et au nom de la fonction du modèle conceptuel. La résolution des noms de fonctions pour LINQ respecte la casse.  
  
2. Appelez la fonction dans une requête LINQ to Entities.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment appeler une fonction définie dans le modèle conceptuel à partir d’une requête de LINQ to Entities. L'exemple utilise le modèle School. Pour plus d’informations sur le modèle School, consultez [création de l’exemple de base de données School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) et [génération du fichier School. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).  
  
 La fonction de modèle conceptuel suivante retourne le nombre d'années écoulées depuis l'embauche d'un formateur. Pour plus d’informations sur l’ajout de la fonction à un [modèle conceptuel, consultez Procédure : Définir des fonctions personnalisées dans le](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))modèle conceptuel.)  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a>Exemples  
 Ensuite, ajoutez la méthode suivante à votre application et utilisez un objet <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> pour la mapper à la fonction de modèle conceptuel :  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a>Exemple  
 Vous pouvez maintenant appeler la fonction de modèle conceptuel à partir d’une requête de LINQ to Entities. Le code suivant appelle la méthode pour afficher tous les formateurs embauchés il y a plus de dix ans :  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du fichier. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Requêtes dans LINQ to Entities](queries-in-linq-to-entities.md)
- [Appel de fonctions dans les requêtes LINQ to Entities](calling-functions-in-linq-to-entities-queries.md)
- [Guide pratique : Appeler des fonctions définies par modèle comme méthodes d’objet](how-to-call-model-defined-functions-as-object-methods.md)
