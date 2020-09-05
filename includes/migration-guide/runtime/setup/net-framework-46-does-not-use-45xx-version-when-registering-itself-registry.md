---
ms.openlocfilehash: a9011514c7c4393ec44de2c7fae88768cdccf435
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496308"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a><span data-ttu-id="94a59-101">.NET Framework 4.6 n’utilise pas une version 4.5.x.x lors de son inscription dans le Registre</span><span class="sxs-lookup"><span data-stu-id="94a59-101">The .NET Framework 4.6 does not use a 4.5.x.x version when registering itself in the registry</span></span>

#### <a name="details"></a><span data-ttu-id="94a59-102">Détails</span><span class="sxs-lookup"><span data-stu-id="94a59-102">Details</span></span>

<span data-ttu-id="94a59-103">Comme prévu, la clé de version définie dans le Registre (au niveau <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) pour .NET Framework 4.6 commence par 4.6 et non 4.5.</span><span class="sxs-lookup"><span data-stu-id="94a59-103">As one might expect, the version key set in the registry (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) for the .NET Framework 4.6 begins with '4.6', not '4.5'.</span></span> <span data-ttu-id="94a59-104">Les applications qui dépendent de ces clés de Registre pour savoir quelles versions du .NET Framework sont installées sur un ordinateur doivent être mises à jour afin de comprendre que 4.6 est une nouvelle version possible et qui est compatible avec les précédentes versions 4.5.x.</span><span class="sxs-lookup"><span data-stu-id="94a59-104">Apps that depend on these registry keys to know which .NET Framework versions are installed on a machine should be updated to understand that 4.6 is a new possible version, and one that is compatible with previous 4.5.x releases.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="94a59-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="94a59-105">Suggestion</span></span>

<span data-ttu-id="94a59-106">Mettez à jour les applications qui cherchent à découvrir une installation de .NET Framework 4.5 en recherchant les clés de Registre 4.5 pour accepter également 4.6.</span><span class="sxs-lookup"><span data-stu-id="94a59-106">Update apps probing for a .NET Framework 4.5 install by looking for 4.5 registry keys to also accept 4.6.</span></span>

| <span data-ttu-id="94a59-107">Name</span><span class="sxs-lookup"><span data-stu-id="94a59-107">Name</span></span>    | <span data-ttu-id="94a59-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="94a59-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="94a59-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="94a59-109">Scope</span></span>   |<span data-ttu-id="94a59-110">Edge</span><span class="sxs-lookup"><span data-stu-id="94a59-110">Edge</span></span>|
|<span data-ttu-id="94a59-111">Version</span><span class="sxs-lookup"><span data-stu-id="94a59-111">Version</span></span>|<span data-ttu-id="94a59-112">4,6</span><span class="sxs-lookup"><span data-stu-id="94a59-112">4.6</span></span>|
|<span data-ttu-id="94a59-113">Type</span><span class="sxs-lookup"><span data-stu-id="94a59-113">Type</span></span>|<span data-ttu-id="94a59-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="94a59-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="94a59-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="94a59-115">Affected APIs</span></span>

<span data-ttu-id="94a59-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="94a59-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
