---
title: 'Comment : appeler des fonctions de base de données personnalisées'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: 9879803c970b7965bf152c216367b216e201af38
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540306"
---
# <a name="how-to-call-custom-database-functions"></a>Comment : appeler des fonctions de base de données personnalisées

Cette rubrique décrit comment appeler des fonctions personnalisées définies dans la base de données dans des requêtes LINQ to Entities.

Les fonctions de base de données qui sont appelées à partir de requêtes LINQ to Entities sont exécutées dans la base de données. L'exécution de fonctions dans la base de données peut améliorer les performances de l'application.

La procédure ci-dessous fournit un plan de haut niveau pour l'appel d'une fonction de base de données personnalisée. L'exemple qui suit fournit plus de détails sur les étapes de la procédure.

## <a name="to-call-custom-functions-that-are-defined-in-the-database"></a>Pour appeler des fonctions personnalisées définies dans la base de données

1. Créez une fonction personnalisée dans votre base de données.

     Pour plus d’informations sur la création de fonctions personnalisées dans SQL Server, consultez [CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql).

2. Déclarez une fonction dans la partie SSDL (Store Schema Definition Language) de votre fichier .edmx. Le nom de la fonction doit être le même que le nom de la fonction déclarée dans la base de données.

     Pour plus d’informations, consultez [Function, élément (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).

3. Ajoutez une méthode correspondante à une classe dans votre code d'application et appliquez un attribut <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> à la méthode. Notez que les paramètres <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> et <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de l'attribut sont respectivement le nom de l'espace de noms du modèle conceptuel et le nom de la fonction dans le modèle conceptuel. La résolution des noms de fonctions pour LINQ respecte la casse.

4. Appelez la méthode dans une requête LINQ to Entities.  

## <a name="example"></a> Exemple

L'exemple suivant montre comment appeler une fonction de base de données personnalisée dans une requête LINQ to Entities. L'exemple utilise le modèle School. Pour plus d’informations sur le modèle School, consultez [création de l’exemple de base de données School](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) et [génération du fichier School. edmx](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).

Le code suivant ajoute la fonction `AvgStudentGrade` à l'exemple de base de données School.

> [!NOTE]
> La procédure d'appel d'une fonction de base de données personnalisée est la même indépendamment du serveur de base de données. Toutefois, le code ci-dessous est spécifique à la création d'une fonction dans une base de données SQL Server. Le code pour la création d'une fonction personnalisée sur d'autres serveurs de bases de données peut différer.

[!code-sql[DP L2E MapToDBFunction#1](~/samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]

## <a name="example"></a> Exemple

Ensuite, déclarez une fonction dans le Store Schema Definition Language (SSDL) de votre fichier *. edmx* . Le code suivant déclare la `AvgStudentGrade` fonction en SSDL :

[!code-xml[DP L2E MapToDBFunction#2](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]

## <a name="example"></a> Exemple

À présent, créez une méthode et mappez-la à la fonction déclarée dans le langage SSDL. La méthode dans la classe suivante est mappée à la fonction définie dans le langage SSDL (ci-dessus) à l'aide d'un attribut <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Lorsque cette méthode est appelée, la fonction correspondante dans la base de données est exécutée.

[!code-csharp[DP L2E MapToDBFunction#3](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
[!code-vb[DP L2E MapToDBFunction#3](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]

## <a name="example"></a> Exemple

Enfin, appelez la méthode dans une requête LINQ to Entities. Le code suivant affiche le nom des étudiants et la moyenne des notes sur la console :

[!code-csharp[DP L2E MapToDBFunction#4](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
[!code-vb[DP L2E MapToDBFunction#4](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]

## <a name="see-also"></a>Voir aussi

- [Présentation d'un fichier .edmx](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Requêtes dans LINQ to Entities](queries-in-linq-to-entities.md)
