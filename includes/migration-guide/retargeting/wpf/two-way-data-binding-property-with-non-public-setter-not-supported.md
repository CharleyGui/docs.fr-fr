---
ms.openlocfilehash: 5f1a8af37a305ab0904801002dd99e17e8eca62e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616057"
---
### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a><span data-ttu-id="31e50-101">La liaison de données bidirectionnelle avec une propriété ayant un accesseur Set non public n’est pas prise en charge</span><span class="sxs-lookup"><span data-stu-id="31e50-101">Two-way data-binding to a property with a non-public setter is not supported</span></span>

#### <a name="details"></a><span data-ttu-id="31e50-102">Détails</span><span class="sxs-lookup"><span data-stu-id="31e50-102">Details</span></span>

<span data-ttu-id="31e50-103">La liaison de données avec une propriété sans accesseur Set public n’a jamais été prise en charge.</span><span class="sxs-lookup"><span data-stu-id="31e50-103">Attempting to data bind to a property without a public setter has never been a supported scenario.</span></span> <span data-ttu-id="31e50-104">À compter de .NET Framework 4.5.1, ce scénario lève une exception <xref:System.InvalidOperationException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="31e50-104">Beginning in the .NET Framework 4.5.1, this scenario will throw an <xref:System.InvalidOperationException?displayProperty=fullName>.</span></span> <span data-ttu-id="31e50-105">Notez que cette nouvelle exception sera levée uniquement pour les applications qui ciblent spécifiquement le .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="31e50-105">Note that this new exception will only be thrown for apps that specifically target the .NET Framework 4.5.1.</span></span> <span data-ttu-id="31e50-106">Si une application cible le .NET Framework 4.5, l’appel sera autorisé.</span><span class="sxs-lookup"><span data-stu-id="31e50-106">If an app targets the .NET Framework 4.5, the call will be allowed.</span></span> <span data-ttu-id="31e50-107">Si l’application ne cible pas une version particulière du .NET Framework, la liaison sera traitée comme étant unidirectionnelle.</span><span class="sxs-lookup"><span data-stu-id="31e50-107">If the app does not target a particular .NET Framework version, the binding will be treated as one-way.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="31e50-108">Suggestion</span><span class="sxs-lookup"><span data-stu-id="31e50-108">Suggestion</span></span>

<span data-ttu-id="31e50-109">L’application doit être mise à jour pour utiliser une liaison unidirectionnelle ou exposer publiquement l’accesseur Set de la propriété.</span><span class="sxs-lookup"><span data-stu-id="31e50-109">The app should be updated to either use one-way binding, or expose the property's setter publicly.</span></span> <span data-ttu-id="31e50-110">Vous pouvez également cibler le .NET Framework 4.5 pour obtenir l’ancien comportement de l’application.</span><span class="sxs-lookup"><span data-stu-id="31e50-110">Alternatively, targeting the .NET Framework 4.5 will cause the app to exhibit the old behavior.</span></span>

| <span data-ttu-id="31e50-111">Nom</span><span class="sxs-lookup"><span data-stu-id="31e50-111">Name</span></span>    | <span data-ttu-id="31e50-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="31e50-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="31e50-113">Étendue</span><span class="sxs-lookup"><span data-stu-id="31e50-113">Scope</span></span>   | <span data-ttu-id="31e50-114">Secondaire</span><span class="sxs-lookup"><span data-stu-id="31e50-114">Minor</span></span>       |
| <span data-ttu-id="31e50-115">Version</span><span class="sxs-lookup"><span data-stu-id="31e50-115">Version</span></span> | <span data-ttu-id="31e50-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="31e50-116">4.5.1</span></span>       |
| <span data-ttu-id="31e50-117">Type</span><span class="sxs-lookup"><span data-stu-id="31e50-117">Type</span></span>    | <span data-ttu-id="31e50-118">Reciblage</span><span class="sxs-lookup"><span data-stu-id="31e50-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="31e50-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="31e50-119">Affected APIs</span></span>

- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>
