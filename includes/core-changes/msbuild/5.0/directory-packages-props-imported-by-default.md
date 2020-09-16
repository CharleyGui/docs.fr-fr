---
ms.openlocfilehash: 4a916a4178535763712ebd58fde1a81e456da0d1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538815"
---
### <a name="directorypackagesprops-files-is-imported-by-default"></a><span data-ttu-id="d34f9-101">Les fichiers Directory. Packages. props sont importés par défaut</span><span class="sxs-lookup"><span data-stu-id="d34f9-101">Directory.Packages.props files is imported by default</span></span>

<span data-ttu-id="d34f9-102">Les fichiers *. props* de NuGet importent automatiquement un fichier nommé *Directory. Packages. props* s’il se trouve dans le dossier du projet ou dans l’un de ses ancêtres.</span><span class="sxs-lookup"><span data-stu-id="d34f9-102">NuGet's *.props* files automatically import a file named *Directory.Packages.props* if it's found in the project folder or any of its ancestors.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d34f9-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d34f9-103">Version introduced</span></span>

<span data-ttu-id="d34f9-104">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="d34f9-104">5.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="d34f9-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="d34f9-105">Change description</span></span>

<span data-ttu-id="d34f9-106">Dans les versions précédentes de .NET, vous pouviez avoir un fichier nommé *Directory. Packages. props* dans votre fichier projet et il ne sera pas automatiquement importé par le fichier *. props* de NuGet au moment de la génération.</span><span class="sxs-lookup"><span data-stu-id="d34f9-106">In previous .NET versions, you could have a file named *Directory.Packages.props* in your project file and it wouldn't be automatically imported by NuGet's *.props* file at build time.</span></span>

<span data-ttu-id="d34f9-107">À compter de .NET 5,0, un tel fichier *est* importé automatiquement s’il existe dans le dossier du projet ou dans l’un de ses ancêtres.</span><span class="sxs-lookup"><span data-stu-id="d34f9-107">Starting in .NET 5.0, such a file *is* automatically imported if it exists in the project folder or any of its ancestors.</span></span> <span data-ttu-id="d34f9-108">Si vous avez un fichier portant ce nom dans le dossier de votre projet, cette importation automatique peut modifier le comportement de la Build.</span><span class="sxs-lookup"><span data-stu-id="d34f9-108">If you have a file with this name in your project folder, this automatic import could change behavior of the build.</span></span> <span data-ttu-id="d34f9-109">Par exemple, le fichier est importé, mais il n’a pas été précédemment, ou l’ordre de son importation peut changer si vous l’importez spécifiquement.</span><span class="sxs-lookup"><span data-stu-id="d34f9-109">For example, the file will be imported but it wasn't before, or the order of when it's imported could change if you specifically import it.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d34f9-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="d34f9-110">Reason for change</span></span>

<span data-ttu-id="d34f9-111">Cette modification a été apportée afin de prendre en charge le contrôle de [version de package central](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) pour NuGet.</span><span class="sxs-lookup"><span data-stu-id="d34f9-111">This change was made in order to support [central package versioning](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) for NuGet.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d34f9-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d34f9-112">Recommended action</span></span>

<span data-ttu-id="d34f9-113">Renommez le fichier *Directory. Packages. props* existant s’il ne doit pas être importé automatiquement.</span><span class="sxs-lookup"><span data-stu-id="d34f9-113">Rename the existing *Directory.Packages.props* file if it should not be imported automatically.</span></span>

#### <a name="category"></a><span data-ttu-id="d34f9-114">Category</span><span class="sxs-lookup"><span data-stu-id="d34f9-114">Category</span></span>

<span data-ttu-id="d34f9-115">MSBuild</span><span class="sxs-lookup"><span data-stu-id="d34f9-115">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d34f9-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="d34f9-116">Affected APIs</span></span>

<span data-ttu-id="d34f9-117">N/A</span><span class="sxs-lookup"><span data-stu-id="d34f9-117">N/A</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
