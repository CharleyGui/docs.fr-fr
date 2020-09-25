---
title: "Comment : appeler des fonctions définies par modèle comme méthodes d'objet"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
ms.openlocfilehash: 5e5ae2fd838a34d7f665b23a14db2a599367e801
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197792"
---
# <a name="how-to-call-model-defined-functions-as-object-methods"></a>Comment : appeler des fonctions définies par modèle comme méthodes d'objet

Cette rubrique décrit comment appeler une fonction définie par modèle comme une méthode sur un objet <xref:System.Data.Objects.ObjectContext> ou comme une méthode statique sur une classe personnalisée. Une *fonction définie par modèle* est une fonction définie dans le modèle conceptuel. Les procédures décrites dans cette rubrique montrent comment appeler directement ces fonctions au lieu de les appeler à partir de requêtes LINQ to Entities. Pour plus d’informations sur l’appel des fonctions définies par modèle dans les requêtes LINQ to Entities, consultez [Comment : appeler des fonctions définies par modèle dans des requêtes](how-to-call-model-defined-functions-in-queries.md).  
  
 Si vous appelez une fonction définie par modèle comme une méthode <xref:System.Data.Objects.ObjectContext> ou comme une méthode statique sur une classe personnalisée, vous devez mapper en premier la méthode à la fonction définie par modèle avec un attribut <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Toutefois, lorsque vous définissez une méthode sur la classe <xref:System.Data.Objects.ObjectContext>, vous devez utiliser la propriété <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> pour exposer le fournisseur LINQ, alors que lorsque vous définissez une méthode statique sur une classe personnalisée, vous devez utiliser la propriété <xref:System.Linq.IQueryable.Provider%2A> pour exposer le fournisseur LINQ. Pour plus d'informations, consultez les exemples qui suivent les procédures ci-dessous.  
  
 Les procédures suivantes fournissent une présentation de haut niveau pour l'appel d'une fonction définie par modèle comme une méthode sur un objet <xref:System.Data.Objects.ObjectContext> et comme une méthode statique sur une classe personnalisée. Les exemples qui suivent fournissent plus de détail sur les étapes des procédures. Les procédures supposent que vous avez défini une fonction dans le modèle conceptuel. Pour plus d’informations, consultez [Comment : définir des fonctions personnalisées dans le modèle conceptuel](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).  
  
### <a name="to-call-a-model-defined-function-as-a-method-on-an-objectcontext-object"></a>Pour appeler une fonction définie par modèle comme une méthode sur un objet ObjectContext  
  
1. Ajoutez un fichier source pour étendre la classe partielle dérivée de la classe <xref:System.Data.Objects.ObjectContext>, générée automatiquement par les outils Entity Framework. La définition du stub de CLR dans un fichier source distinct empêche la perte des modifications lorsque le fichier est régénéré.  
  
2. Ajoutez une méthode CLR (Common Language Runtime) à votre classe <xref:System.Data.Objects.ObjectContext> qui effectue les opérations suivantes :  
  
    - Elle est mappée à la fonction définie dans le modèle conceptuel. Pour mapper la méthode, vous devez lui appliquer un attribut <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Notez que les paramètres <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> et <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de l'attribut correspondent au nom de l'espace de noms du modèle conceptuel et au nom de la fonction dans le modèle conceptuel, respectivement. La résolution des noms de fonctions pour LINQ respecte la casse.  
  
    - Elle retourne les résultats de la méthode <xref:System.Linq.IQueryProvider.Execute%2A> retournée par la propriété <xref:System.Data.Objects.ObjectContext.QueryProvider%2A>.  
  
3. Appelez la méthode en tant que membre sur une instance de la classe <xref:System.Data.Objects.ObjectContext>.  
  
### <a name="to-call-a-model-defined-function-as-static-method-on-a-custom-class"></a>Pour appeler une fonction définie par modèle comme une méthode statique sur une classe personnalisée  
  
1. Ajoutez une classe à votre application avec une méthode statique qui effectue les opérations suivantes :  
  
    - Elle est mappée à la fonction définie dans le modèle conceptuel. Pour mapper la méthode, vous devez lui appliquer un attribut <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Notez que les paramètres <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> et <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de l'attribut correspondent au nom de l'espace de noms du modèle conceptuel et au nom de la fonction dans le modèle conceptuel, respectivement.  
  
    - Elle accepte un argument <xref:System.Linq.IQueryable>.  
  
    - Elle retourne les résultats de la méthode <xref:System.Linq.IQueryProvider.Execute%2A> retournée par la propriété <xref:System.Linq.IQueryable.Provider%2A>.  
  
2. Appelez la méthode comme méthode statique sur la classe personnalisée.  
  
## <a name="example"></a>Exemple  

 **Appel d'une fonction définie par modèle comme une méthode sur un objet ObjectContext**  
  
 L'exemple suivant montre comment appeler une fonction définie par modèle comme une méthode sur un objet <xref:System.Data.Objects.ObjectContext>. L’exemple utilise le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).  
  
 Considérez la fonction de modèle conceptuel ci-dessous qui retourne le revenu généré par un produit donné. (Pour plus d’informations sur l’ajout de la fonction à votre modèle conceptuel, consultez [Comment : définir des fonctions personnalisées dans le modèle conceptuel](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  

## <a name="example"></a>Exemple  

 Le code suivant ajoute une méthode à la classe `AdventureWorksEntities` qui est mappée à la fonction de modèle conceptuel ci-dessus.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## <a name="example"></a>Exemple  

 Le code suivant appelle la méthode ci-dessus pour afficher le revenu généré par un produit donné :  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment appeler une fonction définie par modèle qui retourne une collection (en tant qu’objet <xref:System.Linq.IQueryable%601>). Considérez la fonction de modèle conceptuel ci-dessous qui retourne tous les détails `SalesOrderDetails` pour un ID de produit donné.  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## <a name="example"></a>Exemple  

 Le code suivant ajoute une méthode à la classe `AdventureWorksEntities` qui est mappée à la fonction de modèle conceptuel ci-dessus.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## <a name="example"></a>Exemple  

 Le code suivant appelle la méthode. Notez que la requête <xref:System.Linq.IQueryable%601> retournée est encore affinée pour retourner les totaux de ligne pour chaque `SalesOrderDetail`.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## <a name="example"></a>Exemple  

 **Appel d'une fonction définie par modèle comme une méthode statique sur une classe personnalisée**  
  
 L'exemple suivant montre comment appeler une fonction définie par modèle comme une méthode statique sur une classe personnalisée. L’exemple utilise le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).  
  
> [!NOTE]
> Lorsque vous appelez une fonction définie par modèle comme une méthode statique sur une classe personnalisée, la fonction définie par modèle doit accepter une collection et retourner une agrégation de valeurs dans la collection.  
  
 Considérez la fonction de modèle conceptuel ci-dessous, qui retourne le revenu produit pour une collection SalesOrderDetail. (Pour plus d’informations sur l’ajout de la fonction à votre modèle conceptuel, consultez [Comment : définir des fonctions personnalisées dans le modèle conceptuel](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]
  
## <a name="example"></a>Exemple  

 Le code suivant ajoute une classe à votre application qui contient une méthode statique mappée à la fonction de modèle conceptuel ci-dessus.  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## <a name="example"></a>Exemple  

 Le code suivant appelle la méthode ci-dessus pour afficher le revenu produit pour une collection SalesOrderDetail :  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Présentation d'un fichier .edmx](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Requêtes dans LINQ to Entities](queries-in-linq-to-entities.md)
- [Appel de fonctions dans les requêtes LINQ to Entities](calling-functions-in-linq-to-entities-queries.md)
