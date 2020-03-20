---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857255"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="3d822-101">La valeur par défaut de MsmqSecureHashAlgorithm dans WCF est désormais SHA256</span><span class="sxs-lookup"><span data-stu-id="3d822-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3d822-102">Détails</span><span class="sxs-lookup"><span data-stu-id="3d822-102">Details</span></span>|<span data-ttu-id="3d822-103">À compter de .NET Framework 4.7.1, l’algorithme de signature des messages par défaut dans WCF pour les messages Msmq est SHA256.</span><span class="sxs-lookup"><span data-stu-id="3d822-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="3d822-104">Dans .NET Framework 4.7 et versions antérieures, l’algorithme de signature des messages par défaut est SHA1.</span><span class="sxs-lookup"><span data-stu-id="3d822-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="3d822-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="3d822-105">Suggestion</span></span>|<span data-ttu-id="3d822-106">Si vous rencontrez des problèmes de compatibilité avec cette modification dans .NET Framework 4.7.1 ou version ultérieure, vous pouvez choisir de ne pas adhérer à la modification en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="3d822-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="3d822-107">Étendue</span><span class="sxs-lookup"><span data-stu-id="3d822-107">Scope</span></span>|<span data-ttu-id="3d822-108">Secondaire</span><span class="sxs-lookup"><span data-stu-id="3d822-108">Minor</span></span>|
|<span data-ttu-id="3d822-109">Version</span><span class="sxs-lookup"><span data-stu-id="3d822-109">Version</span></span>|<span data-ttu-id="3d822-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="3d822-110">4.7.1</span></span>|
|<span data-ttu-id="3d822-111">Type</span><span class="sxs-lookup"><span data-stu-id="3d822-111">Type</span></span>|<span data-ttu-id="3d822-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="3d822-112">Runtime</span></span>|
