---
title: 'Procédure : Implémenter CopyToDataTable<T> quand le type générique T n’est pas un DataRow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 776ff6062282d12b622ec89cfa9990513da64a07
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194594"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="f8914-102">Procédure : Implémenter CopyToDataTable\<T> quand le type générique T n’est pas un DataRow</span><span class="sxs-lookup"><span data-stu-id="f8914-102">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>

<span data-ttu-id="f8914-103">L'objet <xref:System.Data.DataTable> est souvent utilisé pour la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="f8914-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="f8914-104">La méthode <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> prend les résultats d'une requête et copie les données dans un objet <xref:System.Data.DataTable> qui peut ensuite être utilisé pour la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="f8914-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="f8914-105">Toutefois, les méthodes <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> ne fonctionneront que sur une source <xref:System.Collections.Generic.IEnumerable%601> où le paramètre générique `T` est de type <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="f8914-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="f8914-106">Bien qu'utile, cela ne permet pas de créer des tables à partir d'une séquence de types scalaires, de requêtes qui projettent des types anonymes ou de requêtes qui effectuent des jointures de tables.</span><span class="sxs-lookup"><span data-stu-id="f8914-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="f8914-107">Cette rubrique décrit comment implémenter deux classes d’extension `CopyToDataTable<T>` personnalisées qui acceptent un paramètre générique `T` d’un type autre que <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="f8914-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="f8914-108">La logique pour créer un objet <xref:System.Data.DataTable> à partir d'une source <xref:System.Collections.Generic.IEnumerable%601> est contenue dans la classe `ObjectShredder<T>`, laquelle est ensuite encapsulée dans deux méthodes d'extension `CopyToDataTable<T>` surchargées.</span><span class="sxs-lookup"><span data-stu-id="f8914-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="f8914-109">La méthode `Shred` de la classe `ObjectShredder<T>` retourne les objets <xref:System.Data.DataTable> remplis et accepte trois paramètres d'entrée : une source <xref:System.Collections.Generic.IEnumerable%601>, un objet <xref:System.Data.DataTable> et une énumération <xref:System.Data.LoadOption>.</span><span class="sxs-lookup"><span data-stu-id="f8914-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="f8914-110">Le schéma initial de l'objet <xref:System.Data.DataTable> retourné est basé sur le schéma du type `T`.</span><span class="sxs-lookup"><span data-stu-id="f8914-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="f8914-111">Si une table existante est fournie comme paramètre d'entrée, le schéma doit être cohérent avec le schéma du type `T`.</span><span class="sxs-lookup"><span data-stu-id="f8914-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="f8914-112">Chaque propriété publique et champ public du type `T` est converti en objet <xref:System.Data.DataColumn> dans la table retournée.</span><span class="sxs-lookup"><span data-stu-id="f8914-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="f8914-113">Si la séquence source contient un type dérivé de `T`, le schéma de table retourné est développé pour toute propriété publique ou tout champ public supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="f8914-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="f8914-114">Pour des exemples d’utilisation des méthodes `CopyToDataTable<T>` personnalisées, consultez [Création d’un DataTable à partir d’une requête](creating-a-datatable-from-a-query-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="f8914-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="f8914-115">Pour implémenter les méthodes CopyToDataTable personnalisées \<T> dans votre application</span><span class="sxs-lookup"><span data-stu-id="f8914-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1. <span data-ttu-id="f8914-116">Implémentez la classe `ObjectShredder<T>` pour créer un objet <xref:System.Data.DataTable> à partir d'une source <xref:System.Collections.Generic.IEnumerable%601> :</span><span class="sxs-lookup"><span data-stu-id="f8914-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="f8914-117">L’exemple précédent suppose que les propriétés et les champs de `DataColumn` ne sont pas des types valeur Nullable.</span><span class="sxs-lookup"><span data-stu-id="f8914-117">The preceding example assumes that the properties and fields of the `DataColumn` are not nullable value types.</span></span> <span data-ttu-id="f8914-118">Pour gérer les propriétés et les champs avec des types valeur Nullable, utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f8914-118">To handle properties and fields with nullable value types, use the following code:</span></span>

    ```csharp
    // Nullable-aware code for properties.
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);

    // Nullable-aware code for fields.
    DataColumn dc = table.Columns.Contains(f.Name) ? table.Columns[f.Name] : table.Columns.Add(f.Name, Nullable.GetUnderlyingType(f.FieldType) ?? f.FieldType);
    ```

2. <span data-ttu-id="f8914-119">Implémentez les méthodes d’extension `CopyToDataTable<T>` personnalisées dans une classe :</span><span class="sxs-lookup"><span data-stu-id="f8914-119">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. <span data-ttu-id="f8914-120">Ajoutez la classe `ObjectShredder<T>` et les méthodes d’extension `CopyToDataTable<T>` à votre application.</span><span class="sxs-lookup"><span data-stu-id="f8914-120">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        ' Your application code using CopyToDataTable<T>.  
    End Sub  
End Module  
  
Public Module CustomLINQtoDataSetMethods  
…  
End Module  
  
Public Class ObjectShredder(Of T)  
…  
End Class
```
  
```csharp
class Program  
{  
    static void Main(string[] args)  
    {  
        // Your application code using CopyToDataTable<T>.  
    }  
}  
public static class CustomLINQtoDataSetMethods  
{  
…  
}  
public class ObjectShredder<T>  
{  
…  
}  
```
  
## <a name="see-also"></a><span data-ttu-id="f8914-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8914-121">See also</span></span>

- [<span data-ttu-id="f8914-122">Création d’un DataTable à partir d’une requête</span><span class="sxs-lookup"><span data-stu-id="f8914-122">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [<span data-ttu-id="f8914-123">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="f8914-123">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)
