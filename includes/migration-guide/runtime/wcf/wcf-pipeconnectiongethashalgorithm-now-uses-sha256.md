---
ms.openlocfilehash: 0f87f9e9b87860da97ce96e18104b44ec4327c91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621093"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="99d95-101">PipeConnection.GetHashAlgorithm dans WCF utilise maintenant SHA256</span><span class="sxs-lookup"><span data-stu-id="99d95-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="99d95-102">Détails</span><span class="sxs-lookup"><span data-stu-id="99d95-102">Details</span></span>

<span data-ttu-id="99d95-103">À compter de .NET Framework 4.7.1, Windows Communication Foundation utilise un hachage SHA256 pour générer des noms aléatoires pour les canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="99d95-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="99d95-104">Dans .NET Framework 4.7 et versions antérieures, il utilisait un hachage SHA1.</span><span class="sxs-lookup"><span data-stu-id="99d95-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="99d95-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="99d95-105">Suggestion</span></span>

<span data-ttu-id="99d95-106">Si vous rencontrez des problèmes de compatibilité avec cette modification dans .NET Framework 4.7.1 ou version ultérieure, vous pouvez choisir de ne pas y adhérer en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="99d95-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="99d95-107">Nom</span><span class="sxs-lookup"><span data-stu-id="99d95-107">Name</span></span>    | <span data-ttu-id="99d95-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="99d95-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="99d95-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="99d95-109">Scope</span></span>   |<span data-ttu-id="99d95-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="99d95-110">Minor</span></span>|
|<span data-ttu-id="99d95-111">Version</span><span class="sxs-lookup"><span data-stu-id="99d95-111">Version</span></span>|<span data-ttu-id="99d95-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="99d95-112">4.7.1</span></span>|
|<span data-ttu-id="99d95-113">Type</span><span class="sxs-lookup"><span data-stu-id="99d95-113">Type</span></span>|<span data-ttu-id="99d95-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="99d95-114">Runtime</span></span>|
