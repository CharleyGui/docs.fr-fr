---
title: 'Procédure : Appeler des fonctions définies par modèle dans les requêtes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: 32cdb5b0f27817856ab586eb38f89df63c1c4d3b
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539856"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a>Procédure : Appeler des fonctions définies par modèle dans les requêtes
Cette rubrique décrit comment appeler des fonctions qui sont définies dans le modèle conceptuel à partir de LINQ aux requêtes d’entités.  
  
 La procédure ci-dessous fournit un plan de haut niveau pour appeler une fonction définie par modèle à partir de dans LINQ pour interroger des entités. L'exemple qui suit fournit plus de détails sur les étapes de la procédure. La procédure suppose que vous avez défini une fonction dans le modèle conceptuel. Pour plus d'informations, voir [Procédure : Définir des fonctions personnalisées dans le modèle conceptuel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a>Pour appeler une fonction définie dans le modèle conceptuel  
  
1. Ajoutez une méthode CLR (Common Language Runtime) à votre application qui se mappe à la fonction définie dans le modèle conceptuel. Pour mapper la méthode, vous devez lui appliquer un attribut <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Notez que les paramètres <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> et <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de l'attribut correspondent respectivement au nom de l'espace de noms du modèle conceptuel et au nom de la fonction du modèle conceptuel. La résolution des noms de fonctions pour LINQ respecte la casse.  
  
2. Appelez la fonction dans une requête LINQ to Entities.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment appeler une fonction qui est définie dans le modèle conceptuel à partir de LINQ pour interroger des entités. L'exemple utilise le modèle School. Pour plus d’informations sur le modèle School, consultez [création de la base de données School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) et [générant le fichier de School .edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).  
  
 La fonction de modèle conceptuel suivante retourne le nombre d'années écoulées depuis l'embauche d'un formateur. Pour plus d’informations sur l’ajout de la fonction à un modèle conceptuel, consultez [Comment : Définir des fonctions personnalisées dans le modèle conceptuel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a>Exemple  
 Ensuite, ajoutez la méthode suivante à votre application et utilisez un objet <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> pour la mapper à la fonction de modèle conceptuel :  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a>Exemple  
 Vous pouvez maintenant appeler la fonction de modèle conceptuel à partir dans LINQ pour interroger des entités. Le code suivant appelle la méthode pour afficher tous les formateurs embauchés il y a plus de dix ans :  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [vue d’ensemble du fichier .edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Requêtes dans LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [Appel de fonctions dans les requêtes LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [Guide pratique pour Appeler des fonctions définies par modèle comme méthodes d’objet](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
