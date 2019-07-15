---
ms.openlocfilehash: 08c16f261338148619de2e484c73046b9d9a6bfe
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858446"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a><span data-ttu-id="c3691-101">.NET Framework 4.6 n’utilise pas une version 4.5.x.x lors de son inscription dans le Registre</span><span class="sxs-lookup"><span data-stu-id="c3691-101">The .NET Framework 4.6 does not use a 4.5.x.x version when registering itself in the registry</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c3691-102">Détails</span><span class="sxs-lookup"><span data-stu-id="c3691-102">Details</span></span>|<span data-ttu-id="c3691-103">Comme prévu, la clé de version définie dans le Registre (au niveau <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) pour .NET Framework 4.6 commence par 4.6 et non 4.5.</span><span class="sxs-lookup"><span data-stu-id="c3691-103">As one might expect, the version key set in the registry (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) for the .NET Framework 4.6 begins with '4.6', not '4.5'.</span></span> <span data-ttu-id="c3691-104">Les applications qui dépendent de ces clés de Registre pour savoir quelles versions du .NET Framework sont installées sur un ordinateur doivent être mises à jour afin de comprendre que 4.6 est une nouvelle version possible et qui est compatible avec les précédentes versions 4.5.x.</span><span class="sxs-lookup"><span data-stu-id="c3691-104">Apps that depend on these registry keys to know which .NET Framework versions are installed on a machine should be updated to understand that 4.6 is a new possible version, and one that is compatible with previous 4.5.x releases.</span></span>|
|<span data-ttu-id="c3691-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="c3691-105">Suggestion</span></span>|<span data-ttu-id="c3691-106">Mettez à jour les applications qui cherchent à découvrir une installation de .NET Framework 4.5 en recherchant les clés de Registre 4.5 pour accepter également 4.6.</span><span class="sxs-lookup"><span data-stu-id="c3691-106">Update apps probing for a .NET Framework 4.5 install by looking for 4.5 registry keys to also accept 4.6.</span></span>|
|<span data-ttu-id="c3691-107">Portée</span><span class="sxs-lookup"><span data-stu-id="c3691-107">Scope</span></span>|<span data-ttu-id="c3691-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="c3691-108">Edge</span></span>|
|<span data-ttu-id="c3691-109">Version</span><span class="sxs-lookup"><span data-stu-id="c3691-109">Version</span></span>|<span data-ttu-id="c3691-110">4.6</span><span class="sxs-lookup"><span data-stu-id="c3691-110">4.6</span></span>|
|<span data-ttu-id="c3691-111">Type</span><span class="sxs-lookup"><span data-stu-id="c3691-111">Type</span></span>|<span data-ttu-id="c3691-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="c3691-112">Runtime</span></span>|

