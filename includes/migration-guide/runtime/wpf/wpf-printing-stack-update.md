---
ms.openlocfilehash: e613f0c52c77efebf250f5935d5cbfc29bc09a6b
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802552"
---
### <a name="wpf-printing-stack-update"></a><span data-ttu-id="37462-101">Mise à jour de la pile d’impression WPF</span><span class="sxs-lookup"><span data-stu-id="37462-101">WPF Printing Stack Update</span></span>

|   |   |
|---|---|
|<span data-ttu-id="37462-102">Détails</span><span class="sxs-lookup"><span data-stu-id="37462-102">Details</span></span>|<span data-ttu-id="37462-103">Les API d’impression de WPF utilisant <xref:System.Printing.PrintQueue?displayProperty=name> appellent l’API Print Document Package de Windows au lieu de l’API d’impression XPS, qui est maintenant dépréciée.</span><span class="sxs-lookup"><span data-stu-id="37462-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=name> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="37462-104">Le changement a été fait pour des raisons de maintenance : ni les utilisateurs ni les développeurs ne devraient voir de changements de comportement ou d’utilisation de l’API.</span><span class="sxs-lookup"><span data-stu-id="37462-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="37462-105">La nouvelle pile d’impression est activée par défaut lors de l’exécution dans Windows 10 Creators Update.</span><span class="sxs-lookup"><span data-stu-id="37462-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="37462-106">L’ancienne pile d’impression continue de fonctionner comme avant sur les versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="37462-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>|
|<span data-ttu-id="37462-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="37462-107">Suggestion</span></span>|<span data-ttu-id="37462-108">Pour utiliser l’ancienne pile dans Windows 10 Creators Update, définissez la valeur REG_DWORD <code>UseXpsOMPrinting</code> de la clé de Registre <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> sur <code>1</code>.</span><span class="sxs-lookup"><span data-stu-id="37462-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>|
|<span data-ttu-id="37462-109">Portée</span><span class="sxs-lookup"><span data-stu-id="37462-109">Scope</span></span>|<span data-ttu-id="37462-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="37462-110">Edge</span></span>|
|<span data-ttu-id="37462-111">Version</span><span class="sxs-lookup"><span data-stu-id="37462-111">Version</span></span>|<span data-ttu-id="37462-112">4.7</span><span class="sxs-lookup"><span data-stu-id="37462-112">4.7</span></span>|
|<span data-ttu-id="37462-113">Type</span><span class="sxs-lookup"><span data-stu-id="37462-113">Type</span></span>|<span data-ttu-id="37462-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="37462-114">Runtime</span></span>|

