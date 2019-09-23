---
ms.openlocfilehash: 4fbec1028b6d75b90d4638814c877c263c8c8936
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182073"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a><span data-ttu-id="ce004-101">TypeDescriptionProviderAttribute déplacé vers un autre assembly</span><span class="sxs-lookup"><span data-stu-id="ce004-101">TypeDescriptionProviderAttribute moved to another assembly</span></span>

<span data-ttu-id="ce004-102">La <xref:System.ComponentModel.TypeDescriptionProviderAttribute> classe a été déplacée.</span><span class="sxs-lookup"><span data-stu-id="ce004-102">The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ce004-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="ce004-103">Change description</span></span>

<span data-ttu-id="ce004-104">Dans .net Core 2,2 et les versions antérieures, <xref:System.ComponentModel.TypeDescriptionProviderAttribute> la classe se trouve dans l’assembly *System. ComponentModel. TypeConverter* .</span><span class="sxs-lookup"><span data-stu-id="ce004-104">In .NET Core 2.2 and earlier versions, The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="ce004-105">À compter de .NET Core 3,0, il se trouve dans l’assembly *System. ObjectModel* .</span><span class="sxs-lookup"><span data-stu-id="ce004-105">Starting with .NET Core 3.0, it is found in the *System.ObjectModel* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ce004-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ce004-106">Version introduced</span></span>

<span data-ttu-id="ce004-107">3.0</span><span class="sxs-lookup"><span data-stu-id="ce004-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ce004-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="ce004-108">Recommended action</span></span>

<span data-ttu-id="ce004-109">Cette modification affecte uniquement les applications qui utilisent la réflexion pour <xref:System.ComponentModel.TypeDescriptionProviderAttribute> charger le type en appelant une méthode <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> telle que ou une <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> surcharge de qui suppose que le type se trouve dans un assembly particulier.</span><span class="sxs-lookup"><span data-stu-id="ce004-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="ce004-110">Si tel est le cas, l’assembly référencé dans l’appel de méthode doit être mis à jour pour refléter le nouvel emplacement de l’assembly du type.</span><span class="sxs-lookup"><span data-stu-id="ce004-110">If that is the case, the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="ce004-111">Category</span><span class="sxs-lookup"><span data-stu-id="ce004-111">Category</span></span>

<span data-ttu-id="ce004-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce004-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ce004-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="ce004-113">Affected APIs</span></span>

- <span data-ttu-id="ce004-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ce004-114">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->