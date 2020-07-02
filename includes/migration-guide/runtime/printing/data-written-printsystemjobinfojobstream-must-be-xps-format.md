---
ms.openlocfilehash: a007022bf32ffe76861f6f9016a7edace17b0f61
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620045"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a><span data-ttu-id="8d228-101">Les données écrites dans PrintSystemJobInfo.JobStream doivent être au format XPS</span><span class="sxs-lookup"><span data-stu-id="8d228-101">Data written to PrintSystemJobInfo.JobStream must be in XPS format</span></span>

#### <a name="details"></a><span data-ttu-id="8d228-102">Détails</span><span class="sxs-lookup"><span data-stu-id="8d228-102">Details</span></span>

<span data-ttu-id="8d228-103">La propriété <xref:System.Printing.PrintSystemJobInfo.JobStream> expose le flux d’un travail d’impression.</span><span class="sxs-lookup"><span data-stu-id="8d228-103">The <xref:System.Printing.PrintSystemJobInfo.JobStream> property exposes the stream of a print job.</span></span> <span data-ttu-id="8d228-104">L’utilisateur peut envoyer des données brutes aux composants d’impression du système d’exploitation sous-jacent en écrivant dans ce flux. À compter de .NET Framework 4.5 sur Windows 8 et les versions ultérieures du système d’exploitation Windows, les données écrites dans ce flux doivent être au format XPS en tant que flux de package.</span><span class="sxs-lookup"><span data-stu-id="8d228-104">The user can send raw data to the underlying operating system printing components by writing to this stream.Starting with the .NET Framework 4.5 on Windows 8 and later versions of the Windows operating system, data written to this stream must be in XPS format as a package stream.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8d228-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="8d228-105">Suggestion</span></span>

<span data-ttu-id="8d228-106">Pour sortir le contenu d’impression, vous pouvez procéder de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="8d228-106">To output print content, you can do either of the following:</span></span><ul><li><span data-ttu-id="8d228-107">Utilisez la classe <xref:System.Windows.Xps.XpsDocumentWriter> pour sortir le contenu d’impression.</span><span class="sxs-lookup"><span data-stu-id="8d228-107">Use the <xref:System.Windows.Xps.XpsDocumentWriter> class to output print content.</span></span> <span data-ttu-id="8d228-108">Il s’agit de l’alternative recommandée.</span><span class="sxs-lookup"><span data-stu-id="8d228-108">This is the recommended alternative.</span></span></li><li><span data-ttu-id="8d228-109">Vérifiez que les données envoyées au flux retourné par la propriété <xref:System.Printing.PrintSystemJobInfo.JobStream> sont au format XPS en tant que flux de package.</span><span class="sxs-lookup"><span data-stu-id="8d228-109">Ensure that the data sent to the stream returned by the <xref:System.Printing.PrintSystemJobInfo.JobStream> property is in XPS format as a package stream.</span></span></li></ul>

| <span data-ttu-id="8d228-110">Nom</span><span class="sxs-lookup"><span data-stu-id="8d228-110">Name</span></span>    | <span data-ttu-id="8d228-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="8d228-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8d228-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="8d228-112">Scope</span></span>   |<span data-ttu-id="8d228-113">Secondaire</span><span class="sxs-lookup"><span data-stu-id="8d228-113">Minor</span></span>|
|<span data-ttu-id="8d228-114">Version</span><span class="sxs-lookup"><span data-stu-id="8d228-114">Version</span></span>|<span data-ttu-id="8d228-115">4,5</span><span class="sxs-lookup"><span data-stu-id="8d228-115">4.5</span></span>|
|<span data-ttu-id="8d228-116">Type</span><span class="sxs-lookup"><span data-stu-id="8d228-116">Type</span></span>|<span data-ttu-id="8d228-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="8d228-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8d228-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="8d228-118">Affected APIs</span></span>

-<xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|
