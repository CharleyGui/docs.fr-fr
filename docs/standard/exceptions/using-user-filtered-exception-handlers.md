---
title: Utiliser des gestionnaires d’exceptions filtrés par l’utilisateur
description: Découvrez comment utiliser des gestionnaires d’exceptions filtrés par l’utilisateur en C# et Visual Basic.
ms.date: 12/14/2020
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2dba43ad2fc685a6555ab43fc973814fd7f359a3
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512669"
---
# <a name="use-user-filtered-exception-handlers"></a><span data-ttu-id="5ebdf-103">Utiliser des gestionnaires d’exceptions filtrés par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="5ebdf-103">Use user-filtered exception handlers</span></span>

<span data-ttu-id="5ebdf-104">Les gestionnaires d’exceptions filtrés par l’utilisateur interceptent et gèrent les exceptions selon des critères que vous définissez pour l’exception.</span><span class="sxs-lookup"><span data-stu-id="5ebdf-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="5ebdf-105">Ces gestionnaires utilisent l' `catch` instruction avec le `when` mot clé ( `Catch` et `When` dans Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5ebdf-105">These handlers use the `catch` statement with the `when` keyword (`Catch` and `When` in Visual Basic).</span></span>  
  
 <span data-ttu-id="5ebdf-106">Cette technique est utile lorsqu’un objet d’exception particulier correspond à plusieurs erreurs.</span><span class="sxs-lookup"><span data-stu-id="5ebdf-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="5ebdf-107">Dans ce cas, l’objet possède généralement une propriété qui contient le code d’erreur associé à l’erreur.</span><span class="sxs-lookup"><span data-stu-id="5ebdf-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="5ebdf-108">Vous pouvez utiliser la propriété code d’erreur dans l’expression pour sélectionner uniquement l’erreur particulière que vous souhaitez gérer dans cette `catch` clause.</span><span class="sxs-lookup"><span data-stu-id="5ebdf-108">You can use the error code property in the expression to select only the particular error you want to handle in that `catch` clause.</span></span>  
  
 <span data-ttu-id="5ebdf-109">L’exemple suivant illustre l' `catch` / `when` instruction.</span><span class="sxs-lookup"><span data-stu-id="5ebdf-109">The following example illustrates the `catch`/`when` statement.</span></span>

```csharp
try
{
    //Try statements.  
}
catch (Exception ex) when (ex.Message.Contains("404"))
{
    //Catch statements.
}
```  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 <span data-ttu-id="5ebdf-110">L’expression de la clause filtrée par l’utilisateur n’est pas limitée.</span><span class="sxs-lookup"><span data-stu-id="5ebdf-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="5ebdf-111">Si une exception se produit pendant l’exécution de l’expression filtrée par l’utilisateur, cette exception est ignorée et l’expression filtrée est considérée comme ayant la valeur False.</span><span class="sxs-lookup"><span data-stu-id="5ebdf-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="5ebdf-112">Dans ce cas, le common language runtime continue la recherche d’un gestionnaire pour l’exception actuelle.</span><span class="sxs-lookup"><span data-stu-id="5ebdf-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combine-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="5ebdf-113">Combiner l’exception spécifique et les clauses filtrées par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="5ebdf-113">Combine the specific exception and the user-filtered clauses</span></span>  

 <span data-ttu-id="5ebdf-114">Une `catch` instruction peut contenir à la fois l’exception spécifique et les clauses filtrées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5ebdf-114">A `catch` statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="5ebdf-115">Le runtime teste tout d’abord l’exception spécifique.</span><span class="sxs-lookup"><span data-stu-id="5ebdf-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="5ebdf-116">Si l’exception spécifique réussit, le runtime exécute le filtre de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5ebdf-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="5ebdf-117">Le filtre générique peut contenir une référence à la variable déclarée dans le filtre de la classe.</span><span class="sxs-lookup"><span data-stu-id="5ebdf-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="5ebdf-118">Notez que l’ordre des deux clauses de filtre ne peut pas être inversé.</span><span class="sxs-lookup"><span data-stu-id="5ebdf-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="5ebdf-119">L’exemple suivant montre une exception spécifique dans l’instruction **catch** , ainsi que la clause filtrée par l’utilisateur à l’aide du mot clé **When** .</span><span class="sxs-lookup"><span data-stu-id="5ebdf-119">The following example shows a specific exception in the **catch** statement as well as the user-filtered clause using the **when** keyword.</span></span>  
  
```csharp
try
{
    //Try statements.  
}
catch (System.Net.Http.HttpRequestException ex) when (ex.Message.Contains("404"))
{
    //Catch statements.
}
```  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="5ebdf-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ebdf-120">See also</span></span>

- [<span data-ttu-id="5ebdf-121">Exceptions</span><span class="sxs-lookup"><span data-stu-id="5ebdf-121">Exceptions</span></span>](index.md)
