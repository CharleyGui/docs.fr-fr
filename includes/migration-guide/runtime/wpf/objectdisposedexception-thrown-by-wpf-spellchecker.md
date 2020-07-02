---
ms.openlocfilehash: b836b26f3f52e9d0cc78feb764629bd2fa306657
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621791"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="c5d79-101">ObjectDisposedException levée par le vérificateur orthographique de WPF</span><span class="sxs-lookup"><span data-stu-id="c5d79-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

#### <a name="details"></a><span data-ttu-id="c5d79-102">Détails</span><span class="sxs-lookup"><span data-stu-id="c5d79-102">Details</span></span>

<span data-ttu-id="c5d79-103">Les applications WPF plantent parfois lors de l’arrêt de l’application avec une <xref:System.ObjectDisposedException?displayProperty=fullName> levée par le vérificateur orthographique.</span><span class="sxs-lookup"><span data-stu-id="c5d79-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=fullName> thrown by the spellchecker.</span></span> <span data-ttu-id="c5d79-104">Ce problème est résolu dans .NET Framework 4.7 WPF via une gestion différente de l’exception, qui permet aux applications de ne plus en être affectée de cette façon.</span><span class="sxs-lookup"><span data-stu-id="c5d79-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="c5d79-105">Notez que des exceptions occasionnelles continuent d’être observées dans les applications s’exécutant sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="c5d79-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c5d79-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="c5d79-106">Suggestion</span></span>

<span data-ttu-id="c5d79-107">Mettre à niveau vers .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="c5d79-107">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="c5d79-108">Nom</span><span class="sxs-lookup"><span data-stu-id="c5d79-108">Name</span></span>    | <span data-ttu-id="c5d79-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="c5d79-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c5d79-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="c5d79-110">Scope</span></span>   |<span data-ttu-id="c5d79-111">Edge</span><span class="sxs-lookup"><span data-stu-id="c5d79-111">Edge</span></span>|
|<span data-ttu-id="c5d79-112">Version</span><span class="sxs-lookup"><span data-stu-id="c5d79-112">Version</span></span>|<span data-ttu-id="c5d79-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="c5d79-113">4.6.1</span></span>|
|<span data-ttu-id="c5d79-114">Type</span><span class="sxs-lookup"><span data-stu-id="c5d79-114">Type</span></span>|<span data-ttu-id="c5d79-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="c5d79-115">Runtime</span></span>|
