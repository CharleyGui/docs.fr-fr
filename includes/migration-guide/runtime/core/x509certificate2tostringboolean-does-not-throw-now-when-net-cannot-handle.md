---
ms.openlocfilehash: 51208762cea2a5688c5d43e5d444d4e014e5f0b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621323"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="94d20-101">X509Certificate2.ToString(Boolean) ne lève plus d’exception quand .NET ne peut pas gérer le certificat</span><span class="sxs-lookup"><span data-stu-id="94d20-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

#### <a name="details"></a><span data-ttu-id="94d20-102">Détails</span><span class="sxs-lookup"><span data-stu-id="94d20-102">Details</span></span>

<span data-ttu-id="94d20-103">Dans .NET Framework 4.5.2 et antérieur, cette méthode levait une exception quand la valeur <code>true</code> était passée au paramètre verbose alors que des certificats non pris en charge par le .NET Framework étaient installés.</span><span class="sxs-lookup"><span data-stu-id="94d20-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="94d20-104">À présent, la méthode n’échoue plus et retourne une chaîne valide qui omet les parties inaccessibles du certificat.</span><span class="sxs-lookup"><span data-stu-id="94d20-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="94d20-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="94d20-105">Suggestion</span></span>

<span data-ttu-id="94d20-106">Le code qui dépend de <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> doit être mis à jour pour s’attendre à ce que la chaîne retournée omette certaines données du certificat (telles que la clé publique, la clé privée et les extensions), ce qui aurait auparavant entraîné la levée d’une exception par l’API.</span><span class="sxs-lookup"><span data-stu-id="94d20-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>

| <span data-ttu-id="94d20-107">Nom</span><span class="sxs-lookup"><span data-stu-id="94d20-107">Name</span></span>    | <span data-ttu-id="94d20-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="94d20-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="94d20-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="94d20-109">Scope</span></span>   |<span data-ttu-id="94d20-110">Edge</span><span class="sxs-lookup"><span data-stu-id="94d20-110">Edge</span></span>|
|<span data-ttu-id="94d20-111">Version</span><span class="sxs-lookup"><span data-stu-id="94d20-111">Version</span></span>|<span data-ttu-id="94d20-112">4.6</span><span class="sxs-lookup"><span data-stu-id="94d20-112">4.6</span></span>|
|<span data-ttu-id="94d20-113">Type</span><span class="sxs-lookup"><span data-stu-id="94d20-113">Type</span></span>|<span data-ttu-id="94d20-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="94d20-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="94d20-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="94d20-115">Affected APIs</span></span>

-<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
