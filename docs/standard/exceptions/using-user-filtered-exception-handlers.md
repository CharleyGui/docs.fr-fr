---
title: Utilisation de gestionnaires filtrés par l'utilisateur
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
ms.openlocfilehash: 5537404178b746310f720c5b0c075c77287dda4c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708451"
---
# <a name="using-user-filtered-exception-handlers"></a><span data-ttu-id="5d374-102">Utilisation de gestionnaires filtrés par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5d374-102">Using User-Filtered Exception Handlers</span></span>

<span data-ttu-id="5d374-103">Visual Basic prend actuellement en charge les exceptions filtrées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5d374-103">Currently, Visual Basic supports user-filtered exceptions.</span></span> <span data-ttu-id="5d374-104">Les gestionnaires d’exceptions filtrés par l’utilisateur interceptent et gèrent les exceptions selon des critères que vous définissez pour l’exception.</span><span class="sxs-lookup"><span data-stu-id="5d374-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="5d374-105">Ces gestionnaires utilisent l’instruction **Catch** avec le mot clé **When**.</span><span class="sxs-lookup"><span data-stu-id="5d374-105">These handlers use the **Catch** statement with the **When** keyword.</span></span>  
  
 <span data-ttu-id="5d374-106">Cette technique est utile lorsqu’un objet d’exception particulier correspond à plusieurs erreurs.</span><span class="sxs-lookup"><span data-stu-id="5d374-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="5d374-107">Dans ce cas, l’objet possède généralement une propriété qui contient le code d’erreur associé à l’erreur.</span><span class="sxs-lookup"><span data-stu-id="5d374-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="5d374-108">Vous pouvez utiliser la propriété de code d’erreur dans l’expression pour sélectionner uniquement l’erreur particulière que vous souhaitez gérer dans cette clause **Catch**.</span><span class="sxs-lookup"><span data-stu-id="5d374-108">You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.</span></span>  
  
 <span data-ttu-id="5d374-109">L’exemple Visual Basic suivant illustre l’instruction **Catch/When**.</span><span class="sxs-lookup"><span data-stu-id="5d374-109">The following Visual Basic example illustrates the **Catch/When** statement.</span></span>  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 <span data-ttu-id="5d374-110">L’expression de la clause filtrée par l’utilisateur n’est pas limitée.</span><span class="sxs-lookup"><span data-stu-id="5d374-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="5d374-111">Si une exception se produit pendant l’exécution de l’expression filtrée par l’utilisateur, cette exception est ignorée et l’expression filtrée est considérée comme ayant la valeur False.</span><span class="sxs-lookup"><span data-stu-id="5d374-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="5d374-112">Dans ce cas, le common language runtime continue la recherche d’un gestionnaire pour l’exception actuelle.</span><span class="sxs-lookup"><span data-stu-id="5d374-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="5d374-113">Combinaison de l’exception spécifique et des clauses filtrées par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="5d374-113">Combining the Specific Exception and the User-Filtered Clauses</span></span>  
 <span data-ttu-id="5d374-114">Une instruction catch peut contenir à la fois l’exception spécifique et les clauses filtrées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5d374-114">A catch statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="5d374-115">Le runtime teste tout d’abord l’exception spécifique.</span><span class="sxs-lookup"><span data-stu-id="5d374-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="5d374-116">Si l’exception spécifique réussit, le runtime exécute le filtre de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5d374-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="5d374-117">Le filtre générique peut contenir une référence à la variable déclarée dans le filtre de la classe.</span><span class="sxs-lookup"><span data-stu-id="5d374-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="5d374-118">Notez que l’ordre des deux clauses de filtre ne peut pas être inversé.</span><span class="sxs-lookup"><span data-stu-id="5d374-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="5d374-119">L’exemple Visual Basic suivant illustre l’exception spécifique `ClassLoadException` dans l’instruction **Catch** ainsi que la clause filtrée par l’utilisateur à l’aide du mot clé **When**.</span><span class="sxs-lookup"><span data-stu-id="5d374-119">The following Visual Basic example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.</span></span>  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="5d374-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d374-120">See also</span></span>

- [<span data-ttu-id="5d374-121">Exceptions</span><span class="sxs-lookup"><span data-stu-id="5d374-121">Exceptions</span></span>](index.md)
