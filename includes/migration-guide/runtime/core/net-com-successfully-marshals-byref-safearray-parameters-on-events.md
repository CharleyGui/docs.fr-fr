---
ms.openlocfilehash: 1907c9b82c9685899d328f67da8001c0fa4fb697
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497797"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="d57ce-101">.NET COM marshale avec succès les paramètres ByRef SafeArray sur les événements</span><span class="sxs-lookup"><span data-stu-id="d57ce-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

#### <a name="details"></a><span data-ttu-id="d57ce-102">Détails</span><span class="sxs-lookup"><span data-stu-id="d57ce-102">Details</span></span>

<span data-ttu-id="d57ce-103">Dans .NET Framework 4.7.2 et versions antérieures, le marshaling en code natif d’un paramètre ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) sur un événement COM était voué à l’échec.</span><span class="sxs-lookup"><span data-stu-id="d57ce-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="d57ce-104">Avec cette modification, le [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) est maintenant correctement marshalé.</span><span class="sxs-lookup"><span data-stu-id="d57ce-104">With this change the [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="d57ce-105">[ x ] Quirked</span><span class="sxs-lookup"><span data-stu-id="d57ce-105">[ x ] Quirked</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="d57ce-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="d57ce-106">Suggestion</span></span>

<span data-ttu-id="d57ce-107">Si les paramètres ByRef SafeArray correctement marshalés sur des événements COM interromptent l’exécution, vous pouvez désactiver ce code en ajoutant le commutateur de configuration suivant à la configuration de votre application :</span><span class="sxs-lookup"><span data-stu-id="d57ce-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="d57ce-108">Name</span><span class="sxs-lookup"><span data-stu-id="d57ce-108">Name</span></span>    | <span data-ttu-id="d57ce-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="d57ce-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d57ce-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="d57ce-110">Scope</span></span>   |<span data-ttu-id="d57ce-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="d57ce-111">Minor</span></span>|
|<span data-ttu-id="d57ce-112">Version</span><span class="sxs-lookup"><span data-stu-id="d57ce-112">Version</span></span>|<span data-ttu-id="d57ce-113">4.8</span><span class="sxs-lookup"><span data-stu-id="d57ce-113">4.8</span></span>|
|<span data-ttu-id="d57ce-114">Type</span><span class="sxs-lookup"><span data-stu-id="d57ce-114">Type</span></span>|<span data-ttu-id="d57ce-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="d57ce-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="d57ce-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="d57ce-116">Affected APIs</span></span>

<span data-ttu-id="d57ce-117">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="d57ce-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
