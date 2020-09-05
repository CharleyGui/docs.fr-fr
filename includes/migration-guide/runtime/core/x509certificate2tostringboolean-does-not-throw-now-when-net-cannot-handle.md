---
ms.openlocfilehash: 7f8f97adcca7e66fa5756212bb977daadd92b8b6
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496550"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="b8d6d-101">X509Certificate2.ToString(Boolean) ne lève plus d’exception quand .NET ne peut pas gérer le certificat</span><span class="sxs-lookup"><span data-stu-id="b8d6d-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

#### <a name="details"></a><span data-ttu-id="b8d6d-102">Détails</span><span class="sxs-lookup"><span data-stu-id="b8d6d-102">Details</span></span>

<span data-ttu-id="b8d6d-103">Dans .NET Framework 4.5.2 et antérieur, cette méthode levait une exception quand la valeur <code>true</code> était passée au paramètre verbose alors que des certificats non pris en charge par le .NET Framework étaient installés.</span><span class="sxs-lookup"><span data-stu-id="b8d6d-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="b8d6d-104">À présent, la méthode n’échoue plus et retourne une chaîne valide qui omet les parties inaccessibles du certificat.</span><span class="sxs-lookup"><span data-stu-id="b8d6d-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b8d6d-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="b8d6d-105">Suggestion</span></span>

<span data-ttu-id="b8d6d-106">Le code qui dépend de <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> doit être mis à jour pour s’attendre à ce que la chaîne retournée omette certaines données du certificat (telles que la clé publique, la clé privée et les extensions), ce qui aurait auparavant entraîné la levée d’une exception par l’API.</span><span class="sxs-lookup"><span data-stu-id="b8d6d-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>

| <span data-ttu-id="b8d6d-107">Name</span><span class="sxs-lookup"><span data-stu-id="b8d6d-107">Name</span></span>    | <span data-ttu-id="b8d6d-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="b8d6d-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b8d6d-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="b8d6d-109">Scope</span></span>   |<span data-ttu-id="b8d6d-110">Edge</span><span class="sxs-lookup"><span data-stu-id="b8d6d-110">Edge</span></span>|
|<span data-ttu-id="b8d6d-111">Version</span><span class="sxs-lookup"><span data-stu-id="b8d6d-111">Version</span></span>|<span data-ttu-id="b8d6d-112">4,6</span><span class="sxs-lookup"><span data-stu-id="b8d6d-112">4.6</span></span>|
|<span data-ttu-id="b8d6d-113">Type</span><span class="sxs-lookup"><span data-stu-id="b8d6d-113">Type</span></span>|<span data-ttu-id="b8d6d-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="b8d6d-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="b8d6d-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="b8d6d-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)`

-->
