---
title: "Comment : créer des exceptions définies par l'utilisateur"
description: Découvrez comment créer des exceptions définies par l’utilisateur, qui sont une alternative à la hiérarchie des classes d’exception dérivées de la classe de base exception dans .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
ms.openlocfilehash: b0a8549c9bacf322a0685c7b505185ab1d1101f6
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828125"
---
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="d03be-103">Guide pratique pour créer des exceptions définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="d03be-103">How to create user-defined exceptions</span></span>

<span data-ttu-id="d03be-104">.NET fournit une hiérarchie de classes d’exception dérivées de la classe de base <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="d03be-104">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="d03be-105">Toutefois, si aucune exception prédéfinie ne répond à vos besoins, vous pouvez créer vos propres classes d’exception en les dérivant de la classe <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="d03be-105">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="d03be-106">Quand vous créez vos propres exceptions, terminez le nom de la classe définie par l’utilisateur par le mot « Exception » et implémentez les trois constructeurs communs, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d03be-106">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception", and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="d03be-107">L’exemple définit une nouvelle classe d’exception nommée `EmployeeListNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="d03be-107">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="d03be-108">La classe est dérivée de l’exception <xref:System.Exception> et inclut trois constructeurs.</span><span class="sxs-lookup"><span data-stu-id="d03be-108">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="d03be-109">Dans les situations où vous utilisez la communication à distance, vous devez vérifier que les métadonnées des exceptions définies par l’utilisateur sont disponibles sur le serveur (appelé) et le client (objet proxy ou appelant).</span><span class="sxs-lookup"><span data-stu-id="d03be-109">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="d03be-110">Pour plus d’informations, consultez les [Bonnes pratiques pour les exceptions](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="d03be-110">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d03be-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d03be-111">See also</span></span>

- [<span data-ttu-id="d03be-112">Exceptions</span><span class="sxs-lookup"><span data-stu-id="d03be-112">Exceptions</span></span>](index.md)
