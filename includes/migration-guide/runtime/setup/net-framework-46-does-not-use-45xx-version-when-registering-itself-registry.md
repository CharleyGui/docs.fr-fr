---
ms.openlocfilehash: 09fb7a54fccd5cf37800483c64e2fa6a54681f11
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621324"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a><span data-ttu-id="f333b-101">.NET Framework 4.6 n’utilise pas une version 4.5.x.x lors de son inscription dans le Registre</span><span class="sxs-lookup"><span data-stu-id="f333b-101">The .NET Framework 4.6 does not use a 4.5.x.x version when registering itself in the registry</span></span>

#### <a name="details"></a><span data-ttu-id="f333b-102">Détails</span><span class="sxs-lookup"><span data-stu-id="f333b-102">Details</span></span>

<span data-ttu-id="f333b-103">Comme prévu, la clé de version définie dans le Registre (au niveau <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) pour .NET Framework 4.6 commence par 4.6 et non 4.5.</span><span class="sxs-lookup"><span data-stu-id="f333b-103">As one might expect, the version key set in the registry (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) for the .NET Framework 4.6 begins with '4.6', not '4.5'.</span></span> <span data-ttu-id="f333b-104">Les applications qui dépendent de ces clés de Registre pour savoir quelles versions du .NET Framework sont installées sur un ordinateur doivent être mises à jour afin de comprendre que 4.6 est une nouvelle version possible et qui est compatible avec les précédentes versions 4.5.x.</span><span class="sxs-lookup"><span data-stu-id="f333b-104">Apps that depend on these registry keys to know which .NET Framework versions are installed on a machine should be updated to understand that 4.6 is a new possible version, and one that is compatible with previous 4.5.x releases.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f333b-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="f333b-105">Suggestion</span></span>

<span data-ttu-id="f333b-106">Mettez à jour les applications qui cherchent à découvrir une installation de .NET Framework 4.5 en recherchant les clés de Registre 4.5 pour accepter également 4.6.</span><span class="sxs-lookup"><span data-stu-id="f333b-106">Update apps probing for a .NET Framework 4.5 install by looking for 4.5 registry keys to also accept 4.6.</span></span>

| <span data-ttu-id="f333b-107">Nom</span><span class="sxs-lookup"><span data-stu-id="f333b-107">Name</span></span>    | <span data-ttu-id="f333b-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="f333b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f333b-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="f333b-109">Scope</span></span>   |<span data-ttu-id="f333b-110">Edge</span><span class="sxs-lookup"><span data-stu-id="f333b-110">Edge</span></span>|
|<span data-ttu-id="f333b-111">Version</span><span class="sxs-lookup"><span data-stu-id="f333b-111">Version</span></span>|<span data-ttu-id="f333b-112">4.6</span><span class="sxs-lookup"><span data-stu-id="f333b-112">4.6</span></span>|
|<span data-ttu-id="f333b-113">Type</span><span class="sxs-lookup"><span data-stu-id="f333b-113">Type</span></span>|<span data-ttu-id="f333b-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="f333b-114">Runtime</span></span>|
