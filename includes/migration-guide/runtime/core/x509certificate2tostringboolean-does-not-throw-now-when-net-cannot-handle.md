---
ms.openlocfilehash: d48519443aeee05617538cf2cc12bea49ad3e16d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858582"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="37095-101">X509Certificate2.ToString(Boolean) ne lève plus d’exception quand .NET ne peut pas gérer le certificat</span><span class="sxs-lookup"><span data-stu-id="37095-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

|   |   |
|---|---|
|<span data-ttu-id="37095-102">Détails</span><span class="sxs-lookup"><span data-stu-id="37095-102">Details</span></span>|<span data-ttu-id="37095-103">Dans .NET Framework 4.5.2 et antérieur, cette méthode levait une exception quand la valeur <code>true</code> était passée au paramètre verbose alors que des certificats non pris en charge par le .NET Framework étaient installés.</span><span class="sxs-lookup"><span data-stu-id="37095-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="37095-104">À présent, la méthode n’échoue plus et retourne une chaîne valide qui omet les parties inaccessibles du certificat.</span><span class="sxs-lookup"><span data-stu-id="37095-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>|
|<span data-ttu-id="37095-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="37095-105">Suggestion</span></span>|<span data-ttu-id="37095-106">Le code qui dépend de <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> doit être mis à jour pour s’attendre à ce que la chaîne retournée omette certaines données du certificat (telles que la clé publique, la clé privée et les extensions), ce qui aurait auparavant entraîné la levée d’une exception par l’API.</span><span class="sxs-lookup"><span data-stu-id="37095-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>|
|<span data-ttu-id="37095-107">Portée</span><span class="sxs-lookup"><span data-stu-id="37095-107">Scope</span></span>|<span data-ttu-id="37095-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="37095-108">Edge</span></span>|
|<span data-ttu-id="37095-109">Version</span><span class="sxs-lookup"><span data-stu-id="37095-109">Version</span></span>|<span data-ttu-id="37095-110">4.6</span><span class="sxs-lookup"><span data-stu-id="37095-110">4.6</span></span>|
|<span data-ttu-id="37095-111">Type</span><span class="sxs-lookup"><span data-stu-id="37095-111">Type</span></span>|<span data-ttu-id="37095-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="37095-112">Runtime</span></span>|
|<span data-ttu-id="37095-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="37095-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|

