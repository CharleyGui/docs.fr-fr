---
title: Interopérabilité des exceptions
ms.date: 01/16/2020
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- interop, exceptions
- exceptions, interop
ms.openlocfilehash: db7c9943c298607aa91a4bd08ddc12bbafc872be
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830621"
---
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a><span data-ttu-id="63695-102">Utilisation d’exceptions d’interopérabilité dans du code non managé</span><span class="sxs-lookup"><span data-stu-id="63695-102">Working with Interop Exceptions in Unmanaged Code</span></span>

<span data-ttu-id="63695-103">L’interopérabilité des exceptions de code non managé est uniquement prise en charge sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="63695-103">Unmanaged code exception interop is supported on Windows platforms only.</span></span> <span data-ttu-id="63695-104">Des problèmes de portabilité se posent sur les plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="63695-104">Portability issues arise on non-Windows platforms.</span></span> <span data-ttu-id="63695-105">Étant donné que l’ABI UNIX n’a aucune définition pour la gestion des exceptions, le code managé ne peut pas savoir comment les mécanismes d’exception fonctionnent en coulisses.</span><span class="sxs-lookup"><span data-stu-id="63695-105">Since the Unix ABI has no definition for exception handling, managed code can't know how exception mechanisms work under the covers.</span></span> <span data-ttu-id="63695-106">Par conséquent, les exceptions peuvent aboutir à des comportements imprévisibles et des blocages.</span><span class="sxs-lookup"><span data-stu-id="63695-106">Therefore, exceptions can end up resulting in unpredictable behaviors and crashes.</span></span>

## <a name="setjmplongjmp-behaviors"></a><span data-ttu-id="63695-107">Comportements setjmp/longjmp</span><span class="sxs-lookup"><span data-stu-id="63695-107">Setjmp/Longjmp Behaviors</span></span>

<span data-ttu-id="63695-108">L’interopérabilité avec `setjmp` les `longjmp` fonctions et C n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="63695-108">Interop with `setjmp` and `longjmp` C functions is not supported.</span></span> <span data-ttu-id="63695-109">Vous ne pouvez pas utiliser `longjmp` pour ignorer des frames managés.</span><span class="sxs-lookup"><span data-stu-id="63695-109">You can't use `longjmp` to skip over managed frames.</span></span>

<span data-ttu-id="63695-110">Pour plus d’informations, consultez [la documentation longjmp](/cpp/c-runtime-library/reference/longjmp).</span><span class="sxs-lookup"><span data-stu-id="63695-110">For more information, see [longjmp documentation](/cpp/c-runtime-library/reference/longjmp).</span></span>

## <a name="see-also"></a><span data-ttu-id="63695-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63695-111">See also</span></span>

- [<span data-ttu-id="63695-112">Exceptions</span><span class="sxs-lookup"><span data-stu-id="63695-112">Exceptions</span></span>](index.md)
- [<span data-ttu-id="63695-113">Interopérabilité avec des bibliothèques natives</span><span class="sxs-lookup"><span data-stu-id="63695-113">Interop with Native Libraries</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
