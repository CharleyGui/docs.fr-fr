---
ms.openlocfilehash: 83d3f24680531d1e447f047151a28c98ce0da04b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620070"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a><span data-ttu-id="24e36-101">Les navigateurs managés hébergeant des contrôles de .NET Framework 1.1 et 2.0 sont bloqués</span><span class="sxs-lookup"><span data-stu-id="24e36-101">Managed browser hosting controls from the .NET Framework 1.1 and 2.0 are blocked</span></span>

#### <a name="details"></a><span data-ttu-id="24e36-102">Détails</span><span class="sxs-lookup"><span data-stu-id="24e36-102">Details</span></span>

<span data-ttu-id="24e36-103">L'hébergement de ces contrôles est bloqué dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="24e36-103">Hosting these controls is blocked in Internet Explorer.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="24e36-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="24e36-104">Suggestion</span></span>

<span data-ttu-id="24e36-105">Internet Explorer ne démarrera pas les applications qui utilisent des contrôles d'hébergement de navigateur géré.</span><span class="sxs-lookup"><span data-stu-id="24e36-105">Internet Explorer will fail to launch an application that uses managed browser hosting controls.</span></span> <span data-ttu-id="24e36-106">Le comportement précédent peut être restauré en définissant la valeur de EnableIEHosting de la sous-clé de Registre <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> sur <code>1</code> pour les systèmes x86 et pour les processus 32 bits sur les systèmes x64, et définissant la valeur <code>EnableIEHosting</code> de la sous-clé de Registre <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> sur <code>1</code> pour les processus 64 bits sur les systèmes x64.</span><span class="sxs-lookup"><span data-stu-id="24e36-106">The previous behavior can be restored by setting the EnableIEHosting value of the registry subkey <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> to <code>1</code> for x86 systems and for 32-bit processes on x64 systems, and by setting the <code>EnableIEHosting</code> value of the registry subkey <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> to <code>1</code> for 64-bit processes on x64 systems.</span></span>

| <span data-ttu-id="24e36-107">Nom</span><span class="sxs-lookup"><span data-stu-id="24e36-107">Name</span></span>    | <span data-ttu-id="24e36-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="24e36-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="24e36-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="24e36-109">Scope</span></span>   |<span data-ttu-id="24e36-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="24e36-110">Minor</span></span>|
|<span data-ttu-id="24e36-111">Version</span><span class="sxs-lookup"><span data-stu-id="24e36-111">Version</span></span>|<span data-ttu-id="24e36-112">4,5</span><span class="sxs-lookup"><span data-stu-id="24e36-112">4.5</span></span>|
|<span data-ttu-id="24e36-113">Type</span><span class="sxs-lookup"><span data-stu-id="24e36-113">Type</span></span>|<span data-ttu-id="24e36-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="24e36-114">Runtime</span></span>|
