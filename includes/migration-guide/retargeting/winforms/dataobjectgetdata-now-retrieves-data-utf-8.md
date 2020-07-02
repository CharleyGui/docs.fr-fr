---
ms.openlocfilehash: 3f330d5e601d599231ef0336b785e677fe1d114e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616051"
---
### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a><span data-ttu-id="d1e6d-101">DataObject.GetData récupère maintenant les données au format UTF-8</span><span class="sxs-lookup"><span data-stu-id="d1e6d-101">DataObject.GetData now retrieves data as UTF-8</span></span>

#### <a name="details"></a><span data-ttu-id="d1e6d-102">Détails</span><span class="sxs-lookup"><span data-stu-id="d1e6d-102">Details</span></span>

<span data-ttu-id="d1e6d-103">Pour les applications qui ciblent le .NET Framework 4 ou qui s’exécutent sur le .NET Framework 4.5.1 ou versions antérieures, `DataObject.GetData` récupère les données au format HTML sous forme de chaîne ASCII.</span><span class="sxs-lookup"><span data-stu-id="d1e6d-103">For apps that target the .NET Framework 4 or that run on the .NET Framework 4.5.1 or earlier versions, `DataObject.GetData` retrieves HTML-formatted data as an ASCII string.</span></span> <span data-ttu-id="d1e6d-104">Ainsi, les caractères non-ASCII (caractères dont les codes ASCII sont supérieurs à 0x7F) sont représentés par deux caractères aléatoires.</span><span class="sxs-lookup"><span data-stu-id="d1e6d-104">As a result, non-ASCII characters (characters whose ASCII codes are greater than 0x7F) are represented by two random characters.</span></span><p/><span data-ttu-id="d1e6d-105">Pour les applications qui ciblent le .NET Framework 4.5 ou version ultérieure et qui s’exécutent sur le .NET Framework 4.5.2, `DataObject.GetData` récupère les données au format HTML sous la forme de données UTF-8, qui représentent correctement les caractères supérieurs à 0x7F.</span><span class="sxs-lookup"><span data-stu-id="d1e6d-105">For apps that target the .NET Framework 4.5 or later and run on the .NET Framework 4.5.2, `DataObject.GetData` retrieves HTML-formatted data as UTF-8, which represents characters greater than 0x7F correctly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d1e6d-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="d1e6d-106">Suggestion</span></span>

<span data-ttu-id="d1e6d-107">Si vous avez implémenté une solution de contournement pour ce problème d’encodage des chaînes au format HTML (par exemple, en encodant explicitement la chaîne HTML récupérée à partir du Presse-papiers en la passant à <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>) et que vous reciblez votre application de la version 4 à la version 4.5, cette solution doit être supprimée. Si l’ancien comportement est nécessaire, l’application peut cibler le .NET Framework 4.0 pour l’obtenir.</span><span class="sxs-lookup"><span data-stu-id="d1e6d-107">If you implemented a workaround for the encoding problem with HTML-formatted strings (for example, by explicitly encoding the HTML string retrieved from the Clipboard by passing it to <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>) and you're retargeting your app from version 4 to 4.5, that workaround should be removed.If the old behavior is needed for some reason, the app can target the .NET Framework 4.0 to get that behavior.</span></span>

| <span data-ttu-id="d1e6d-108">Nom</span><span class="sxs-lookup"><span data-stu-id="d1e6d-108">Name</span></span>    | <span data-ttu-id="d1e6d-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="d1e6d-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d1e6d-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="d1e6d-110">Scope</span></span>   | <span data-ttu-id="d1e6d-111">Edge</span><span class="sxs-lookup"><span data-stu-id="d1e6d-111">Edge</span></span>        |
| <span data-ttu-id="d1e6d-112">Version</span><span class="sxs-lookup"><span data-stu-id="d1e6d-112">Version</span></span> | <span data-ttu-id="d1e6d-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="d1e6d-113">4.5.2</span></span>       |
| <span data-ttu-id="d1e6d-114">Type</span><span class="sxs-lookup"><span data-stu-id="d1e6d-114">Type</span></span>    | <span data-ttu-id="d1e6d-115">Reciblage</span><span class="sxs-lookup"><span data-stu-id="d1e6d-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="d1e6d-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="d1e6d-116">Affected APIs</span></span>

- <xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType>
