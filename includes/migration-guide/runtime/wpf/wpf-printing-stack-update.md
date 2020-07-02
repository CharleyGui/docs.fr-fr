---
ms.openlocfilehash: 5e2e8d1ec5d698d1c1649c2a0a1b4b77dbdf4022
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621276"
---
### <a name="wpf-printing-stack-update"></a><span data-ttu-id="7dbc8-101">Mise à jour de la pile d’impression WPF</span><span class="sxs-lookup"><span data-stu-id="7dbc8-101">WPF Printing Stack Update</span></span>

#### <a name="details"></a><span data-ttu-id="7dbc8-102">Détails</span><span class="sxs-lookup"><span data-stu-id="7dbc8-102">Details</span></span>

<span data-ttu-id="7dbc8-103">Les API d’impression de WPF utilisant <xref:System.Printing.PrintQueue?displayProperty=fullName> appellent l’API Print Document Package de Windows au lieu de l’API d’impression XPS, qui est maintenant dépréciée.</span><span class="sxs-lookup"><span data-stu-id="7dbc8-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=fullName> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="7dbc8-104">Le changement a été fait pour des raisons de maintenance : ni les utilisateurs ni les développeurs ne devraient voir de changements de comportement ou d’utilisation de l’API.</span><span class="sxs-lookup"><span data-stu-id="7dbc8-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="7dbc8-105">La nouvelle pile d’impression est activée par défaut lors de l’exécution dans Windows 10 Creators Update.</span><span class="sxs-lookup"><span data-stu-id="7dbc8-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="7dbc8-106">L’ancienne pile d’impression continue de fonctionner comme avant sur les versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="7dbc8-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7dbc8-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="7dbc8-107">Suggestion</span></span>

<span data-ttu-id="7dbc8-108">Pour utiliser l’ancienne pile dans Windows 10 Creators Update, définissez la valeur REG_DWORD <code>UseXpsOMPrinting</code> de la clé de Registre <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> sur <code>1</code>.</span><span class="sxs-lookup"><span data-stu-id="7dbc8-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>

| <span data-ttu-id="7dbc8-109">Nom</span><span class="sxs-lookup"><span data-stu-id="7dbc8-109">Name</span></span>    | <span data-ttu-id="7dbc8-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="7dbc8-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7dbc8-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="7dbc8-111">Scope</span></span>   |<span data-ttu-id="7dbc8-112">Edge</span><span class="sxs-lookup"><span data-stu-id="7dbc8-112">Edge</span></span>|
|<span data-ttu-id="7dbc8-113">Version</span><span class="sxs-lookup"><span data-stu-id="7dbc8-113">Version</span></span>|<span data-ttu-id="7dbc8-114">4,7</span><span class="sxs-lookup"><span data-stu-id="7dbc8-114">4.7</span></span>|
|<span data-ttu-id="7dbc8-115">Type</span><span class="sxs-lookup"><span data-stu-id="7dbc8-115">Type</span></span>|<span data-ttu-id="7dbc8-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="7dbc8-116">Runtime</span></span>|
