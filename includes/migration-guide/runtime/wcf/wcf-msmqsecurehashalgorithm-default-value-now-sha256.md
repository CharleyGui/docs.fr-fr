---
ms.openlocfilehash: ccdf232d743c9e270b6ed21f698998eb95a97399
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621087"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="e2a0d-101">La valeur par défaut de MsmqSecureHashAlgorithm dans WCF est désormais SHA256</span><span class="sxs-lookup"><span data-stu-id="e2a0d-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="e2a0d-102">Détails</span><span class="sxs-lookup"><span data-stu-id="e2a0d-102">Details</span></span>

<span data-ttu-id="e2a0d-103">À compter de .NET Framework 4.7.1, l’algorithme de signature des messages par défaut dans WCF pour les messages Msmq est SHA256.</span><span class="sxs-lookup"><span data-stu-id="e2a0d-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="e2a0d-104">Dans .NET Framework 4.7 et versions antérieures, l’algorithme de signature des messages par défaut est SHA1.</span><span class="sxs-lookup"><span data-stu-id="e2a0d-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e2a0d-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="e2a0d-105">Suggestion</span></span>

<span data-ttu-id="e2a0d-106">Si vous rencontrez des problèmes de compatibilité avec cette modification dans .NET Framework 4.7.1 ou version ultérieure, vous pouvez choisir de ne pas adhérer à la modification en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="e2a0d-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="e2a0d-107">Nom</span><span class="sxs-lookup"><span data-stu-id="e2a0d-107">Name</span></span>    | <span data-ttu-id="e2a0d-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="e2a0d-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e2a0d-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="e2a0d-109">Scope</span></span>   |<span data-ttu-id="e2a0d-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="e2a0d-110">Minor</span></span>|
|<span data-ttu-id="e2a0d-111">Version</span><span class="sxs-lookup"><span data-stu-id="e2a0d-111">Version</span></span>|<span data-ttu-id="e2a0d-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="e2a0d-112">4.7.1</span></span>|
|<span data-ttu-id="e2a0d-113">Type</span><span class="sxs-lookup"><span data-stu-id="e2a0d-113">Type</span></span>|<span data-ttu-id="e2a0d-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="e2a0d-114">Runtime</span></span>|
