---
ms.openlocfilehash: 2c44c2e1658f8de556d3f7222de3fa6d4594163a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497147"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a><span data-ttu-id="ae30f-101">La désérialisation des objets MailMessage sérialisés sous .NET Framework 4.5 peut échouer</span><span class="sxs-lookup"><span data-stu-id="ae30f-101">Deserialization of MailMessage objects serialized under the .NET Framework 4.5 may fail</span></span>

#### <a name="details"></a><span data-ttu-id="ae30f-102">Détails</span><span class="sxs-lookup"><span data-stu-id="ae30f-102">Details</span></span>

<span data-ttu-id="ae30f-103">À compter de .NET Framework 4.5, les objets <xref:System.Web.Mail.MailMessage> peuvent inclure des caractères non-ASCII.</span><span class="sxs-lookup"><span data-stu-id="ae30f-103">Starting with the .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objects can include non-ASCII characters.</span></span> <span data-ttu-id="ae30f-104">Dans le .NET Framework 4, seuls les caractères ASCII sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ae30f-104">In the .NET Framework 4, only ASCII characters are supported.</span></span> <span data-ttu-id="ae30f-105">Les objets <xref:System.Web.Mail.MailMessage> qui contiennent des caractères non-ASCII et qui sont sérialisés sous .NET Framework 4.5 ou ultérieur ne peuvent pas être désérialisés dans .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ae30f-105"><xref:System.Web.Mail.MailMessage> objects that contain non-ASCII characters and that are serialized under the .NET Framework 4.5 or later cannot be deserialized under the .NET Framework 4.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ae30f-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="ae30f-106">Suggestion</span></span>

<span data-ttu-id="ae30f-107">Vérifiez que votre code assure la gestion des exceptions lors de la désérialisation d’un objet <xref:System.Web.Mail.MailMessage>.</span><span class="sxs-lookup"><span data-stu-id="ae30f-107">Ensure that your code provides exception handling when deserializing a <xref:System.Web.Mail.MailMessage> object.</span></span>

| <span data-ttu-id="ae30f-108">Name</span><span class="sxs-lookup"><span data-stu-id="ae30f-108">Name</span></span>    | <span data-ttu-id="ae30f-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="ae30f-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ae30f-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="ae30f-110">Scope</span></span>   |<span data-ttu-id="ae30f-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="ae30f-111">Minor</span></span>|
|<span data-ttu-id="ae30f-112">Version</span><span class="sxs-lookup"><span data-stu-id="ae30f-112">Version</span></span>|<span data-ttu-id="ae30f-113">4,5</span><span class="sxs-lookup"><span data-stu-id="ae30f-113">4.5</span></span>|
|<span data-ttu-id="ae30f-114">Type</span><span class="sxs-lookup"><span data-stu-id="ae30f-114">Type</span></span>|<span data-ttu-id="ae30f-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="ae30f-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ae30f-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="ae30f-116">Affected APIs</span></span>

- <xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Web.Mail.MailMessage`

-->
