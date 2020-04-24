---
ms.openlocfilehash: 394f2daebad7b6af94bee4d7876796e87fe8ab19
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135622"
---
### <a name="handling-corrupted-state-exceptions-is-not-supported"></a><span data-ttu-id="1a743-101">La gestion des exceptions d’état endommagé n’est pas prise en charge</span><span class="sxs-lookup"><span data-stu-id="1a743-101">Handling corrupted state exceptions is not supported</span></span>

<span data-ttu-id="1a743-102">La gestion des exceptions d’état de processus endommagées dans .NET Core n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="1a743-102">Handling corrupted-process-state exceptions in .NET Core is not supported.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1a743-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="1a743-103">Change description</span></span>

<span data-ttu-id="1a743-104">Auparavant, les exceptions d’état de processus endommagé pouvaient être interceptées et gérées par les gestionnaires d’exceptions de code managé, par exemple, à l’aide d’une instruction [try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) en C#.</span><span class="sxs-lookup"><span data-stu-id="1a743-104">Previously, corrupted-process-state exceptions could be caught and handled by managed code exception handlers, for example, by using a [try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) statement in C#.</span></span>

<span data-ttu-id="1a743-105">À compter de .NET Core 1,0, les exceptions d’état de processus endommagées ne peuvent pas être gérées par le code managé.</span><span class="sxs-lookup"><span data-stu-id="1a743-105">Starting in .NET Core 1.0, corrupted-process-state exceptions cannot be handled by managed code.</span></span> <span data-ttu-id="1a743-106">La common language runtime ne remet pas d’exceptions d’état de processus endommagées au code managé.</span><span class="sxs-lookup"><span data-stu-id="1a743-106">The common language runtime doesn't deliver corrupted-process-state exceptions to managed code.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1a743-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="1a743-107">Version introduced</span></span>

<span data-ttu-id="1a743-108">1.0</span><span class="sxs-lookup"><span data-stu-id="1a743-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1a743-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="1a743-109">Recommended action</span></span>

<span data-ttu-id="1a743-110">Évitez la nécessité de gérer les exceptions d’état de processus endommagées en résolvant les situations qui les mènent à la place.</span><span class="sxs-lookup"><span data-stu-id="1a743-110">Avoid the need to handle corrupted-process-state exceptions by addressing the situations that lead to them instead.</span></span> <span data-ttu-id="1a743-111">S’il est absolument nécessaire de gérer les exceptions d’état de processus endommagées, écrivez le gestionnaire d’exceptions en code C ou C++.</span><span class="sxs-lookup"><span data-stu-id="1a743-111">If it's absolutely necessary to handle corrupted-process-state exceptions, write the exception handler in C or C++ code.</span></span>

#### <a name="category"></a><span data-ttu-id="1a743-112">Category</span><span class="sxs-lookup"><span data-stu-id="1a743-112">Category</span></span>

<span data-ttu-id="1a743-113">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="1a743-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1a743-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="1a743-114">Affected APIs</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName>
- [<span data-ttu-id="1a743-115">legacyCorruptedStateExceptionsPolicy (élément)</span><span class="sxs-lookup"><span data-stu-id="1a743-115">legacyCorruptedStateExceptionsPolicy element</span></span>](~/docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)

<!--

#### Affected APIs

- `T:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute`

-->
