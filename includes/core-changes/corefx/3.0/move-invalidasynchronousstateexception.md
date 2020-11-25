---
ms.openlocfilehash: 78678b4b352bb063d1521e9aee3492c0cee059b8
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032027"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="c2ad7-101">InvalidAsynchronousStateException déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="c2ad7-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="c2ad7-102">La <xref:System.ComponentModel.InvalidAsynchronousStateException> classe a été déplacée.</span><span class="sxs-lookup"><span data-stu-id="c2ad7-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c2ad7-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="c2ad7-103">Change description</span></span>

<span data-ttu-id="c2ad7-104">Dans .NET Core 2,2 et les versions antérieures, la <xref:System.ComponentModel.InvalidAsynchronousStateException> classe se trouve dans l’assembly *System. ComponentModel. TypeConverter* .</span><span class="sxs-lookup"><span data-stu-id="c2ad7-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="c2ad7-105">À compter de .NET Core 3,0, il se trouve dans l’assembly *System. ComponentModel. Primitives* .</span><span class="sxs-lookup"><span data-stu-id="c2ad7-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c2ad7-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c2ad7-106">Version introduced</span></span>

<span data-ttu-id="c2ad7-107">3.0</span><span class="sxs-lookup"><span data-stu-id="c2ad7-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c2ad7-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="c2ad7-108">Recommended action</span></span>

<span data-ttu-id="c2ad7-109">Cette modification affecte uniquement les applications qui utilisent la réflexion pour charger le <xref:System.ComponentModel.InvalidAsynchronousStateException> en appelant une méthode telle que <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> ou une surcharge de <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> qui suppose que le type se trouve dans un assembly particulier.</span><span class="sxs-lookup"><span data-stu-id="c2ad7-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="c2ad7-110">Si tel est le cas, mettez à jour l’assembly référencé dans l’appel de la méthode pour refléter le nouvel emplacement de l’assembly du type.</span><span class="sxs-lookup"><span data-stu-id="c2ad7-110">If that is the case, update the assembly referenced in the method call to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="c2ad7-111">Category</span><span class="sxs-lookup"><span data-stu-id="c2ad7-111">Category</span></span>

<span data-ttu-id="c2ad7-112">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="c2ad7-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c2ad7-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="c2ad7-113">Affected APIs</span></span>

<span data-ttu-id="c2ad7-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c2ad7-114">None.</span></span>

<!--

#### Affected APIs

- Not detectable via API analysis

-->
