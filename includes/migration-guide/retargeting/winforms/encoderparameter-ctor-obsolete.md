---
ms.openlocfilehash: 4ad7c4c2781480c08ad4cf27e40de445b1c50671
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617241"
---
### <a name="encoderparameter-ctor-is-obsolete"></a><span data-ttu-id="7ee00-101">Le constructeur EncoderParameter est obsolète</span><span class="sxs-lookup"><span data-stu-id="7ee00-101">EncoderParameter ctor is obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="7ee00-102">Détails</span><span class="sxs-lookup"><span data-stu-id="7ee00-102">Details</span></span>

<span data-ttu-id="7ee00-103">Le constructeur <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> est désormais obsolète et génère des avertissements quand il est utilisé.</span><span class="sxs-lookup"><span data-stu-id="7ee00-103">The <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> constructor is obsolete now and will introduce build warnings if used.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7ee00-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="7ee00-104">Suggestion</span></span>

<span data-ttu-id="7ee00-105">Même si le constructeur <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> continue de fonctionner, le constructeur suivant doit être utilisé à sa place pour éviter l’avertissement de génération indiquant qu’il est obsolète durant la recompilation du code avec les outils .NET Framework 4.5 : <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span><span class="sxs-lookup"><span data-stu-id="7ee00-105">Although the <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>constructor will continue to work, the following constructor should be used instead to avoid the obsolete build warning when re-compiling code with .NET Framework  4.5 tools: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span></span>

| <span data-ttu-id="7ee00-106">Nom</span><span class="sxs-lookup"><span data-stu-id="7ee00-106">Name</span></span>    | <span data-ttu-id="7ee00-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="7ee00-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7ee00-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="7ee00-108">Scope</span></span>   | <span data-ttu-id="7ee00-109">Secondaire</span><span class="sxs-lookup"><span data-stu-id="7ee00-109">Minor</span></span>       |
| <span data-ttu-id="7ee00-110">Version</span><span class="sxs-lookup"><span data-stu-id="7ee00-110">Version</span></span> | <span data-ttu-id="7ee00-111">4,5</span><span class="sxs-lookup"><span data-stu-id="7ee00-111">4.5</span></span>         |
| <span data-ttu-id="7ee00-112">Type</span><span class="sxs-lookup"><span data-stu-id="7ee00-112">Type</span></span>    | <span data-ttu-id="7ee00-113">Reciblage</span><span class="sxs-lookup"><span data-stu-id="7ee00-113">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="7ee00-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="7ee00-114">Affected APIs</span></span>

- <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>
