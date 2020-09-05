---
ms.openlocfilehash: e42bce91afab68e509cb35a8992fa3ca2f096872
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496154"
---
### <a name="wpf-printing-stack-update"></a><span data-ttu-id="086e4-101">Mise à jour de la pile d’impression WPF</span><span class="sxs-lookup"><span data-stu-id="086e4-101">WPF Printing Stack Update</span></span>

#### <a name="details"></a><span data-ttu-id="086e4-102">Détails</span><span class="sxs-lookup"><span data-stu-id="086e4-102">Details</span></span>

<span data-ttu-id="086e4-103">Les API d’impression de WPF utilisant <xref:System.Printing.PrintQueue?displayProperty=fullName> appellent l’API Print Document Package de Windows au lieu de l’API d’impression XPS, qui est maintenant dépréciée.</span><span class="sxs-lookup"><span data-stu-id="086e4-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=fullName> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="086e4-104">Le changement a été fait pour des raisons de maintenance : ni les utilisateurs ni les développeurs ne devraient voir de changements de comportement ou d’utilisation de l’API.</span><span class="sxs-lookup"><span data-stu-id="086e4-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="086e4-105">La nouvelle pile d’impression est activée par défaut lors de l’exécution dans Windows 10 Creators Update.</span><span class="sxs-lookup"><span data-stu-id="086e4-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="086e4-106">L’ancienne pile d’impression continue de fonctionner comme avant sur les versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="086e4-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="086e4-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="086e4-107">Suggestion</span></span>

<span data-ttu-id="086e4-108">Pour utiliser l’ancienne pile dans Windows 10 Creators Update, définissez la valeur REG_DWORD <code>UseXpsOMPrinting</code> de la clé de Registre <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> sur <code>1</code>.</span><span class="sxs-lookup"><span data-stu-id="086e4-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>

| <span data-ttu-id="086e4-109">Name</span><span class="sxs-lookup"><span data-stu-id="086e4-109">Name</span></span>    | <span data-ttu-id="086e4-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="086e4-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="086e4-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="086e4-111">Scope</span></span>   |<span data-ttu-id="086e4-112">Edge</span><span class="sxs-lookup"><span data-stu-id="086e4-112">Edge</span></span>|
|<span data-ttu-id="086e4-113">Version</span><span class="sxs-lookup"><span data-stu-id="086e4-113">Version</span></span>|<span data-ttu-id="086e4-114">4,7</span><span class="sxs-lookup"><span data-stu-id="086e4-114">4.7</span></span>|
|<span data-ttu-id="086e4-115">Type</span><span class="sxs-lookup"><span data-stu-id="086e4-115">Type</span></span>|<span data-ttu-id="086e4-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="086e4-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="086e4-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="086e4-117">Affected APIs</span></span>

<span data-ttu-id="086e4-118">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="086e4-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
