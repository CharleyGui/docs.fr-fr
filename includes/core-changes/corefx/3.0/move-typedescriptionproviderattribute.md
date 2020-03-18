---
ms.openlocfilehash: 57ca2ad839aab8d61da1a929660920efe1190334
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147534"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a><span data-ttu-id="4282d-101">TypeDescriptionProviderAttribute a déménagé à un autre assemblage</span><span class="sxs-lookup"><span data-stu-id="4282d-101">TypeDescriptionProviderAttribute moved to another assembly</span></span>

<span data-ttu-id="4282d-102">La <xref:System.ComponentModel.TypeDescriptionProviderAttribute> classe a été déplacée.</span><span class="sxs-lookup"><span data-stu-id="4282d-102">The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4282d-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="4282d-103">Change description</span></span>

<span data-ttu-id="4282d-104">Dans .NET Core 2.2 et <xref:System.ComponentModel.TypeDescriptionProviderAttribute> les versions antérieures, La classe se trouve dans *l’assemblage System.ComponentModel.TypeConverter.*</span><span class="sxs-lookup"><span data-stu-id="4282d-104">In .NET Core 2.2 and earlier versions, The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="4282d-105">En commençant par .NET Core 3.0, il se trouve dans l’assemblage *System.ObjectModel.*</span><span class="sxs-lookup"><span data-stu-id="4282d-105">Starting with .NET Core 3.0, it is found in the *System.ObjectModel* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4282d-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4282d-106">Version introduced</span></span>

<span data-ttu-id="4282d-107">3.0</span><span class="sxs-lookup"><span data-stu-id="4282d-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4282d-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="4282d-108">Recommended action</span></span>

<span data-ttu-id="4282d-109">Ce changement n’affecte que les <xref:System.ComponentModel.TypeDescriptionProviderAttribute> applications qui utilisent <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> la réflexion pour <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> charger le type en appelant une méthode telle que ou une surcharge de ce qui suppose que le type est dans un assemblage particulier.</span><span class="sxs-lookup"><span data-stu-id="4282d-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="4282d-110">Si tel est le cas, l’assemblage référencé dans l’appel de méthode doit être mis à jour pour refléter le nouveau lieu d’assemblage du type.</span><span class="sxs-lookup"><span data-stu-id="4282d-110">If that is the case, the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="4282d-111">Category</span><span class="sxs-lookup"><span data-stu-id="4282d-111">Category</span></span>

<span data-ttu-id="4282d-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4282d-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4282d-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="4282d-113">Affected APIs</span></span>

<span data-ttu-id="4282d-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4282d-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
