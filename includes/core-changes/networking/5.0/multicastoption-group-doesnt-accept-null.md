---
ms.openlocfilehash: 88a0b7e04c7015ca3fa5abd8a6897dafcbe41c49
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557961"
---
### <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a><span data-ttu-id="83d95-101">MulticastOption. Group n’accepte pas de valeur null</span><span class="sxs-lookup"><span data-stu-id="83d95-101">MulticastOption.Group doesn't accept a null value</span></span>

<span data-ttu-id="83d95-102"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> n’accepte plus la valeur `null` .</span><span class="sxs-lookup"><span data-stu-id="83d95-102"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> no longer accepts a value of `null`.</span></span> <span data-ttu-id="83d95-103">Si vous affectez à la propriété la valeur `null` , une <xref:System.ArgumentNullException> exception est levée.</span><span class="sxs-lookup"><span data-stu-id="83d95-103">If you set the property to `null`, an <xref:System.ArgumentNullException> is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="83d95-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="83d95-104">Version introduced</span></span>

<span data-ttu-id="83d95-105">5.0</span><span class="sxs-lookup"><span data-stu-id="83d95-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="83d95-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="83d95-106">Change description</span></span>

<span data-ttu-id="83d95-107">Dans les versions précédentes de .NET, vous pouvez affecter <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> à la propriété la valeur `null` .</span><span class="sxs-lookup"><span data-stu-id="83d95-107">In previous versions of .NET, you can set the <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> property to `null`.</span></span> <span data-ttu-id="83d95-108">Si le <xref:System.Net.Sockets.MulticastOption> est passé par la suite à <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> , le runtime lève une exception <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="83d95-108">If the <xref:System.Net.Sockets.MulticastOption> is later passed to <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType>, the runtime throws a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="83d95-109">Dans .NET 5,0 et versions ultérieures, une <xref:System.ArgumentNullException> exception est levée si vous affectez à la propriété la valeur `null` .</span><span class="sxs-lookup"><span data-stu-id="83d95-109">In .NET 5.0 and later, an <xref:System.ArgumentNullException> is thrown if you set the property to `null`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="83d95-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="83d95-110">Reason for change</span></span>

<span data-ttu-id="83d95-111">Pour être cohérente avec les règles de conception de l’infrastructure, la propriété a été mise à jour pour lever une <xref:System.ArgumentNullException> si la valeur est `null` .</span><span class="sxs-lookup"><span data-stu-id="83d95-111">To be consistent with the Framework Design Guidelines, the property has been updated to throw an <xref:System.ArgumentNullException> if the value is `null`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="83d95-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="83d95-112">Recommended action</span></span>

<span data-ttu-id="83d95-113">Assurez-vous que vous n’affectez pas la valeur <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> `null` .</span><span class="sxs-lookup"><span data-stu-id="83d95-113">Make sure that you don't set <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> to `null`.</span></span>

#### <a name="category"></a><span data-ttu-id="83d95-114">Category</span><span class="sxs-lookup"><span data-stu-id="83d95-114">Category</span></span>

<span data-ttu-id="83d95-115">Mise en réseau</span><span class="sxs-lookup"><span data-stu-id="83d95-115">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="83d95-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="83d95-116">Affected APIs</span></span>

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

-->
