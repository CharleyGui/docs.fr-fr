---
ms.openlocfilehash: 19359422f79f8240676b0057c7391f6b06f961ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147547"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="e62b1-101">InvalidAsynchroneStateException a déménagé à une autre assemblée</span><span class="sxs-lookup"><span data-stu-id="e62b1-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="e62b1-102">La <xref:System.ComponentModel.InvalidAsynchronousStateException> classe a été déplacée.</span><span class="sxs-lookup"><span data-stu-id="e62b1-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e62b1-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="e62b1-103">Change description</span></span>

<span data-ttu-id="e62b1-104">Dans .NET Core 2.2 et <xref:System.ComponentModel.InvalidAsynchronousStateException> les versions antérieures, la classe se trouve dans *l’assemblage System.ComponentModel.TypeConverter.*</span><span class="sxs-lookup"><span data-stu-id="e62b1-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="e62b1-105">En commençant par .NET Core 3.0, il se trouve dans *l’assemblage System.ComponentModel.Primitives.*</span><span class="sxs-lookup"><span data-stu-id="e62b1-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e62b1-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e62b1-106">Version introduced</span></span>

<span data-ttu-id="e62b1-107">3.0</span><span class="sxs-lookup"><span data-stu-id="e62b1-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e62b1-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="e62b1-108">Recommended action</span></span>

<span data-ttu-id="e62b1-109">Ce changement n’affecte que les <xref:System.ComponentModel.InvalidAsynchronousStateException> applications qui utilisent <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> la réflexion <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> pour charger le en appelant une méthode telle que ou une surcharge de ce qui suppose que le type est dans un assemblage particulier.</span><span class="sxs-lookup"><span data-stu-id="e62b1-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="e62b1-110">Si tel est le cas, l’assemblage référencé dans l’appel de méthode doit être mis à jour pour refléter le nouveau lieu d’assemblage du type.</span><span class="sxs-lookup"><span data-stu-id="e62b1-110">If that is the case, the assembly the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="e62b1-111">Category</span><span class="sxs-lookup"><span data-stu-id="e62b1-111">Category</span></span>

<span data-ttu-id="e62b1-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="e62b1-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e62b1-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="e62b1-113">Affected APIs</span></span>

<span data-ttu-id="e62b1-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e62b1-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
