---
ms.openlocfilehash: aadf5eb85c8736c29639d49bc8baf21545d2467c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606873"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="5c767-101">.NET COM marshale avec succès les paramètres ByRef SafeArray sur les événements</span><span class="sxs-lookup"><span data-stu-id="5c767-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

#### <a name="details"></a><span data-ttu-id="5c767-102">Détails</span><span class="sxs-lookup"><span data-stu-id="5c767-102">Details</span></span>

<span data-ttu-id="5c767-103">Dans .NET Framework 4.7.2 et versions antérieures, le marshaling en code natif d’un paramètre ByRef [SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray) sur un événement COM était voué à l’échec.</span><span class="sxs-lookup"><span data-stu-id="5c767-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="5c767-104">Avec cette modification, le [SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray) est maintenant correctement marshalé.</span><span class="sxs-lookup"><span data-stu-id="5c767-104">With this change the [SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="5c767-105">[ x ] Quirked</span><span class="sxs-lookup"><span data-stu-id="5c767-105">[ x ] Quirked</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="5c767-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="5c767-106">Suggestion</span></span>

<span data-ttu-id="5c767-107">Si les paramètres ByRef SafeArray correctement marshalés sur des événements COM interromptent l’exécution, vous pouvez désactiver ce code en ajoutant le commutateur de configuration suivant à la configuration de votre application :</span><span class="sxs-lookup"><span data-stu-id="5c767-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="5c767-108">Name</span><span class="sxs-lookup"><span data-stu-id="5c767-108">Name</span></span>    | <span data-ttu-id="5c767-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="5c767-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5c767-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="5c767-110">Scope</span></span>   |<span data-ttu-id="5c767-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="5c767-111">Minor</span></span>|
|<span data-ttu-id="5c767-112">Version</span><span class="sxs-lookup"><span data-stu-id="5c767-112">Version</span></span>|<span data-ttu-id="5c767-113">4.8</span><span class="sxs-lookup"><span data-stu-id="5c767-113">4.8</span></span>|
|<span data-ttu-id="5c767-114">Type</span><span class="sxs-lookup"><span data-stu-id="5c767-114">Type</span></span>|<span data-ttu-id="5c767-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="5c767-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="5c767-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="5c767-116">Affected APIs</span></span>

<span data-ttu-id="5c767-117">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="5c767-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
