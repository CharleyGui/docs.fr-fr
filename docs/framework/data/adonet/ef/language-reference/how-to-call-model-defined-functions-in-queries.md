---
title: 'Comment : appeler des fonctions définies par modèle dans les requêtes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: b142ef820e964eaf5f1afed53a6b12a9344c7dda
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189329"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a><span data-ttu-id="22e47-102">Comment : appeler des fonctions définies par modèle dans les requêtes</span><span class="sxs-lookup"><span data-stu-id="22e47-102">How to: Call Model-Defined Functions in Queries</span></span>

<span data-ttu-id="22e47-103">Cette rubrique explique comment appeler des fonctions définies dans le modèle conceptuel à partir d’LINQ to Entities requêtes.</span><span class="sxs-lookup"><span data-stu-id="22e47-103">This topic describes how to call functions that are defined in the conceptual model from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="22e47-104">La procédure ci-dessous fournit un plan de haut niveau pour l’appel d’une fonction définie par modèle à partir d’une requête de LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="22e47-104">The procedure below provides a high-level outline for calling a model-defined function from within a LINQ to Entities query.</span></span> <span data-ttu-id="22e47-105">L'exemple qui suit fournit plus de détails sur les étapes de la procédure.</span><span class="sxs-lookup"><span data-stu-id="22e47-105">The example that follows provides more detail about the steps in the procedure.</span></span> <span data-ttu-id="22e47-106">La procédure suppose que vous avez défini une fonction dans le modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="22e47-106">The procedure assumes that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="22e47-107">Pour plus d’informations, consultez [Comment : définir des fonctions personnalisées dans le modèle conceptuel](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="22e47-107">For more information, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span></span>  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a><span data-ttu-id="22e47-108">Pour appeler une fonction définie dans le modèle conceptuel</span><span class="sxs-lookup"><span data-stu-id="22e47-108">To call a function defined in the conceptual model</span></span>  
  
1. <span data-ttu-id="22e47-109">Ajoutez une méthode CLR (Common Language Runtime) à votre application qui se mappe à la fonction définie dans le modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="22e47-109">Add a common language runtime (CLR) method to your application that maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="22e47-110">Pour mapper la méthode, vous devez lui appliquer un attribut <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="22e47-110">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="22e47-111">Notez que les paramètres <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> et <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de l'attribut correspondent respectivement au nom de l'espace de noms du modèle conceptuel et au nom de la fonction du modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="22e47-111">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="22e47-112">La résolution des noms de fonctions pour LINQ respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="22e47-112">Function name resolution for LINQ is case sensitive.</span></span>  
  
2. <span data-ttu-id="22e47-113">Appelez la fonction dans une requête LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="22e47-113">Call the function in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22e47-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="22e47-114">Example</span></span>  

 <span data-ttu-id="22e47-115">L’exemple suivant montre comment appeler une fonction définie dans le modèle conceptuel à partir d’une requête de LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="22e47-115">The following example demonstrates how to call a function that is defined in the conceptual model from within a LINQ to Entities query.</span></span> <span data-ttu-id="22e47-116">L'exemple utilise le modèle School.</span><span class="sxs-lookup"><span data-stu-id="22e47-116">The example uses the School model.</span></span> <span data-ttu-id="22e47-117">Pour plus d’informations sur le modèle School, consultez [création de l’exemple de base de données School](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) et [génération du fichier School. edmx](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="22e47-117">For information about the School model, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>  
  
 <span data-ttu-id="22e47-118">La fonction de modèle conceptuel suivante retourne le nombre d'années écoulées depuis l'embauche d'un formateur.</span><span class="sxs-lookup"><span data-stu-id="22e47-118">The following conceptual model function returns the number of years since an instructor was hired.</span></span> <span data-ttu-id="22e47-119">Pour plus d’informations sur l’ajout de la fonction à un modèle conceptuel, consultez [Comment : définir des fonctions personnalisées dans le modèle conceptuel](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)</span><span class="sxs-lookup"><span data-stu-id="22e47-119">For information about adding the function to a conceptual model, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)</span></span>  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="22e47-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="22e47-120">Example</span></span>  

 <span data-ttu-id="22e47-121">Ensuite, ajoutez la méthode suivante à votre application et utilisez un objet <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> pour la mapper à la fonction de modèle conceptuel :</span><span class="sxs-lookup"><span data-stu-id="22e47-121">Next, add the following method to your application and use an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to map it to the conceptual model function:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="22e47-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="22e47-122">Example</span></span>  

 <span data-ttu-id="22e47-123">Vous pouvez maintenant appeler la fonction de modèle conceptuel à partir d’une requête de LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="22e47-123">Now you can call the conceptual model function from within a LINQ to Entities query.</span></span> <span data-ttu-id="22e47-124">Le code suivant appelle la méthode pour afficher tous les formateurs embauchés il y a plus de dix ans :</span><span class="sxs-lookup"><span data-stu-id="22e47-124">The following code calls the method to display all instructors that were hired more than ten years ago:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="22e47-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22e47-125">See also</span></span>

- <span data-ttu-id="22e47-126">[Présentation d'un fichier .edmx](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="22e47-126">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="22e47-127">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="22e47-127">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="22e47-128">Appel de fonctions dans les requêtes LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="22e47-128">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="22e47-129">Comment : appeler des fonctions définies par modèle comme méthodes d'objet</span><span class="sxs-lookup"><span data-stu-id="22e47-129">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)
