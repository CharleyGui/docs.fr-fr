---
ms.openlocfilehash: 9d09f598538b9d5ee3f995d6281b8eb4b2668050
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802559"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="3968c-101">ObjectDisposedException levée par le vérificateur orthographique de WPF</span><span class="sxs-lookup"><span data-stu-id="3968c-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3968c-102">Détails</span><span class="sxs-lookup"><span data-stu-id="3968c-102">Details</span></span>|<span data-ttu-id="3968c-103">Les applications WPF plantent parfois lors de l’arrêt de l’application avec une <xref:System.ObjectDisposedException?displayProperty=name> levée par le vérificateur orthographique.</span><span class="sxs-lookup"><span data-stu-id="3968c-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=name> thrown by the spellchecker.</span></span> <span data-ttu-id="3968c-104">Ce problème est résolu dans .NET Framework 4.7 WPF via une gestion différente de l’exception, qui permet aux applications de ne plus en être affectée de cette façon.</span><span class="sxs-lookup"><span data-stu-id="3968c-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="3968c-105">Notez que des exceptions occasionnelles continuent d’être observées dans les applications s’exécutant sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="3968c-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>|
|<span data-ttu-id="3968c-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="3968c-106">Suggestion</span></span>|<span data-ttu-id="3968c-107">Mettre à niveau vers .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="3968c-107">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="3968c-108">Portée</span><span class="sxs-lookup"><span data-stu-id="3968c-108">Scope</span></span>|<span data-ttu-id="3968c-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="3968c-109">Edge</span></span>|
|<span data-ttu-id="3968c-110">Version</span><span class="sxs-lookup"><span data-stu-id="3968c-110">Version</span></span>|<span data-ttu-id="3968c-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="3968c-111">4.6.1</span></span>|
|<span data-ttu-id="3968c-112">Type</span><span class="sxs-lookup"><span data-stu-id="3968c-112">Type</span></span>|<span data-ttu-id="3968c-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="3968c-113">Runtime</span></span>|

