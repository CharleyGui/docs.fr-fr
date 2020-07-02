---
ms.openlocfilehash: 424e8ff704b888aa3d2c1254ac712da4034f59b8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616056"
---
### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a><span data-ttu-id="f9fb0-101">ObsoleteAttribute est exporté à la fois comme ObsoleteAttribute et comme DeprecatedAttribute dans les scénarios WinMD</span><span class="sxs-lookup"><span data-stu-id="f9fb0-101">ObsoleteAttribute exports as both ObsoleteAttribute and DeprecatedAttribute in WinMD scenarios</span></span>

#### <a name="details"></a><span data-ttu-id="f9fb0-102">Détails</span><span class="sxs-lookup"><span data-stu-id="f9fb0-102">Details</span></span>

<span data-ttu-id="f9fb0-103">Quand vous créez une bibliothèque de métadonnées Windows (fichier .winmd), l’attribut <xref:System.ObsoleteAttribute?displayProperty=fullName> est exporté à la fois comme <xref:System.ObsoleteAttribute?displayProperty=fullName> et comme [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).</span><span class="sxs-lookup"><span data-stu-id="f9fb0-103">When you create a Windows Metadata library (.winmd file), the <xref:System.ObsoleteAttribute?displayProperty=fullName> attribute is exported as both <xref:System.ObsoleteAttribute?displayProperty=fullName> and [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f9fb0-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="f9fb0-104">Suggestion</span></span>

<span data-ttu-id="f9fb0-105">La recompilation de code source existant qui utilise l’attribut <xref:System.ObsoleteAttribute?displayProperty=fullName> peut générer des avertissements quand ce code est consommé à partir de C++/CX ou de JavaScript. Nous déconseillons d’appliquer à la fois <xref:System.ObsoleteAttribute?displayProperty=fullName> et [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) au code d’assemblys managés, car cela peut produire des avertissements de génération.</span><span class="sxs-lookup"><span data-stu-id="f9fb0-105">Recompilation of existing source code that uses the <xref:System.ObsoleteAttribute?displayProperty=fullName> attribute may generate warnings when consuming that code from C++/CX or JavaScript.We do not recommend applying both <xref:System.ObsoleteAttribute?displayProperty=fullName> and [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) to code in managed assemblies; it may result in build warnings.</span></span>

| <span data-ttu-id="f9fb0-106">Nom</span><span class="sxs-lookup"><span data-stu-id="f9fb0-106">Name</span></span>    | <span data-ttu-id="f9fb0-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="f9fb0-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f9fb0-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="f9fb0-108">Scope</span></span>   | <span data-ttu-id="f9fb0-109">Edge</span><span class="sxs-lookup"><span data-stu-id="f9fb0-109">Edge</span></span>        |
| <span data-ttu-id="f9fb0-110">Version</span><span class="sxs-lookup"><span data-stu-id="f9fb0-110">Version</span></span> | <span data-ttu-id="f9fb0-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="f9fb0-111">4.5.1</span></span>       |
| <span data-ttu-id="f9fb0-112">Type</span><span class="sxs-lookup"><span data-stu-id="f9fb0-112">Type</span></span>    | <span data-ttu-id="f9fb0-113">Reciblage</span><span class="sxs-lookup"><span data-stu-id="f9fb0-113">Retargeting</span></span> |
