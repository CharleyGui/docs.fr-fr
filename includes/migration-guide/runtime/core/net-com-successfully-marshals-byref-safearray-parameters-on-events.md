---
ms.openlocfilehash: 6ff23bbe8c48235770d39cb7d35a1df7de6c5201
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68440263"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="1ee37-101">.NET COM marshale avec succès les paramètres ByRef SafeArray sur les événements</span><span class="sxs-lookup"><span data-stu-id="1ee37-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1ee37-102">Détails</span><span class="sxs-lookup"><span data-stu-id="1ee37-102">Details</span></span>|<span data-ttu-id="1ee37-103">Dans .NET Framework 4.7.2 et versions antérieures, le marshaling en code natif d’un paramètre ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) sur un événement COM était voué à l’échec.</span><span class="sxs-lookup"><span data-stu-id="1ee37-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="1ee37-104">Avec cette modification, le [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) est maintenant correctement marshalé.</span><span class="sxs-lookup"><span data-stu-id="1ee37-104">With this change the [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="1ee37-105">[ x ] Quirked</span><span class="sxs-lookup"><span data-stu-id="1ee37-105">[ x ] Quirked</span></span></li></ul>|
|<span data-ttu-id="1ee37-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="1ee37-106">Suggestion</span></span>|<span data-ttu-id="1ee37-107">Si les paramètres ByRef SafeArray correctement marshalés sur des événements COM interromptent l’exécution, vous pouvez désactiver ce code en ajoutant le commutateur de configuration suivant à la configuration de votre application :</span><span class="sxs-lookup"><span data-stu-id="1ee37-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="1ee37-108">Portée</span><span class="sxs-lookup"><span data-stu-id="1ee37-108">Scope</span></span>|<span data-ttu-id="1ee37-109">Mineur</span><span class="sxs-lookup"><span data-stu-id="1ee37-109">Minor</span></span>|
|<span data-ttu-id="1ee37-110">Version</span><span class="sxs-lookup"><span data-stu-id="1ee37-110">Version</span></span>|<span data-ttu-id="1ee37-111">4.8</span><span class="sxs-lookup"><span data-stu-id="1ee37-111">4.8</span></span>|
|<span data-ttu-id="1ee37-112">Type</span><span class="sxs-lookup"><span data-stu-id="1ee37-112">Type</span></span>|<span data-ttu-id="1ee37-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="1ee37-113">Runtime</span></span>|
