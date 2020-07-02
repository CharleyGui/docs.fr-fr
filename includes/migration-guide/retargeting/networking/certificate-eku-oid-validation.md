---
ms.openlocfilehash: c996dafcf65b1fd428be908be346de603ead6e0b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615677"
---
### <a name="certificate-eku-oid-validation"></a><span data-ttu-id="0fd0e-101">Validation de l’OID de l’utilisation améliorée de la clé (EKU) du certificat</span><span class="sxs-lookup"><span data-stu-id="0fd0e-101">Certificate EKU OID validation</span></span>

#### <a name="details"></a><span data-ttu-id="0fd0e-102">Détails</span><span class="sxs-lookup"><span data-stu-id="0fd0e-102">Details</span></span>

<span data-ttu-id="0fd0e-103">À compter de .NET Framework 4.6, les classes <xref:System.Net.Security.SslStream> ou <xref:System.Net.ServicePointManager> effectuent la validation de l’identificateur d’objet (OID) de l’utilisation améliorée de la clé (EKU).</span><span class="sxs-lookup"><span data-stu-id="0fd0e-103">Starting with .NET Framework 4.6, the <xref:System.Net.Security.SslStream> or <xref:System.Net.ServicePointManager> classes perform enhanced key use (EKU) object identifier (OID) validation.</span></span> <span data-ttu-id="0fd0e-104">Une extension EKU (utilisation améliorée de la clé) est une collection d’identificateurs d’objet indiquant les applications qui utilisent la clé.</span><span class="sxs-lookup"><span data-stu-id="0fd0e-104">An enhanced key usage (EKU) extension is a collection of object identifiers (OIDs) that indicate the applications that use the key.</span></span> <span data-ttu-id="0fd0e-105">La validation de l’OID d’utilisation améliorée de la clé (EKU) utilise des rappels de certificat distant pour garantir que le certificat distant a les OID corrects pour l’utilisation prévue.</span><span class="sxs-lookup"><span data-stu-id="0fd0e-105">EKU OID validation uses remote certificate callbacks to ensure that the remote certificate has the correct OIDs for the intended purpose.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0fd0e-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="0fd0e-106">Suggestion</span></span>

<span data-ttu-id="0fd0e-107">Si cette modification n’est pas souhaitable, vous pouvez désactiver la validation de l’OID de l’EKU de certificat en ajoutant le commutateur suivant à [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) dans le [\`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="0fd0e-107">If this change is undesirable, you can disable certificate EKU OID validation by adding the following switch to the [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) in the [\`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) of your app configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontCheckCertificateEKUs=true" />
</runtime>
```

> [!IMPORTANT]
> <span data-ttu-id="0fd0e-108">Ce paramètre est fourni dans le seul but d’assurer la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="0fd0e-108">This setting is provided for backward compatibility only.</span></span> <span data-ttu-id="0fd0e-109">Son utilisation à d’autres fins n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="0fd0e-109">Its use is otherwise not recommended.</span></span>

| <span data-ttu-id="0fd0e-110">Nom</span><span class="sxs-lookup"><span data-stu-id="0fd0e-110">Name</span></span>    | <span data-ttu-id="0fd0e-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="0fd0e-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0fd0e-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="0fd0e-112">Scope</span></span>   | <span data-ttu-id="0fd0e-113">Secondaire</span><span class="sxs-lookup"><span data-stu-id="0fd0e-113">Minor</span></span>       |
| <span data-ttu-id="0fd0e-114">Version</span><span class="sxs-lookup"><span data-stu-id="0fd0e-114">Version</span></span> | <span data-ttu-id="0fd0e-115">4.6</span><span class="sxs-lookup"><span data-stu-id="0fd0e-115">4.6</span></span>         |
| <span data-ttu-id="0fd0e-116">Type</span><span class="sxs-lookup"><span data-stu-id="0fd0e-116">Type</span></span>    | <span data-ttu-id="0fd0e-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="0fd0e-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="0fd0e-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="0fd0e-118">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
