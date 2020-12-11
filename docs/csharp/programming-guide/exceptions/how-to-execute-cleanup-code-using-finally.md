---
title: Guide pratique pour exécuter le code de nettoyage à l’aide de finally (Guide de programmation C#)
description: Découvrez comment exécuter le code de nettoyage à l’aide d’une instruction’Finally'. Enfin, les instructions garantissent que tout nettoyage nécessaire d’objets se produit immédiatement.
ms.date: 12/09/2020
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: e9b5d3086488d3f7e3c0709317d6fafd15c439e8
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110180"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="eab40-104">Comment exécuter le code de nettoyage à l’aide de finally (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="eab40-104">How to execute cleanup code using finally (C# Programming Guide)</span></span>

<span data-ttu-id="eab40-105">L’objectif d’une instruction `finally` est de vérifier que le nettoyage nécessaire des objets, généralement ceux contenant des ressources externes, se produit immédiatement, même si une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="eab40-105">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="eab40-106">Un exemple de nettoyage de ce type est l’appel à <xref:System.IO.Stream.Close%2A> sur un <xref:System.IO.FileStream> immédiatement après son utilisation au lieu d’attendre que l’objet soit récupéré par garbage collection par le Common Language Runtime, comme suit :</span><span class="sxs-lookup"><span data-stu-id="eab40-106">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>

:::code language="csharp" source="snippets/exceptions/Program.cs" ID="NoCleanup":::

## <a name="example"></a><span data-ttu-id="eab40-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="eab40-107">Example</span></span>

<span data-ttu-id="eab40-108">Pour transformer le code précédent en instruction `try-catch-finally`, le code de nettoyage est séparé du code actif comme suit.</span><span class="sxs-lookup"><span data-stu-id="eab40-108">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>

:::code language="csharp" source="snippets/exceptions/Program.cs" ID="WithCleanup":::

<span data-ttu-id="eab40-109">Comme une exception peut se produire à tout moment dans le `try` bloc avant l' `OpenWrite()` appel, ou `OpenWrite()` si l’appel lui-même peut échouer, nous n’avons pas la garantie que le fichier est ouvert lorsque nous tentons de le fermer.</span><span class="sxs-lookup"><span data-stu-id="eab40-109">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we aren't guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="eab40-110">Le `finally` bloc ajoute une vérification pour s’assurer que l' <xref:System.IO.FileStream> objet ne se trouve pas `null` avant d’appeler la <xref:System.IO.Stream.Close%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="eab40-110">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object isn't `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="eab40-111">Sans la `null` vérification, le `finally` bloc pourrait lever sa propre <xref:System.NullReferenceException> , mais la levée d’exceptions dans des `finally` blocs doit être évitée si possible.</span><span class="sxs-lookup"><span data-stu-id="eab40-111">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it's possible.</span></span>

<span data-ttu-id="eab40-112">Une connexion de base de données est également susceptible d’être fermée dans un bloc `finally`.</span><span class="sxs-lookup"><span data-stu-id="eab40-112">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="eab40-113">Le nombre de connexions à un serveur de base de données étant parfois limité, vous devez fermer les connexions de base de données le plus rapidement possible.</span><span class="sxs-lookup"><span data-stu-id="eab40-113">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="eab40-114">Si une exception est levée avant que vous ne puissiez fermer votre connexion, l’utilisation du `finally` bloc est préférable à l’attente de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="eab40-114">If an exception is thrown before you can close your connection, using the `finally` block is better than waiting for garbage collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="eab40-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eab40-115">See also</span></span>

- [<span data-ttu-id="eab40-116">using, instruction</span><span class="sxs-lookup"><span data-stu-id="eab40-116">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="eab40-117">try-catch</span><span class="sxs-lookup"><span data-stu-id="eab40-117">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="eab40-118">try-finally</span><span class="sxs-lookup"><span data-stu-id="eab40-118">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="eab40-119">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="eab40-119">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
