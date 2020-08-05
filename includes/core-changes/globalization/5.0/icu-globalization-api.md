---
ms.openlocfilehash: 74c3d3247912dcd638a9379d54e682967c5e400b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302705"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a><span data-ttu-id="6cd5a-101">Les API de globalisation utilisent des bibliothèques ICU sur Windows</span><span class="sxs-lookup"><span data-stu-id="6cd5a-101">Globalization APIs use ICU libraries on Windows</span></span>

<span data-ttu-id="6cd5a-102">.NET 5,0 et les versions ultérieures utilisent des bibliothèques [ICU (International Components for Unicode)](http://site.icu-project.org/home) pour la globalisation lorsqu’elles s’exécutent sur Windows 10 mai 2019 Update ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="6cd5a-102">.NET 5.0 and later versions use [International Components for Unicode (ICU)](http://site.icu-project.org/home) libraries for globalization functionality when running on Windows 10 May 2019 Update or later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6cd5a-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="6cd5a-103">Change description</span></span>

<span data-ttu-id="6cd5a-104">Auparavant, les bibliothèques .NET utilisaient des API [NLS (National Language Support)](/windows/win32/intl/national-language-support) pour la fonctionnalité de globalisation.</span><span class="sxs-lookup"><span data-stu-id="6cd5a-104">Previously, .NET libraries used [National Language Support (NLS)](/windows/win32/intl/national-language-support) APIs for globalization functionality.</span></span> <span data-ttu-id="6cd5a-105">Par exemple, les fonctions NLS ont été utilisées pour obtenir les données de culture, telles que les modèles de format de date et d’heure, de comparaison des chaînes et d’exécution de la casse des chaînes dans la culture appropriée.</span><span class="sxs-lookup"><span data-stu-id="6cd5a-105">For example, NLS functions were used to get culture data, such as date and time format patterns, compare strings, and perform string casing in the appropriate culture.</span></span>

<span data-ttu-id="6cd5a-106">À compter de .NET 5,0, si une application s’exécute sur Windows 10 mai 2019 Update ou version ultérieure, les bibliothèques .NET utilisent les API de globalisation [ICU](http://site.icu-project.org/home) .</span><span class="sxs-lookup"><span data-stu-id="6cd5a-106">Starting in .NET 5.0, if an app is running on Windows 10 May 2019 Update or later, .NET libraries use [ICU](http://site.icu-project.org/home) globalization APIs.</span></span> <span data-ttu-id="6cd5a-107">La mise à jour de Windows 10 mai 2019 et les versions ultérieures sont fournies avec la bibliothèque Native ICU.</span><span class="sxs-lookup"><span data-stu-id="6cd5a-107">Windows 10 May 2019 Update and later versions ship with the ICU native library.</span></span> <span data-ttu-id="6cd5a-108">Si le Runtime .NET ne peut pas charger ICU, il utilise NLS à la place.</span><span class="sxs-lookup"><span data-stu-id="6cd5a-108">If the .NET runtime can't load ICU, it uses NLS instead.</span></span>

<span data-ttu-id="6cd5a-109">Cette modification a été introduite pour deux raisons :</span><span class="sxs-lookup"><span data-stu-id="6cd5a-109">This change was introduced for two reasons:</span></span>

- <span data-ttu-id="6cd5a-110">Les applications ont le même comportement de globalisation entre les plateformes, notamment Linux, macOS et Windows.</span><span class="sxs-lookup"><span data-stu-id="6cd5a-110">Apps have the same globalization behavior across platforms, including Linux, macOS, and Windows.</span></span>
- <span data-ttu-id="6cd5a-111">Les applications peuvent contrôler le comportement de globalisation à l’aide de bibliothèques ICU personnalisées.</span><span class="sxs-lookup"><span data-stu-id="6cd5a-111">Apps can control globalization behavior by using custom ICU libraries.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6cd5a-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6cd5a-112">Version introduced</span></span>

<span data-ttu-id="6cd5a-113">.NET 5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="6cd5a-113">.NET 5.0 Preview 4</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6cd5a-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6cd5a-114">Recommended action</span></span>

<span data-ttu-id="6cd5a-115">Aucune action n’est requise de la part du développeur.</span><span class="sxs-lookup"><span data-stu-id="6cd5a-115">No action is required on the part of the developer.</span></span> <span data-ttu-id="6cd5a-116">Toutefois, si vous souhaitez continuer à utiliser les API de globalisation NLS, vous pouvez définir un [commutateur au moment](../../../../docs/core/run-time-config/globalization.md#nls) de l’exécution pour revenir à ce comportement.</span><span class="sxs-lookup"><span data-stu-id="6cd5a-116">However, if you wish to continue using NLS globalization APIs, you can set a [run-time switch](../../../../docs/core/run-time-config/globalization.md#nls) to revert to that behavior.</span></span> <span data-ttu-id="6cd5a-117">Pour plus d’informations sur les commutateurs disponibles, consultez l’article présentation de la [globalisation et de la bibliothèque .net](/dotnet/standard/globalization-localization/globalization-icu) .</span><span class="sxs-lookup"><span data-stu-id="6cd5a-117">For more information about the available switches, see the [.NET globalization and ICU](/dotnet/standard/globalization-localization/globalization-icu) article.</span></span>

#### <a name="category"></a><span data-ttu-id="6cd5a-118">Category</span><span class="sxs-lookup"><span data-stu-id="6cd5a-118">Category</span></span>

<span data-ttu-id="6cd5a-119">Globalisation</span><span class="sxs-lookup"><span data-stu-id="6cd5a-119">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6cd5a-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="6cd5a-120">Affected APIs</span></span>

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- <span data-ttu-id="6cd5a-121">La plupart des types dans l' <xref:System.Globalization?displayProperty=fullName> espace de noms</span><span class="sxs-lookup"><span data-stu-id="6cd5a-121">Most types in the <xref:System.Globalization?displayProperty=fullName> namespace</span></span>

<!--

#### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`

-->
