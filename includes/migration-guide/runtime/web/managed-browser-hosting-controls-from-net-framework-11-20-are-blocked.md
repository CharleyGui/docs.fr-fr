---
ms.openlocfilehash: 26539011f0650c7a3bac9e1c41847561905fff58
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497229"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a><span data-ttu-id="4d2c0-101">Les navigateurs managés hébergeant des contrôles de .NET Framework 1.1 et 2.0 sont bloqués</span><span class="sxs-lookup"><span data-stu-id="4d2c0-101">Managed browser hosting controls from the .NET Framework 1.1 and 2.0 are blocked</span></span>

#### <a name="details"></a><span data-ttu-id="4d2c0-102">Détails</span><span class="sxs-lookup"><span data-stu-id="4d2c0-102">Details</span></span>

<span data-ttu-id="4d2c0-103">L'hébergement de ces contrôles est bloqué dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="4d2c0-103">Hosting these controls is blocked in Internet Explorer.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4d2c0-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="4d2c0-104">Suggestion</span></span>

<span data-ttu-id="4d2c0-105">Internet Explorer ne démarrera pas les applications qui utilisent des contrôles d'hébergement de navigateur géré.</span><span class="sxs-lookup"><span data-stu-id="4d2c0-105">Internet Explorer will fail to launch an application that uses managed browser hosting controls.</span></span> <span data-ttu-id="4d2c0-106">Le comportement précédent peut être restauré en définissant la valeur de EnableIEHosting de la sous-clé de Registre <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> sur <code>1</code> pour les systèmes x86 et pour les processus 32 bits sur les systèmes x64, et définissant la valeur <code>EnableIEHosting</code> de la sous-clé de Registre <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> sur <code>1</code> pour les processus 64 bits sur les systèmes x64.</span><span class="sxs-lookup"><span data-stu-id="4d2c0-106">The previous behavior can be restored by setting the EnableIEHosting value of the registry subkey <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> to <code>1</code> for x86 systems and for 32-bit processes on x64 systems, and by setting the <code>EnableIEHosting</code> value of the registry subkey <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> to <code>1</code> for 64-bit processes on x64 systems.</span></span>

| <span data-ttu-id="4d2c0-107">Name</span><span class="sxs-lookup"><span data-stu-id="4d2c0-107">Name</span></span>    | <span data-ttu-id="4d2c0-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="4d2c0-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4d2c0-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="4d2c0-109">Scope</span></span>   |<span data-ttu-id="4d2c0-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="4d2c0-110">Minor</span></span>|
|<span data-ttu-id="4d2c0-111">Version</span><span class="sxs-lookup"><span data-stu-id="4d2c0-111">Version</span></span>|<span data-ttu-id="4d2c0-112">4,5</span><span class="sxs-lookup"><span data-stu-id="4d2c0-112">4.5</span></span>|
|<span data-ttu-id="4d2c0-113">Type</span><span class="sxs-lookup"><span data-stu-id="4d2c0-113">Type</span></span>|<span data-ttu-id="4d2c0-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="4d2c0-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="4d2c0-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="4d2c0-115">Affected APIs</span></span>

<span data-ttu-id="4d2c0-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="4d2c0-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
