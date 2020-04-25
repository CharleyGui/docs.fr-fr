---
ms.openlocfilehash: d1562cb76f37b6cc2aeb6fe2f7c17c393e169e84
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158470"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="ed8da-101">InvalidAsynchronousStateException déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="ed8da-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="ed8da-102">La <xref:System.ComponentModel.InvalidAsynchronousStateException> classe a été déplacée.</span><span class="sxs-lookup"><span data-stu-id="ed8da-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ed8da-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="ed8da-103">Change description</span></span>

<span data-ttu-id="ed8da-104">Dans .NET Core 2,2 et les versions antérieures, <xref:System.ComponentModel.InvalidAsynchronousStateException> la classe se trouve dans l’assembly *System. ComponentModel. TypeConverter* .</span><span class="sxs-lookup"><span data-stu-id="ed8da-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="ed8da-105">À compter de .NET Core 3,0, il se trouve dans l’assembly *System. ComponentModel. Primitives* .</span><span class="sxs-lookup"><span data-stu-id="ed8da-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ed8da-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ed8da-106">Version introduced</span></span>

<span data-ttu-id="ed8da-107">3.0</span><span class="sxs-lookup"><span data-stu-id="ed8da-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ed8da-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="ed8da-108">Recommended action</span></span>

<span data-ttu-id="ed8da-109">Cette modification affecte uniquement les applications qui utilisent la réflexion pour <xref:System.ComponentModel.InvalidAsynchronousStateException> charger le en appelant une méthode <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> telle que ou une <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> surcharge de qui suppose que le type se trouve dans un assembly particulier.</span><span class="sxs-lookup"><span data-stu-id="ed8da-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="ed8da-110">Si tel est le cas, mettez à jour l’assembly référencé dans l’appel de la méthode pour refléter le nouvel emplacement de l’assembly du type.</span><span class="sxs-lookup"><span data-stu-id="ed8da-110">If that is the case, update the assembly referenced in the method call to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="ed8da-111">Category</span><span class="sxs-lookup"><span data-stu-id="ed8da-111">Category</span></span>

<span data-ttu-id="ed8da-112">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="ed8da-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ed8da-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="ed8da-113">Affected APIs</span></span>

<span data-ttu-id="ed8da-114">Aucune.</span><span class="sxs-lookup"><span data-stu-id="ed8da-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
