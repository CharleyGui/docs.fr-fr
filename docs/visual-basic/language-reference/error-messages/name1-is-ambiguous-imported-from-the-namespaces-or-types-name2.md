---
title: "'<name1>' est ambigu, importé des espaces de noms ou des types '<name2>'"
ms.date: 07/20/2015
f1_keywords:
- vbc30561
- bc30561
helpviewer_keywords:
- BC30561
ms.assetid: 761091f7-1018-4299-b481-3966a4a2c126
ms.openlocfilehash: 73cc604f1e3a06687ca93779a01e698512be198b
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160182"
---
# <a name="bc30561-name1-is-ambiguous-imported-from-the-namespaces-or-types-name2"></a><span data-ttu-id="ca546-102">BC30561 : ' \<name1> 'est ambigu, importé des espaces de noms ou des types' \<name2> '</span><span class="sxs-lookup"><span data-stu-id="ca546-102">BC30561: '\<name1>' is ambiguous, imported from the namespaces or types '\<name2>'</span></span>

<span data-ttu-id="ca546-103">Vous avez fourni un nom ambigu qui entre par conséquent en conflit avec un autre nom.</span><span class="sxs-lookup"><span data-stu-id="ca546-103">You have provided a name that is ambiguous and therefore conflicts with another name.</span></span> <span data-ttu-id="ca546-104">Le compilateur de Visual Basic n’a pas de règles de résolution de conflit ; vous devez lever vous-même toute ambiguïté sur les noms.</span><span class="sxs-lookup"><span data-stu-id="ca546-104">The Visual Basic compiler does not have any conflict resolution rules; you must disambiguate names yourself.</span></span>

 <span data-ttu-id="ca546-105">**ID d’erreur :** BC30561</span><span class="sxs-lookup"><span data-stu-id="ca546-105">**Error ID:** BC30561</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ca546-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ca546-106">To correct this error</span></span>

- <span data-ttu-id="ca546-107">Lever l’ambiguïté du nom en supprimant les importations d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="ca546-107">Disambiguate the name by removing namespace imports.</span></span>

- <span data-ttu-id="ca546-108">Utilisez un nom qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="ca546-108">Fully qualify the name.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca546-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca546-109">See also</span></span>

- [<span data-ttu-id="ca546-110">Imports, instruction (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="ca546-110">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="ca546-111">Espaces de noms dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ca546-111">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="ca546-112">Namespace, instruction</span><span class="sxs-lookup"><span data-stu-id="ca546-112">Namespace Statement</span></span>](../statements/namespace-statement.md)
