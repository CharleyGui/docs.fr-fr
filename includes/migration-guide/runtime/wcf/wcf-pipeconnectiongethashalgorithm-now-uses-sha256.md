---
ms.openlocfilehash: d32725b0d3063d3320b73e02039ff567090da932
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497264"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="a751b-101">PipeConnection.GetHashAlgorithm dans WCF utilise maintenant SHA256</span><span class="sxs-lookup"><span data-stu-id="a751b-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="a751b-102">Détails</span><span class="sxs-lookup"><span data-stu-id="a751b-102">Details</span></span>

<span data-ttu-id="a751b-103">À compter de .NET Framework 4.7.1, Windows Communication Foundation utilise un hachage SHA256 pour générer des noms aléatoires pour les canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="a751b-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="a751b-104">Dans .NET Framework 4.7 et versions antérieures, il utilisait un hachage SHA1.</span><span class="sxs-lookup"><span data-stu-id="a751b-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a751b-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="a751b-105">Suggestion</span></span>

<span data-ttu-id="a751b-106">Si vous rencontrez des problèmes de compatibilité avec cette modification dans .NET Framework 4.7.1 ou version ultérieure, vous pouvez choisir de ne pas y adhérer en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="a751b-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="a751b-107">Name</span><span class="sxs-lookup"><span data-stu-id="a751b-107">Name</span></span>    | <span data-ttu-id="a751b-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="a751b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a751b-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="a751b-109">Scope</span></span>   |<span data-ttu-id="a751b-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="a751b-110">Minor</span></span>|
|<span data-ttu-id="a751b-111">Version</span><span class="sxs-lookup"><span data-stu-id="a751b-111">Version</span></span>|<span data-ttu-id="a751b-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="a751b-112">4.7.1</span></span>|
|<span data-ttu-id="a751b-113">Type</span><span class="sxs-lookup"><span data-stu-id="a751b-113">Type</span></span>|<span data-ttu-id="a751b-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="a751b-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="a751b-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="a751b-115">Affected APIs</span></span>

<span data-ttu-id="a751b-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="a751b-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
