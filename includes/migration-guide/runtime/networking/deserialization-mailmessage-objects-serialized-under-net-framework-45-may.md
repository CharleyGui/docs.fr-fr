---
ms.openlocfilehash: ad953a1562db407c04d7860c60eb5964fe6fe2ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620039"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a><span data-ttu-id="fed2f-101">La désérialisation des objets MailMessage sérialisés sous .NET Framework 4.5 peut échouer</span><span class="sxs-lookup"><span data-stu-id="fed2f-101">Deserialization of MailMessage objects serialized under the .NET Framework 4.5 may fail</span></span>

#### <a name="details"></a><span data-ttu-id="fed2f-102">Détails</span><span class="sxs-lookup"><span data-stu-id="fed2f-102">Details</span></span>

<span data-ttu-id="fed2f-103">À compter de .NET Framework 4.5, les objets <xref:System.Web.Mail.MailMessage> peuvent inclure des caractères non-ASCII.</span><span class="sxs-lookup"><span data-stu-id="fed2f-103">Starting with the .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objects can include non-ASCII characters.</span></span> <span data-ttu-id="fed2f-104">Dans le .NET Framework 4, seuls les caractères ASCII sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="fed2f-104">In the .NET Framework 4, only ASCII characters are supported.</span></span> <span data-ttu-id="fed2f-105">Les objets <xref:System.Web.Mail.MailMessage> qui contiennent des caractères non-ASCII et qui sont sérialisés sous .NET Framework 4.5 ou ultérieur ne peuvent pas être désérialisés dans .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="fed2f-105"><xref:System.Web.Mail.MailMessage> objects that contain non-ASCII characters and that are serialized under the .NET Framework 4.5 or later cannot be deserialized under the .NET Framework 4.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fed2f-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="fed2f-106">Suggestion</span></span>

<span data-ttu-id="fed2f-107">Vérifiez que votre code assure la gestion des exceptions lors de la désérialisation d’un objet <xref:System.Web.Mail.MailMessage>.</span><span class="sxs-lookup"><span data-stu-id="fed2f-107">Ensure that your code provides exception handling when deserializing a <xref:System.Web.Mail.MailMessage> object.</span></span>

| <span data-ttu-id="fed2f-108">Nom</span><span class="sxs-lookup"><span data-stu-id="fed2f-108">Name</span></span>    | <span data-ttu-id="fed2f-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="fed2f-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fed2f-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="fed2f-110">Scope</span></span>   |<span data-ttu-id="fed2f-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="fed2f-111">Minor</span></span>|
|<span data-ttu-id="fed2f-112">Version</span><span class="sxs-lookup"><span data-stu-id="fed2f-112">Version</span></span>|<span data-ttu-id="fed2f-113">4,5</span><span class="sxs-lookup"><span data-stu-id="fed2f-113">4.5</span></span>|
|<span data-ttu-id="fed2f-114">Type</span><span class="sxs-lookup"><span data-stu-id="fed2f-114">Type</span></span>|<span data-ttu-id="fed2f-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="fed2f-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fed2f-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="fed2f-116">Affected APIs</span></span>

-<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
