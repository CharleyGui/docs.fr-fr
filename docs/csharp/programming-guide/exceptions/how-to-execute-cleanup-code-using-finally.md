---
title: Guide pratique pour exécuter le code de nettoyage à l’aide de finally (Guide de programmation C#)
description: Découvrez comment exécuter le code de nettoyage à l’aide d’une instruction’Finally'. Enfin, les instructions garantissent que tout nettoyage nécessaire d’objets se produit immédiatement.
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 283c36ab9b976a92e339000a982340148c2480a8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178643"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="1a5e5-104">Comment exécuter le code de nettoyage à l’aide de finally (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="1a5e5-104">How to execute cleanup code using finally (C# Programming Guide)</span></span>

<span data-ttu-id="1a5e5-105">L’objectif d’une instruction `finally` est de vérifier que le nettoyage nécessaire des objets, généralement ceux contenant des ressources externes, se produit immédiatement, même si une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="1a5e5-105">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="1a5e5-106">Un exemple de nettoyage de ce type est l’appel à <xref:System.IO.Stream.Close%2A> sur un <xref:System.IO.FileStream> immédiatement après son utilisation au lieu d’attendre que l’objet soit récupéré par garbage collection par le Common Language Runtime, comme suit :</span><span class="sxs-lookup"><span data-stu-id="1a5e5-106">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a><span data-ttu-id="1a5e5-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="1a5e5-107">Example</span></span>  

 <span data-ttu-id="1a5e5-108">Pour transformer le code précédent en instruction `try-catch-finally`, le code de nettoyage est séparé du code actif comme suit.</span><span class="sxs-lookup"><span data-stu-id="1a5e5-108">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 <span data-ttu-id="1a5e5-109">Comme une exception peut se produire à tout moment dans le bloc `try` avant l’appel à `OpenWrite()`, ou comme l’appel `OpenWrite()` lui-même peut échouer, nous n’avons aucune garantie que le fichier est ouvert quand nous essayons de le fermer.</span><span class="sxs-lookup"><span data-stu-id="1a5e5-109">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="1a5e5-110">Le bloc `finally` ajoute un contrôle pour garantir que l’objet <xref:System.IO.FileStream> n’est pas `null` avant d’appeler la méthode <xref:System.IO.Stream.Close%2A>.</span><span class="sxs-lookup"><span data-stu-id="1a5e5-110">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="1a5e5-111">Sans le contrôle `null`, le bloc `finally` pourrait lever sa propre <xref:System.NullReferenceException>, mais la levée d’exceptions dans des blocs `finally` doit être évitée, dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="1a5e5-111">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="1a5e5-112">Une connexion de base de données est également susceptible d’être fermée dans un bloc `finally`.</span><span class="sxs-lookup"><span data-stu-id="1a5e5-112">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="1a5e5-113">Le nombre de connexions à un serveur de base de données étant parfois limité, vous devez fermer les connexions de base de données le plus rapidement possible.</span><span class="sxs-lookup"><span data-stu-id="1a5e5-113">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="1a5e5-114">Si une exception est levée avant que vous puissiez fermer votre connexion, c’est un autre cas où il vaut mieux utiliser le bloc `finally` qu’attendre le nettoyage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="1a5e5-114">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a5e5-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a5e5-115">See also</span></span>

- [<span data-ttu-id="1a5e5-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1a5e5-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1a5e5-117">Exceptions et gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="1a5e5-117">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="1a5e5-118">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="1a5e5-118">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="1a5e5-119">using, instruction</span><span class="sxs-lookup"><span data-stu-id="1a5e5-119">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="1a5e5-120">try-catch</span><span class="sxs-lookup"><span data-stu-id="1a5e5-120">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="1a5e5-121">try-finally</span><span class="sxs-lookup"><span data-stu-id="1a5e5-121">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="1a5e5-122">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="1a5e5-122">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
