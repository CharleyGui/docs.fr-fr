---
ms.openlocfilehash: a2d4b7592727ca20ee79867094d6972eb9c4baed
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857255"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="c396d-101">La valeur par défaut de MsmqSecureHashAlgorithm dans WCF est désormais SHA256</span><span class="sxs-lookup"><span data-stu-id="c396d-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c396d-102">Détails</span><span class="sxs-lookup"><span data-stu-id="c396d-102">Details</span></span>|<span data-ttu-id="c396d-103">À compter de .NET Framework 4.7.1, l’algorithme de signature des messages par défaut dans WCF pour les messages Msmq est SHA256.</span><span class="sxs-lookup"><span data-stu-id="c396d-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="c396d-104">Dans .NET Framework 4.7 et versions antérieures, l’algorithme de signature des messages par défaut est SHA1.</span><span class="sxs-lookup"><span data-stu-id="c396d-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="c396d-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="c396d-105">Suggestion</span></span>|<span data-ttu-id="c396d-106">Si vous rencontrez des problèmes de compatibilité avec cette modification dans .NET Framework 4.7.1 ou version ultérieure, vous pouvez choisir de ne pas adhérer à la modification en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="c396d-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="c396d-107">Portée</span><span class="sxs-lookup"><span data-stu-id="c396d-107">Scope</span></span>|<span data-ttu-id="c396d-108">Mineur</span><span class="sxs-lookup"><span data-stu-id="c396d-108">Minor</span></span>|
|<span data-ttu-id="c396d-109">Version</span><span class="sxs-lookup"><span data-stu-id="c396d-109">Version</span></span>|<span data-ttu-id="c396d-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="c396d-110">4.7.1</span></span>|
|<span data-ttu-id="c396d-111">Type</span><span class="sxs-lookup"><span data-stu-id="c396d-111">Type</span></span>|<span data-ttu-id="c396d-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="c396d-112">Runtime</span></span>|

