---
ms.openlocfilehash: 4b41e5fcb6da638457ca8029a635f391b6a7b8ec
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182035"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="3b39b-101">InvalidAsynchronousStateException déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="3b39b-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="3b39b-102">La <xref:System.ComponentModel.InvalidAsynchronousStateException> classe a été déplacée.</span><span class="sxs-lookup"><span data-stu-id="3b39b-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3b39b-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="3b39b-103">Change description</span></span>

<span data-ttu-id="3b39b-104">Dans .net Core 2,2 et les versions antérieures, <xref:System.ComponentModel.InvalidAsynchronousStateException> la classe se trouve dans l’assembly *System. ComponentModel. TypeConverter* .</span><span class="sxs-lookup"><span data-stu-id="3b39b-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="3b39b-105">À compter de .NET Core 3,0, il se trouve dans l’assembly *System. ComponentModel. Primitives* .</span><span class="sxs-lookup"><span data-stu-id="3b39b-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3b39b-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="3b39b-106">Version introduced</span></span>

<span data-ttu-id="3b39b-107">3.0</span><span class="sxs-lookup"><span data-stu-id="3b39b-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3b39b-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="3b39b-108">Recommended action</span></span>

<span data-ttu-id="3b39b-109">Cette modification affecte uniquement les applications qui utilisent la réflexion pour <xref:System.ComponentModel.InvalidAsynchronousStateException> charger le en appelant une méthode <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> telle que ou une <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> surcharge de qui suppose que le type se trouve dans un assembly particulier.</span><span class="sxs-lookup"><span data-stu-id="3b39b-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="3b39b-110">Si tel est le cas, l’assembly référencé dans l’appel de méthode doit être mis à jour pour refléter le nouvel emplacement de l’assembly du type.</span><span class="sxs-lookup"><span data-stu-id="3b39b-110">If that is the case, the assembly the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="3b39b-111">Category</span><span class="sxs-lookup"><span data-stu-id="3b39b-111">Category</span></span>

<span data-ttu-id="3b39b-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="3b39b-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3b39b-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="3b39b-113">Affected APIs</span></span>

- <span data-ttu-id="3b39b-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3b39b-114">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->