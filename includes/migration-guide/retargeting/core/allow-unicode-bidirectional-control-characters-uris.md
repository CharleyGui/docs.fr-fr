---
ms.openlocfilehash: 53d74db1a77e62cc64250658281fd3e4706fe494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614427"
---
### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a><span data-ttu-id="e608d-101">Autoriser les caractères de contrôle bidirectionnels Unicode dans les URI</span><span class="sxs-lookup"><span data-stu-id="e608d-101">Allow Unicode Bidirectional Control Characters in URIs</span></span>

#### <a name="details"></a><span data-ttu-id="e608d-102">Détails</span><span class="sxs-lookup"><span data-stu-id="e608d-102">Details</span></span>

<span data-ttu-id="e608d-103">Unicode spécifie plusieurs caractères de contrôle spéciaux utilisés pour définir l’orientation du texte.</span><span class="sxs-lookup"><span data-stu-id="e608d-103">Unicode specifies several special control characters used to specify the orientation of text.</span></span> <span data-ttu-id="e608d-104">Dans les versions précédentes du .NET Framework, ces caractères n’étaient pas correctement supprimés de tous les URI, même s’ils étaient encodés en pourcentage.</span><span class="sxs-lookup"><span data-stu-id="e608d-104">In previous versions of the .NET Framework, these characters were incorrectly stripped from all URIs even if they were present in their percent-encoded form.</span></span> <span data-ttu-id="e608d-105">Pour mieux suivre la spécification [RFC 3987](https://tools.ietf.org/html/rfc3987), nous autorisons désormais ces caractères dans les URI.</span><span class="sxs-lookup"><span data-stu-id="e608d-105">In order to better follow [RFC 3987](https://tools.ietf.org/html/rfc3987), we now allow these characters in URIs.</span></span> <span data-ttu-id="e608d-106">Si une URI en contient qui ne sont pas encodés, ils sont encodés en pourcentage.</span><span class="sxs-lookup"><span data-stu-id="e608d-106">When found unencoded in a URI, they are percent-encoded.</span></span> <span data-ttu-id="e608d-107">Si elle en contient qui sont encodés en pourcentage, ils sont laissés tels quels.</span><span class="sxs-lookup"><span data-stu-id="e608d-107">When found percent-encoded they are left as-is.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e608d-108">Suggestion</span><span class="sxs-lookup"><span data-stu-id="e608d-108">Suggestion</span></span>

<span data-ttu-id="e608d-109">Pour les applications qui ciblent des versions du .NET Framework à partir de la version 4.7.2, la prise en charge des caractères bidirectionnels Unicode est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="e608d-109">For applications that target versions of .NET Framework starting with 4.7.2, support for Unicode bidirectional characters is enabled by default.</span></span> <span data-ttu-id="e608d-110">Si ce changement n’est pas souhaitable, vous pouvez le désactiver en ajoutant le commutateur [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant à la section `<runtime>` du fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="e608d-110">If this change is undesirable, you can disable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true" />
</runtime>
```

<span data-ttu-id="e608d-111">Pour les applications qui ciblent des versions antérieures du .NET Framework, mais qui s’exécutent sur .NET Framework versions 4.7.2 et ultérieures, la prise en charge des caractères bidirectionnels Unicode est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="e608d-111">For applications that target earlier versions of the .NET Framework but are running under versions starting with .NET Framework 4.7.2, support for Unicode bidirectional characters is disabled by default.</span></span> <span data-ttu-id="e608d-112">Vous pouvez l’activer en ajoutant le commutateur [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant à la section `<runtime>` du fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="e608d-112">You can enable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file::</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false" />
</runtime>
```

| <span data-ttu-id="e608d-113">Nom</span><span class="sxs-lookup"><span data-stu-id="e608d-113">Name</span></span>    | <span data-ttu-id="e608d-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="e608d-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e608d-115">Étendue</span><span class="sxs-lookup"><span data-stu-id="e608d-115">Scope</span></span>   | <span data-ttu-id="e608d-116">Secondaire</span><span class="sxs-lookup"><span data-stu-id="e608d-116">Minor</span></span>       |
| <span data-ttu-id="e608d-117">Version</span><span class="sxs-lookup"><span data-stu-id="e608d-117">Version</span></span> | <span data-ttu-id="e608d-118">4.7.2</span><span class="sxs-lookup"><span data-stu-id="e608d-118">4.7.2</span></span>       |
| <span data-ttu-id="e608d-119">Type</span><span class="sxs-lookup"><span data-stu-id="e608d-119">Type</span></span>    | <span data-ttu-id="e608d-120">Reciblage</span><span class="sxs-lookup"><span data-stu-id="e608d-120">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="e608d-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="e608d-121">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
